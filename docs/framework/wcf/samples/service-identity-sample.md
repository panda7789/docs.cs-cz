---
title: Ukázka identity služby
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 375246127b6b39440360f48fc7b24bd0388a35e5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347928"
---
# <a name="service-identity-sample"></a>Ukázka identity služby
Tato ukázka identity služby ukazuje, jak nastavit identitu pro službu. V době návrhu může klient získat identitu pomocí metadat služby a pak za běhu může ověřit identitu služby. Pojmem identity služby je umožněno klientovi ověřit službu před voláním jakékoli jeho operace, což zajistí ochranu klienta před neověřenými voláními. V zabezpečeném připojení služba také ověřuje přihlašovací údaje klienta, a to ještě před tím, než jim povolí přístup, ale tato ukázka se nezaměřuje. Podívejte se na ukázky v [klientovi](../../../../docs/framework/wcf/samples/client.md) , které ukazují ověřování serveru.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

 Tato ukázka ilustruje následující funkce:

- Jak nastavit různé typy identit na různých koncových bodech pro službu. Každý typ identity má různé možnosti. Typ identity, který se má použít, závisí na typu přihlašovacích údajů zabezpečení použitých ve vazbě koncového bodu.

- Identita může být buď nastavena deklarativně v konfiguraci, nebo imperativně v kódu. Obvykle pro klienta i službu, které byste měli použít k nastavení identity.

- Jak nastavit vlastní identitu na klientovi. Vlastní identita je typicky přizpůsobení stávajícího typu identity, který klientovi umožňuje prozkoumávat jiné informace o deklaracích identity, které jsou uvedené v přihlašovacích údajích služby, aby bylo možné ověřit autorizační rozhodnutí před voláním služby.

    > [!NOTE]
    > Tato ukázka ověří identitu konkrétního certifikátu s názvem identity.com a klíč RSA obsažený v tomto certifikátu. Při použití certifikátů a typů identit RSA v konfiguraci na klientovi je snadné získat tyto hodnoty pomocí nástroje WSDL pro službu, kde jsou tyto hodnoty serializovány.

 Následující vzorový kód ukazuje, jak nakonfigurovat identitu koncového bodu služby pomocí serveru DNS (Domain Name Server) certifikátu pomocí WSHttpBinding.

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 Identitu je také možné zadat v konfiguračním souboru App. config. Následující příklad ukazuje, jak nastavit identitu hlavního názvu uživatele (UPN) pro koncový bod služby.

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

 Vlastní identitu lze nastavit v klientovi odvozením z <xref:System.ServiceModel.EndpointIdentity> a <xref:System.ServiceModel.Security.IdentityVerifier>ch tříd. Koncepční třídu <xref:System.ServiceModel.Security.IdentityVerifier> lze považovat za ekvivalent klienta `AuthorizationManager` třídy služby. Následující příklad kódu ukazuje implementaci `OrgEndpointIdentity`, která ukládá název organizace, který se bude shodovat s názvem subjektu certifikátu serveru. Ověření autorizace pro název organizace se vyskytuje v metodě `CheckAccess` třídy `CustomIdentityVerifier`.

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

 V této ukázce se používá certifikát s názvem identity.com, který je ve složce řešení identity pro konkrétní jazyk.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači

1. V [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo Windows Vista importujte soubor certifikátu identity. pfx do složky řešení identity do úložiště certifikátů LocalMachine/my (osobní) pomocí nástroje snap-in konzoly MMC. Tento soubor je chráněný heslem. Během importu se zobrazí výzva k zadání hesla. Do pole heslo zadejte `xyz`. Další informace najdete v tématu [Postupy: zobrazení certifikátů pomocí modulu snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) . Až to uděláte, spusťte Setup. bat ve Developer Command Prompt pro Visual Studio s oprávněními správce, který tento certifikát zkopíruje do úložiště CurrentUser/Důvěryhodné osoby pro použití v klientovi.

2. V systému Windows Server 2003 spusťte instalační program Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012 s oprávněními správce. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.

    > [!NOTE]
    > Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012. Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat. Po dokončení ukázky se ujistěte, že jste odebrali certifikáty spuštěním souboru Cleanup. bat. Další ukázky zabezpečení používají stejné certifikáty.  
  
3. Z adresáře \service\bin spusťte Service. exe. Ujistěte se, že služba indikuje, že je připravena, a zobrazí výzvu ke stisknutí klávesy \<Enter > k ukončení služby.  
  
4. Spusťte soubor Client. exe z adresáře \client\bin nebo stiskněte klávesu F5 v aplikaci Visual Studio a sestavte a spusťte. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
5. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Před sestavou klientské části Ukázky nezapomeňte změnit hodnotu adresy koncového bodu služby v souboru Client.cs v metodě `CallServiceCustomClientIdentity`. Pak Sestavte ukázku.  
  
2. Vytvořte adresář na počítači služby.  
  
3. Zkopírujte programové soubory služby z service\bin do adresáře na počítači služby. Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.  
  
4. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
5. Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači. Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.  
  
6. Ve službě spusťte `setup.bat service` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce. Spuštění `setup.bat` s argumentem `service` vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.  
  
7. Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.  
  
8. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby. Existuje více instancí, které je třeba změnit.  
  
9. Na straně klienta spusťte ImportServiceCert. bat ve Developer Command Prompt pro Visual Studio otevřené s oprávněními správce. Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.  
  
10. Na počítači služby spusťte z příkazového řádku Service. exe.  
  
11. V klientském počítači spusťte z příkazového řádku soubor Client. exe. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Po dokončení ukázky spusťte na složce Samples Cleanup. bat.  
  
    > [!NOTE]
    > Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi. Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
