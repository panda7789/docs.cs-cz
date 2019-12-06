---
title: Ukázka identity služby
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: eb2dd3c6392164905cf755075856608ec5fcaf30
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837789"
---
# <a name="service-identity-sample"></a><span data-ttu-id="8d05d-102">Ukázka identity služby</span><span class="sxs-lookup"><span data-stu-id="8d05d-102">Service Identity Sample</span></span>
<span data-ttu-id="8d05d-103">Tato ukázka identity služby ukazuje, jak nastavit identitu pro službu.</span><span class="sxs-lookup"><span data-stu-id="8d05d-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="8d05d-104">V době návrhu může klient získat identitu pomocí metadat služby a pak za běhu může ověřit identitu služby.</span><span class="sxs-lookup"><span data-stu-id="8d05d-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="8d05d-105">Pojmem identity služby je umožněno klientovi ověřit službu před voláním jakékoli jeho operace, což zajistí ochranu klienta před neověřenými voláními.</span><span class="sxs-lookup"><span data-stu-id="8d05d-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="8d05d-106">V zabezpečeném připojení služba také ověřuje přihlašovací údaje klienta, a to ještě před tím, než jim povolí přístup, ale tato ukázka se nezaměřuje.</span><span class="sxs-lookup"><span data-stu-id="8d05d-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="8d05d-107">Podívejte se na ukázky v [klientovi](../../../../docs/framework/wcf/samples/client.md) , které ukazují ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="8d05d-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="8d05d-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8d05d-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="8d05d-109">Tato ukázka ilustruje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="8d05d-109">This sample illustrates the following features:</span></span>

- <span data-ttu-id="8d05d-110">Jak nastavit různé typy identit na různých koncových bodech pro službu.</span><span class="sxs-lookup"><span data-stu-id="8d05d-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="8d05d-111">Každý typ identity má různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="8d05d-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="8d05d-112">Typ identity, který se má použít, závisí na typu přihlašovacích údajů zabezpečení použitých ve vazbě koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8d05d-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>

- <span data-ttu-id="8d05d-113">Identita může být buď nastavena deklarativně v konfiguraci, nebo imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="8d05d-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="8d05d-114">Obvykle pro klienta i službu, které byste měli použít k nastavení identity.</span><span class="sxs-lookup"><span data-stu-id="8d05d-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>

- <span data-ttu-id="8d05d-115">Jak nastavit vlastní identitu na klientovi.</span><span class="sxs-lookup"><span data-stu-id="8d05d-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="8d05d-116">Vlastní identita je typicky přizpůsobení stávajícího typu identity, který klientovi umožňuje prozkoumávat jiné informace o deklaracích identity, které jsou uvedené v přihlašovacích údajích služby, aby bylo možné ověřit autorizační rozhodnutí před voláním služby.</span><span class="sxs-lookup"><span data-stu-id="8d05d-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8d05d-117">Tato ukázka ověří identitu konkrétního certifikátu s názvem identity.com a klíč RSA obsažený v tomto certifikátu.</span><span class="sxs-lookup"><span data-stu-id="8d05d-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="8d05d-118">Při použití certifikátů a typů identit RSA v konfiguraci na klientovi je snadné získat tyto hodnoty pomocí nástroje WSDL pro službu, kde jsou tyto hodnoty serializovány.</span><span class="sxs-lookup"><span data-stu-id="8d05d-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>

 <span data-ttu-id="8d05d-119">Následující vzorový kód ukazuje, jak nakonfigurovat identitu koncového bodu služby pomocí serveru DNS (Domain Name Server) certifikátu pomocí WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="8d05d-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 <span data-ttu-id="8d05d-120">Identitu je také možné zadat v konfiguračním souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="8d05d-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="8d05d-121">Následující příklad ukazuje, jak nastavit identitu hlavního názvu uživatele (UPN) pro koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="8d05d-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>

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

 <span data-ttu-id="8d05d-122">Vlastní identitu lze nastavit v klientovi odvozením z <xref:System.ServiceModel.EndpointIdentity> a <xref:System.ServiceModel.Security.IdentityVerifier>ch tříd.</span><span class="sxs-lookup"><span data-stu-id="8d05d-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="8d05d-123">Koncepční třídu <xref:System.ServiceModel.Security.IdentityVerifier> lze považovat za ekvivalent klienta `AuthorizationManager` třídy služby.</span><span class="sxs-lookup"><span data-stu-id="8d05d-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="8d05d-124">Následující příklad kódu ukazuje implementaci `OrgEndpointIdentity`, která ukládá název organizace, který se bude shodovat s názvem subjektu certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="8d05d-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="8d05d-125">Ověření autorizace pro název organizace se vyskytuje v metodě `CheckAccess` třídy `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="8d05d-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>

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

 <span data-ttu-id="8d05d-126">V této ukázce se používá certifikát s názvem identity.com, který je ve složce řešení identity pro konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="8d05d-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8d05d-127">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="8d05d-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8d05d-128">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8d05d-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="8d05d-129">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8d05d-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="8d05d-130">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8d05d-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="8d05d-131">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="8d05d-131">To run the sample on the same computer</span></span>

