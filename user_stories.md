# User Stories

---

## Admin User Stories

**Title:** Admin Login  
_As an admin, I want to log into the portal with my username and password, so that I can manage the platform securely._  

**Acceptance Criteria:**  
1. Login requires valid username and password.  
2. Incorrect credentials are rejected with an error message.  
3. On success, admin is redirected to the dashboard.  

**Priority:** High  
**Story Points:** 3  
**Notes:** –  

---

**Title:** Admin Logout  
_As an admin, I want to log out of the portal, so that I can protect system access._  

**Acceptance Criteria:**  
1. Logout option is available on all admin pages.  
2. Clicking logout ends the session.  
3. User is redirected to the login page.  

**Priority:** High  
**Story Points:** 2  
**Notes:** –  

---

**Title:** Add Doctor Profile  
_As an admin, I want to add doctors to the portal, so that they can manage appointments and patient data._  

**Acceptance Criteria:**  
1. Admin can enter doctor details (name, specialty, contact info).  
2. Doctor profile is saved in the database.  
3. Doctor receives login credentials.  

**Priority:** High  
**Story Points:** 5  
**Notes:** Doctor ID must be unique.  

---

**Title:** Delete Doctor Profile  
_As an admin, I want to delete a doctor’s profile from the portal, so that I can remove inactive or incorrect records._  

**Acceptance Criteria:**  
1. Admin can select a doctor to delete.  
2. Confirmation prompt is displayed before deletion.  
3. Doctor is removed from the database.  

**Priority:** Medium  
**Story Points:** 3  
**Notes:** Deletion should not break linked appointments.  

---

**Title:** Run Usage Report in MySQL  
_As an admin, I want to run a stored procedure in MySQL CLI to get the number of appointments per month, so that I can track usage statistics._  

**Acceptance Criteria:**  
1. Stored procedure retrieves total appointments per month.  
2. Output is displayed in CLI.  
3. Report matches database records.  

**Priority:** Medium  
**Story Points:** 8  
**Notes:** Ensure procedure runs with proper admin privileges.  

---

## Patient User Stories

**Title:** View Doctors List  
_As a patient, I want to view a list of doctors without logging in, so that I can explore options before registering._  

**Acceptance Criteria:**  
1. Doctors list is visible to unauthenticated users.  
2. List shows doctor name, specialty, and availability.  
3. Patients are prompted to sign up to book.  

**Priority:** Medium  
**Story Points:** 3  
**Notes:** Should not expose sensitive doctor data.  

---

**Title:** Patient Registration  
_As a patient, I want to sign up using my email and password, so that I can book appointments._  

**Acceptance Criteria:**  
1. Registration requires unique email.  
2. Password must meet security rules.  
3. Successful registration logs the patient in.  

**Priority:** High  
**Story Points:** 5  
**Notes:** Email confirmation optional.  

---

**Title:** Patient Login  
_As a patient, I want to log into the portal, so that I can manage my bookings._  

**Acceptance Criteria:**  
1. Login requires valid email and password.  
2. Invalid credentials return an error.  
3. On success, patient dashboard is displayed.  

**Priority:** High  
**Story Points:** 3  
**Notes:** Session timeout after inactivity.  

---

**Title:** Patient Logout  
_As a patient, I want to log out of the portal, so that I can secure my account._  

**Acceptance Criteria:**  
1. Logout button is available on all pages.  
2. Logging out ends the session.  
3. Redirect to login/home page.  

**Priority:** High  
**Story Points:** 2  
**Notes:** –  

---

**Title:** Book Appointment  
_As a patient, I want to log in and book an hour-long appointment, so that I can consult with a doctor._  

**Acceptance Criteria:**  
1. Patients can select a doctor and available time slot.  
2. Appointment is saved in the system.  
3. Confirmation is shown after booking.  

**Priority:** High  
**Story Points:** 8  
**Notes:** Appointment duration fixed at 1 hour.  

---

**Title:** View Upcoming Appointments  
_As a patient, I want to view my upcoming appointments, so that I can prepare accordingly._  

**Acceptance Criteria:**  
1. List of upcoming appointments is shown in the dashboard.  
2. Each entry shows date, time, and doctor.  
3. Canceled appointments are not listed.  

**Priority:** Medium  
**Story Points:** 3  
**Notes:** Include pagination if list is long.  

---

## Doctor User Stories

**Title:** Doctor Login  
_As a doctor, I want to log into the portal, so that I can manage my appointments._  

**Acceptance Criteria:**  
1. Login requires valid doctor credentials.  
2. Invalid credentials return an error.  
3. On success, doctor dashboard is displayed.  

**Priority:** High  
**Story Points:** 3  
**Notes:** Secure authentication required.  

---

**Title:** Doctor Logout  
_As a doctor, I want to log out of the portal, so that I can protect my data._  

**Acceptance Criteria:**  
1. Logout option available on all pages.  
2. Logging out ends the session.  
3. Redirect to login page.  

**Priority:** High  
**Story Points:** 2  
**Notes:** –  

---

**Title:** View Appointment Calendar  
_As a doctor, I want to view my appointment calendar, so that I can stay organized._  

**Acceptance Criteria:**  
1. Calendar shows all upcoming appointments.  
2. Each appointment displays patient name and time.  
3. Supports daily, weekly, and monthly views.  

**Priority:** High  
**Story Points:** 5  
**Notes:** Integrate with appointment repository.  

---

**Title:** Mark Unavailability  
_As a doctor, I want to mark my unavailability, so that patients can only book available slots._  

**Acceptance Criteria:**  
1. Doctor can block out specific times.  
2. Blocked times are not shown to patients.  
3. Existing appointments are unaffected.  

**Priority:** High  
**Story Points:** 5  
**Notes:** Sync with booking logic.  

---

**Title:** Update Profile  
_As a doctor, I want to update my profile with specialization and contact info, so that patients have up-to-date information._  

**Acceptance Criteria:**  
1. Doctor can edit profile fields (specialization, phone, email).  
2. Updates are saved in the database.  
3. Patients see the updated information.  

**Priority:** Medium  
**Story Points:** 3  
**Notes:** Ensure only authenticated doctor can update.  

---

**Title:** View Patient Details  
_As a doctor, I want to view the patient details for upcoming appointments, so that I can be prepared._  

**Acceptance Criteria:**  
1. Appointment details show patient name, age, and reason for visit.  
2. Patient medical history (if available) is displayed.  
3. Data is read-only for doctors.  

**Priority:** Medium  
**Story Points:** 5  
**Notes:** Respect patient privacy (only show necessary info).  
