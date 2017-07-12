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
  <code> virtualenv venv </code>
  <code> . venv/bin/activate </code>
  </li>

  <br>
  
  <li> 
  Install all requirements <br>
  <code> pip install -r requirements.txt </code>
  </li>

  <br>
  
  <li> 
  Collect all static files <br>
  <code> python manage.py collectstatic </code>
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
  <strong> ** only required once to create an eb instance </strong> <br>
  <code> eb init --profile saml </code>
  </li>
   
  <br>
  
  <li> 
  Create and deploy to eb environment <br>
  <strong> ** only required on first deployment </strong> <br>
  <code> eb create </code>
  </li>
   
  <br>
  
  <li> 
  Future deployments to eb environment <br>
  <code> eb deploy </code>
  </li>
</ul>
