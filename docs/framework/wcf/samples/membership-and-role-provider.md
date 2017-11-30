---
title: "Členství a poskytovatel rolí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2107c5ae03330eb82567ab483dcd7003a35e189
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="membership-and-role-provider"></a>Členství a poskytovatel rolí
Ukázka členství a poskytovatel rolí ukazuje, jak můžete použít službu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství a rolí k ověřování a autorizaci klientů.  
  
 V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Ukázka ukazuje, jak:  
  
-   Klienta můžete ověřit pomocí kombinace hesla uživatelské jméno.  
  
-   Server můžete ověřit pověření klienta vůči [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství.  
  
-   Server lze ověřit pomocí certifikátu X.509 serveru.  
  
-   Server můžete namapovat ověřeného klienta do role pomocí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí.  
  
-   Server můžete použít `PrincipalPermissionAttribute` pro řízení přístupu k některé metody, které jsou zveřejněné službou.  
  
 Zprostředkovatele členství a role jsou nakonfigurovány pro použití úložiště zajišťoval podporu systému SQL Server. Připojovací řetězec a různé možnosti jsou určené v konfiguračním souboru služby. Zprostředkovatel členství je zadaný název `SqlMembershipProvider` při zprostředkovatele rolí je zadaný název `SqlRoleProvider`.  
  
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
  
 Službu zpřístupní jeden koncový bod pro komunikaci se službou, která je definovaná pomocí konfiguračního souboru Web.config. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s standardní `wsHttpBinding`, který ve výchozím nastavení používá ověřování systému Windows. Tato ukázka nastaví standardní `wsHttpBinding` používat ověřování uživatelského jména. Chování Určuje, zda má být použit pro ověřování služby je certifikát serveru. Certifikát serveru musí obsahovat stejné hodnoty `SubjectName` jako `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) konfigurační prvek. Kromě chování Určuje, že ověřování hesla uživatelské jméno páry provádí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství a role mapování provádí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí tak, že zadáte názvy definované pro dva poskytovatelé.  
  
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
  
 Při spuštění vzorového klienta volá různých operací služby v části tři různé uživatelské účty: Alici, Roberta a Karel. Operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Všechny čtyři volání jako uživatel, že by měl být úspěšné "Alice". Uživatel "Bob" měli obdržet chybu při pokusu o volání metody dělení odepření přístupu. Uživatel "Karel" měli získat chybu při pokusu o volání odepření přístupu násobení metoda. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
2.  Ujistěte se, že jste nakonfigurovali [databáze aplikačních služeb ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    >  Pokud používáte systém SQL Server Express Edition, je název serveru. \SQLEXPRESS. Tento server se musí použít při konfiguraci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikační služby databáze také jako připojovací řetězec souboru Web.config.  
  
    > [!NOTE]
    >  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Účet pracovního procesu musí mít oprávnění v databázi, který se vytvoří v tomto kroku. K tomu použijte nástroj sqlcmd nebo SQL Server Management Studio.  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, použijte následující pokyny.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Ujistěte se, že cesta obsahuje složku, kde je umístěna Makecert.exe.  
  
2.  Spuštění Setup.bat od vzorku instalační složku v sadě Visual Studio příkazovém řádku spusťte s oprávněními správce. Tím se nainstaluje potřebné ke spuštění ukázky certifikáty služeb.  
  
3.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
4.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvořte adresář na počítači se službou. Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).  
  
2.  Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Taky zkopírujte soubory Setup.bat, GetComputerName.vbs a Cleanup.bat k počítači služby.  
  
3.  Vytvořte adresář na klientském počítači pro binární soubory klienta.  
  
4.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
5.  Na serveru, otevřete příkazový řádek sady Visual Studio s oprávněními správce a spusťte `setup.bat service`. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6.  Upravit soubor Web.config tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), což je stejný jako název plně kvalifikované domény počítače.  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.  
  
9. Na klientovi otevřete příkazový řádek sady Visual Studio s oprávněními správce a spusťte ImportServiceCert.bat. Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
10. Na klientském počítači spusťte z příkazového řádku Client.exe. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
> [!NOTE]
>  Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači. Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>Instalační program dávkového souboru  
 Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění vlastním hostováním aplikace, která vyžaduje zabezpečení na základě certifikátu serveru. Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci.  
  
-   Vytvoření certifikátu serveru.  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít. Proměnná % název_serveru % Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. Tento dávkový soubor použije se výchozí hodnota je localhost.  
  
     Certifikát je uložen v tomto úložišti (osobních) v části LocalMachine umístění úložiště.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.  
  
     Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
## <a name="see-also"></a>Viz také
