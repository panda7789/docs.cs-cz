---
title: Ukázka identity služby
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 64adee14c3c0a0ba8071bbaca35b8712280e10b4
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221957"
---
# <a name="service-identity-sample"></a>Ukázka identity služby
Tato ukázka identity služby ukazuje, jak nastavit identitu služby. V době návrhu klient může načíst identitu pomocí metadat služby a za běhu pak se klient může ověřit identitu služby. Koncept identitu služby je umožnit klient k ověření služby před voláním některé z jeho operace, a tím chrání před neověřená volání klienta. Na zabezpečeném připojení služby také ověří přihlašovací údaje klienta před povolením přístupu, ale nejedná se o fokus této ukázky. Zobrazit ukázky [klienta](../../../../docs/framework/wcf/samples/client.md) , které zobrazí ověřování serveru.

> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.

 Tato ukázka ilustruje následující funkce:

-   Jak nastavit různé typy identit na různých koncových bodů služby. Každý typ identity má různé možnosti. Typ identity použití je závislá na typu zabezpečovací přihlašovací údaje použité pro vazbu koncového bodu.

-   Identity můžete buď nastavit deklarativně v konfiguraci nebo imperativně v kódu. Obvykle byste měli klienta a služby použít konfiguraci nastavení identity.

-   Jak nastavit vlastní identitu na straně klienta. Přizpůsobení existujícího typu identita, která umožňuje klientovi zkontrolujte přihlašovací údaje služby pro rozhodnutí o autorizaci před voláním služby k dispozici další informace o deklaraci identity je obvykle vlastní identitu.

    > [!NOTE]
    >  Tato ukázka ověří identitu konkrétní certifikát nazvaný identity.com a klíče RSA, které jsou obsaženy v rámci tohoto certifikátu. Při použití typů identity certifikát a RSA v konfigurace na straně klienta, snadný způsob, jak získat tyto hodnoty je ke kontrole WSDL pro službu, kde jsou tyto hodnoty serializovat.

 Následující ukázkový kód ukazuje, jak nakonfigurovat identitu koncového bodu služby se serveru DNS (Domain Name) WSHttpBinding pomocí certifikátu.

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 Identitu můžete také uvést v konfiguraci v souboru App.config. Následující příklad ukazuje, jak nastavit identita UPN (hlavní název uživatele) pro koncový bod služby.

```xml
<endpoint address="upnidentity"
        behaviorConfiguration=""
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_Windows"
        name="WSHttpBinding_ICalculator_Windows"
        contract="Microsoft.ServiceModel.Samples.ICalculator">
  <!-- Set the UPN identity for this endpoint -->
  <identity>
      <userPrincipalName value="host\myservice.com" />
  </identity >
</endpoint>
```

 Vlastní identity můžete nastavit na straně klienta odvozením z <xref:System.ServiceModel.EndpointIdentity> a <xref:System.ServiceModel.Security.IdentityVerifier> třídy. Koncepčně <xref:System.ServiceModel.Security.IdentityVerifier> třídy lze považovat za klienta služby odpovídající `AuthorizationManager` třídy. Následující příklad kódu ukazuje implementaci `OrgEndpointIdentity`, která ukládá název organizace tak, aby odpovídaly v názvu subjektu certifikátu serveru. Probíhá kontrola autorizace pro název organizace `CheckAccess` metodu na `CustomIdentityVerifier` třídy.

```csharp
// This custom EndpointIdentity stores an organization name
public class OrgEndpointIdentity : EndpointIdentity
{
    private string orgClaim;
    public OrgEndpointIdentity(string orgName)
    {
        orgClaim = orgName;
    }
    public string OrganizationClaim
    {
        get { return orgClaim; }
        set { orgClaim = value; }
    }
}

//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to
//check that X.509 certificate's distinguished name claim contains
//the organization name e.g. the string value "O=Contoso"
class CustomIdentityVerifier : IdentityVerifier
{
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)
    {
        bool returnvalue = false;
        foreach (ClaimSet claimset in authContext.ClaimSets)
        {
            foreach (Claim claim in claimset)
            {
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")
                {
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))
                    {
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);
                        Console.WriteLine("Right: {0}", claim.Right);
                        Console.WriteLine("Resource: {0}",claim.Resource);
                        Console.WriteLine();
                        returnvalue = true;
                    }
                }
            }
        }
        return returnvalue;
    }
}
```

 Tato ukázka používá certifikát nazvaný identity.com, která je ve složce řešení Identity specifické pro jazyk.

### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači

1.  Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo [!INCLUDE[wv](../../../../includes/wv-md.md)], importovat soubor certifikátu Identity.pfx ve složce řešení Identity do úložiště LocalMachine/My (osobní) certifikátů pomocí nástroje modulu snap-in konzoly MMC. Tento soubor je chráněn heslem. Během importu, zobrazí se výzva k zadání hesla. Typ `xyz` do pole heslo. Další informace najdete v tématu [jak: Zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) tématu. Až to uděláte, spusťte Setup.bat v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce, který zkopíruje tento certifikát do úložiště CurrentUser/důvěryhodné osoby pro použití na klientovi.

2.  Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], spusťte Setup.bat ve složce instalace ukázkové uvnitř sady Visual Studio 2012 příkazový řádek s oprávněními správce. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.

    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek. Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory. Ujistěte se odebrat certifikáty spuštěním Cleanup.bat po dokončení s ukázkou. Další ukázky zabezpečení použijte stejné certifikáty.  
  
3.  Spusťte v adresáři \service\bin Service.exe. Ujistěte se, že služba označuje, že je připravená a zobrazí výzva ke stisknutí klávesy \<Enter > ukončení služby.  
  
4.  Spusťte Client.exe z adresáře \client\bin nebo stisknutím klávesy F5 v sadě Visual Studio k vytvoření a spuštění. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
5.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1.  Před sestavením klientské části Ukázky, nezapomeňte změnit hodnotu pro adresu koncového bodu služby v souboru Client.cs `CallServiceCustomClientIdentity` metody. Potom sestavte ukázku.  
  
2.  Vytvoření adresáře na počítači se službou.  
  
3.  Zkopírujte soubory programu služby z service\bin do adresáře na počítači se službou. Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.  
  
4.  Vytvoření adresáře v klientském počítači pro binární soubory klienta.  
  
5.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.  
  
6.  Ve službě, spusťte `setup.bat service` otevřeného v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby. Existuje více instancí, které musí být změněny.  
  
9. Na straně klienta spouštění ImportServiceCert.bat v příkazovém řádku pro vývojáře pro sadu Visual Studio otevřeného s oprávněními správce. To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
10. Na počítači se službou spusťte Service.exe z příkazového řádku.  
  
11. Na klientském počítači spusťte Client.exe z příkazového řádku. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
-   Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích. Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="see-also"></a>Viz také
