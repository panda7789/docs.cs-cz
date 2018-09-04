---
title: Vyrovnávací paměť přijímat
ms.date: 03/30/2017
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
ms.openlocfilehash: b95577c71493275f30703b4366fab32a51097bd2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526801"
---
# <a name="buffered-receive"></a><span data-ttu-id="45998-102">Vyrovnávací paměť přijímat</span><span class="sxs-lookup"><span data-stu-id="45998-102">Buffered Receive</span></span>
<span data-ttu-id="45998-103">Tento příklad ukazuje, jak vytvořit a nakonfigurovat funkci ve vyrovnávací paměti příjmu ve Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="45998-103">This sample demonstrates how to set up and configure the buffered receive feature in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="45998-104">Vyrovnávací paměť přijímat umožňuje vytvořit pracovní postup k vytvoření pracovního postupu bez nutnosti starat o pořadí, ve kterém jsou zprávy přijímány.</span><span class="sxs-lookup"><span data-stu-id="45998-104">Buffered receive allows the workflow author to create a workflow without having to worry about the order in which messages are received.</span></span> <span data-ttu-id="45998-105">Funkce ve vyrovnávací paměti receive ukládá do vyrovnávací paměti zpráv místně a poskytnout je, když pracovní postup je připravený je přijmout.</span><span class="sxs-lookup"><span data-stu-id="45998-105">The buffered receive feature buffers messages locally and delivers them when the workflow is ready to receive them.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="45998-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="45998-106">Demonstrates</span></span>  
 <span data-ttu-id="45998-107">Zpracování zpráv mimo pořadí pomocí uložených do vyrovnávací paměti přijímat pomocí aktivit zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="45998-107">Out-of-order message processing using buffered receive with messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="45998-108">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="45998-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="45998-109">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="45998-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="45998-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="45998-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45998-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="45998-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a><span data-ttu-id="45998-112">Diskuse</span><span class="sxs-lookup"><span data-stu-id="45998-112">Discussion</span></span>  
 <span data-ttu-id="45998-113">V této ukázce je implementováno pomocí služby Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] a obsahuje posloupnost <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="45998-113">In this sample, a Windows Communication Foundation (WCF) service is implemented using [!INCLUDE[wf1](../../../../includes/wf1-md.md)] and has a sequence of <xref:System.ServiceModel.Activities.Receive> activities.</span></span> <span data-ttu-id="45998-114">Tento pracovní postup modely jednoduché půjčky schvalovací proces, který tam, kde pracovní postup očekává tři oznámení o půjčku ke schválení.</span><span class="sxs-lookup"><span data-stu-id="45998-114">This workflow models a simple loan approval process where the workflow expects three notifications for a loan to be approved.</span></span> <span data-ttu-id="45998-115">Windows Communication Foundation (WCF) klientská aplikace odešle tři korelační oznámení v obráceném pořadí, než co služba očekává.</span><span class="sxs-lookup"><span data-stu-id="45998-115">A Windows Communication Foundation (WCF) client application sends three correlated notifications in the reverse order of what the service expects.</span></span> <span data-ttu-id="45998-116">Protože funkce ve vyrovnávací paměti receive je zapnutá na službu, každou zprávu mimo pořadí ukládány do vyrovnávací paměti na službu a zpracovat, protože pracovní postup bude připravený je přijmout.</span><span class="sxs-lookup"><span data-stu-id="45998-116">Because the buffered receive feature is turned on at the service, each out-of-order message is buffered at the service and processed as the workflow becomes ready to receive it.</span></span>  
  
 <span data-ttu-id="45998-117">Funkce ve vyrovnávací paměti příjmu vyžaduje <xref:System.ServiceModel.Activities.ReceiveContent> podporu – od vazby, proto službu používá <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="45998-117">The buffered receive feature requires <xref:System.ServiceModel.Activities.ReceiveContent> support from the binding, therefore the service uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="45998-118">Žádná zvláštní konfigurace je potřebná pro svázání, takže se používají výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="45998-118">No special configuration is required for the binding, so the defaults are used.</span></span>  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 <span data-ttu-id="45998-119">Služba také poskytuje metadata pro službu pomocí <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="45998-119">The service also exposes metadata for the service using <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span></span>  
  
 <span data-ttu-id="45998-120">Podobně je koncový bod klienta konfigurovat pomocí <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="45998-120">Similarly, the client endpoint is configured using <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="45998-121">Kód klienta a konfigurace je generována pomocí **přidat odkaz na službu** funkce sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45998-121">The client code and configuration is generated by using the **Add Service Reference** feature of Visual Studio.</span></span> <span data-ttu-id="45998-122">V následujícím příkladu je koncový bod generovaného klienta v souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="45998-122">The following example is the generated client endpoint in the App.config file.</span></span>  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 <span data-ttu-id="45998-123">Tato ukázka vyžaduje, že jsou povoleny následující součásti Windows:</span><span class="sxs-lookup"><span data-stu-id="45998-123">This sample requires that the following Windows components are enabled:</span></span>  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]<span data-ttu-id="45998-124"> Kompatibilita správy, metabáze a konfigurace kompatibility</span><span class="sxs-lookup"><span data-stu-id="45998-124"> Management Compatibility, Metabase, and Configuration Compatibility</span></span>  
  
3.  <span data-ttu-id="45998-125">Webové služby, funkce pro vývoj aplikací a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="45998-125">World Wide Web Services, Application Development Features, and ASP.NET</span></span>  
  
