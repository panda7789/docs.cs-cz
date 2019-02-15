---
title: Ukázka identity služby
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 33d3344e6a74e2afa9ad36f9df2e36eb8e1cb17b
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303891"
---
# <a name="service-identity-sample"></a><span data-ttu-id="e0d4f-102">Ukázka identity služby</span><span class="sxs-lookup"><span data-stu-id="e0d4f-102">Service Identity Sample</span></span>
<span data-ttu-id="e0d4f-103">Tato ukázka identity služby ukazuje, jak nastavit identitu služby.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="e0d4f-104">V době návrhu klient může načíst identitu pomocí metadat služby a za běhu pak se klient může ověřit identitu služby.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="e0d4f-105">Koncept identitu služby je umožnit klient k ověření služby před voláním některé z jeho operace, a tím chrání před neověřená volání klienta.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="e0d4f-106">Na zabezpečeném připojení služby také ověří přihlašovací údaje klienta před povolením přístupu, ale nejedná se o fokus této ukázky.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="e0d4f-107">Zobrazit ukázky [klienta](../../../../docs/framework/wcf/samples/client.md) , které zobrazí ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>

> [!NOTE]
>  <span data-ttu-id="e0d4f-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="e0d4f-109">Tato ukázka ilustruje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="e0d4f-109">This sample illustrates the following features:</span></span>

-   <span data-ttu-id="e0d4f-110">Jak nastavit různé typy identit na různých koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="e0d4f-111">Každý typ identity má různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="e0d4f-112">Typ identity použití je závislá na typu zabezpečovací přihlašovací údaje použité pro vazbu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>

-   <span data-ttu-id="e0d4f-113">Identity můžete buď nastavit deklarativně v konfiguraci nebo imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="e0d4f-114">Obvykle byste měli klienta a služby použít konfiguraci nastavení identity.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>

-   <span data-ttu-id="e0d4f-115">Jak nastavit vlastní identitu na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="e0d4f-116">Přizpůsobení existujícího typu identita, která umožňuje klientovi zkontrolujte přihlašovací údaje služby pro rozhodnutí o autorizaci před voláním služby k dispozici další informace o deklaraci identity je obvykle vlastní identitu.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="e0d4f-117">Tato ukázka ověří identitu konkrétní certifikát nazvaný identity.com a klíče RSA, které jsou obsaženy v rámci tohoto certifikátu.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="e0d4f-118">Při použití typů identity certifikát a RSA v konfigurace na straně klienta, snadný způsob, jak získat tyto hodnoty je ke kontrole WSDL pro službu, kde jsou tyto hodnoty serializovat.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>

 <span data-ttu-id="e0d4f-119">Následující ukázkový kód ukazuje, jak nakonfigurovat identitu koncového bodu služby se serveru DNS (Domain Name) WSHttpBinding pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 <span data-ttu-id="e0d4f-120">Identitu můžete také uvést v konfiguraci v souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="e0d4f-121">Následující příklad ukazuje, jak nastavit identita UPN (hlavní název uživatele) pro koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>

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

 <span data-ttu-id="e0d4f-122">Vlastní identity můžete nastavit na straně klienta odvozením z <xref:System.ServiceModel.EndpointIdentity> a <xref:System.ServiceModel.Security.IdentityVerifier> třídy.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="e0d4f-123">Koncepčně <xref:System.ServiceModel.Security.IdentityVerifier> třídy lze považovat za klienta služby odpovídající `AuthorizationManager` třídy.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="e0d4f-124">Následující příklad kódu ukazuje implementaci `OrgEndpointIdentity`, která ukládá název organizace tak, aby odpovídaly v názvu subjektu certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="e0d4f-125">Probíhá kontrola autorizace pro název organizace `CheckAccess` metodu na `CustomIdentityVerifier` třídy.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>

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

 <span data-ttu-id="e0d4f-126">Tato ukázka používá certifikát nazvaný identity.com, která je ve složce řešení Identity specifické pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e0d4f-127">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="e0d4f-127">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="e0d4f-128">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0d4f-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="e0d4f-129">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0d4f-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3.  <span data-ttu-id="e0d4f-130">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0d4f-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="e0d4f-131">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="e0d4f-131">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="e0d4f-132">Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo [!INCLUDE[wv](../../../../includes/wv-md.md)], importovat soubor certifikátu Identity.pfx ve složce řešení Identity do úložiště LocalMachine/My (osobní) certifikátů pomocí nástroje modulu snap-in konzoly MMC.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or [!INCLUDE[wv](../../../../includes/wv-md.md)], import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="e0d4f-133">Tento soubor je chráněn heslem.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-133">This file is password protected.</span></span> <span data-ttu-id="e0d4f-134">Během importu, zobrazí se výzva k zadání hesla.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-134">During the import you are asked for a password.</span></span> <span data-ttu-id="e0d4f-135">Typ `xyz` do pole heslo.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="e0d4f-136">Další informace najdete v tématu [jak: Zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="e0d4f-137">Až to uděláte, spusťte Setup.bat v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce, který zkopíruje tento certifikát do úložiště CurrentUser/důvěryhodné osoby pro použití na klientovi.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-137">Once this is done, run Setup.bat in a Developer Command Prompt for Visual Studio with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>

