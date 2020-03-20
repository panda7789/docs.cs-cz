---
title: Zabezpečení zprávy pomocí služby Řízení front zpráv
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 2048b27f15787c70abda65ae582849276469c763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144432"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="57660-102">Zabezpečení zprávy pomocí služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="57660-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="57660-103">Tato ukázka ukazuje, jak implementovat aplikaci, která používá WS-Security s ověřováním certifikátu X.509v3 pro klienta a vyžaduje ověření serveru pomocí certifikátu X.509v3 serveru přes službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="57660-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="57660-104">Zabezpečení zpráv je někdy více žádoucí zajistit, aby zprávy v úložišti služby MSMQ zůstat šifrované a aplikace může provádět vlastní ověřování zprávy.</span><span class="sxs-lookup"><span data-stu-id="57660-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="57660-105">Tato ukázka je založena na [transacted MSMQ binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="57660-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="57660-106">Zprávy jsou zašifrovány a podepsány.</span><span class="sxs-lookup"><span data-stu-id="57660-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="57660-107">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="57660-107">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="57660-108">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="57660-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="57660-109">Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici.</span><span class="sxs-lookup"><span data-stu-id="57660-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="57660-110">Pokud fronta není k dispozici, služba ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="57660-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="57660-111">Nejprve můžete spustit službu a vytvořit frontu, nebo ji můžete vytvořit pomocí Správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="57660-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="57660-112">Vytvořenífronty v systému Windows 2008 postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="57660-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="57660-113">Otevřete Správce serveru v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="57660-113">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="57660-114">Rozbalte kartu **Funkce.**</span><span class="sxs-lookup"><span data-stu-id="57660-114">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="57660-115">Klepněte pravým tlačítkem myši na **položku Fronty soukromých zpráv**a vyberte příkaz **Nová**, **Soukromá fronta**.</span><span class="sxs-lookup"><span data-stu-id="57660-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="57660-116">Zaškrtněte políčko **Transakční** transakce.</span><span class="sxs-lookup"><span data-stu-id="57660-116">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="57660-117">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="57660-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="57660-118">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="57660-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="57660-119">Spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="57660-119">To run the sample on the same computer</span></span>

1. <span data-ttu-id="57660-120">Ujistěte se, že cesta obsahuje složku, která obsahuje Makecert.exe a FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="57660-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="57660-121">Spusťte soubor Setup.bat z ukázkové instalační složky.</span><span class="sxs-lookup"><span data-stu-id="57660-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="57660-122">Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="57660-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="57660-123">Ujistěte se, že odeberete certifikáty spuštěním souboru Cleanup.bat po dokončení ukázky.</span><span class="sxs-lookup"><span data-stu-id="57660-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="57660-124">Jiné ukázky zabezpečení používají stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="57660-124">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="57660-125">Spusťte soubor Service.exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="57660-125">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="57660-126">Spusťte soubor Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="57660-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="57660-127">Aktivita klienta je zobrazena v aplikaci klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="57660-127">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="57660-128">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="57660-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="57660-129">Spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="57660-129">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="57660-130">Zkopírujte soubory Setup.bat, Cleanup.bat a ImportClientCert.bat do servisního počítače.</span><span class="sxs-lookup"><span data-stu-id="57660-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="57660-131">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="57660-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="57660-132">Zkopírujte soubory klientských programů do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="57660-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="57660-133">Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="57660-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="57660-134">Na serveru spusťte . `setup.bat service`</span><span class="sxs-lookup"><span data-stu-id="57660-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="57660-135">Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="57660-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="57660-136">Upravte soubor service.exe.config služby tak, aby `findValue` odrážel nový název certifikátu (v atributu [ \<v serviceCertificate>), ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="57660-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="57660-137">Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="57660-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="57660-138">Na straně klienta spusťte `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="57660-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="57660-139">Spuštění `setup.bat` s `client` argumentem vytvoří klientský certifikát s názvem client.com a exportuje klientský certifikát do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="57660-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="57660-140">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="57660-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="57660-141">To provést nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="57660-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="57660-142">Je také nutné změnit název certifikátu služby tak, aby byl stejný jako plně `findValue` kvalifikovaný `defaultCertificate` název `serviceCertificate` domény `clientCredentials`počítače služby (v atributu v prvku under ).</span><span class="sxs-lookup"><span data-stu-id="57660-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="57660-143">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="57660-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="57660-144">Na straně klienta spusťte `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="57660-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="57660-145">Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="57660-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="57660-146">Na serveru, `ImportClientCert.bat`spustit , To importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="57660-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="57660-147">V servisním počítači spusťte program Service.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="57660-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="57660-148">V klientském počítači spusťte soubor Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="57660-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="57660-149">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="57660-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="57660-150">Chcete-li vyčistit po vzorku</span><span class="sxs-lookup"><span data-stu-id="57660-150">To clean up after the sample</span></span>  
  
- <span data-ttu-id="57660-151">Po dokončení spuštění ukázky spusťte soubor Cleanup.bat ve složce ukázek.</span><span class="sxs-lookup"><span data-stu-id="57660-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="57660-152">Tento skript neodebere certifikáty služeb v klientovi při spuštění této ukázky v počítačích.</span><span class="sxs-lookup"><span data-stu-id="57660-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="57660-153">Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty v počítačích, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="57660-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="57660-154">Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`příkaz: Například: .</span><span class="sxs-lookup"><span data-stu-id="57660-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="57660-155">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57660-155">Requirements</span></span>
 <span data-ttu-id="57660-156">Tato ukázka vyžaduje, aby byla služba MSMQ nainstalována a spuštěna.</span><span class="sxs-lookup"><span data-stu-id="57660-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="57660-157">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="57660-157">Demonstrates</span></span>
 <span data-ttu-id="57660-158">Klient zašifruje zprávu pomocí veřejného klíče služby a podepíše zprávu pomocí vlastního certifikátu.</span><span class="sxs-lookup"><span data-stu-id="57660-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="57660-159">Služba, která čte zprávu z fronty, ověří klientský certifikát s certifikátem v úložišti důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="57660-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="57660-160">Potom dešifruje zprávu a odešle zprávu do operace služby.</span><span class="sxs-lookup"><span data-stu-id="57660-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="57660-161">Vzhledem k tomu, že zpráva WCF (Windows Communication Foundation) je přenášena jako datová část v těle zprávy služby MSMQ, tělo zůstane šifrované v úložišti služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="57660-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="57660-162">Tím se zpráva zabezpečí před nežádoucím zveřejněním zprávy.</span><span class="sxs-lookup"><span data-stu-id="57660-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="57660-163">Všimněte si, že služba MSMQ sama o sobě neví, zda je zpráva, kterou nese, šifrována.</span><span class="sxs-lookup"><span data-stu-id="57660-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="57660-164">Ukázka ukazuje, jak lze s msmq používat vzájemné ověřování na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="57660-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="57660-165">Certifikáty jsou vyměňovány mimo pásmo.</span><span class="sxs-lookup"><span data-stu-id="57660-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="57660-166">To je vždy případ s aplikací ve frontě, protože služba a klient nemusí být spuštěna současně.</span><span class="sxs-lookup"><span data-stu-id="57660-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="57660-167">Popis</span><span class="sxs-lookup"><span data-stu-id="57660-167">Description</span></span>
 <span data-ttu-id="57660-168">Ukázkový kód klienta a služby jsou stejné jako [transacted msmq vazby](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku s jedním rozdílem.</span><span class="sxs-lookup"><span data-stu-id="57660-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="57660-169">Smlouva o operaci je anotována s úrovní ochrany, což naznačuje, že zpráva musí být podepsána a zašifrována.</span><span class="sxs-lookup"><span data-stu-id="57660-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="57660-170">Chcete-li zajistit, že zpráva je zabezpečena pomocí požadovaného tokenu k identifikaci služby a klienta, App.config obsahuje informace o pověření.</span><span class="sxs-lookup"><span data-stu-id="57660-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="57660-171">Konfigurace klienta určuje certifikát služby pro ověření služby.</span><span class="sxs-lookup"><span data-stu-id="57660-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="57660-172">Používá úložiště LocalMachine jako důvěryhodné úložiště k spoléhání se na platnost služby.</span><span class="sxs-lookup"><span data-stu-id="57660-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="57660-173">Určuje také klientský certifikát, který je připojen ke zprávě pro ověřování služby klienta.</span><span class="sxs-lookup"><span data-stu-id="57660-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="57660-174">Všimněte si, že režim zabezpečení je nastaven na Message a ClientCredentialType je nastavena na certifikát.</span><span class="sxs-lookup"><span data-stu-id="57660-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="57660-175">Konfigurace služby zahrnuje chování služby, které určuje pověření služby, které se používají při ověření služby klientem.</span><span class="sxs-lookup"><span data-stu-id="57660-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="57660-176">Název subjektu certifikátu serveru `findValue` je uveden v atributu v [ \<>serviceCredentials ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="57660-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="57660-177">Ukázka ukazuje řízení ověřování pomocí konfigurace a jak získat identitu volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="57660-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 <span data-ttu-id="57660-178">Při spuštění kód služby zobrazí identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="57660-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="57660-179">Následuje ukázkový výstup z kódu služby:</span><span class="sxs-lookup"><span data-stu-id="57660-179">The following is a sample output from the service code:</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a><span data-ttu-id="57660-180">Komentáře</span><span class="sxs-lookup"><span data-stu-id="57660-180">Comments</span></span>

- <span data-ttu-id="57660-181">Vytvoření klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="57660-181">Creating the client certificate.</span></span>

     <span data-ttu-id="57660-182">Následující řádek v dávkovém souboru vytvoří klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="57660-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="57660-183">Zadaný název klienta se používá v názvu subjektu vytvořeného certifikátu.</span><span class="sxs-lookup"><span data-stu-id="57660-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="57660-184">Certifikát je uložen `My` v `CurrentUser` úložišti v umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="57660-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="57660-185">Instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="57660-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="57660-186">Následující řádek v dávkovém souboru zkopíruje klientský certifikát do úložiště TrustedPeople serveru, aby server mohl činit příslušná rozhodnutí o důvěryhodnosti nebo nedůvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="57660-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="57660-187">Aby byl certifikát nainstalovaný v úložišti TrustedPeople důvěryhodný službou WCF (Windows Communication Foundation), `PeerOrChainTrust` `PeerTrust` musí být režim ověření klientského certifikátu nastaven na hodnotu nebo hodnotu.</span><span class="sxs-lookup"><span data-stu-id="57660-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="57660-188">Podívejte se na předchozí ukázku konfigurace služby, kde se dozvíte, jak to lze provést pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="57660-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="57660-189">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="57660-189">Creating the server certificate.</span></span>

     <span data-ttu-id="57660-190">Následující řádky z dávkového souboru Setup.bat vytvářejí certifikát serveru, který má být použit:</span><span class="sxs-lookup"><span data-stu-id="57660-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="57660-191">Proměnná %SERVER_NAME% určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="57660-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="57660-192">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="57660-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="57660-193">Pokud je dávkový soubor instalace spuštěn s argumentem služby `setup.bat service`(například) %SERVER_NAME% obsahuje plně kvalifikovaný název domény počítače. V opačném případě je výchozí localhost</span><span class="sxs-lookup"><span data-stu-id="57660-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="57660-194">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="57660-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="57660-195">Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta.</span><span class="sxs-lookup"><span data-stu-id="57660-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="57660-196">Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="57660-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="57660-197">Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="57660-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="57660-198">Pokud používáte edici systému Microsoft Windows, která není v USA, je nutné upravit soubor Setup.bat a nahradit název účtu NT AUTHORITY\NETWORK SERVICE místním ekvivalentem.</span><span class="sxs-lookup"><span data-stu-id="57660-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57660-199">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="57660-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="57660-200">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="57660-200">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="57660-201">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="57660-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="57660-202">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="57660-202">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