4.  <span data-ttu-id="45998-126">Server Microsoft zpráv fronty (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="45998-126">Microsoft Message Queues (MSMQ) Server</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="45998-127">K nastavení a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="45998-127">To set up, and build the sample</span></span>  
  
1.  <span data-ttu-id="45998-128">Na [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazový řádek, registrace technologie ASP.NET tak, že zadáte `aspnet_regiis –I` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="45998-128">At a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by typing `aspnet_regiis –I` and press ENTER.</span></span>  
  
2.  <span data-ttu-id="45998-129">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako správce.</span><span class="sxs-lookup"><span data-stu-id="45998-129">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an Administrator.</span></span>  
  
3.  <span data-ttu-id="45998-130">Otevřete LoanService.sln.</span><span class="sxs-lookup"><span data-stu-id="45998-130">Open LoanService.sln.</span></span>  
  
4.  <span data-ttu-id="45998-131">Když se zobrazí výzva, pokud chcete vytvořit virtuální adresář pro projekt LoanService, vyberte **Ano**.</span><span class="sxs-lookup"><span data-stu-id="45998-131">When asked if you would like to create the virtual directories for the LoanService project, select **Yes**.</span></span>  
  
#### <a name="to-set-up-the-service-queues"></a><span data-ttu-id="45998-132">Nastavení služby front</span><span class="sxs-lookup"><span data-stu-id="45998-132">To set up the service queues</span></span>  
  
1.  <span data-ttu-id="45998-133">Stisknutím klávesy F5 spusťte aplikaci LoanClient, která vytvoří front a aktivuje služby definované v Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="45998-133">Press F5 to run the LoanClient application that creates the queues and activates the service defined in Service1.xamlx.</span></span>  
  
2.  <span data-ttu-id="45998-134">Otevřít **Správa počítače** konzoly spuštěním Compmgmt.msc z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="45998-134">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
3.  <span data-ttu-id="45998-135">V **Správa počítače** rozbalte **služby**, **aplikací**, **služby Řízení front zpráv**, **soukromé fronty** .</span><span class="sxs-lookup"><span data-stu-id="45998-135">In the **Computer Management** console, expand **Service**, **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
4.  <span data-ttu-id="45998-136">Klikněte pravým tlačítkem na loanservice/service1.xamlx fronty a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="45998-136">Right-click the loanservice/service1.xamlx queue and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="45998-137">Vyberte **zabezpečení** karta a přidat **přijímá zprávy všem**, **prohlížet zprávy** a **poslat zprávu** oprávnění.</span><span class="sxs-lookup"><span data-stu-id="45998-137">Select the **Security** tab, and add **Everyone Receives Message**, **Peek Message** and **Send Message** permissions.</span></span>  
  
6.  <span data-ttu-id="45998-138">Otevřít [!INCLUDE[iis60](../../../../includes/iis60-md.md)] správce.</span><span class="sxs-lookup"><span data-stu-id="45998-138">Open the [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Manager.</span></span>  
  
7.  <span data-ttu-id="45998-139">Přejděte do **Server**, **lokality**, **výchozí webová stránka**, **privátní**, **LoanService** a vyberte  **Rozšířené možnosti**</span><span class="sxs-lookup"><span data-stu-id="45998-139">Browse to **Server**, **Sites**, **Default Web site**, **Private**, **LoanService** and select **Advanced Options**</span></span>  
  
8.  <span data-ttu-id="45998-140">Změnit **povolené protokoly** bude **http**, **net.msmq**.</span><span class="sxs-lookup"><span data-stu-id="45998-140">Change the **Enabled Protocols** to be **http**, **net.msmq**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="45998-141">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="45998-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="45998-142">Přejděte do http://localhost/private/loanservice/service1.xamlx zajistit, že je služba spuštěna.</span><span class="sxs-lookup"><span data-stu-id="45998-142">Browse to http://localhost/private/loanservice/service1.xamlx to ensure that the service is running.</span></span>  
  
2.  <span data-ttu-id="45998-143">Stisknutím klávesy F5 spusťte aplikaci LoanClient.</span><span class="sxs-lookup"><span data-stu-id="45998-143">Press F5 to run the LoanClient application.</span></span> <span data-ttu-id="45998-144">Po dokončení pracovního postupu by měl být soubor s příponou out.txt uložen C:\Inbox, který obsahuje výsledek výměně zpráv.</span><span class="sxs-lookup"><span data-stu-id="45998-144">Once the workflow is complete, an out.txt file should be saved to C:\Inbox that contains the result of the message exchange.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="45998-145">Vyčistit</span><span class="sxs-lookup"><span data-stu-id="45998-145">To clean up</span></span>  
  
1.  <span data-ttu-id="45998-146">Otevřít **Správa počítače** konzoly spuštěním Compmgmt.msc z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="45998-146">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
2.  <span data-ttu-id="45998-147">Rozbalte **služby** a **aplikací**, **služby Řízení front zpráv**, **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="45998-147">Expand **Service** and **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="45998-148">Odstraňte frontu loanservice/service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="45998-148">Delete the loanservice/service1.xamlx queue.</span></span>  
  
4.  <span data-ttu-id="45998-149">Odeberte adresář C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="45998-149">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="45998-150">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="45998-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="45998-151">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="45998-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="45998-152">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="45998-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45998-153">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="45998-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
