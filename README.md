<h2> Pivot on AWS Elastic Beanstalk </h2>

<h3> Setup </h3>

<ul>
  <li> 
  Clone the repository <br>
  <code> git clone https://github.com/abztrakt/pivot-on-eb.git </code>
  </li>

  <br>
  
  <li> 
  Navigate to the Project Root <br>
  <code> cd pivot-on-eb </code>
  </li>

  <br>
  
  <li> 
  Create and activate a virtual env <br>
  <code> virtualenv venv </code> <br>
  <code> . venv/bin/activate </code>
  </li>

  <br>
  
  <li> 
  Install all requirements <br>
  <code> pip install -r requirements.txt </code>
  </li>
  
  <br>
  
  <li> 
  Create .htpasswd file for BASIC AUTH on server <br>
  <code> htpasswd -c ./.htpasswd username password </code>
  </li>
</ul>

<h3> Deployment </h3>

<ul>
  <li> 
  Authenticate (This is unique to UW federated login, if you're just using an IAM user you can skip this step) <br>
  <code> awslogin </code>
  </li>
   
  <br>
  
  <li> 
  Initialize the eb cli (The saml profile is unique to UW federated login) <br>
  <strong> ** only required once to create an eb application </strong> <br>
  <code> eb init --profile saml </code>
  </li>
   
  <br>
  
  <li> 
  Create and deploy to eb environment <br>
  <strong> ** only required on first deployment </strong> <br>
  <strong> * since we have not commited htpasswd, this step should fail; perform a staged deploy next. </strong> <br>
  <code> eb create </code>
  </li>
   
  <br>
  
  <li> 
  Future deployments to eb environment <br>
  <code> eb deploy </code>
  </li>
</ul>

<h3> FAQ's </h3>

<ul>
  <li> 
  How do I fix 'attempt to write a readonly database'? <br>
  <code> eb ssh </code> <br>
  <code> cd /opt/python/current/app </code> <br>
  <code> sudo su </code> <br>
  <code> chown wsgi:root db.sqlite3 </code> 
  
  </li>
   
  <br>
  
  <li> 
  How do I perform a staged deploy or deploy uncommited changes? <br>
  <code> git add --all </code> <br>
  <code> eb deploy --staged </code>
  
  </li>
   
  <br>
  
  <li> 
  How do I run management commands from eb console? <br>
  <pre>To run manage.py commands from eb console: 
  <a href= 'https://stackoverflow.com/questions/19997343/run-manage-py-from-aws-eb-linux-instance'>https://stackoverflow.com/questions/19997343/run-manage-py-from-aws-eb-linux-instance</a></pre>

  </li>
</ul>
