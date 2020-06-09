---
title: Důvěryhodná služba facade
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: e7aa5e96fb8104c8140a8cebc6be45d2000821aa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591290"
---
# <a name="trusted-facade-service"></a>Důvěryhodná služba facade
Tato ukázka scénáře ukazuje, jak flowovat informace o identitě volajících z jedné služby do jiné pomocí infrastruktury zabezpečení Windows Communication Foundation (WCF).  
  
 Jedná se o běžný vzor návrhu k vystavení funkcí poskytovaných službou do veřejné sítě pomocí služby fasády. Služba fasády se obvykle nachází v hraniční síti (označované také jako DMZ, demilitarizovaná Zone a monitorovaná podsíť) a komunikuje se službou back-end, která implementuje obchodní logiku a má přístup k interním datům. Komunikační kanál mezi službou fasády a back-end službou prochází přes bránu firewall a je obvykle omezený jenom pro jediný účel.  
  
 Tato ukázka se skládá z následujících součástí:  
  
- Klient kalkulačky  
  
- Služba na fasádu kalkulačky  
  
- Back-end služba kalkulačky  
  
 Služba fasády zodpovídá za ověření žádosti a ověřování volajícího. Po úspěšném ověření a ověření předá požadavek službě back-end pomocí řízeného komunikačního kanálu z hraniční sítě do interní sítě. V rámci předávané žádosti služba fasády obsahuje informace o identitě volajícího, aby služba back-end mohla tyto informace použít ve svém zpracování. Identita volajícího se přenáší pomocí `Username` tokenu zabezpečení uvnitř záhlaví zprávy `Security` . Ukázka používá infrastrukturu zabezpečení WCF k přenosu a extrakci těchto informací z `Security` hlavičky.  
  
> [!IMPORTANT]
> Back-end služba důvěřuje službě fasády k ověření volajícího. Proto služba back-end neověřuje volajícího znovu. používá informace o identitě poskytované službou fasády v přesměrovaném požadavku. Z důvodu tohoto vztahu důvěryhodnosti musí back-end služba ověřit službu fasády, aby se zajistilo, že Předaná zpráva pochází z důvěryhodného zdroje – v tomto případě je to služba fasády.  
  
