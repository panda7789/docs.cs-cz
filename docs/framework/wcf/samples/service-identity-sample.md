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
ms.workload: dotnet
ms.openlocfilehash: 5a89839294f74d733ec7f607a0afda53148fbd57
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="service-identity-sample"></a><span data-ttu-id="3fb8d-102">Ukázka identity služby</span><span class="sxs-lookup"><span data-stu-id="3fb8d-102">Service Identity Sample</span></span>
<span data-ttu-id="3fb8d-103">Tato ukázka identity služby ukazuje, jak nastavení identity pro službu.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="3fb8d-104">V době návrhu klient může načíst identitu pomocí metadat služby a pak v době běhu může klient ověřit identitu služby.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="3fb8d-105">Koncept identita služby je umožnit klienta k ověření služby před voláním kteroukoli z jeho operací, a chránit proti neověřená volání klienta.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="3fb8d-106">Na zabezpečeném připojení služby také ověří pověření klienta dřív, než ji povolí přístup, ale nejedná se fokus této ukázky.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="3fb8d-107">Najdete v části Ukázky [klienta](../../../../docs/framework/wcf/samples/client.md) , zobrazit ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fb8d-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3fb8d-109">Tato ukázka znázorňuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="3fb8d-109">This sample illustrates the following features:</span></span>  
  
-   <span data-ttu-id="3fb8d-110">Jak nastavit různé typy identity na jiný koncové body pro službu.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="3fb8d-111">Každý typ identity má různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="3fb8d-112">Typ identity používat je závislá na typu zabezpečení pověření používaná na vazby pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>  
  
-   <span data-ttu-id="3fb8d-113">Identitu můžete buď nastavit deklarativně v konfiguraci nebo imperativní v kódu.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="3fb8d-114">Obvykle pro klienta a služby využít konfigurace nastavení identity.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>  
  
-   <span data-ttu-id="3fb8d-115">Jak nastavit vlastní identitu na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="3fb8d-116">Přizpůsobení existujícího typu identity, která umožňuje klientovi vyhledejte další informace o deklaraci identity, který je zadaný v přihlašovacích údajích služby pro autorizační rozhodnutí před volání služby je obvykle vlastní identitu.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3fb8d-117">Tato ukázka ověří identitu konkrétní certifikát nazvaný identity.com a klíče RSA obsažené v rámci tohoto certifikátu.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="3fb8d-118">Při použití typů identit certifikát a RSA v konfiguraci na straně klienta, snadný způsob, jak získat tyto hodnoty je kontrola WSDL pro službu, kde jsou tyto hodnoty serializovat.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>  
  
 <span data-ttu-id="3fb8d-119">Následující vzorový kód ukazuje, jak nakonfigurovat identitu koncového bodu služby se serveru DNS (Domain Name) WSHttpBinding pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>  
  
