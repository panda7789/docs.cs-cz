---
title: Ukázka zabezpečení zpráv
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: a4835f8f276786aa87506bc2be2a2bba534f4166
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112473"
---
# <a name="message-security-sample"></a><span data-ttu-id="f88d3-102">Ukázka zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="f88d3-102">Message Security Sample</span></span>
<span data-ttu-id="f88d3-103">Tato ukázka předvádí, jak implementovat aplikaci, která se používá `basicHttpBinding` a zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="f88d3-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="f88d3-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="f88d3-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f88d3-105">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f88d3-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f88d3-106">Režim zabezpečení `basicHttpBinding` můžete nastavit následující hodnoty: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` a `None`.</span><span class="sxs-lookup"><span data-stu-id="f88d3-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="f88d3-107">V následující ukázka service souboru App.config, určuje definice koncového bodu `basicHttpBinding` a odkazuje na vazbu konfigurace s názvem `Binding1`, jak je znázorněno v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="f88d3-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="f88d3-108">Nastaví konfiguraci vazby `mode` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) k `Message` a nastaví `clientCredentialType` atribut [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)k `Certificate` jak je znázorněno v následující ukázková konfigurace:</span><span class="sxs-lookup"><span data-stu-id="f88d3-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="f88d3-109">Certifikát, který službu používá ke svému ověření ke klientovi je nastavena v sekci chování konfiguračního souboru v rámci `serviceCredentials` elementu.</span><span class="sxs-lookup"><span data-stu-id="f88d3-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="f88d3-110">Režim ověřování, který se vztahuje na certifikát, který klient použije ke svému ověření ke službě je také nastavena v sekci chování v rámci `clientCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="f88d3-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"   
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication   
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="f88d3-111">Stejné informace pro vazby a zabezpečení jsou uvedeny v souboru konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="f88d3-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="f88d3-112">Identita volajícího se zobrazí v okně konzoly služby pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="f88d3-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="f88d3-113">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="f88d3-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f88d3-114">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="f88d3-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="f88d3-115">K nastavení a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="f88d3-115">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="f88d3-116">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f88d3-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f88d3-117">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f88d3-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="f88d3-118">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="f88d3-118">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="f88d3-119">Spusťte Setup.bat z instalační složky s ukázkou.</span><span class="sxs-lookup"><span data-stu-id="f88d3-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="f88d3-120">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="f88d3-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f88d3-121">Dávkový soubor Setup.bat je navržena pro spouštění na příkazovém řádku sady SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="f88d3-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="f88d3-122">To vyžaduje, aby proměnné prostředí MSSDK bodu do adresáře, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="f88d3-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="f88d3-123">Tato proměnná prostředí je nastavena automaticky v příkazovém řádku Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="f88d3-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2.  <span data-ttu-id="f88d3-124">Spusťte aplikaci služby z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="f88d3-124">Run the service application from \service\bin.</span></span>  
  
3.  <span data-ttu-id="f88d3-125">Spuštění klientské aplikace z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="f88d3-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="f88d3-126">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="f88d3-126">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="f88d3-127">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f88d3-127">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
5.  <span data-ttu-id="f88d3-128">Odeberte certifikáty spuštěním Cleanup.bat po dokončení s ukázkou.</span><span class="sxs-lookup"><span data-stu-id="f88d3-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="f88d3-129">Další ukázky zabezpečení použijte stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="f88d3-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="f88d3-130">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="f88d3-130">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="f88d3-131">Vytvoření adresáře v počítači služby pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="f88d3-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="f88d3-132">Programové soubory nástroje služby zkopírujte do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="f88d3-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="f88d3-133">Také kopírovat soubory Setup.bat Cleanup.bat a ImportClientCert.bat k serveru.</span><span class="sxs-lookup"><span data-stu-id="f88d3-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3.  <span data-ttu-id="f88d3-134">Vytvoření adresáře na klientský počítač určený k binárních souborů klienta.</span><span class="sxs-lookup"><span data-stu-id="f88d3-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="f88d3-135">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="f88d3-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="f88d3-136">Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="f88d3-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="f88d3-137">Na serveru, spusťte `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="f88d3-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="f88d3-138">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="f88d3-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="f88d3-139">Upravit Service.exe.config tak, aby odrážely nový název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) která je stejná jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="f88d3-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="f88d3-140">Také změňte hodnotu základní adresa pro zadejte název počítače plně kvalifikovaný místo localhost</span><span class="sxs-lookup"><span data-stu-id="f88d3-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost</span></span>`.`  
  
7.  <span data-ttu-id="f88d3-141">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="f88d3-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="f88d3-142">Na straně klienta, spouštění `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="f88d3-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="f88d3-143">Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="f88d3-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="f88d3-144">V souboru Client.exe.config v klientském počítači. Změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="f88d3-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="f88d3-145">Provedete to nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="f88d3-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="f88d3-146">Také změnit `findValue` atribut [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) na nový název certifikátu služby, který je plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="f88d3-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="f88d3-147">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="f88d3-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="f88d3-148">Na straně klienta spouštění ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="f88d3-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="f88d3-149">To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="f88d3-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="f88d3-150">Na serveru, spusťte ImportClientCert.bat to importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="f88d3-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="f88d3-151">Na počítači služby spusťte Service.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f88d3-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="f88d3-152">Na klientském počítači a spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f88d3-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1.  <span data-ttu-id="f88d3-153">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f88d3-153">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="f88d3-154">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="f88d3-154">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="f88d3-155">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="f88d3-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f88d3-156">Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky napříč počítači.</span><span class="sxs-lookup"><span data-stu-id="f88d3-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="f88d3-157">Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty mezi počítači, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="f88d3-157">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="f88d3-158">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad:</span><span class="sxs-lookup"><span data-stu-id="f88d3-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example:</span></span> `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
>  <span data-ttu-id="f88d3-159">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="f88d3-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f88d3-160">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f88d3-160">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f88d3-161">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f88d3-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f88d3-162">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f88d3-162">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
