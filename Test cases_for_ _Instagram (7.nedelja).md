### **1\. Test Case – Instagram**

**Test Case 1: Successfully uploading a photo to profile**  
 **Title:** TC\_IG\_01 – Uploading a photo to Instagram profile

**Preconditions:**

* The user is logged into their Instagram account

* The user must grant permission for Instagram to access the camera/gallery

* The user must have at least one photo in the gallery folder

**Steps:**

1. Click the button to create a new post (+)

   * **Expected Result:** The phone's gallery opens

2. Select a photo from the phone gallery

   * **Expected Result:** The photo is selected

3. Click "Next"

   * **Expected Result:** The image filter tool is displayed

4. Click "Next" again

   * **Expected Result:** The post description tool is displayed

5. Click the "Share" button

**Expected Result:**  
 The photo is successfully uploaded

---

### **2\. Test Case 2: Sending a message via Instagram Direct**

**Title:** TC\_IG\_02 – Sending a direct message

**Preconditions:**

* The user is logged in

* The user has access to Instagram Direct

* The user has at least one contact to whom they can send a direct message

**Steps:**

1. Click the message icon (top right)

2. Select a contact from the list

3. Enter message text

4. Click the "Send" button

**Expected Result:**  
 The message is successfully sent and displayed in the conversation window

---

### **3\. Bug Report Example – Instagram**

**Bug ID:** BUG\_IG\_01

**Title:** Instagram app crashes when attempting to upload a Story with a GIF

**Environment:**

* App version: Instagram 325.0.0.20.170

* Operating System: Android 15

* Device model: Samsung Galaxy S22 Ultra

**Priority:** High  
 **Severity:** Critical

**Precondition:**  
 The user is logged into their Instagram account

**Steps to Reproduce:**

1. Click the option to create a new Story

2. Select an image from the gallery

3. Add a GIF over the image

4. Click "Your Story" to post

**Expected Result:**  
 The Story is successfully uploaded with the GIF

**Actual Result:**  
 The app crashes after clicking "Your Story"

**Note:**  
 The issue is reproducible in 4 out of 4 attempts

