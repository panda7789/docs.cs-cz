---
title: Důvěryhodná služba facade
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 4b02928224f1cb96a25dc71941273625e7d9e5e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091548"
---
# <a name="trusted-facade-service"></a>Důvěryhodná služba facade
Tento ukázkový scénář ukazuje, jak tok volajícího informace o identitách z jedné služby do jiného pomocí Windows Communication Foundation (WCF) Infrastruktura zabezpečení.  
  
 To je běžný vzor návrhu ke zveřejnění funkce poskytované službou ve veřejné síti pomocí služby průčelí. Služba průčelí obvykle nachází v hraniční síti (označované také jako DMZ, demilitarizovaná zóna a monitorovaná podsíť) a komunikuje s back-end službu, která implementuje obchodní logiku a má přístup k interní data. Komunikační kanál mezi službou průčelí a back-end službu prochází přes bránu firewall a je obvykle omezené pouze jedinému účelu.  
  
 Tento příklad se skládá z následujících součástí:  
  
-   Kalkulačka klienta  
  
-   Kalkulačka průčelí služby  
  
-   Kalkulačka back-end službou  
  
 Adaptační vrstva služby zodpovídá za ověření žádosti a ověřování volající. Po úspěšném ověření a ověření předá požadavek do služby back-end pomocí řízené komunikační kanál z hraniční sítě k interní síti. Jako součást předaný požadavek průčelí služba obsahuje informace o identitu volajícího tak, aby službě back-end tyto informace můžete použít v jeho zpracování. Identita volajícího se přenáší prostřednictvím `Username` token zabezpečení ve zprávě `Security` záhlaví. Ukázka používá k přenosu a získání informací z Infrastruktura zabezpečení WCF `Security` záhlaví.  
  
> [!IMPORTANT]
>  Back-end službu vztahy důvěryhodnosti služby průčelí ověřit volající. Z tohoto důvodu back-end službu neověřuje volající znovu. používá informace o identitě poskytovaný službou průčelí v předaný požadavek. Díky tomuto vztahu důvěryhodnosti musí back-end službu ověřit službě průčelí a ujistěte se, že přesměrovaná zpráva pochází z důvěryhodného zdroje – v takovém případě adaptační vrstva služby.  
  
## <a name="implementation"></a>Implementace  
 Existují dvě cesty komunikace v této ukázce. Nejprve je mezi klientem a službu průčelí, druhá je mezi službou průčelí a back-end službu.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Komunikační trasa mezi klientem a službou průčelí  
 Klient do cesty komunikace služby průčelí používá `wsHttpBinding` s `UserName` typu pověření klienta. To znamená, že klient používá uživatelské jméno a heslo k ověření průčelí služba a služba průčelí certifikát X.509 používá k ověření klienta. Konfigurace vazby vypadá jako v následujícím příkladu.  
  
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
  
 Službu průčelí ověřuje pomocí vlastního volajícího `UserNamePasswordValidator` implementace. Pro demonstrační účely ověřování pouze zaručí, že uživatelské jméno volajícího odpovídá prezentované heslo. V reálné situaci pravděpodobně ověření uživatele pomocí služby Active Directory nebo vlastního poskytovatele členství technologie ASP.NET. Program pro ověření implementace se nachází v `FacadeService.cs` souboru.  
  
