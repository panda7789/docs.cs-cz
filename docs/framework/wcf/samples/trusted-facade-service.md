---
title: Důvěryhodná služba facade
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 08e115d297439910c16601051539a23a5a6bebc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="trusted-facade-service"></a>Důvěryhodná služba facade
Tento ukázkový scénář ukazuje, jak přenést informace identitu volajícího z jedné služby do jiného pomocí služby Windows Communication Foundation (WCF) Infrastruktura zabezpečení.  
  
 Je běžné vzoru návrhu ke zveřejnění funkce poskytované službou k veřejné síti pomocí průčelí za služby. Služba průčelí za většinou nachází v hraniční síti (označované také jako DMZ, demilitarizovaná zóna a monitorovaná podsíť) a komunikuje se službou back-end, který implementuje obchodní logiky a má přístup k interní data. Komunikační kanál mezi průčelí za služby a služby back-end přejde přes bránu firewall a je obvykle omezené pro pouze jedinému účelu.  
  
 Tato ukázka se skládá z následujících součástí:  
  
-   Kalkulačky klienta  
  
-   Kalkulačky průčelí za služby  
  
-   Back-end službu kalkulačky  
  
 Službu průčelí za zodpovídá za ověření žádosti a ověřování volající. Po úspěšném ověření a ověření se předá požadavek back-end službu pomocí řízené komunikační kanál z hraniční sítě k interní síti. Jako součást předaný požadavek službu průčelí za obsahuje informace o identitu volajícího, aby službě back-end tyto informace můžete použít v jeho zpracování. Identitu volajícího se přenášejí pomocí `Username` token zabezpečení uvnitř zprávu `Security` záhlaví. Ukázce se používá [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury zabezpečení k přenosu a získání informací z `Security` záhlaví.  
  
> [!IMPORTANT]
>  Back-end službu důvěřuje průčelí za službu, kterou chcete ověřit volající. Z toho důvodu back-end službu neověřuje volající znovu; používá informace o identitě poskytovaný službou průčelí za v přesměrovaná žádosti. Díky tomuto vztahu důvěryhodnosti musí ověřit službě back-end službu průčelí za tak, aby zajistila, že přesměrovaná zpráva pochází z důvěryhodného zdroje – v takovém případě průčelí za službu.  
  
## <a name="implementation"></a>Implementace  
 Existují dva komunikační cesty v této ukázce. Nejprve je mezi klientem a službu průčelí za sekundu je mezi průčelí za služby a služby back-end.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Komunikační trasa mezi klientem a službou průčelí za  
 Klient k cestě komunikace služby průčelí za používá `wsHttpBinding` s `UserName` typu pověření klienta. To znamená, že klient použije uživatelské jméno a heslo k ověření průčelí za služby a služby průčelí za používá certifikát X.509 k ověření klienta. Konfigurace vazeb vypadá jako v následujícím příkladu.  
  
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
  
 Službu průčelí za ověří volajícího pomocí vlastní `UserNamePasswordValidator` implementace. Pro demonstrační účely ověřování jenom zaručí, že uživatelské jméno volajícího odpovídá vidění heslo. V případě skutečných pravděpodobně ověření uživatele pomocí služby Active Directory nebo vlastního zprostředkovatele členství technologie ASP.NET. Implementace validátoru se nachází v `FacadeService.cs` souboru.  
  
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
  
 Vlastní validátor je nakonfigurována pro používání uvnitř `serviceCredentials` chování v konfiguračním souboru průčelí za služby. Toto chování je také použít ke konfiguraci služby certifikát X.509.  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Komunikační trasa mezi službou průčelí za a back-end službu  
 Používá službu průčelí za cestu komunikace služby back-end `customBinding` který se skládá z několika součástí vazby. Tato vazba má dvě věci. Ověřuje průčelí za služby a back-end službu zajistěte, aby komunikace zabezpečená a pochází z důvěryhodného zdroje. Kromě toho také přenášení počáteční volajícího identity uvnitř `Username` tokenu zabezpečení. V tomto případě se přenáší pouze uživatelské jméno počáteční volajícího na službě back-end, heslo není součástí zprávy. Je to proto, že back-end službu důvěřuje průčelí za službu, kterou chcete ověřit volající před předáním požadavku na ni. Protože průčelí za služby se ověří na službě back-end, můžete informace obsažené v předaný požadavek důvěřovat back-end službu.  
  
 Zde je konfigurace vazeb pro tuto cestu komunikace.  
  
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
  
 [ \<Zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) prvku vazby má na starosti přenosu uživatelského jména a extrakce počáteční volajícího. [ \<WindowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) a [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) postará o ověřování průčelí za a back-end služby a zpráv ochrany.  
  
 Předání žádosti, musí implementace služby průčelí za zadat uživatelské jméno počáteční volajícího, aby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Tato infrastruktura zabezpečení můžete umístit do přesměrovaná zpráva. Počáteční volajícího uživatelské jméno je součástí implementace služby průčelí za nastavením v `ClientCredentials` vlastnost na instanci proxy serveru klienta služby průčelí za používá ke komunikaci s back-end službu.  
  
 Následující kód ukazuje, jak `GetCallerIdentity` metoda se implementuje na průčelí za službu. Ostatní metody pomocí stejného vzoru.  
  
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
  
 Jak ukazuje předchozí kód, heslo není nastaven na `ClientCredentials` , pouze uživatelské jméno je nastavena. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktura zabezpečení vytvoří token zabezpečení uživatelské jméno bez zadání hesla v tomto případě tedy přesně co je nutné v tomto scénáři.  
  
 Na službě back-end musí být ověřeny informací obsažených v tokenu zabezpečení, uživatelské jméno. Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení se pokouší mapovat uživatele na účet systému Windows pomocí zadaného hesla. V takovém případě není zadané heslo a back-end službu není nutné k ověření uživatelského jména, protože již bylo provedeno ověření službou průčelí za. K implementaci tuto funkci v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vlastní `UserNamePasswordValidator` je k dispozici, pouze vynucuje, uživatelské jméno je zadána v tokenu a nebude provádět žádné další ověřování.  
  
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
  
 Vlastní validátor je nakonfigurována pro používání uvnitř `serviceCredentials` chování v konfiguračním souboru průčelí za služby.  
  
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
  
 Extrahovat informace uživatelského jména a informace o účtu služby průčelí za důvěryhodné, používá implementace služby back-end `ServiceSecurityContext` třídy. Následující kód ukazuje jak `GetCallerIdentity` metoda není implementována.  
  
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
  
 Informace o účtu služby průčelí za je extrahována pomocí `ServiceSecurityContext.Current.WindowsIdentity` vlastnost. Pro přístup k informacím o počáteční volající používá služba back-end `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` vlastnost. Hledá `Identity` deklarace identity s typem `Name`. Tento požadavek je automaticky generován [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktura zabezpečení z informací obsažených v `Username` tokenu zabezpečení.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta. Můžete stisknutím klávesy ENTER v oknech konzoly služby průčelí za a back-end vypnutí služby.  
  
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
  
 Dávkový soubor Setup.bat součástí ukázkový scénář důvěryhodné Facade umožňuje nakonfigurovat server se příslušný certifikát ke spuštění průčelí za služby, která vyžaduje zabezpečení na základě certifikátu k vlastnímu ověření klienta. Přečtěte si postup instalace na konci tohoto tématu podrobnosti.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory.  
  
-   Vytvoření certifikátu serveru.  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     `%SERVER_NAME%` Proměnná Určuje název serveru – výchozí hodnota je localhost. Certifikát je uložen v úložišti LocalMachine.  
  
-   Instalace služby průčelí za certifikátu do úložiště důvěryhodných certifikátů klienta.  
  
     Následující řádek zkopíruje do úložiště důvěryhodných osob na klientský certifikát průčelí za služby. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky na stejném počítači  
  
1.  Ujistěte se, že cesta obsahuje složku, kde je umístěna Makecert.exe.  
  
2.  Spuštění Setup.bat od vzorku instalační složku. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
3.  Spusťte BackendService.exe z adresáře \BackendService\bin v okně samostatné konzoly  
  
4.  Spusťte FacadeService.exe z adresáře \FacadeService\bin v okně samostatné konzoly  
  
5.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
6.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
1.  Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
  
## <a name="see-also"></a>Viz také
