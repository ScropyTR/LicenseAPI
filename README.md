## Maven

[![](https://jitpack.io/v/ScropyTR/LicenseAPI.svg)](https://jitpack.io/#ScropyTR/LicenseAPI)

```pom.xml
<dependency>
    <groupId>com.github.ScropyTR</groupId>
    <artifactId>LicenseAPI</artifactId>
    <version>1.0.5</version>
</dependency>
 
<repository>
    <id>jitpack.io</id>
    <url>https://jitpack.io</url>
</repository>
```

## Setup

```java
    @Override
    public void onEnable() {

        FileConfiguration licenseFile = ConfigUtils.getConfig(this, "license");

        License license = new License(licenseFile.getString("license-key"), this);

        if (license.isValid()) {
            Bukkit.getConsoleSender().sendMessage("License is valid");
            Bukkit.getConsoleSender().sendMessage("License Key : "+license.getLicense());
            Bukkit.getConsoleSender().sendMessage("License Holder : "+license.getLicensedTo());
            Bukkit.getConsoleSender().sendMessage("License Manager : "+license.getGeneratedBy());
            Bukkit.getConsoleSender().sendMessage("Date of License : "+license.getGeneratedIn());

            getCommand("mainGUI").setExecutor(new JoinMessageCMD());
            Bukkit.getServer().getPluginManager().registerEvents(new Events(), this);
        } else {
            Bukkit.getConsoleSender().sendMessage("License is invalid");
            Bukkit.getPluginManager().disablePlugin(this);
        }

    }
```
