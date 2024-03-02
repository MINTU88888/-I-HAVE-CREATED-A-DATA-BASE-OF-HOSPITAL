# -I-HAVE-CREATED-A-DATA-BASE-OF-HOSPITAL
IN THIS DATABASE I HAVE INSERTED THE INFORMATION OF PATIENTS USING MY SQL 

 CREATE DATABASE hospitial_data;
 use hospitial_data;

  CREATE TABLE patients (
  patient_id INT PRIMARY KEY ,
  first_name VARCHAR(30),
  last_name VARCHAR(40),
  father_name VARCHAR(70),
  mother_name VARCHAR(90),
  age INT,
  phone_number INT
  );

  INSERT INTO patients(patient_id , first_name , last_name , father_name , mother_name , age , phone_number)
  VALUES (1 , 'mintu' , 'rohilla' , 'surender' , 'neelam' , 28 , 798-868-5865),
	  (2 , 'sidhu' , 'mota_bhai' , 'mintu' , 'aarya' , 22 , 702-707-7569);
       
   

   CREATE TABLE medicalhistory (
   history_id INT PRIMARY KEY ,
   surgery VARCHAR(200),
   dector_name VARCHAR(30),
   patient_id INT,
   FOREIGN KEY (patient_id) REFERENCES patients(patient_id)
   );


   INSERT INTO MedicalHistory (history_id, surgery, dector_name, patient_id) 
   VALUES (1, 'bronchoscopy', 'dr_khan', 1), 
       (2, 'Hypertension', 'navi', 1),
       (3, 'cystoscopy', 'dr_khan', 2),
       (4, 'sigmoidoscopy', 'dr_khan', 1);


    CREATE TABLE Staff (
    staff_id INT PRIMARY KEY,
    staff_name VARCHAR(255),
    roles VARCHAR(255),
    department VARCHAR(255),
    experience VARCHAR(230)
    );


   INSERT INTO Staff (staff_id, staff_name, roles, department, experience) 
   VALUES (1, 'John Doe', 'Nurse', 'Emergency', 16), 
       (2, 'Jane Smith', 'Doctor', 'Cardiology', 22),
	     (3, 'jake', 'Nurse', 'opd', 12);
       

    CREATE TABLE Prescriptions (
    prescription_id INT PRIMARY KEY,
    patient_id INT,
    medician_name VARCHAR(255),
    dosage VARCHAR(50),
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id)
   );

  INSERT INTO Prescriptions (prescription_id, patient_id, medician_name, dosage) 
  VALUES (1, 1, 'Aspirin', '100mg'),
	     (2, 1, 'PCM', '80mg'),
       (3, 1, 'dispirin', '200mg'),
       (4, 2, 'Penicillin', '500mg'),
       (5, 2, 'cecko', '400');
      
       
    CREATE TABLE billing (
    billing_id INT PRIMARY KEY,
    patient_id INT,
    amount DECIMAL(10,2),
    amount_status VARCHAR(200),
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id)
    );

   INSERT INTO billing (billing_id, patient_id, amount, amount_status) 
   VALUES (101, 1, 500.00, 'Outstanding'), 
          (102, 2, 1000.00, 'Paid');
      

    CREATE TABLE Wardes (
    ward_id INT PRIMARY KEY,
    ward_name VARCHAR(255),
    total_bed INT,
    available_bed INT
   );


   INSERT INTO wardes(ward_id, ward_name, total_bed, available_bed)
   VALUES(100001, 'Emergency Ward', 300, 104),
      (100002, 'Cardiology Ward', 90, 20),
      (100003, 'opd', 700, 200),
      (100004, 'main_ward', 500, null);


    CREATE TABLE Lab_Tests (
    test_id INT PRIMARY KEY,
    patient_id INT,
    test_type VARCHAR(255),
    test_date DATE,
    result VARCHAR(255),
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id)
    );

    INSERT INTO Lab_Tests(test_id, patient_id, test_type, test_date, result)
    VALUES(1001, 1, 'blood', '2024-03-29', 'good'),
      (1002, 1, 'eye', '2024-02-12', 'bad'),
      (1003, 2, 'eye', '2023-09-04', 'good'),
      (1004, 2, 'blood', '2024-09-08', 'bad');

    CREATE TABLE Emergency_Contacts (
    contact_id INT PRIMARY KEY,
    patient_id INT,
    contacts_name VARCHAR(255),
    phone_number VARCHAR(20),
    patient_relationship VARCHAR(40),
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id)
    );

   INSERT INTO Emergency_Contacts(contact_id, patient_id, contacts_name, phone_number, patient_relationship)
   VALUES(1, 1, 'surender', 7865489309, 'father'),
	    (2,1,'neelam', 8796555587, 'mother'),
      (3,2,'mintu', 7988685865, 'father'),
      (4,2,'aarya', 2323458989, 'mother');
     

    CREATE TABLE Appointments (
    appointment_id INT PRIMARY KEY,
    patient_id INT,
    Appointment_time DATETIME,
    duration INT,
    status VARCHAR(50),
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id)
    );


   INSERT INTO Appointments (appointment_id, patient_id, Appointment_time, duration, status) 
   VALUES (1, 1, '2024-03-05 10:00:00', 60, 'Scheduled'), 
          (2, 2, '2024-03-10 14:00:00', 30, 'Completed');