```  
//Create a service endpoint and set its identity to the certificate's DNS                 
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);  
// Client are Anonymous to the service  
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;  
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);  
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));  
ep.Address = epa;  
```  
  
 <span data-ttu-id="3fb8d-120">Identity lze zadat také v konfiguraci v souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="3fb8d-121">Následující příklad ukazuje, jak nastavit identitu hlavní název uživatele (hlavní název uživatele) pro koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>  
  
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
  
 <span data-ttu-id="3fb8d-122">Vlastní identitu můžete nastavit na straně klienta odvozené z <xref:System.ServiceModel.EndpointIdentity> a <xref:System.ServiceModel.Security.IdentityVerifier> třídy.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="3fb8d-123">Koncepčně <xref:System.ServiceModel.Security.IdentityVerifier> třídy lze považovat za klienta ekvivalentní služby `AuthorizationManager` třídy.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="3fb8d-124">Následující příklad kódu ukazuje implementaci `OrgEndpointIdentity`, která ukládá název organizace tak, aby odpovídaly v názvu subjektu certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="3fb8d-125">Kontrola autorizace pro název organizace probíhá v `CheckAccess` metodu `CustomIdentityVerifier` třídy.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>  
  
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
  
 <span data-ttu-id="3fb8d-126">Tato ukázka používá certifikát nazvaný identity.com, což je ve složce řešení Identity konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3fb8d-127">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="3fb8d-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3fb8d-128">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fb8d-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="3fb8d-129">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fb8d-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="3fb8d-130">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fb8d-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="3fb8d-131">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="3fb8d-131">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="3fb8d-132">Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo [!INCLUDE[wv](../../../../includes/wv-md.md)], importovat soubor certifikátu Identity.pfx ve složce řešení Identity do úložiště certifikátů LocalMachine/My (osobní) pomocí modulu snap-in nástroje konzoly MMC.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or [!INCLUDE[wv](../../../../includes/wv-md.md)], import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="3fb8d-133">Tento soubor je chráněný heslem.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-133">This file is password protected.</span></span> <span data-ttu-id="3fb8d-134">Během importu se zobrazí výzva k zadání hesla.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-134">During the import you are asked for a password.</span></span> <span data-ttu-id="3fb8d-135">Typ `xyz` do pole heslo.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="3fb8d-136">Další informace najdete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="3fb8d-137">Až bude vše Hotovo, spusťte v příkazovém řádku Visual Studio s oprávněními správce, který kopíruje tento certifikát do úložiště CurrentUser nebo důvěryhodné osoby pro použití na klientovi Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-137">Once this is done, run Setup.bat in a Visual Studio command prompt with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>  
  
2.  <span data-ttu-id="3fb8d-138">Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], spusťte Setup.bat ze složky instalace ukázkové uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt with administrator privileges.</span></span> <span data-ttu-id="3fb8d-139">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-139">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3fb8d-140">Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-140">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="3fb8d-141">Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-141">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="3fb8d-142">Ujistěte se, spuštěním Cleanup.bat po dokončení s ukázkou certifikáty odebrat.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="3fb8d-143">Další ukázky zabezpečení použijte stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-143">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="3fb8d-144">Spusťte Service.exe z adresáře \service\bin.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="3fb8d-145">Ujistěte se, že službu označuje je připravené a zobrazí výzvu k stiskněte klávesu \<Enter > ukončit službu.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4.  <span data-ttu-id="3fb8d-146">Spusťte Client.exe z adresáře \client\bin nebo stisknutím klávesy F5 ve Visual Studiu sestavit a spustit.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="3fb8d-147">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-147">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="3fb8d-148">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="3fb8d-148">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="3fb8d-149">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="3fb8d-149">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="3fb8d-150">Před vytvořením klienta část vzorku, nezapomeňte změnit hodnotu pro adresa koncového bodu služby v souboru Client.cs ve `CallServiceCustomClientIdentity` metoda.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="3fb8d-151">Potom sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-151">Then build the sample.</span></span>  
  
2.  <span data-ttu-id="3fb8d-152">Vytvořte adresář na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-152">Create a directory on the service computer.</span></span>  
  
3.  <span data-ttu-id="3fb8d-153">Zkopírujte soubory programu služby z service\bin do adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="3fb8d-154">Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4.  <span data-ttu-id="3fb8d-155">Vytvořte adresář na klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5.  <span data-ttu-id="3fb8d-156">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="3fb8d-157">Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6.  <span data-ttu-id="3fb8d-158">Na službu, spusťte `setup.bat service` ve z příkazového řádku Visual Studia otevřen s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-158">On the service, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="3fb8d-159">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7.  <span data-ttu-id="3fb8d-160">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="3fb8d-161">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="3fb8d-162">Existuje více instancí, které je potřeba změnit.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="3fb8d-163">V klientovi spusťte ImportServiceCert.bat v z příkazového řádku Visual Studia otevřít s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-163">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="3fb8d-164">Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="3fb8d-165">Na počítači se službou spusťte Service.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="3fb8d-166">Na klientském počítači spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="3fb8d-167">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="3fb8d-167">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="3fb8d-168">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="3fb8d-168">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="3fb8d-169">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3fb8d-170">Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="3fb8d-171">Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-171">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="3fb8d-172">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="3fb8d-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb8d-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fb8d-173">See Also</span></span>
