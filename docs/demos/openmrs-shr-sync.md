# Synchronization of Clinical Data 

## Synchronization of Patient Data
This tutorial demonstrates the FHIR-based synhronization of patient data between iSantePlus instances. 

The demonstrated communication workflow involves the following components:
 - a **Master Patient Index (MPI)**
 - a **Shared Health Record (SHR)**
 - and two instances of **iSantePlus**

The communication between these systems utilizes the FHIR clinical data standard for representing clinical data, and is orchestrated by the [OpenHIM](http://openhim.org/) middleware. 

### Import existing Patient
For the first part of this tutorial, we will be using the patient `Rafael Lessai`. This patient was created in the iSantePlus instance available at www.isanteplusdemo.com/openmrs, but does not exist in the instance at http://52.37.13.123:8080/openmrs. 

To start, we will import this patient in the second iSantePlus instance, review the Continuity of Care document (CCD) for the patient,
add some additional clinical data, and see this information represented in the CCD of the original instance.

**I) Review Patient data in isanteplusdemo.com**
1. 

**II) Import Patient in Another Location**
1. Log into http://52.37.13.123:8080/openmrs/
2. Click `Register a Patient`
3. Begin typing in the names of the patient you created in step `I`
4. You should see a pop-up show up at the top of the screen with existing patient suggestions. 
5. Click on the `View suggestions` button
6. You should see your patient


### Create a new Patient

**I) Create a Patient**
1. Log into https://isanteplusdemo.com/openmrs
2. Click `Register a Patient`
3. Fill in all of the required patient information and `Confirm` to create the patient.
4. On the patient chart screen, note the `patientId` in the url bar. 

**II) (Optional) View Patient in OpenCR**
1. Log into http://18.158.139.243:3000/crux/#/Login
2. Search for your created patient by `Surname` to find the entry.



**III) (Optional) View Patient in SHR**
1. Wait a minute or so, and navigate to http://18.158.139.243:8092/hapi-fhir-jpaserver
2. Choose `Patient` from the left-hand `Resources` navigation.
3. Check the `Reverse includes` checkbox on the bottom of the screen.
4. Search by `name` OR by `_id` (using the noted uuid from above) 

**IV) Import Patient in Another Location**
1. Log into http://52.37.13.123:8080/openmrs/
2. Click `Register a Patient`
3. Begin typing in the names of the patient you created in step `I`
4. You should see a pop-up show up at the top of the screen with existing patient suggestions. 
5. Click on the `View suggestions` button
6. You should see your patient

**V) Create a bit of medical history**
Log back into https://isanteplusdemo.com/openmrs and add a bit of medical history to the patient:

1. Vital Signs

2. Allergies
    -
3. Immunization

4. Medications

5. Laboratory Orders
    
**VI) View Medical History as CCD Document**
1. Go back to http://52.37.13.123:8080/openmrs/

2. Find your patient and navigate to their chart

3. Click on `Registration Summary` in the right-hand `General Actions` sidebar.

4. Look for the `Continuity of Care` section and click the `Import` button.

5. Click on `Registration Summary` again, and then on the `View` button in the `Continuity of Care` section


## Appendix

### Login Information

#### iSantePlus

**iSantePlus Instance #1**  
https://isanteplusdemo.com/openmrs

**iSantePlus Instance #2**  
http://52.37.13.123:8080/openmrs/

**Login Info**
- user: admin
- password: Admin123

#### OpenHIM Console  
http://18.158.139.243:3001/

**Login Info**
- user: root@openhim.org
- password: Haiti1234

#### OpenCR Console
http://18.158.139.243:3000/crux/#/Login

**Login Info**
- user: root@intrahealth.org
- password: intrahealth

### Utilized Tools and Modules
- https://openmrs.org/
- https://github.com/pmanko/openmrs-module-fhir2/tree/FM2-303-isanteplus-compatibility
- https://github.com/pmanko/atomfeed/tree/db-url-port-fix
- https://github.com/pmanko/openmrs-module-atomfeed/tree/isanteplus-fixes
- https://github.com/pmanko/openmrs-fhir-analytics/tree/isanteplus-local-sync
- https://github.com/pmanko/openmrs-module-mpi-client/tree/openmrs-fhir-module
- https://github.com/pmanko/openmrs-module-xds-sender/tree/1-fhir-shr
- https://github.com/stansL/openmrs-module-registrationcore/tree/integrate_ocr_fhir_search-