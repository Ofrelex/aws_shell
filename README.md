# 5 Essential Skills for Shell Scripting in Cloud Computing

Step-by-step explanation** of the mini project **"5 Essential Skills for Shell Scripting in Cloud Computing"** based on the scenario and requirements:

---

## **Project Objective**:

To learn and apply five essential shell scripting skills (functions, arrays, environment variables, command line arguments, error handling) by building an automated script that provisions AWS infrastructure for a data science use case.

---

## **Understanding the Requirement**

### **Organization**:

**DataWise Solutions** – A data science consulting firm focused on deploying analytical and ML environments.

### **Client**:

An **e-commerce startup** needing a **data science workspace** on **AWS** to:

* Run computations via **EC2 instances**
* Store customer interaction datasets via **S3 buckets**

---

## **What the Script Needs to Do**

We are to write a **shell script** that:

* Automates the **creation of EC2 instances**
* Sets up **S3 buckets**
* Uses **functions** for modularity
* Uses **arrays** to track resources created
* Uses **environment variables** for sensitive config
* Accepts **command line arguments** for flexible input
* Implements **error handling** to deal with AWS CLI issues

---

## **Step-by-Step Process**

### Step 1: **Define the Script Structure**

Break the script into clearly defined sections using **functions**, such as:

* `create_ec2_instance()`
* `create_s3_bucket()`
* `check_resources()`
* `handle_error()`

### Step 2: **Use Environment Variables**

* Store sensitive configs like:

  ```bash
  export AWS_ACCESS_KEY_ID="your_access_key"
  export AWS_SECRET_ACCESS_KEY="your_secret_key"
  export AWS_DEFAULT_REGION="us-west-2"
  ```

### Step 3: **Accept Command Line Arguments**

* Allow flexibility:

  ```bash
  ./deploy.sh t2.micro my-data-bucket
  ```

  In script:

  ```bash
  INSTANCE_TYPE=$1
  BUCKET_NAME=$2
  ```

### Step 4: **Use Arrays to Track Resources**

* Example:

  ```bash
  declare -a CREATED_RESOURCES
  CREATED_RESOURCES+=("EC2 Instance ID")
  CREATED_RESOURCES+=("S3 Bucket Name")
  ```

### Step 5: **Implement Error Handling**

* For every AWS command, check success:

  ```bash
  if [ $? -ne 0 ]; then
    echo "Error creating EC2 instance"
    exit 1
  fi
  ```

### Step 6: **Develop Modular Functions**

Each function encapsulates a specific task:

```bash
create_ec2_instance() {
  # AWS CLI command to launch instance
}

create_s3_bucket() {
  # AWS CLI command to create S3 bucket
}
```

### Step 7: **Build the Main Script Execution Logic**

* Parse arguments
* Call functions in order
* Print summary of created resources

---

## **Expected Deliverables**

1. A **shell script** (e.g., `deploy.sh`) demonstrating all 5 concepts.
2. A brief **README** or documentation explaining:

   * How to run the script
   * What arguments to pass
   * Sample output

---

## **Summary of Technical Concepts Demonstrated**

| Concept                   | Application in Script                                      |
| ------------------------- | ---------------------------------------------------------- |
| **Functions**             | Encapsulate tasks (create EC2, create S3, check status)    |
| **Arrays**                | Store and manage created resources                         |
| **Environment Variables** | Securely pass AWS credentials and configs                  |
| **Command Line Args**     | Customize instance type, bucket name, region, etc.         |
| **Error Handling**        | Ensure script can recover or exit gracefully on AWS errors |

---

## Final Thoughts

This project gives learners real-world experience in:

* Using shell scripting to automate AWS tasks
* Applying clean code practices (modular, reusable, and secure scripting)
* Building deployable solutions for cloud infrastructure
