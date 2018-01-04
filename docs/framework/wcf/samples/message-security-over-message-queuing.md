---
title: "Zabezpečení zprávy pomocí služby Řízení front zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2969ccf059a32fb2751259bdd1fa6686f69058d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="bbea8-102">Zabezpečení zprávy pomocí služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="bbea8-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="bbea8-103">Tento příklad znázorňuje implementaci aplikace, která využívá WS-zabezpečení x.509 v3 s ověřováním pomocí certifikátu pro klienta a vyžaduje server ověřování pomocí certifikátu x.509 v3 serveru přes služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="bbea8-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="bbea8-104">Zpráva, že zabezpečení je někdy další žádoucí zajistit, že zůstat šifrovaných zpráv v úložišti služby MSMQ a aplikace můžete provádět vlastní ověřování zprávy.</span><span class="sxs-lookup"><span data-stu-id="bbea8-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>  
  
 <span data-ttu-id="bbea8-105">Tato ukázka je založena na [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="bbea8-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="bbea8-106">Zprávy jsou šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="bbea8-106">The messages are encrypted and signed.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bbea8-107">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="bbea8-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bbea8-108">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bbea8-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bbea8-109">Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty.</span><span class="sxs-lookup"><span data-stu-id="bbea8-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="bbea8-110">Pokud fronta neexistuje, vytvoří služba jeden.</span><span class="sxs-lookup"><span data-stu-id="bbea8-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="bbea8-111">Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="bbea8-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="bbea8-112">Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="bbea8-112">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="bbea8-113">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bbea8-113">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="bbea8-114">Rozbalte **funkce** kartě.</span><span class="sxs-lookup"><span data-stu-id="bbea8-114">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="bbea8-115">Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="bbea8-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="bbea8-116">Zkontrolujte **transakcí** pole.</span><span class="sxs-lookup"><span data-stu-id="bbea8-116">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="bbea8-117">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="bbea8-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="bbea8-118">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bbea8-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="bbea8-119">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="bbea8-119">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="bbea8-120">Ujistěte se, že cesta obsahuje složku, která obsahuje Makecert.exe a FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="bbea8-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>  
  
2.  <span data-ttu-id="bbea8-121">Spuštění Setup.bat od vzorku instalační složku.</span><span class="sxs-lookup"><span data-stu-id="bbea8-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="bbea8-122">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="bbea8-122">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bbea8-123">Ujistěte se, spuštěním Cleanup.bat po dokončení s ukázkou certifikáty odebrat.</span><span class="sxs-lookup"><span data-stu-id="bbea8-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="bbea8-124">Další ukázky zabezpečení použijte stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="bbea8-124">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="bbea8-125">Spusťte Service.exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="bbea8-125">Launch Service.exe from \service\bin.</span></span>  
  
4.  <span data-ttu-id="bbea8-126">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="bbea8-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="bbea8-127">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="bbea8-127">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="bbea8-128">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="bbea8-128">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="bbea8-129">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="bbea8-129">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="bbea8-130">Zkopírujte soubory Setup.bat, Cleanup.bat a ImportClientCert.bat na počítač služby.</span><span class="sxs-lookup"><span data-stu-id="bbea8-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2.  <span data-ttu-id="bbea8-131">Vytvořte adresář na klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="bbea8-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3.  <span data-ttu-id="bbea8-132">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="bbea8-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="bbea8-133">Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="bbea8-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4.  <span data-ttu-id="bbea8-134">Na serveru, spusťte `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="bbea8-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="bbea8-135">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="bbea8-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5.  <span data-ttu-id="bbea8-136">Upravit service.exe.config služby tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) což je stejný jako název plně kvalifikované domény počítače.</span><span class="sxs-lookup"><span data-stu-id="bbea8-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6.  <span data-ttu-id="bbea8-137">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="bbea8-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="bbea8-138">Na klientovi, spusťte `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="bbea8-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="bbea8-139">Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="bbea8-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8.  <span data-ttu-id="bbea8-140">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="bbea8-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="bbea8-141">To nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="bbea8-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="bbea8-142">Musíte taky změnit název certifikátu služby být stejné jako plně kvalifikovaný název domény počítače, služby (v `findValue` atribut `defaultCertificate` element `serviceCertificate` pod `clientCredentials`).</span><span class="sxs-lookup"><span data-stu-id="bbea8-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="bbea8-143">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="bbea8-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="bbea8-144">Na klientovi, spusťte `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="bbea8-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="bbea8-145">Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="bbea8-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="bbea8-146">Na serveru, spusťte `ImportClientCert.bat`, tento klientský certifikát naimportuje ze souboru Client.cer do LocalMachine - úložiště TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="bbea8-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="bbea8-147">Na počítači se službou spusťte z příkazového řádku Service.exe.</span><span class="sxs-lookup"><span data-stu-id="bbea8-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="bbea8-148">Na klientském počítači spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="bbea8-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="bbea8-149">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="bbea8-149">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="bbea8-150">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="bbea8-150">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="bbea8-151">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="bbea8-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bbea8-152">Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="bbea8-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="bbea8-153">Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="bbea8-153">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="bbea8-154">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="bbea8-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbea8-155">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bbea8-155">Requirements</span></span>  
 <span data-ttu-id="bbea8-156">Tato ukázka vyžaduje, aby služby MSMQ nainstalovaná a spuštěná.</span><span class="sxs-lookup"><span data-stu-id="bbea8-156">This sample requires that MSMQ is installed and running.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="bbea8-157">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="bbea8-157">Demonstrates</span></span>  
 <span data-ttu-id="bbea8-158">Klient zašifruje pomocí veřejného klíče služby zprávu a podepisuje zprávy pomocí svůj vlastní certifikát.</span><span class="sxs-lookup"><span data-stu-id="bbea8-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="bbea8-159">Čtení zprávy z fronty služby ověřuje klientský certifikát s certifikátem v úložišti důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="bbea8-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="bbea8-160">Potom zprávu dešifruje a odešle zprávu, která se operace služby.</span><span class="sxs-lookup"><span data-stu-id="bbea8-160">It then decrypts the message and dispatches the message to the service operation.</span></span>  
  
 <span data-ttu-id="bbea8-161">Protože [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zpráva Probíhá jako datovou část v těle zprávy služby MSMQ, text zůstávají šifrovaná v úložišti služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="bbea8-161">Because the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="bbea8-162">To zabezpečuje zprávu od nežádoucí zpřístupnění zprávy.</span><span class="sxs-lookup"><span data-stu-id="bbea8-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="bbea8-163">Modul služby MSMQ, samotné není vědět jestli se šifrují zprávy, které je provedení.</span><span class="sxs-lookup"><span data-stu-id="bbea8-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>  
  
 <span data-ttu-id="bbea8-164">Ukázka ukazuje, jak vzájemné ověřování na zprávu úroveň lze použít s služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="bbea8-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="bbea8-165">Certifikáty jsou výměně out-of-band.</span><span class="sxs-lookup"><span data-stu-id="bbea8-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="bbea8-166">To je vždy tomu u aplikace ve frontě, protože služba a klient nemusí být spuštěná ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="bbea8-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bbea8-167">Popis</span><span class="sxs-lookup"><span data-stu-id="bbea8-167">Description</span></span>  
 <span data-ttu-id="bbea8-168">Ukázkový kód klienta a služby jsou stejné jako [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) ukázku s jedním rozdílem.</span><span class="sxs-lookup"><span data-stu-id="bbea8-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="bbea8-169">Kontrakt operaci je označena úroveň ochrany, což naznačuje, že zprávy musí být podepsat a zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="bbea8-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>  
  
```  
// Define a service contract.   
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 <span data-ttu-id="bbea8-170">Aby se zajistilo, že je zpráva zabezpečené pomocí požadovaný token k identifikaci klienta a služby, souboru App.config obsahuje přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="bbea8-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>  
  
 <span data-ttu-id="bbea8-171">Konfigurace klienta Určuje certifikát služby k ověřování.</span><span class="sxs-lookup"><span data-stu-id="bbea8-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="bbea8-172">Jeho LocalMachine úložiště jako důvěryhodné úložiště používá moct spolehnout na platnosti služby.</span><span class="sxs-lookup"><span data-stu-id="bbea8-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="bbea8-173">Určuje také klientský certifikát, který je připojen se zprávou pro ověřování služby klienta.</span><span class="sxs-lookup"><span data-stu-id="bbea8-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>  
  
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
  
 <span data-ttu-id="bbea8-174">Všimněte si, že režim zabezpečení je nastaven na zprávu a ClientCredentialType nastavena na certifikát.</span><span class="sxs-lookup"><span data-stu-id="bbea8-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>  
  
 <span data-ttu-id="bbea8-175">Konfigurace služby obsahuje chování služby, který určuje pověření služby, které se používají, když klient se ověří službu.</span><span class="sxs-lookup"><span data-stu-id="bbea8-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="bbea8-176">Název subjektu certifikátu serveru je zadán v `findValue` atribut [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="bbea8-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="bbea8-177">Ukázka ukazuje řízení ověřování pomocí konfigurace a jak získat identitu volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="bbea8-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>  
  
```  
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
  
 <span data-ttu-id="bbea8-178">Při spuštění kódu služby zobrazí identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="bbea8-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="bbea8-179">Následuje příklad výstupu z kódu služby:</span><span class="sxs-lookup"><span data-stu-id="bbea8-179">The following is a sample output from the service code:</span></span>  
  
```  
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
  
## <a name="comments"></a><span data-ttu-id="bbea8-180">Komentáře</span><span class="sxs-lookup"><span data-stu-id="bbea8-180">Comments</span></span>  
  
-   <span data-ttu-id="bbea8-181">Vytvoření certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="bbea8-181">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="bbea8-182">Následující řádek v dávkovém souboru, vytvoří certifikát klienta.</span><span class="sxs-lookup"><span data-stu-id="bbea8-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="bbea8-183">Zadaný název klienta se používá v názvu subjektu certifikátu vytvořili.</span><span class="sxs-lookup"><span data-stu-id="bbea8-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="bbea8-184">Certifikát je uložen v `My` uložit na `CurrentUser` umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="bbea8-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="bbea8-185">Instalace klientského certifikátu do úložiště důvěryhodných certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="bbea8-185">Installing the client certificate into server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="bbea8-186">Následující řádek v kopie souborů batch certifikát klienta do serveru TrustedPeople úložiště tak, aby server můžete provést příslušné důvěryhodnosti nebo ne důvěryhodnosti rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="bbea8-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="bbea8-187">Pro certifikát nainstalovaný v úložišti TrustedPeople k být důvěryhodný [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služba, režim ověření certifikátu klienta musí být nastavená na `PeerOrChainTrust` nebo `PeerTrust` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bbea8-187">For a certificate installed in the TrustedPeople store to be trusted by a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="bbea8-188">Viz předchozí ukázka konfigurace služby se dozvíte, jak to lze provést pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="bbea8-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>  
  
    ```  
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="bbea8-189">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="bbea8-189">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="bbea8-190">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který se má použít:</span><span class="sxs-lookup"><span data-stu-id="bbea8-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="bbea8-191">Proměnná % název_serveru % Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="bbea8-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="bbea8-192">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="bbea8-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="bbea8-193">Jestli dávkový soubor Instalační program se spustí s parametrem služby (například `setup.bat service`) název_serveru % obsahuje plně kvalifikovaný název domény počítače. V opačném případě je standardně nastavena na místního hostitele</span><span class="sxs-lookup"><span data-stu-id="bbea8-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>  
  
-   <span data-ttu-id="bbea8-194">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="bbea8-194">Installing server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="bbea8-195">Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob na klienta.</span><span class="sxs-lookup"><span data-stu-id="bbea8-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="bbea8-196">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="bbea8-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="bbea8-197">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="bbea8-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="bbea8-198">Pokud používáte jiný USA Anglickou edici systému Microsoft Windows, je nutné upravit Setup.bat a nahraďte název účtu "Služba NT AUTHORITY\NETWORK" vaše místní ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="bbea8-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bbea8-199">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="bbea8-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bbea8-200">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bbea8-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bbea8-201">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bbea8-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bbea8-202">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bbea8-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
  
## <a name="see-also"></a><span data-ttu-id="bbea8-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbea8-203">See Also</span></span>
