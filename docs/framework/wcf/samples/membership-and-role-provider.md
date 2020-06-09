---
title: Členství a poskytovatel rolí
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: e77e353fba194cb25b466387cf9def6773635e00
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591758"
---
# <a name="membership-and-role-provider"></a>Členství a poskytovatel rolí
Ukázka členství a zprostředkovatele rolí předvádí, jak může služba k ověřování a autorizaci klientů použít poskytovatele členství a rolí ASP.NET.  
  
 V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Ukázka ukazuje, jak:  
  
- Klient se může ověřit pomocí kombinace uživatelského jména a hesla.  
  
- Server může ověřit pověření klienta pro poskytovatele členství ASP.NET.  
  
- Server se dá ověřit pomocí certifikátu X. 509 serveru.  
  
- Server může mapovat ověřeného klienta na roli pomocí poskytovatele rolí ASP.NET.  
  
- Server může použít `PrincipalPermissionAttribute` k řízení přístupu k určitým metodám, které jsou zpřístupněné službou.  
  
 Zprostředkovatelé členství a rolí jsou nakonfigurováni tak, aby používal úložiště zajištěné SQL Server. Připojovací řetězec a různé možnosti jsou zadány v konfiguračním souboru služby. Zprostředkovateli členství je uveden název, `SqlMembershipProvider` zatímco poskytovatel role má název `SqlRoleProvider` .  
  
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
  
 Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, která je definována pomocí konfiguračního souboru Web. config. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována se standardem `wsHttpBinding` , který používá ověřování systému Windows. Tato ukázka nastavuje standard `wsHttpBinding` pro použití ověřování uživatelského jména. Chování určuje, že se má certifikát serveru použít k ověřování služby. Certifikát serveru musí obsahovat stejnou hodnotu `SubjectName` jako `findValue` atribut v [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) konfiguračním elementu. Kromě toho chování určuje, že zprostředkovatel členství v ASP.NET a mapování rolí provádí zprostředkovatel rolí ASP.NET zadáním názvů definovaných pro tyto dva zprostředkovatele.  
  
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
  
 Když spustíte ukázku, klient zavolá různé operace služby za tři různé uživatelské účty: Alice, Bob a Charlie. Požadavky na operace a odpovědi se zobrazí v okně konzoly klienta. Všechna čtyři volání vytvořená jako uživatel "Alice" by měla být úspěšná. Uživatel Bob by měl při pokusu o volání metody dělení získat chybu odepření přístupu. Při pokusu o volání metody násobení by uživatel Charlie měl získat chybu odepření přístupu. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
2. Ujistěte se, že jste nakonfigurovali [databázi ASP.NET aplikační služby](https://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    > Pokud používáte edici SQL Server Express, název serveru je .\SQLEXPRESS. Tento server by měl být použit při konfiguraci databáze ASP.NET Aplikační služby a také v připojovacím řetězci Web. config.  
  
    > [!NOTE]
    > Účet pracovního procesu ASP.NET musí mít oprávnění pro databázi, která je vytvořena v tomto kroku. Provedete to pomocí nástroje Sqlcmd nebo SQL Server Management Studio.  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle následujících pokynů.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači  
  
1. Ujistěte se, že cesta obsahuje složku, ve které se nachází nástroj Makecert. exe.  
  
2. Spusťte Setup. bat z ukázkové instalační složky ve Developer Command Prompt pro Visual Studio spusťte s oprávněními správce. Tím se nainstaluje certifikát služby vyžadovaný pro spuštění ukázky.  
  
3. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
4. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Vytvořte adresář na počítači služby. Vytvořte virtuální aplikaci s názvem ServiceModelSamples pro tento adresář pomocí nástroje pro správu služby Internetová informační služba (IIS).  
  
2. Zkopírujte programové soubory služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby. Ujistěte se, že jste zkopírovali soubory do podadresáře \Bin. Zkopírujte také soubory Setup. bat, GetComputerName. vbs a Cleanup. bat do počítače služby.  
  
3. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
4. Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači. Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.  
  
5. Na serveru otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a spusťte `setup.bat service` . Při spuštění `setup.bat` s `service` argumentem se vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.  
  
6. Upravte soubor Web. config tak, aby odrážel nový název certifikátu (v `findValue` atributu [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), který je stejný jako plně kvalifikovaný název domény počítače.  
  
7. Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.  
  
8. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.  
  
9. V klientovi otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a spusťte ImportServiceCert. bat. Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.  
  
10. V klientském počítači spusťte z příkazového řádku soubor Client. exe. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Po dokončení ukázky Spusťte Cleanup. bat ve složce Samples.  
  
> [!NOTE]
> Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi. Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople. Použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .  
  
## <a name="the-setup-batch-file"></a>Instalační dávkový soubor  
 Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s příslušnými certifikáty pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.  
  
 Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.  
  
- Vytváří se certifikát serveru.  
  
     Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít. Proměnná% SERVER_NAME% Určuje název serveru. Změňte tuto proměnnou tak, aby určovala vlastní název serveru. Tato dávková soubor se nastaví jako výchozí hodnota localhost.  
  
     Certifikát je uložený v osobním úložišti (osobní) v umístění úložiště LocalMachine.  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.  
  
     Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