2.  <span data-ttu-id="e0d4f-138">Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], spusťte Setup.bat ve složce instalace ukázkové uvnitř sady Visual Studio 2012 příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt with administrator privileges.</span></span> <span data-ttu-id="e0d4f-139">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-139">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="e0d4f-140">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-140">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="e0d4f-141">Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-141">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="e0d4f-142">Ujistěte se odebrat certifikáty spuštěním Cleanup.bat po dokončení s ukázkou.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="e0d4f-143">Další ukázky zabezpečení použijte stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-143">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="e0d4f-144">Spusťte v adresáři \service\bin Service.exe.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="e0d4f-145">Ujistěte se, že služba označuje, že je připravená a zobrazí výzva ke stisknutí klávesy \<Enter > ukončení služby.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4.  <span data-ttu-id="e0d4f-146">Spusťte Client.exe z adresáře \client\bin nebo stisknutím klávesy F5 v sadě Visual Studio k vytvoření a spuštění.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="e0d4f-147">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-147">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="e0d4f-148">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e0d4f-148">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="e0d4f-149">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="e0d4f-149">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="e0d4f-150">Před sestavením klientské části Ukázky, nezapomeňte změnit hodnotu pro adresu koncového bodu služby v souboru Client.cs `CallServiceCustomClientIdentity` metody.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="e0d4f-151">Potom sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-151">Then build the sample.</span></span>  
  
2.  <span data-ttu-id="e0d4f-152">Vytvoření adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-152">Create a directory on the service computer.</span></span>  
  
3.  <span data-ttu-id="e0d4f-153">Zkopírujte soubory programu služby z service\bin do adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="e0d4f-154">Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4.  <span data-ttu-id="e0d4f-155">Vytvoření adresáře v klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5.  <span data-ttu-id="e0d4f-156">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="e0d4f-157">Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6.  <span data-ttu-id="e0d4f-158">Ve službě, spusťte `setup.bat service` otevřeného v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-158">On the service, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="e0d4f-159">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7.  <span data-ttu-id="e0d4f-160">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="e0d4f-161">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="e0d4f-162">Existuje více instancí, které musí být změněny.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="e0d4f-163">Na straně klienta spouštění ImportServiceCert.bat v příkazovém řádku pro vývojáře pro sadu Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-163">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="e0d4f-164">To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="e0d4f-165">Na počítači se službou spusťte Service.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="e0d4f-166">Na klientském počítači spusťte Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="e0d4f-167">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e0d4f-167">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e0d4f-168">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="e0d4f-168">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="e0d4f-169">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0d4f-170">Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="e0d4f-171">Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-171">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="e0d4f-172">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="e0d4f-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0d4f-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0d4f-173">See also</span></span>
