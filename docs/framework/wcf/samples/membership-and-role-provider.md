---
title: Členství a poskytovatel rolí
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 117be783c2d4a72ff9d1c4509566274b1043a43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144458"
---
# <a name="membership-and-role-provider"></a>Členství a poskytovatel rolí
Ukázka členství a zprostředkovatele rolí ukazuje, jak může služba používat ASP.NET poskytovatele členství a rolí k ověřování a autorizaci klientů.  
  
 V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Vzorek ukazuje, jak:  
  
- Klient se může ověřit pomocí kombinace uživatelského jména a hesla.  
  
- Server může ověřit pověření klienta vůči poskytovateli členství ASP.NET.  
  
- Server lze ověřit pomocí certifikátu X.509 serveru.  
  
- Server může namapovat ověřeného klienta na roli pomocí ASP.NET zprostředkovatele rolí.  
  
- Server můžete použít `PrincipalPermissionAttribute` k řízení přístupu k určité metody, které jsou vystaveny službou.  
  
 Poskytovatelé členství a rolí jsou nakonfigurováni tak, aby používali úložiště podporované sql serverem. Připojovací řetězec a různé možnosti jsou určeny v konfiguračním souboru služby. Poskytovatel členství je uveden `SqlMembershipProvider` název, zatímco zprostředkovatel `SqlRoleProvider`role je uveden název .  
  
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
  
 Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, která je definována pomocí konfiguračního souboru Web.config. Koncový bod se skládá z adresy, vazby a smlouvy. Vazba je konfigurována `wsHttpBinding`se standardem , který je ve výchozím nastavení nastaven na ověřování systému Windows. Tato ukázka `wsHttpBinding` nastaví standard pro použití ověřování uživatelského jména. Chování určuje, že certifikát serveru má být použit pro ověřování služby. Certifikát serveru musí obsahovat stejnou `SubjectName` hodnotu jako `findValue` atribut v prvku [ \<konfigurace serviceCertificate>.](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) Kromě toho chování určuje, že ověřování párů uživatelského jména a hesla provádí poskytovatel členství ASP.NET a mapování rolí provádí poskytovatel role ASP.NET zadáním názvů definovaných pro dva zprostředkovatele.  
  
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
  
 Při spuštění ukázky klient volá různé operace služby pod tři různé uživatelské účty: Alice, Bob a Charlie. Požadavky na operaci a odpovědi jsou zobrazeny v okně klientské konzole. Všechny čtyři volání jako uživatel "Alice" by měl být úspěšný. Uživatel "Bob" by měl získat chybu odepřen přístup při pokusu o volání Divide metoda. Uživatel "Charlie" by měl získat chybu odepřen přístup při pokusu o volání Multiply metoda. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [spuštění windows communication foundation ukázky](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
2. Ujistěte se, že jste nakonfigurovali [databázi ASP.NET aplikačních služeb](https://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    > Pokud používáte sql server Express Edition, název serveru je .\SQLEXPRESS. Tento server by měl být použit při konfiguraci databáze ASP.NET aplikačních služeb a také v připojovacím řetězci Web.config.  
  
    > [!NOTE]
    > Účet ASP.NET pracovního procesu musí mít oprávnění k databázi, která je vytvořena v tomto kroku. K tomu použijte nástroj sqlcmd nebo SQL Server Management Studio.  
  
3. Chcete-li vzorek spustit v konfiguraci jednoho nebo mezi počítači, postupujte podle následujících pokynů.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky ve stejném počítači  
  
1. Ujistěte se, že cesta obsahuje složku, kde je umístěn makecert.exe.  
  
2. Spusťte soubor Setup.bat z ukázkové instalační složky v příkazovém řádku pro vývojáře pro aplikaci Visual Studio, která je spuštěna s oprávněními správce. Tím nainstalujete certifikáty služby potřebné pro spuštění ukázky.  
  
3. Spusťte soubor Client.exe z \client\bin. Aktivita klienta je zobrazena v aplikaci klientské konzole.  
  
4. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky v počítačích  
  
1. Vytvořte adresář v počítači služby. Vytvořte virtuální aplikaci s názvem ServiceModelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).  
  
2. Zkopírujte soubory servisních programů ze vzorků \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře v počítači služby. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Zkopírujte také soubory Setup.bat, GetComputerName.vbs a Cleanup.bat do servisního počítače.  
  
3. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
4. Zkopírujte soubory klientských programů do klientského adresáře v klientském počítači. Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
5. Na serveru otevřete příkazový řádek pro vývojáře pro `setup.bat service`visual studio s oprávněními správce a spusťte . Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6. Upravte web.config tak, aby odrážel `findValue` nový název certifikátu (v atributu [ \<v serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.  
  
7. Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.  
  
8. V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.  
  
9. Na straně klienta otevřete příkazový řádek pro vývojáře pro visual studio s oprávněními správce a spusťte soubor ImportServiceCert.bat. Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.  
  
10. V klientském počítači spusťte soubor Client.exe z příkazového řádku. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Chcete-li vyčistit po vzorku  
  
- Spusťte cleanup.bat ve složce ukázky po dokončení spuštění ukázky.  
  
> [!NOTE]
> Tento skript neodebere certifikáty služeb v klientovi při spuštění této ukázky v počítačích. Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty v počítačích, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople. Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`příkaz: Například: .  
  
## <a name="the-setup-batch-file"></a>Dávkový soubor instalace  
 Dávkový soubor Setup.bat, který je součástí této ukázky, umožňuje nakonfigurovat server s příslušnými certifikáty tak, aby spouštěl samoobslužnou aplikaci, která vyžaduje zabezpečení založené na certifikátech serveru. Tento dávkový soubor musí být upraven tak, aby fungoval napříč počítači nebo aby fungoval v nehostovaném případě.  
  
 Následující text poskytuje stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby byly spuštěny v příslušné konfiguraci.  
  
- Vytvoření certifikátu serveru.  
  
     Následující řádky z dávkového souboru Setup.bat vytvoří certifikát serveru, který má být použit. Proměnná %SERVER_NAME% určuje název serveru. Změňte tuto proměnnou a zadejte vlastní název serveru. Tento dávkový soubor je výchozí pro localhost.  
  
     Certifikát je uložen v úložišti Moje (osobní) pod umístěním úložiště LocalMachine.  
  
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
  
     Následující řádky v dávkovém souboru Setup.bat zkopírují certifikát serveru do úložiště důvěryhodných osob klienta. Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné. Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem certifikátem serveru není vyžadován.  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
