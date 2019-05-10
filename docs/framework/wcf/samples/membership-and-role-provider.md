---
title: Členství a poskytovatel rolí
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 73084bb766274d6eab497555e82e029f94be0359
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638402"
---
# <a name="membership-and-role-provider"></a>Členství a poskytovatel rolí
Zprostředkovatel členství a rolí ukázka demonstruje, jak můžete použít službu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství a rolí k ověřování a autorizaci klientů.  
  
 V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Vzorek ukazuje, jak:  
  
- Klient může ověřit pomocí kombinace uživatelského jména hesla.  
  
- Server můžete ověřit přihlašovací údaje klienta proti [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství.  
  
- Na serveru, lze ověřit pomocí certifikátu X.509 serveru.  
  
- Server můžete namapovat ověřený klient do role pomocí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí.  
  
- Server můžete použít `PrincipalPermissionAttribute` pro řízení přístupu k určité metody, které jsou vystaveny službou.  
  
 Zprostředkovatele členství a role jsou nakonfigurovány pro použití úložiště se opírá o systému SQL Server. Připojovací řetězec a různé možnosti jsou uvedeny v konfiguračním souboru služby. Zprostředkovatel členství je označen názvem `SqlMembershipProvider` při zprostředkovatele rolí je označen názvem `SqlRoleProvider`.  
  
```xml  
<!-- Set the connection string for SQL Server -->  
<connectionStrings>  
  <add name="SqlConn"   
       connectionString="Data Source=localhost;Integrated Security=SSPI;Initial Catalog=aspnetdb;" />  
</connectionStrings>  
  
<system.web>  
  <!-- Configure the Sql Membership Provider -->  
  <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
    <providers>  
      <clear />  
      <add   
        name="SqlMembershipProvider"   
        type="System.Web.Security.SqlMembershipProvider"   
        connectionStringName="SqlConn"  
        applicationName="MembershipAndRoleProviderSample"  
        enablePasswordRetrieval="false"  
        enablePasswordReset="false"  
        requiresQuestionAndAnswer="false"  
        requiresUniqueEmail="true"  
        passwordFormat="Hashed" />  
    </providers>  
  </membership>  
  
  <!-- Configure the Sql Role Provider -->  
  <roleManager enabled ="true"   
               defaultProvider ="SqlRoleProvider" >  
    <providers>  
      <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
    </providers>  
  </roleManager>  
</system.web>  
```  
  
 Služba poskytuje jeden koncový bod pro komunikaci se službou, která je definována pomocí konfiguračního souboru Web.config. Koncový bod se skládá z adresy, vazby a kontrakt. Je vazba konfigurována se standardní `wsHttpBinding`, která ve výchozím nastavení používá ověřování Windows. Tato ukázka nastaví standardní `wsHttpBinding` ověřování uživatelského jména. Chování Určuje, že certifikát serveru se bude používat pro ověřování služby. Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) konfiguračního prvku. Kromě toho chování Určuje, že ověřování uživatelského jména hesla páry provádí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství a rolí mapování se provádí pomocí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí tak, že zadáte názvy definované pro dva poskytovatelé.  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Set up a binding that uses Username as the client credential type -->  
      <binding>  
        <security mode ="Message">  
          <message clientCredentialType ="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!-- Configure role based authorization to use the Role Provider -->  
        <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                              roleProviderName ="SqlRoleProvider" />  
        <serviceCredentials>  
          <!-- Configure user name authentication to use the Membership Provider -->  
          <userNameAuthentication userNamePasswordValidationMode ="MembershipProvider"   
                                  membershipProviderName ="SqlMembershipProvider"/>  
          <!-- Configure the service certificate -->  
          <serviceCertificate storeLocation ="LocalMachine"   
                              storeName ="My"   
                              x509FindType ="FindBySubjectName"  
                              findValue ="localhost" />  
        </serviceCredentials>  
        <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
        <serviceDebug includeExceptionDetailInFaults="false" />  
        <serviceMetadata httpGetEnabled="true"/>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Při spuštění ukázky klient volá různé operace služby do dvou různých uživatelských účtů: Alici, Roberta a Karel. Operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Všechny čtyři volání provedli jako uživatel "Alice" uspěli. Uživatel "Bob" by měl získat chybu při pokusu o volání metody dělení odepření přístupu. Uživatel "Karel" by měl získat chybu při pokusu o volání odepření přístupu vynásobí metody. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
2. Ujistěte se, že jste nakonfigurovali [databáze aplikačních služeb ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    >  Pokud používáte systém SQL Server Express Edition, je název vašeho serveru. \SQLEXPRESS. Tento server by měl při konfiguraci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] databáze služeb aplikací stejně jako v souboru Web.config připojovací řetězec.  
  
    > [!NOTE]
    >  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Účet pracovního procesu musí mít oprávnění databáze, která se vytvoří v tomto kroku. K tomu použijte nástroj sqlcmd nebo SQL Server Management Studio.  
  
3. Ke spuštění ukázky v konfiguraci s jedním nebo více počítači, použijte následující pokyny.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1. Ujistěte se, že cesta obsahuje složku, kde je umístěn Makecert.exe.  
  
2. Spusťte Setup.bat z instalační složky s ukázkou v příkazovém řádku pro vývojáře pro sadu Visual Studio spusťte s oprávněními správce. Tím se nainstaluje služba certifikáty požadované ke spuštění ukázky.  
  
3. Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
4. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1. Vytvoření adresáře na počítači se službou. Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).  
  
2. Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Také kopírovat soubory Setup.bat GetComputerName.vbs a Cleanup.bat k počítači služby.  
  
3. Vytvoření adresáře v klientském počítači pro binární soubory klienta.  
  
4. Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.  
  
5. Na serveru, otevřete příkazový řádek vývojáře pro sadu Visual Studio s oprávněními správce a spusťte `setup.bat service`. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6. Upravit soubor Web.config tak, aby odrážely nový název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), což je stejné jako plně kvalifikovaný název domény počítače.  
  
7. Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8. V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.  
  
9. V klientském počítači otevřete příkazový řádek vývojáře pro sadu Visual Studio s oprávněními správce a spusťte ImportServiceCert.bat. To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
10. Na klientském počítači spusťte Client.exe z příkazového řádku. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
- Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
> [!NOTE]
>  Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích. Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>Instalační dávkový soubor  
 Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace v místním prostředí, která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.  
  
 Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v odpovídající konfiguraci.  
  
- Vytváří se certifikát serveru.  
  
     Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít. % Proměnná % název_serveru Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. Tento dávkový soubor výchozí hodnota je localhost.  
  
     Certifikát je uložen v úložišti (osobních) v části umístění úložiště LocalMachine.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.  
  
     Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
