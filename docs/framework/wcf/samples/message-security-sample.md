---
title: Ukázka zabezpečení zpráv
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 43e1a9104bdd44509d86bd198559c5e7477a9964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183521"
---
# <a name="message-security-sample"></a><span data-ttu-id="ce331-102">Ukázka zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="ce331-102">Message Security Sample</span></span>
<span data-ttu-id="ce331-103">Tato ukázka ukazuje, jak implementovat `basicHttpBinding` aplikaci, která používá zabezpečení a zprávy.</span><span class="sxs-lookup"><span data-stu-id="ce331-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="ce331-104">Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="ce331-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce331-105">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ce331-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ce331-106">Režim zabezpečení `basicHttpBinding` lze nastavit na následující `Message`hodnoty: `TransportWithMessageCredential` `TransportCredentialOnly` , `None` `Transport`, a .</span><span class="sxs-lookup"><span data-stu-id="ce331-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="ce331-107">V následujícím ukázkovém souboru App.config určuje `basicHttpBinding` definice koncového bodu `Binding1`a odkazuje na konfiguraci vazby s názvem , jak je znázorněno v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="ce331-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="ce331-108">Konfigurace vazby `mode` nastaví atribut [ \<>zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `clientCredentialType` `Message` a nastaví atribut `Certificate` [ \<>zprávy](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) tak, jak je znázorněno v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="ce331-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="ce331-109">Certifikát, který služba používá k ověření sám klientovi je nastavena v `serviceCredentials` části chování konfiguračního souboru pod elementem.</span><span class="sxs-lookup"><span data-stu-id="ce331-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="ce331-110">Ověřovací režim, který se vztahuje k certifikátu, který klient používá k ověření sám `clientCertificate` služby je také nastavena v části chování pod element.</span><span class="sxs-lookup"><span data-stu-id="ce331-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
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
  
 <span data-ttu-id="ce331-111">Stejné podrobnosti o vazbě a zabezpečení jsou určeny v konfiguračním souboru klienta.</span><span class="sxs-lookup"><span data-stu-id="ce331-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="ce331-112">Identita volajícího se zobrazí v okně konzoly služby pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="ce331-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="ce331-113">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ce331-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ce331-114">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="ce331-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="ce331-115">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="ce331-115">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="ce331-116">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce331-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ce331-117">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce331-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="ce331-118">Spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="ce331-118">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="ce331-119">Spusťte soubor Setup.bat z ukázkové instalační složky.</span><span class="sxs-lookup"><span data-stu-id="ce331-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="ce331-120">Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="ce331-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ce331-121">Dávkový soubor Setup.bat je určen ke spuštění z příkazového řádku sady Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="ce331-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="ce331-122">Vyžaduje, aby proměnná prostředí sady MSSDK přecšuje do adresáře, ve kterém je sada SDK nainstalována.</span><span class="sxs-lookup"><span data-stu-id="ce331-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="ce331-123">Tato proměnná prostředí je automaticky nastavena v příkazovém řádku sady Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="ce331-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2. <span data-ttu-id="ce331-124">Spusťte aplikaci služby z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="ce331-124">Run the service application from \service\bin.</span></span>  
  
3. <span data-ttu-id="ce331-125">Spusťte klientskou aplikaci z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="ce331-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="ce331-126">Aktivita klienta je zobrazena v aplikaci klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="ce331-126">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="ce331-127">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ce331-127">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
5. <span data-ttu-id="ce331-128">Po dokončení ukázky odeberte certifikáty spuštěním souboru Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="ce331-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="ce331-129">Jiné ukázky zabezpečení používají stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="ce331-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="ce331-130">Spuštění ukázky napříč počítači</span><span class="sxs-lookup"><span data-stu-id="ce331-130">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="ce331-131">Vytvořte adresář na servisním počítači pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="ce331-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="ce331-132">Zkopírujte soubory programu služby do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="ce331-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="ce331-133">Na server také zkopírujte soubory Setup.bat, Cleanup.bat a ImportClientCert.bat.</span><span class="sxs-lookup"><span data-stu-id="ce331-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3. <span data-ttu-id="ce331-134">Vytvořte adresář v klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="ce331-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="ce331-135">Zkopírujte soubory klientského programu do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="ce331-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="ce331-136">Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="ce331-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="ce331-137">Na serveru spusťte . `setup.bat service`</span><span class="sxs-lookup"><span data-stu-id="ce331-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="ce331-138">Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="ce331-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="ce331-139">Upravte service.exe.config tak, aby odrážel `findValue` nový název certifikátu (v atributu [ \<v prvku serviceCertificate>),](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="ce331-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="ce331-140">Změňte také hodnotu základní adresy a zadejte plně kvalifikovaný název počítače namísto localhost`.`</span><span class="sxs-lookup"><span data-stu-id="ce331-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7. <span data-ttu-id="ce331-141">Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="ce331-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="ce331-142">Na straně klienta spusťte `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="ce331-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="ce331-143">Spuštění `setup.bat` s `client` argumentem vytvoří klientský certifikát s názvem client.com a exportuje klientský certifikát do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="ce331-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="ce331-144">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="ce331-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="ce331-145">Provést nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="ce331-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="ce331-146">Změňte `findValue` také atribut [ \<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) na nový název certifikátu služby, který je plně kvalifikovaným názvem domény serveru.</span><span class="sxs-lookup"><span data-stu-id="ce331-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="ce331-147">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="ce331-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="ce331-148">Na straně klienta spusťte ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="ce331-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="ce331-149">Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="ce331-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="ce331-150">Na serveru spusťte ImportClientCert.bat, Importuje to klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="ce331-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="ce331-151">Na servisním počítači spusťte service.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ce331-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="ce331-152">V klientském počítači spusťte soubor Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ce331-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1. <span data-ttu-id="ce331-153">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ce331-153">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ce331-154">Chcete-li vyčistit po vzorku</span><span class="sxs-lookup"><span data-stu-id="ce331-154">To clean up after the sample</span></span>  
  
- <span data-ttu-id="ce331-155">Po dokončení spuštění ukázky spusťte soubor Cleanup.bat ve složce ukázek.</span><span class="sxs-lookup"><span data-stu-id="ce331-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ce331-156">Tento skript neodebere certifikáty služeb na straně klienta při spuštění této ukázky v počítačích.</span><span class="sxs-lookup"><span data-stu-id="ce331-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="ce331-157">Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="ce331-157">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="ce331-158">Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující příkaz: Například:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="ce331-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ce331-159">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="ce331-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ce331-160">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="ce331-160">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ce331-161">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ce331-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ce331-162">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ce331-162">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
