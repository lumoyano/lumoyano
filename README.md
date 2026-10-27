<div align="center">

# Lucas Almeida

**Software engineering · Cybersecurity · Infrastructure**

<!-- Replace this introduction with your preferred title, target roles, and short bio. -->
I'm a Software Engineering student at Brigham Young University–Idaho, specializing in Embedded Systems, with a background in cybersecurity, IT infrastructure, and software development.

My interest in technology started with programming at a young age and has grown into a curiosity about how computers, networks, and software work together. I enjoy exploring systems beyond the surface, whether that means developing applications, investigating security incidents, experimenting with hardware, or building my own infrastructure.

I believe some of the best learning happens through experimentation, troubleshooting, and challenging what I think I know. This GitHub is a collection of that process: projects I've built, problems I've worked through, and ideas I'm continuing to explore.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-334155?style=flat)](https://www.linkedin.com/in/lucas-mda/)
[![Email](https://img.shields.io/badge/Email-334155?style=flat&logo=gmail&logoColor=CBD5E1)](mailto:lumoyano10@gmail.com)
[![LeetCode](https://img.shields.io/badge/LeetCode-334155?style=flat&logo=leetcode&logoColor=CBD5E1)](https://leetcode.com/u/lukmda/)

</div>

---

## Engineering in practice

I work across application development, IT infrastructure, and security investigations. My projects focus on connecting systems, managing data, and troubleshooting the details that make software work.

- **Infrastructure:** Developed an on-premises NetBox proof of concept for the City of Rexburg and populated **800+ IPs, 60+ VMs, and 30+ VLANs**, replacing fragmented spreadsheet inventory.
- **Automation:** Migrated **200+ knowledge-base articles** using PowerShell and the Jitbit API, alongside documentation cleanup and revision.
- **Security operations:** Volunteer SOC analyst and Tier 2 mentor using Security Onion, Zeek logs, and PCAP analysis. Analyzed **650,000+ alerts across 60 network IDs** over four months to identify recurring false-positive patterns affecting SCADA monitoring.

**Credentials:** CompTIA Security+ · TCM Practical Security Analyst Associate · BYU–Idaho Cybersecurity Certificate  
**Education:** B.S. Software Engineering, Embedded Systems — anticipated December 2026

---

## Selected projects

### FMB — PostgreSQL product management

**Java · JavaFX · PostgreSQL · JDBC · Jsoup**

A solo desktop application for managing products, categories, and product types. Separates domain models, JavaFX controllers, and data-access classes, with parameterized CRUD operations and scraping utilities for product details and ingredients.

**Engineering focus:** Relational data management, desktop interaction, external-data ingestion, and database troubleshooting.

[Explore FMB](https://github.com/lumoyano/FMB) · [Database implementation](https://github.com/lumoyano/FMB/blob/d3bad226095e9560812bc710cafdf2b4ed4e186b/src/main/java/fmb/serviceData/ProductData.java)

<details>
<summary><strong>Code spotlight — parameterized product updates</strong></summary>

The update binds product values separately from SQL and closes the statement and connection through try-with-resources. This is the original repository implementation.

```java
    @Override
    public void update(Product product) {
        try (Connection db = DriverManager.getConnection(getInstance().URL, getInstance().USERNAME, getInstance().PASSWORD);
                 PreparedStatement statement = db.prepareStatement("UPDATE products SET productname=?, productbrand=?, " +
                         "producttype=?, productcategory=?, ingredients=? WHERE productid=?")) {

            statement.setString(1, product.getProductName());
            statement.setString(2, product.getProductBrand());
            statement.setInt(3, product.getProductType());
            statement.setInt(4, product.getProductCategory());
            statement.setString(5, product.getIngredientsAsString());
            statement.setInt(6, product.getProductID());

            int rowsUpdated = statement.executeUpdate();
            if (rowsUpdated > 0) {
                System.out.println("Product updated successfully.");
            } else {
                System.out.println("Failed to update product.");
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
```

[View source at this revision](https://github.com/lumoyano/FMB/blob/d3bad226095e9560812bc710cafdf2b4ed4e186b/src/main/java/fmb/serviceData/ProductData.java#L123-L145)

</details>

### Blockchain in Java — signatures, persistence, and peers

**Java · Java Cryptography Architecture · SQLite · JDBC · JavaFX · Sockets**

A solo educational implementation based on Spiro Buzharovski’s *Introducing Blockchain with Java*. Integrated block, transaction, and wallet models with persistence, a desktop interface, and background mining and peer communication.

**Troubleshooting spotlight:** Replaced an internal `sun.security` key implementation with standard `KeyFactory` and `X509EncodedKeySpec` handling to reconstruct DSA public keys for signature verification. Worked through JavaFX setup, SQL integration, and service-layer debugging.

[Explore blockchain-personal](https://github.com/lumoyano/blockchain-personal)

<details>
<summary><strong>Code spotlight — reconstructing a key to verify a transaction</strong></summary>

This function decodes the sender’s stored public key, initializes verification, and checks the transaction signature. It illustrates the compatibility fix within an educational implementation.

```java
    public boolean isVerified(Signature signing) throws InvalidKeyException, SignatureException, NoSuchAlgorithmException, InvalidKeySpecException {
        KeyFactory keyFactory = KeyFactory.getInstance("DSA");
        X509EncodedKeySpec keySpec = new X509EncodedKeySpec(this.getFrom());
        signing.initVerify(keyFactory.generatePublic(keySpec));
        signing.update(this.toString().getBytes());
        return signing.verify(this.signature);
    }
```

[View source at this revision](https://github.com/lumoyano/blockchain-personal/blob/a28aa9ee70732537438f08d6e997946fd1ef528f/src/main/model/Transaction.java#L55-L61)

</details>

### Infrastructure and systems experiments

| Project | Implemented focus | Stage |
| :--- | :--- | :--- |
| [SkyHost](https://github.com/lumoyano/skyhost) | FastAPI host-health polling and host selection; QCOW2 template overlays and libvirt VM lifecycle code | Lab prototype |
| [syswatch](https://github.com/lumoyano/syswatch) | Rust CLI for system information, Windows settings checks, and timeout-bounded TCP network probes | Early implementation |

---

## Currently exploring

**REPLAY — controller input telemetry**  
An in-progress senior project investigating repeatable input capture and interpretation for gaming sessions. Current work covers USB/HID traffic investigation, controlled capture experiments, and evaluating Windows GameInput for controller telemetry. Privacy and clear measurement limits guide the work; the collector remains in feasibility evaluation.

**Security and infrastructure lab**  
Ubuntu, Docker, UFW, VPN access, NetBox, and AdGuard DNS, with Splunk Enterprise investigation practice using BOTSv3.

<!-- Add the second private project when its public description is ready. -->

---

## Tools and technologies

![Java](https://img.shields.io/badge/Java-334155?style=flat)
![Python](https://img.shields.io/badge/Python-334155?style=flat&logo=python&logoColor=CBD5E1)
![Rust](https://img.shields.io/badge/Rust-334155?style=flat&logo=rust&logoColor=CBD5E1)
![Kotlin](https://img.shields.io/badge/Kotlin-334155?style=flat&logo=kotlin&logoColor=CBD5E1)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-334155?style=flat&logo=postgresql&logoColor=CBD5E1)
![PowerShell](https://img.shields.io/badge/PowerShell-334155?style=flat)
![Linux](https://img.shields.io/badge/Linux-334155?style=flat&logo=linux&logoColor=CBD5E1)
![Docker](https://img.shields.io/badge/Docker-334155?style=flat&logo=docker&logoColor=CBD5E1)

**Application development:** JavaFX · JDBC · SQLite · Jsoup · FastAPI · REST APIs  
**Security analysis:** Security Onion · Zeek · Splunk · Wireshark · PCAP analysis · Alert triage  
**Infrastructure:** NetBox/IPAM · Windows · Ubuntu · Bash · Git/GitHub

<details>
<summary><strong>Public repository language overview</strong></summary>

<p align="center">
  <a href="https://github.com/lumoyano?tab=repositories">
    <img src="https://github-stats-extended.vercel.app/api/top-langs/?username=lumoyano&layout=compact&langs_count=6&exclude_repo=lumoyano.github.io,BTAPP,Hello-World&bg_color=161B22&title_color=8DB6AD&text_color=CBD5E1&border_color=334155&hide_border=true" alt="Language distribution in selected public repositories" />
  </a>
</p>

Generated by [GitHub Stats Extended](https://github.com/stats-organization/github-stats-extended). Public repository language distribution reflects code volume, not proficiency; the portfolio export, BTAPP, and Hello-World are excluded.

</details>

---

<p align="center">
  <a href="https://www.linkedin.com/in/lucas-mda/">LinkedIn</a> ·
  <a href="mailto:lumoyano10@gmail.com">Email</a> ·
  <a href="https://leetcode.com/u/lukmda/">LeetCode</a>
</p>
