---
title: Důvěryhodná služba facade
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 17901b7a68d4701287d02bc7ee3174683e777fd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143743"
---
# <a name="trusted-facade-service"></a>Důvěryhodná služba facade
Tento scénář ukázka ukazuje, jak tok volajícího informace o identitě z jedné služby do druhé pomocí windows communication foundation (WCF) infrastruktury zabezpečení.  
  
 Jedná se o běžný návrhový vzor, který poskytuje funkce poskytované službou veřejné síti pomocí služby fasády. Služba fasády se obvykle nachází v hraniční síti (označované také jako DMZ, demilitarizovaná zóna a promítaná podsíť) a komunikuje s back-endovou službou, která implementuje obchodní logiku a má přístup k interním datům. Komunikační kanál mezi službou fasády a back-endovou službou prochází bránou firewall a je obvykle omezen pouze na jeden účel.  
  
 Tento vzorek se skládá z následujících složek:  
  
- Klient kalkulačky  
  
- Kalkulačka fasádní služba  
  
- Služba back-end kalkulačky  
  
 Služba fasády je zodpovědná za ověření požadavku a ověření volajícího. Po úspěšném ověření a ověření předá požadavek back-endové službě pomocí řízeného komunikačního kanálu z hraniční sítě do interní sítě. Jako součást předané žádosti fasádní služba obsahuje informace o identitě volajícího tak, aby back-endová služba mohla tyto informace použít při zpracování. Identita volajícího je přenášena `Username` pomocí tokenu `Security` zabezpečení uvnitř záhlaví zprávy. Ukázka používá infrastrukturu zabezpečení WCF k přenosu `Security` a extrahování těchto informací z hlavičky.  
  
> [!IMPORTANT]
> Back-endová služba důvěřuje službě fasády k ověření volajícího. Z tohoto důvodu back-endová služba neověřuje volajícího znovu; používá informace o totožnosti poskytnuté službou fasády v předaných požadavcích. Z důvodu tohoto vztahu důvěryhodnosti musí služba back-end ověřit službu fasády, aby bylo zajištěno, že předávaná zpráva pochází z důvěryhodného zdroje - v tomto případě z fasádní služby.  
  
## <a name="implementation"></a>Implementace  
 V této ukázce jsou dvě komunikační cesty. První je mezi klientem a fasádní službou, druhá je mezi fasádní službou a back-endovou službou.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Komunikační cesta mezi klientem a fasádní službou  
 Klient komunikační cesty služby fasády `wsHttpBinding` používá `UserName` s typem pověření klienta. To znamená, že klient používá uživatelské jméno a heslo k ověření služby fasády a služba fasády používá certifikát X.509 k ověření klientovi. Konfigurace vazby vypadá jako následující příklad.  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 Služba fasády ověřuje volajícího `UserNamePasswordValidator` pomocí vlastní implementace. Pro demonstrační účely ověřování pouze zajišťuje, že uživatelské jméno volajícího odpovídá prezentované heslo. V reálné situaci je uživatel pravděpodobně ověřen pomocí služby Active Directory nebo vlastního poskytovatele členství ASP.NET. Implementace validátoru je `FacadeService.cs` umístěna v souboru.  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 Vlastní validátor je nakonfigurován tak, `serviceCredentials` aby byl použit uvnitř chování v konfiguračním souboru služby fasády. Toto chování se také používá ke konfiguraci certifikátu X.509 služby.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate
               findValue="localhost"
               storeLocation="LocalMachine"
               storeName="My"
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Komunikační cesta mezi službou Fasáda a Backend Service  
 Služba fasády pro komunikační cestu back-endové `customBinding` služby používá a, která se skládá z několika elementů vazby. Tato vazba dosahuje dvě věci. Ověřuje službu fasády a back-endovou službu, aby bylo zajištěno, že komunikace je zabezpečená a pochází z důvěryhodného zdroje. Navíc také přenáší identitu počátečního volajícího uvnitř `Username` tokenu zabezpečení. V tomto případě pouze počáteční volajícího uživatelské jméno je přenesena do back-endové služby, heslo není součástí zprávy. Důvodem je, že back-endová služba důvěřuje službě fasády k ověření volajícího před předáním požadavku. Vzhledem k tomu, že služba fasády se ověřuje samo službě back-end, může back-endová služba důvěřovat informacím obsaženým v předaný požadavek.  
  
 Následuje konfigurace vazby pro tuto komunikační cestu.  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 [ \<Prvek vazby>zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) se postará o přenos a extrakci uživatelského jména volajícího. [ \<WindowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) a [ \<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) starat o ověřování fasády a back-endové služby a ochranu zpráv.  
  
 Chcete-li předat požadavek, implementace služby fasády musí poskytnout počáteční volajícího uživatelské jméno tak, aby wcf infrastruktury zabezpečení můžete umístit do předané zprávy. Uživatelské jméno počátečního volajícího je k dispozici v implementaci služby `ClientCredentials` fasády nastavením ve vlastnosti instance proxy klienta, kterou služba fasády používá ke komunikaci se službou back-end.  
  
 Následující kód ukazuje, jak `GetCallerIdentity` je metoda implementována ve službě fasády. Jiné metody používají stejný vzor.  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 Jak je znázorněno v předchozím kódu, `ClientCredentials` heslo není nastaveno na vlastnost, je nastaveno pouze uživatelské jméno. WCF infrastruktury zabezpečení vytvoří token zabezpečení uživatelského jména bez hesla v tomto případě, což je přesně to, co je požadováno v tomto scénáři.  
  
 V back-endové službě musí být ověřeny informace obsažené v tokenu zabezpečení uživatelského jména. Ve výchozím nastavení se zabezpečení WCF pokusí namapovat uživatele na účet systému Windows pomocí poskytnutého hesla. V tomto případě není k dispozici žádné heslo a back-endová služba není vyžadována k ověření uživatelského jména, protože ověřování již bylo provedeno službou fasády. Chcete-li implementovat tuto funkci `UserNamePasswordValidator` v WCF, vlastní je za předpokladu, že pouze vynucuje, že uživatelské jméno je zadán v tokenu a neprovádí žádné další ověřování.  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 Vlastní validátor je nakonfigurován tak, `serviceCredentials` aby byl použit uvnitř chování v konfiguračním souboru služby fasády.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Chcete-li extrahovat informace o uživatelském jménu a informace o účtu `ServiceSecurityContext` služby důvěryhodné fasády, používá implementace back-endové služby třídu. Následující kód ukazuje, `GetCallerIdentity` jak je metoda implementována.  
  
