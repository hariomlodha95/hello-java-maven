# Run a Simple Java Maven Build Job in Jenkins

## 🎯 Objective

Use Jenkins to build a simple Java application using Maven — your first step into CI/CD.

---

## 🛠 Tools Required (All Free)

* **Jenkins** (locally installed or via Docker)
* **Java JDK 8 or 11**
* **Maven**
* **Git** (optional)

---

## 📦 Deliverables

* A basic Java **HelloWorld** application (`pom.xml` included)
* Jenkins Freestyle job for Maven build
* Screenshot of successful build showing **BUILD SUCCESS**

---

## 📁 Project Structure (hello-java-maven)

```
hello-java-maven/
│
├── pom.xml
└── src/
    └── main/
        └── java/
            └── HelloWorld.java
```

---

### 1️⃣ Create Java Application

`src/main/java/HelloWorld.java`

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}
```

---

### 2️⃣ Create pom.xml

`pom.xml`

```xml
<project>
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>hello</artifactId>
    <version>1.0</version>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

---

## 🚀 3️⃣ Start Jenkins (Docker Recommended)

Run Jenkins using Docker:

```bash
docker run -p 8080:8080 jenkins/jenkins:lts
```

Open Jenkins UI:
**[http://localhost:8080](http://localhost:8080)**

---

## 🔧 4️⃣ Configure Maven in Jenkins

Jenkins UI:

* **Manage Jenkins → Global Tool Configuration → Maven**
* Add Maven

  * Name: `Maven-3.8.6`
  * Install Automatically: ✔️

---

## 🏗️ 5️⃣ Create Jenkins Freestyle Job

1. Jenkins Dashboard → **New Item**
2. Select **Freestyle Project**
3. Name it: `hello-java-maven-build`
4. **Source Code Management**

   * Add Git repo OR skip and use local path
5. **Build Section → Add Build Step**

   * Select: **Invoke top-level Maven targets**
   * Goals:

```
clean package
```

---

## ▶️ 6️⃣ Run the Build

Click **Build Now** and open **Console Output**.

Expected result:

```
[INFO] BUILD SUCCESS
```

✔️ Your Java Maven project has been successfully built using Jenkins!

