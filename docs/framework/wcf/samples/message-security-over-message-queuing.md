---
title: Zabezpečení zprávy pomocí služby Řízení front zpráv
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 03f4bd3f580163868920622a74ae4f34d7a1a97a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714799"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="e0596-102">Zabezpečení zprávy pomocí služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="e0596-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="e0596-103">Tato ukázka předvádí, jak implementovat aplikaci, která používá WS-Security s ověřováním certifikátů X. 509 v3 pro klienta, a vyžaduje ověření serveru pomocí certifikátu X. 509 v3 serveru přes službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e0596-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="e0596-104">Zabezpečení zpráv je někdy žádoucí, aby zprávy v úložišti služby MSMQ zůstaly šifrované a aplikace může provádět vlastní ověřování zprávy.</span><span class="sxs-lookup"><span data-stu-id="e0596-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="e0596-105">Tato ukázka je založená na ukázce s [transakčními vazbami služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="e0596-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="e0596-106">Zprávy jsou zašifrovány a podepsány.</span><span class="sxs-lookup"><span data-stu-id="e0596-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e0596-107">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="e0596-107">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e0596-108">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0596-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e0596-109">Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e0596-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="e0596-110">Pokud fronta není přítomna, služba ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="e0596-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="e0596-111">Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e0596-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="e0596-112">Pomocí těchto kroků vytvořte ve Windows 2008 frontu.</span><span class="sxs-lookup"><span data-stu-id="e0596-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="e0596-113">Otevřete Správce serveru v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="e0596-113">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="e0596-114">Rozbalte kartu **funkce** .</span><span class="sxs-lookup"><span data-stu-id="e0596-114">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="e0596-115">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.</span><span class="sxs-lookup"><span data-stu-id="e0596-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="e0596-116">Zaškrtněte políčko **transakční** .</span><span class="sxs-lookup"><span data-stu-id="e0596-116">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="e0596-117">Jako název nové fronty zadejte `ServiceModelSamplesTransacted`.</span><span class="sxs-lookup"><span data-stu-id="e0596-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="e0596-118">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0596-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="e0596-119">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="e0596-119">To run the sample on the same computer</span></span>