## <a name="implementation"></a>Implementace  
 V této ukázce jsou k dispozici dvě cesty komunikace. První je mezi klientem a službou fasády, druhým je mezi službou fasády a back-end službou.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Komunikační cesta mezi klientem a službou fasády  
 Klient pro komunikační cestu služby fasády používá `wsHttpBinding` s `UserName` typem pověření klienta. To znamená, že klient nástroje používá uživatelské jméno a heslo k ověření ve službě fasády a služba fasády používá k ověření klienta certifikát X. 509. Konfigurace vazby vypadá jako v následujícím příkladu.  
  
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
  
 Služba fasády ověřuje volajícího pomocí vlastní `UserNamePasswordValidator` implementace. Pro demonstrační účely ověřování zajišťuje pouze uživatelské jméno volajícího, které odpovídá prezentovanému heslu. V reálném čase se uživatel pravděpodobně ověřuje pomocí služby Active Directory nebo vlastního poskytovatele členství v ASP.NET. Implementace validátoru se nachází v `FacadeService.cs` souboru.  
  
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
  
 Vlastní validátor je nakonfigurován tak, aby se používal v rámci `serviceCredentials` chování v konfiguračním souboru služby fasády. Toto chování se používá také ke konfiguraci certifikátu X. 509 služby.  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Komunikační cesta mezi službou fasády a back-end službou  
 Služba fasády pro komunikační cestu služby back-end používá sadu `customBinding` , která se skládá z několika prvků vazby. Tato vazba dosahuje dvou věcí. Ověřuje službu fasády a back-end službu, aby bylo zajištěno, že komunikace je zabezpečená a pochází z důvěryhodného zdroje. Kromě toho také přenáší identitu počátečního volajícího v `Username` tokenu zabezpečení. V takovém případě se do služby back-end přenáší jenom počáteční uživatelské jméno volajícího, heslo není zahrnuté do zprávy. Důvodem je, že back-end služba důvěřuje službě fasády, aby před předáním žádosti do ní ověřila volajícího. Vzhledem k tomu, že se služba fasády ověřuje pro back-end službu, může služba back-end důvěřovat informacím obsaženým v přesměrovaném požadavku.  
  
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
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)Element Binding se stará o přenos a extrakci počátečního uživatelského jména volajícího. [\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md)A [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) postará se o ověřování fasády a back-endové služby a ochrany zpráv.  
  
 Pro přeposlání žádosti musí implementace služby fasády poskytnout počáteční uživatelské jméno volajícího, aby mohla infrastruktura zabezpečení WCF umístit tuto zprávu do předané zprávy. Počáteční uživatelské jméno volajícího je k dispozici v implementaci služby fasády tím, že ji nastavíte ve `ClientCredentials` vlastnosti instance proxy serveru klienta, kterou služba fasády používá ke komunikaci se službou back-end.  
  
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
  
 Jak je znázorněno v předchozím kódu, heslo není nastaveno pro `ClientCredentials` vlastnost, je nastaveno pouze uživatelské jméno. Infrastruktura zabezpečení WCF vytvoří v tomto případě token zabezpečení uživatelského jména bez hesla, což je přesně to, co se v tomto scénáři vyžaduje.  
  
 V back-end službě musí být ověřené informace obsažené v tokenu zabezpečení uživatelského jména. Ve výchozím nastavení se zabezpečení služby WCF pokusí uživatele mapovat na účet systému Windows pomocí zadaného hesla. V tomto případě není k dispozici žádné heslo a služba back-end není pro ověření uživatelského jména nutná, protože ověřování již provedla služba fasády. K implementaci této funkce ve službě WCF je k `UserNamePasswordValidator` dispozici vlastní, která vynutila pouze zadání uživatelského jména v tokenu a neprovádí žádné další ověřování.  
  
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
  
 Vlastní validátor je nakonfigurován tak, aby se používal v rámci `serviceCredentials` chování v konfiguračním souboru služby fasády.  
  
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
  
 Chcete-li extrahovat informace o uživatelském jménu a informace o účtu důvěryhodné služby fasády, implementace back-end služby používá `ServiceSecurityContext` třídu. Následující kód ukazuje, jak `GetCallerIdentity` je metoda implementována.  
  
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
  
 Informace o účtu služby fasády se extrahují pomocí `ServiceSecurityContext.Current.WindowsIdentity` Vlastnosti. Chcete-li získat přístup k informacím o počátečním volajícím, služba back-end používá `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` vlastnost. Vyhledá `Identity` deklaraci identity s typem `Name` . Tato deklarace je automaticky generovaná infrastrukturou zabezpečení WCF z informací obsažených v `Username` tokenu zabezpečení.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta. Chcete-li ukončit služby, stiskněte klávesu ENTER ve Windows a v konzole služby back-end Service.  
  
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
  
 Dávkový soubor Setup. bat, který je součástí ukázky důvěryhodných scénářů průčelí, vám umožní nakonfigurovat server s relevantním certifikátem pro spuštění služby fasády, která vyžaduje, aby se k ověřování na klienta vyžadovalo zabezpečení založené na certifikátech. Podrobnosti najdete v postupu nastavení na konci tohoto tématu.  
  
 Níže najdete stručný přehled různých částí dávkových souborů.  
  
- Vytváří se certifikát serveru.  
  
     Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     `%SERVER_NAME%`Proměnná Určuje název serveru – výchozí hodnota je localhost. Certifikát je uložený v úložišti LocalMachine.  
  
- Instalace certifikátu služby fasády do důvěryhodného úložiště certifikátů klienta.  
  
     Následující řádek zkopíruje certifikát služby fasády do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky na stejném počítači  
  
1. Ujistěte se, že cesta obsahuje složku, ve které se nachází nástroj Makecert. exe.  
  
2. Z ukázkové instalační složky spusťte Setup. bat. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
3. Spusťte BackendService. exe z adresáře \BackendService\bin v samostatném okně konzoly.  
  
4. Spusťte FacadeService. exe z adresáře \FacadeService\bin v samostatném okně konzoly.  
  
5. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
6. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
1. Po dokončení ukázky spusťte na složce Samples Cleanup. bat.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