```csharp  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 Informace o účtu služby fasády jsou `ServiceSecurityContext.Current.WindowsIdentity` extrahovány pomocí vlastnosti. Pro přístup k informacím o počátečním `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` volajícím používá back-endová služba vlastnost. Hledá `Identity` nárok s typem `Name`. Tato deklarace je automaticky generována infrastrukturou zabezpečení WCF z informací obsažených v tokenu `Username` zabezpečení.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta. Chcete-li služby vypnout stisknutím klávesy ENTER v oknech konzoly služby a back-end.  
  
```console  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Dávkový soubor Setup.bat, který je součástí ukázky scénáře Trusted Facade, umožňuje nakonfigurovat server s příslušným certifikátem tak, aby spouštěl službu fasády, která vyžaduje zabezpečení založené na certifikátu k ověření klientovi. Podrobnosti naleznete v postupu nastavení na konci tohoto tématu.  
  
 Následující text poskytuje stručný přehled různých částí dávkových souborů.  
  
- Vytvoření certifikátu serveru.  
  
     Následující řádky z dávkového souboru Setup.bat vytvoří certifikát serveru, který má být použit.  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     Proměnná `%SERVER_NAME%` určuje název serveru - výchozí hodnota je localhost. Certifikát je uložen v úložišti LocalMachine.  
  
- Instalace certifikátu fasádní služby do důvěryhodného úložiště certifikátů klienta.  
  
     Následující řádek zkopíruje certifikát fasádní služby do úložiště důvěryhodných osob klienta. Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné. Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem certifikátem serveru není vyžadován.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky ve stejném počítači  
  
1. Ujistěte se, že cesta obsahuje složku, kde je umístěn makecert.exe.  
  
2. Spusťte soubor Setup.bat z ukázkové instalační složky. Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.  
  
3. Spuštění nástroje BackendService.exe z adresáře \BackendService\bin v samostatném okně konzoly  
  
4. Spuštění nástroje FacadeService.exe z adresáře \FacadeService\bin v samostatném okně konzoly  
  
5. Spusťte soubor Client.exe z \client\bin. Aktivita klienta je zobrazena v aplikaci klientské konzole.  
  
6. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Chcete-li vyčistit po vzorku  
  
1. Po dokončení spuštění ukázky spusťte soubor Cleanup.bat ve složce ukázek.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