```  
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
  
 Vlastní validátor je nakonfigurován pro použití v `serviceCredentials` chování v konfiguračním souboru služby adaptační vrstva. Toto chování se také používá ke konfiguraci certifikátu X.509 služby.  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Komunikační trasa mezi službou průčelí a back-end službou  
 Používá službu průčelí komunikační trasa back-end službu `customBinding` , který se skládá z několika elementů vazby. Tato vazba provede dvě věci. Ověří se průčelí služby a back-end službu, aby zajistila, že komunikace je zabezpečená a pochází z důvěryhodného zdroje. Kromě toho také přenáší identitu volajícího počáteční uvnitř `Username` token zabezpečení. V takovém případě se přenášejí pouze uživatelské jméno volajícího počáteční do back-end službu, heslo není součástí zprávy. Je to proto, že back-end službu vztahy důvěryhodnosti služby průčelí ověřit volající před předáním požadavku k němu. Protože průčelí service ověří ve službě back-endu, back-end službu můžete důvěřovat informace obsažené v předaný požadavek.  
  
 Následuje konfigurace vazby pro tuto cestu komunikace.  
  
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
  
 [ \<Zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) postará element vazby přenosu uživatelského jména a extrakce počáteční volající. [ \<Zabezpečení windowsstreamsecurity iniciuje >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) a [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) postará o ověřování fasádu a back-endové služby a zprávu ochrany.  
  
 Tento požadavek předá dál, implementace služby průčelí musíte zadat uživatelské jméno počáteční volající tak tuto infrastrukturu zabezpečení WCF to můžete umístit do přesměrovaná zpráva. Uživatelské jméno počáteční volající je součástí implementace služby průčelí nastavením v `ClientCredentials` vlastnost na instanci proxy serveru klienta služby průčelí používá ke komunikaci s back-end službu.  
  
 Následující kód ukazuje, jak `GetCallerIdentity` metoda je implementována ve službě adaptační vrstva. Jiné metody nepoužívají stejným vzorem.  
  
```  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 Jak je znázorněno v předchozím kódu, heslo nenastaví na `ClientCredentials` , pouze uživatelské jméno je nastavena. Infrastruktura zabezpečení WCF vytvoří token zabezpečení uživatelské jméno bez hesla v tomto případě tedy přesně toho, co vyžaduje v tomto scénáři.  
  
 Ve službě back-endu musí být ověřené informace obsažené v tokenu zabezpečení uživatelské jméno. Ve výchozím nastavení zabezpečení WCF pokusí mapovat uživatele na Windows účet pomocí zadaného hesla. V takovém případě není zadáno žádné heslo a k ověření uživatelského jména, protože již bylo provedeno ověření službou průčelí není vyžadována back-end službu. Pro implementaci této funkce ve službě WCF, vlastní `UserNamePasswordValidator` je k dispozici, pouze vynutí, že uživatelské jméno je zadán v tokenu a nebude provádět žádné další ověřování.  
  
```  
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
  
 Vlastní validátor je nakonfigurován pro použití v `serviceCredentials` chování v konfiguračním souboru služby adaptační vrstva.  
  
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
  
 Extrahovat informace uživatelského jména a informace o účtu služby důvěryhodného průčelí, implementace služby back-endu používá `ServiceSecurityContext` třídy. Následující kód ukazuje jak `GetCallerIdentity` metoda je implementována.  
  
```  
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
  
 Informace o účtu služby průčelí se extrahují pomocí `ServiceSecurityContext.Current.WindowsIdentity` vlastnost. Přístup k informacím o počáteční volající back-end služba používá `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` vlastnost. Vyhledá `Identity` deklarace identity s typem `Name`. Tato deklarace identity není automaticky vygenerován pomocí WCF zabezpečení infrastruktury z informací obsažených v `Username` token zabezpečení.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient. Stisknutím klávesy ENTER v oknech konzoly služby fasádu a back-endu pro vypnutí služby.  
  
```  
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
  
 Dávkový soubor Setup.bat součástí ukázkový scénář důvěryhodné Facade umožňuje nakonfigurovat server se příslušný certifikát ke spuštění služby průčelí, které vyžadují zabezpečení na základě certifikátů ke svému ověření ke klientovi. Zobrazit postup nastavení na konci tohoto tématu, kde podrobnosti.  
  
 Následující body nabízí stručný přehled o různých částech dávkové soubory.  
  
-   Vytváří se certifikát serveru.  
  
     Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     `%SERVER_NAME%` Proměnné Určuje název serveru – výchozí hodnota je localhost. Certifikát je uložen v úložišti LocalMachine.  
  
-   Instalace služby průčelí certifikátu do úložiště důvěryhodných certifikátů klienta.  
  
     Následující řádek certifikát služby průčelí zkopíruje do úložiště důvěryhodných osob klienta. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Ujistěte se, že cesta obsahuje složku, kde je umístěn Makecert.exe.  
  
2.  Spusťte Setup.bat z instalační složky s ukázkou. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.  
  
3.  Spuštění BackendService.exe z adresáře \BackendService\bin v okně samostatné konzoly  
  
4.  Spuštění FacadeService.exe z adresáře \FacadeService\bin v okně samostatné konzoly  
  
5.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
6.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
1.  Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
