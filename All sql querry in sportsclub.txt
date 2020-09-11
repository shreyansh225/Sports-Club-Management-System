
secure_login.php*******************************
$user_id_auth = mysqli_real_escape_string($con, $user_id_auth);
$pass_key     = mysqli_real_escape_string($con, $pass_key);

$sql  = "SELECT * FROM admin WHERE username='$user_id_auth' and pass_key='$pass_key'";

change_s_pwd.php***************************
$sql    = "SELECT * FROM admin WHERE username='$user_id_auth' and securekey='$key'";


admin/del_member.php*****************************
 mysqli_query($con, "DELETE FROM users WHERE userid='$msgid'");

admin/del_plan.php****************************
mysqli_query($con, "update plan set active ='no' WHERE pid='$msgid'");


admin/deleteroutine.php****************************
mysqli_query($con, "DELETE FROM sports_timetable WHERE tid='$msgid'");


admin/edit_mem_submit.php**************************
 $query1="update users set username='".$uname."',gender='".$gender."',mobile='".$mobile."',email='".$email."',dob='".$dob."',joining_date='".$jdate."' where userid='".$uid."'";

   if(mysqli_query($con,$query1))
   {
     $query2="update address set streetName='".$stname."',state='".$state."',city='".$city."',zipcode='".$zipcode."' where id='".$uid."'";
     if(mysqli_query($con,$query2)){
        $query3="update health_status set calorie='".$calorie."',height='".$height."',weight='".$weight."',fat='".$fat."',remarks='".$remarks."' where uid='".$uid."'";

admin/edit_member.php*****************************************
 $query  = "SELECT * FROM users u 
 			INNER JOIN address a ON u.userid=a.id
			INNER JOIN  health_status h ON u.userid=h.uid
			WHERE userid='$memid'";

admin/edit_plan.php*********************************************
$id=$_GET['id'];
		$sql="Select * from plan t Where t.pid=$id";

admin/editdetailroutine.php*****************************************
$id=$_GET['id'];
		$sql="Select * from sports_timetable t Where t.tid=$id";

admin/editroutine.php***********************************************
$query  = "select * from sports_timetable";

admin/get_invoice.php*******************************************************
$sql = "Select * from users u INNER JOIN enrolls_to e ON u.userid=e.uid INNER JOIN plan p where p.pid=e.pid and userid='".$uid."' and e.et_id='".$etid."'";
	$res=mysqli_query($con, $sql);
	 if($res){
	$row=mysqli_fetch_array($res,MYSQLI_ASSOC);


admin/health_status_entry.php*****************************************************
$query="update health_status set calorie='".$calorie."', height='".$height."',weight='".$weight."',fat='".$fat."',remarks='".$remarks."' where uid='".$userid."'";

$sql="select * from health_status where uid='".$uid."'";



admin/income_month.php********************************************
$month=$_GET['mm'];
$year=$_GET['yy'];

$query="select DISTINCT u.userid,u.username,u.gender,u.mobile,
u.email,u.joining_date,a.state,a.city,
e.paid_date,e.expire,p.planName,p.amount,p.validity from users u 
INNER JOIN address a on u.userid=a.id 
INNER JOIN enrolls_to e on u.userid=e.uid
INNER JOIN plan p on p.pid=e.pid
where e.paid_date  like '".$year."-".$month."___'";


admin/make_payment.php*************************************************
$uid  = $_POST['userID'];
$planid=$_POST['planID'];
		$query1 = "select * from users WHERE userid='$uid'";
$name = $row1['username'];
		$query2="select * from plan where pid='$planid'";


ADMIN/index.php*******************************************************************************************************
<h2>Paid Income This Month</h2><br>	
date_default_timezone_set("Asia/Calcutta"); 
	$date  = date('Y-m');
	$query = "select * from enrolls_to WHERE  paid_date LIKE '$date%'";


while ($row = mysqli_fetch_array($result, MYSQLI_ASSOC)) {
	$query1="select * from plan where pid='".$row['pid']."'";
	$result1=mysqli_query($con,$query1);

<h2>Total <br>Members</h2><br>
query = "select COUNT(*) from users";

<h2>Joined This Month</h2><br>
date_default_timezone_set("Asia/Calcutta"); 
	$date  = date('Y-m');
	$query = "select COUNT(*) from users WHERE joining_date LIKE '$date%'";

<h2>Total Plan Available</h2><br>	
	<?php
	$query = "select COUNT(*) from plan where active='yes'";



admin/make_payment.php***************************************
$uid  = $_POST['userID'];
    $planid=$_POST['planID'];
    $query1 = "select * from users WHERE userid='$uid'";

$name = $row1['username'];
    $query2="select * from plan where pid='$planid'";


<td height="35"><select name="plan" id="boxx" required onchange="myplandetail(this.value)">
	<option value=""> - Please select - </option>
	<?php
	$query = "select * from plan where active='yes'";


admin/more_userprofile.php**********************************************
$usrname=$_POST['login_id'];
 $fulname=$_POST['full_name'];
 $query="update admin set username='".$usrname."',Full_name='".$fulname."' where username='".$_SESSION['full_name']."'";


admin/new 1.php*******************************************************
$query  = "select * from enrolls_to where renewal='yes' ORDER BY expire";

$query1  = "select * from users WHERE userid='$uid'";



admin/new_entry.php*************************************************
$query="select * from plan where active='yes'";


admin/new_health_status.php**********************************************
$query  = "select * from users ORDER BY joining_date";

 $query1  = "select * from enrolls_to WHERE uid='$uid' AND renewal='yes'";


ADMIN/new_submit.php**************************************************************************************************************
//inserting into users table
$query="insert into users(username,gender,mobile,email,dob,joining_date,userid) values('$uname','$gender','$phn','$email','$dob','$jdate','$memID')";

//Retrieve information of plan selected by user
      $query1="select * from plan where pid='$plan'";

//inserting into enrolls_to table of corresponding userid
          $query2="insert into enrolls_to(pid,uid,paid_date,expire,renewal) values('$plan','$memID','$cdate','$expiredate','yes')";

 $query4="insert into health_status(uid) values('$memID')";
  $query5="insert into address(id,streetName,state,city,zipcode) values('$memID','$stname','$state','$city','$zipcode')";

//Deleting record of users if inserting to enrolls_to table failed to execute
    $query3 = "DELETE FROM users WHERE userid='$memID'";


//Deleting record of users if inserting to enrolls_to table failed to execute
     $query3 = "DELETE FROM users WHERE userid='$memID'";

//Deleting record of users if inserting to enrolls_to table failed to execute
    $query3 = "DELETE FROM users WHERE userid='$memID'";

//Deleting record of users if retrieving inf of plan failed
          $query3 = "DELETE FROM users WHERE userid='$memID'";


admin/over_month.php***********************************************************
if($flag==0)
	$query="select * from users u INNER JOIN address a on u.userid=a.id where u.joining_date like '".$year."-".$month."___'";
else if($flag==1)
	$query="select * from users u INNER JOIN address a on u.userid=a.id where u.joining_date like '".$year."______'";


admin/payment.php*****************************************************
	$query  = "select * from enrolls_to where renewal='yes' ORDER BY expire";

$uid   = $row['uid'];
$planid=$row['pid'];
$query1  = "select * from users WHERE userid='$uid'";



admin/plandetail.php***********************************************
$pid=$_GET['q'];
$query="select * from plan where pid='".$pid."'";



admin/read_member.php************************************************************
$id     = $_POST['name'];
		$query  = "select * from users WHERE userid='$id'";





admin/saveroutine.php**************************************************
$rname=$_POST["rname"];
		$day1=$_POST["day1"];
		$day2=$_POST["day2"];
		$day3=$_POST["day3"];
	    $day4=$_POST["day4"];
		$day5=$_POST["day5"];
		$day6=$_POST["day6"];
		$pid=$_POST["pidd"];
		
		
		$sql="insert into sports_timetable(tname,day1,day2,day3,day4,day5,day6,pid) values('$rname','$day1','$day2','$day3','$day4','$day5','$day6','$pid')";


ADMIN/submit_payment.php*******************************************************************************
//updating renewal from yes to no from enrolls_to table
$query="update enrolls_to set renewal='no' where uid='$memID'";

//inserting new payment data into enrolls_to table
      $query1="select * from plan where pid='$plan'";

 //inserting into enrolls_to table of corresponding userid
          $query2="insert into enrolls_to(pid,uid,paid_date,expire,renewal) values('$plan','$memID','$cdate','$expiredate','yes')";


admin/submit_plan_new.php*******************************************
//Inserting data into plan table
    $query="insert into plan(pid,planName,description,validity,amount,active) values('$planid','$name','$desc','$planval','$amount','yes')";



admin/table_view.php********************************************
$query  = "select * from users ORDER BY joining_date";

$uid   = $row['userid'];
 $query1  = "select * from enrolls_to WHERE uid='$uid' AND renewal='yes'";



admin/updateplan.php***********************************************
$query1="update plan set planName='".$pname."',description='".$pdesc."',validity='".$pval."',amount='".$pamt."' where pid='".$id."'";


admin/updateroitine.php************************************************
$query1="update timetable set day1='".$day1."',day2='".$day2."',day3='".$day3."',day4='".$day4."',day5='".$day5."',day6='".$day6."' where tid=".$id."";


admin/view_eme.php**********************************************
$query  = "select * from users ORDER BY joining_date";

$query1  = "select * from enrolls_to WHERE uid='$uid' AND renewal='yes'";



admin/view_plan.php*********************************************
$query  = "select * from plan where active='yes' ORDER BY amount DESC";


admin/viewall_detail.php*****************************************************
<h3>Edit Member Details</h3>
$query  = "SELECT * FROM users u 
		INNER JOIN address a ON u.userid=a.id
		INNER JOIN  health_status h ON u.userid=h.uid
		INNER JOIN enrolls_to e on u.userid=e.uid
		INNER JOIN plan p on e.pid=p.pid
		WHERE userid='$memid' and e.renewal='yes'";


admin/viewdetailroutine.php**************************************
$id=$_GET['id'];
		$sql="Select * from sports_timetable t Where t.tid=$id";


admin/viewroutine.php***************************************
$query  = "select * from sports_timetable";