1. <span data-ttu-id="e0596-120">Ujistěte se, že cesta zahrnuje složku, která obsahuje nástroj Makecert. exe a FindPrivateKey. exe.</span><span class="sxs-lookup"><span data-stu-id="e0596-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="e0596-121">Z ukázkové instalační složky spusťte Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="e0596-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="e0596-122">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="e0596-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e0596-123">Po dokončení ukázky se ujistěte, že jste odebrali certifikáty spuštěním souboru Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="e0596-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="e0596-124">Další ukázky zabezpečení používají stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="e0596-124">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="e0596-125">Spustit Service. exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="e0596-125">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="e0596-126">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="e0596-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="e0596-127">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="e0596-127">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="e0596-128">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e0596-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="e0596-129">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="e0596-129">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="e0596-130">Zkopírujte soubory Setup. bat, Cleanup. bat a ImportClientCert. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="e0596-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="e0596-131">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="e0596-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="e0596-132">Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="e0596-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="e0596-133">Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="e0596-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="e0596-134">Na serveru spusťte `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="e0596-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="e0596-135">Spuštění `setup.bat` s argumentem `service` vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.</span><span class="sxs-lookup"><span data-stu-id="e0596-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="e0596-136">Upravte Service. exe. config služby, aby odrážela nový název certifikátu (v atributu `findValue` v [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="e0596-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="e0596-137">Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="e0596-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="e0596-138">Na straně klienta spusťte `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="e0596-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="e0596-139">Spuštění `setup.bat` s argumentem `client` vytvoří klientský certifikát s názvem client.com a vyexportuje klientský certifikát do souboru s názvem Client. cer.</span><span class="sxs-lookup"><span data-stu-id="e0596-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="e0596-140">V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="e0596-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="e0596-141">Provedete to tak, že nahradíte localhost názvem domény na plně kvalifikovaném názvu domény serveru.</span><span class="sxs-lookup"><span data-stu-id="e0596-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="e0596-142">Také je nutné změnit název certifikátu služby tak, aby byl stejný jako plně kvalifikovaný název domény počítače služby (v atributu `findValue` v prvku `defaultCertificate` `serviceCertificate` v části `clientCredentials`).</span><span class="sxs-lookup"><span data-stu-id="e0596-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="e0596-143">Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="e0596-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="e0596-144">Na straně klienta spusťte `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="e0596-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="e0596-145">Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="e0596-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="e0596-146">Na serveru spusťte `ImportClientCert.bat`, naimportuje klientský certifikát ze souboru Client. cer do úložiště LocalMachine-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="e0596-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="e0596-147">Na počítači služby spusťte z příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="e0596-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="e0596-148">V klientském počítači spusťte z příkazového řádku soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="e0596-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="e0596-149">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e0596-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e0596-150">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="e0596-150">To clean up after the sample</span></span>  
  
- <span data-ttu-id="e0596-151">Po dokončení ukázky spusťte na složce Samples Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="e0596-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e0596-152">Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi.</span><span class="sxs-lookup"><span data-stu-id="e0596-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="e0596-153">Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="e0596-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="e0596-154">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="e0596-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0596-155">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0596-155">Requirements</span></span>
 <span data-ttu-id="e0596-156">Tato ukázka vyžaduje, aby byla služba MSMQ nainstalovaná a spuštěná.</span><span class="sxs-lookup"><span data-stu-id="e0596-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e0596-157">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="e0596-157">Demonstrates</span></span>
 <span data-ttu-id="e0596-158">Klient šifruje zprávu pomocí veřejného klíče služby a podepíše zprávu pomocí vlastního certifikátu.</span><span class="sxs-lookup"><span data-stu-id="e0596-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="e0596-159">Služba, která čte zprávu z fronty ověřuje certifikát klienta s certifikátem v úložišti důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="e0596-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="e0596-160">Poté dešifruje zprávu a odešle zprávu do operace služby.</span><span class="sxs-lookup"><span data-stu-id="e0596-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="e0596-161">Vzhledem k tomu, že se zpráva Windows Communication Foundation (WCF) přenese jako datová část v těle zprávy služby MSMQ, text zůstane zašifrovaný v úložišti MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e0596-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="e0596-162">Tím se zpráva zabezpečí ze nechtěného zveřejnění zprávy.</span><span class="sxs-lookup"><span data-stu-id="e0596-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="e0596-163">Mějte na paměti, že samotný služba MSMQ nezáleží na tom, zda je zpráva, kterou přepravuje, šifrovaná.</span><span class="sxs-lookup"><span data-stu-id="e0596-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="e0596-164">Ukázka předvádí, jak se vzájemné ověřování na úrovni zpráv dá použít u služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e0596-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="e0596-165">Certifikáty se vyměňují mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="e0596-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="e0596-166">To je vždycky u aplikace zařazené do fronty, protože služba a klient nemusí být ve stejnou dobu spuštěný.</span><span class="sxs-lookup"><span data-stu-id="e0596-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="e0596-167">Popis</span><span class="sxs-lookup"><span data-stu-id="e0596-167">Description</span></span>
 <span data-ttu-id="e0596-168">Ukázkový klient a kód služby jsou stejné jako v transakční ukázce s [transakčními vazbami služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) s jedním rozdílem.</span><span class="sxs-lookup"><span data-stu-id="e0596-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="e0596-169">Kontrakt operace je opatřen poznámkou s úrovní ochrany, která naznačuje, že musí být zpráva podepsána a zašifrována.</span><span class="sxs-lookup"><span data-stu-id="e0596-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="e0596-170">Aby bylo zajištěno, že je zpráva zabezpečená pomocí požadovaného tokenu k identifikaci služby a klienta, obsahuje soubor App. config informace o přihlašovacích údajích.</span><span class="sxs-lookup"><span data-stu-id="e0596-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="e0596-171">Konfigurace klienta Určuje certifikát služby pro ověření služby.</span><span class="sxs-lookup"><span data-stu-id="e0596-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="e0596-172">Používá své LocalMachine úložiště jako důvěryhodné úložiště k tomu, aby se spoléhala na platnost služby.</span><span class="sxs-lookup"><span data-stu-id="e0596-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="e0596-173">Určuje také klientský certifikát, který je připojen ke zprávě pro ověření služby klienta.</span><span class="sxs-lookup"><span data-stu-id="e0596-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

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

 <span data-ttu-id="e0596-174">Všimněte si, že režim zabezpečení je nastavený na Message a ClientCredentialType je nastavené na certifikát.</span><span class="sxs-lookup"><span data-stu-id="e0596-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="e0596-175">Konfigurace služby zahrnuje chování služby, které určuje přihlašovací údaje služby, které se používají, když klient ověřuje službu.</span><span class="sxs-lookup"><span data-stu-id="e0596-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="e0596-176">Název subjektu certifikátu serveru je zadaný v atributu `findValue` [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="e0596-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

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

 <span data-ttu-id="e0596-177">Ukázka znázorňuje řízení ověřování pomocí konfigurace a jak získat identitu volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="e0596-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="e0596-178">Při spuštění zobrazí kód služby identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="e0596-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="e0596-179">Následuje ukázkový výstup z kódu služby:</span><span class="sxs-lookup"><span data-stu-id="e0596-179">The following is a sample output from the service code:</span></span>

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

## <a name="comments"></a><span data-ttu-id="e0596-180">Komentáře</span><span class="sxs-lookup"><span data-stu-id="e0596-180">Comments</span></span>

- <span data-ttu-id="e0596-181">Vytváří se klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="e0596-181">Creating the client certificate.</span></span>

     <span data-ttu-id="e0596-182">Následující řádek v dávkovém souboru vytvoří klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="e0596-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="e0596-183">Zadaný název klienta se používá v názvu subjektu vytvořeného certifikátu.</span><span class="sxs-lookup"><span data-stu-id="e0596-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="e0596-184">Certifikát je uložený ve službě `My` Store v umístění úložiště `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="e0596-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="e0596-185">Probíhá instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="e0596-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="e0596-186">Následující řádek v dávkovém souboru zkopíruje klientský certifikát do úložiště TrustedPeople serveru, aby server mohl učinit příslušná rozhodnutí týkající se vztahu důvěryhodnosti nebo bez vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="e0596-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="e0596-187">Aby byl certifikát nainstalovaný v úložišti TrustedPeople důvěryhodný službou Windows Communication Foundation (WCF), musí být režim ověřování klientského certifikátu nastaven na hodnotu `PeerOrChainTrust` nebo `PeerTrust`.</span><span class="sxs-lookup"><span data-stu-id="e0596-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="e0596-188">V předchozí ukázce konfigurace služby se dozvíte, jak to lze provést pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="e0596-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="e0596-189">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="e0596-189">Creating the server certificate.</span></span>

     <span data-ttu-id="e0596-190">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít:</span><span class="sxs-lookup"><span data-stu-id="e0596-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="e0596-191">Proměnná% SERVER_NAME% Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="e0596-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="e0596-192">Certifikát je uložený v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="e0596-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="e0596-193">Pokud je instalační dávkový soubor spuštěn s argumentem služby (například `setup.bat service`),% SERVER_NAME% obsahuje plně kvalifikovaný název domény počítače. V opačném případě se použije jako localhost</span><span class="sxs-lookup"><span data-stu-id="e0596-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="e0596-194">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="e0596-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="e0596-195">Následující řádek zkopíruje certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="e0596-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="e0596-196">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="e0596-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="e0596-197">Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="e0596-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="e0596-198">Pokud používáte sadu Microsoft Windows, která není v jazykové verzi, musíte upravit soubor Setup. bat a nahradit název účtu NT AUTHORITY\NETWORK SERVICE svým regionálním ekvivalentem.</span><span class="sxs-lookup"><span data-stu-id="e0596-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e0596-199">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="e0596-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e0596-200">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="e0596-200">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e0596-201">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="e0596-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e0596-202">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e0596-202">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
