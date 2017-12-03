---
title: "Ukázka identity služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cde8966e89a22b19109688d5da0ff5b45eee55ef
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="service-identity-sample"></a>Ukázka identity služby
Tato ukázka identity služby ukazuje, jak nastavení identity pro službu. V době návrhu klient může načíst identitu pomocí metadat služby a pak v době běhu může klient ověřit identitu služby. Koncept identita služby je umožnit klienta k ověření služby před voláním kteroukoli z jeho operací, a chránit proti neověřená volání klienta. Na zabezpečeném připojení služby také ověří pověření klienta dřív, než ji povolí přístup, ale nejedná se fokus této ukázky. Najdete v části Ukázky [klienta](../../../../docs/framework/wcf/samples/client.md) , zobrazit ověřování serveru.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka znázorňuje následující funkce:  
  
-   Jak nastavit různé typy identity na jiný koncové body pro službu. Každý typ identity má různé možnosti. Typ identity používat je závislá na typu zabezpečení pověření používaná na vazby pro koncový bod.  
  
-   Identitu můžete buď nastavit deklarativně v konfiguraci nebo imperativní v kódu. Obvykle pro klienta a služby využít konfigurace nastavení identity.  
  
-   Jak nastavit vlastní identitu na straně klienta. Přizpůsobení existujícího typu identity, která umožňuje klientovi vyhledejte další informace o deklaraci identity, který je zadaný v přihlašovacích údajích služby pro autorizační rozhodnutí před volání služby je obvykle vlastní identitu.  
  
    > [!NOTE]
    >  Tato ukázka ověří identitu konkrétní certifikát nazvaný identity.com a klíče RSA obsažené v rámci tohoto certifikátu. Při použití typů identit certifikát a RSA v konfiguraci na straně klienta, snadný způsob, jak získat tyto hodnoty je kontrola WSDL pro službu, kde jsou tyto hodnoty serializovat.  
  
 Následující vzorový kód ukazuje, jak nakonfigurovat identitu koncového bodu služby se serveru DNS (Domain Name) WSHttpBinding pomocí certifikátu.  
  
```  
//Create a service endpoint and set its identity to the certificate's DNS                 
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);  
// Client are Anonymous to the service  
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;  
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);  
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));  
ep.Address = epa;  
```  
  
 Identity lze zadat také v konfiguraci v souboru App.config. Následující příklad ukazuje, jak nastavit identitu hlavní název uživatele (hlavní název uživatele) pro koncový bod služby.  
  
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
  
 Vlastní identitu můžete nastavit na straně klienta odvozené z <xref:System.ServiceModel.EndpointIdentity> a <xref:System.ServiceModel.Security.IdentityVerifier> třídy. Koncepčně <xref:System.ServiceModel.Security.IdentityVerifier> třídy lze považovat za klienta ekvivalentní služby `AuthorizationManager` třídy. Následující příklad kódu ukazuje implementaci `OrgEndpointIdentity`, která ukládá název organizace tak, aby odpovídaly v názvu subjektu certifikátu serveru. Kontrola autorizace pro název organizace probíhá v `CheckAccess` metodu `CustomIdentityVerifier` třídy.  
  
```  
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
  
 Tato ukázka používá certifikát nazvaný identity.com, což je ve složce řešení Identity konkrétní jazyk.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo [!INCLUDE[wv](../../../../includes/wv-md.md)], importovat soubor certifikátu Identity.pfx ve složce řešení Identity do úložiště certifikátů LocalMachine/My (osobní) pomocí modulu snap-in nástroje konzoly MMC. Tento soubor je chráněný heslem. Během importu se zobrazí výzva k zadání hesla. Typ `xyz` do pole heslo. Další informace najdete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) tématu. Až bude vše Hotovo, spusťte v příkazovém řádku Visual Studio s oprávněními správce, který kopíruje tento certifikát do úložiště CurrentUser nebo důvěryhodné osoby pro použití na klientovi Setup.bat.  
  
2.  Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], spusťte Setup.bat ze složky instalace ukázkové uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek s oprávněními správce. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory. Ujistěte se, spuštěním Cleanup.bat po dokončení s ukázkou certifikáty odebrat. Další ukázky zabezpečení použijte stejné certifikáty.  
  
3.  Spusťte Service.exe z adresáře \service\bin. Ujistěte se, že službu označuje je připravené a zobrazí výzvu k stiskněte klávesu \<Enter > ukončit službu.  
  
4.  Spusťte Client.exe z adresáře \client\bin nebo stisknutím klávesy F5 ve Visual Studiu sestavit a spustit. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
5.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Před vytvořením klienta část vzorku, nezapomeňte změnit hodnotu pro adresa koncového bodu služby v souboru Client.cs ve `CallServiceCustomClientIdentity` metoda. Potom sestavte ukázku.  
  
2.  Vytvořte adresář na počítači se službou.  
  
3.  Zkopírujte soubory programu služby z service\bin do adresáře na počítači se službou. Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.  
  
4.  Vytvořte adresář na klientském počítači pro binární soubory klienta.  
  
5.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
6.  Na službu, spusťte `setup.bat service` ve z příkazového řádku Visual Studia otevřen s oprávněními správce. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby. Existuje více instancí, které je potřeba změnit.  
  
9. V klientovi spusťte ImportServiceCert.bat v z příkazového řádku Visual Studia otevřít s oprávněními správce. Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
10. Na počítači se službou spusťte Service.exe z příkazového řádku.  
  
11. Na klientském počítači spusťte z příkazového řádku Client.exe. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači. Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Viz také