1. <span data-ttu-id="8d05d-132">V [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo Windows Vista importujte soubor certifikátu identity. pfx do složky řešení identity do úložiště certifikátů LocalMachine/my (osobní) pomocí nástroje snap-in konzoly MMC.</span><span class="sxs-lookup"><span data-stu-id="8d05d-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or Windows Vista, import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="8d05d-133">Tento soubor je chráněný heslem.</span><span class="sxs-lookup"><span data-stu-id="8d05d-133">This file is password protected.</span></span> <span data-ttu-id="8d05d-134">Během importu se zobrazí výzva k zadání hesla.</span><span class="sxs-lookup"><span data-stu-id="8d05d-134">During the import you are asked for a password.</span></span> <span data-ttu-id="8d05d-135">Do pole heslo zadejte `xyz`.</span><span class="sxs-lookup"><span data-stu-id="8d05d-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="8d05d-136">Další informace najdete v tématu [Postupy: zobrazení certifikátů pomocí modulu snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) .</span><span class="sxs-lookup"><span data-stu-id="8d05d-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="8d05d-137">Až to uděláte, spusťte Setup. bat ve Developer Command Prompt pro Visual Studio s oprávněními správce, který tento certifikát zkopíruje do úložiště CurrentUser/Důvěryhodné osoby pro použití v klientovi.</span><span class="sxs-lookup"><span data-stu-id="8d05d-137">Once this is done, run Setup.bat in a Developer Command Prompt for Visual Studio with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>

2. <span data-ttu-id="8d05d-138">Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012 s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="8d05d-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt with administrator privileges.</span></span> <span data-ttu-id="8d05d-139">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="8d05d-139">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8d05d-140">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="8d05d-140">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="8d05d-141">Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="8d05d-141">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="8d05d-142">Po dokončení ukázky se ujistěte, že jste odebrali certifikáty spuštěním souboru Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="8d05d-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="8d05d-143">Další ukázky zabezpečení používají stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="8d05d-143">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="8d05d-144">Z adresáře \service\bin spusťte Service. exe.</span><span class="sxs-lookup"><span data-stu-id="8d05d-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="8d05d-145">Ujistěte se, že služba indikuje, že je připravena, a zobrazí výzvu ke stisknutí klávesy \<Enter > k ukončení služby.</span><span class="sxs-lookup"><span data-stu-id="8d05d-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4. <span data-ttu-id="8d05d-146">Spusťte soubor Client. exe z adresáře \client\bin nebo stiskněte klávesu F5 v aplikaci Visual Studio a sestavte a spusťte.</span><span class="sxs-lookup"><span data-stu-id="8d05d-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="8d05d-147">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="8d05d-147">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="8d05d-148">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="8d05d-148">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="8d05d-149">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="8d05d-149">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="8d05d-150">Před sestavou klientské části Ukázky nezapomeňte změnit hodnotu adresy koncového bodu služby v souboru Client.cs v metodě `CallServiceCustomClientIdentity`.</span><span class="sxs-lookup"><span data-stu-id="8d05d-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="8d05d-151">Pak Sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="8d05d-151">Then build the sample.</span></span>  
  
2. <span data-ttu-id="8d05d-152">Vytvořte adresář na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="8d05d-152">Create a directory on the service computer.</span></span>  
  
3. <span data-ttu-id="8d05d-153">Zkopírujte programové soubory služby z service\bin do adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="8d05d-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="8d05d-154">Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="8d05d-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4. <span data-ttu-id="8d05d-155">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="8d05d-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5. <span data-ttu-id="8d05d-156">Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="8d05d-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="8d05d-157">Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="8d05d-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6. <span data-ttu-id="8d05d-158">Ve službě spusťte `setup.bat service` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="8d05d-158">On the service, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="8d05d-159">Spuštění `setup.bat` s argumentem `service` vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.</span><span class="sxs-lookup"><span data-stu-id="8d05d-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7. <span data-ttu-id="8d05d-160">Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="8d05d-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="8d05d-161">V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="8d05d-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="8d05d-162">Existuje více instancí, které je třeba změnit.</span><span class="sxs-lookup"><span data-stu-id="8d05d-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="8d05d-163">Na straně klienta spusťte ImportServiceCert. bat ve Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="8d05d-163">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="8d05d-164">Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="8d05d-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="8d05d-165">Na počítači služby spusťte z příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="8d05d-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="8d05d-166">V klientském počítači spusťte z příkazového řádku soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="8d05d-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="8d05d-167">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="8d05d-167">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="8d05d-168">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="8d05d-168">To clean up after the sample</span></span>  
  
- <span data-ttu-id="8d05d-169">Po dokončení ukázky spusťte na složce Samples Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="8d05d-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8d05d-170">Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi.</span><span class="sxs-lookup"><span data-stu-id="8d05d-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="8d05d-171">Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="8d05d-171">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="8d05d-172">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="8d05d-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
