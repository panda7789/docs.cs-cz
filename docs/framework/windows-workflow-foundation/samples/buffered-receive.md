---
title: "Uložená do vyrovnávací paměti přijímat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b4851425609936d093762895cef6bdbc8ad7823
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="buffered-receive"></a><span data-ttu-id="20392-102">Uložená do vyrovnávací paměti přijímat</span><span class="sxs-lookup"><span data-stu-id="20392-102">Buffered Receive</span></span>
<span data-ttu-id="20392-103">Tato ukázka ukazuje, jak připravit a nakonfigurovat funkci vyrovnávací pamětí příjmu v [!INCLUDE[wf](../../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20392-103">This sample demonstrates how to set up and configure the buffered receive feature in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span> <span data-ttu-id="20392-104">Uložená do vyrovnávací paměti přijímat umožňuje autorovi pracovní postup vytvoření pracovního postupu bez nutnosti starat o pořadí, ve kterém jsou přijaty zprávy.</span><span class="sxs-lookup"><span data-stu-id="20392-104">Buffered receive allows the workflow author to create a workflow without having to worry about the order in which messages are received.</span></span> <span data-ttu-id="20392-105">Funkci vyrovnávací pamětí příjmu vyrovnávacích pamětí zpráv místně a doručí je, když pracovní postup je připravený je přijmout.</span><span class="sxs-lookup"><span data-stu-id="20392-105">The buffered receive feature buffers messages locally and delivers them when the workflow is ready to receive them.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="20392-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="20392-106">Demonstrates</span></span>  
 <span data-ttu-id="20392-107">Zpracování zpráv mimo pořadí pomocí uložených do vyrovnávací paměti, zobrazí se aktivity zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="20392-107">Out-of-order message processing using buffered receive with messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20392-108">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="20392-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="20392-109">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="20392-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="20392-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="20392-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20392-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="20392-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a><span data-ttu-id="20392-112">Diskusní</span><span class="sxs-lookup"><span data-stu-id="20392-112">Discussion</span></span>  
 <span data-ttu-id="20392-113">V této ukázce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby je implementovaná pomocí [!INCLUDE[wf1](../../../../includes/wf1-md.md)] a má posloupnost <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="20392-113">In this sample, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service is implemented using [!INCLUDE[wf1](../../../../includes/wf1-md.md)] and has a sequence of <xref:System.ServiceModel.Activities.Receive> activities.</span></span> <span data-ttu-id="20392-114">Tento pracovní postup modelů proces schválení jednoduché úvěr tam, kde pracovního postupu očekává tři oznámení o úvěr schválení.</span><span class="sxs-lookup"><span data-stu-id="20392-114">This workflow models a simple loan approval process where the workflow expects three notifications for a loan to be approved.</span></span> <span data-ttu-id="20392-115">A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klientská aplikace odešle tři korelační oznámení v obráceném pořadí, než co služba očekává.</span><span class="sxs-lookup"><span data-stu-id="20392-115">A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application sends three correlated notifications in the reverse order of what the service expects.</span></span> <span data-ttu-id="20392-116">Protože funkce receive ve vyrovnávací paměti je zapnutá ve službách, každou zprávu mimo pořadí uložená do vyrovnávací paměti na službu a zpracovat jako pracovní postup bude připravený je přijmout.</span><span class="sxs-lookup"><span data-stu-id="20392-116">Because the buffered receive feature is turned on at the service, each out-of-order message is buffered at the service and processed as the workflow becomes ready to receive it.</span></span>  
  
 <span data-ttu-id="20392-117">Funkce vyrovnávací pamětí příjmu vyžaduje <xref:System.ServiceModel.Activities.ReceiveContent> podpory z vazby, proto služba používá <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="20392-117">The buffered receive feature requires <xref:System.ServiceModel.Activities.ReceiveContent> support from the binding, therefore the service uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="20392-118">Žádná speciální konfigurace je požadované pro vazbu, takže se používají výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="20392-118">No special configuration is required for the binding, so the defaults are used.</span></span>  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 <span data-ttu-id="20392-119">Služba také poskytuje metadata pro používání služby <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="20392-119">The service also exposes metadata for the service using <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span></span>  
  
 <span data-ttu-id="20392-120">Podobně je koncový bod klient konfigurován pomocí <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="20392-120">Similarly, the client endpoint is configured using <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="20392-121">Kód klienta a konfigurace je generována pomocí **přidat odkaz na službu** funkce [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20392-121">The client code and configuration is generated by using the **Add Service Reference** feature of [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="20392-122">V následujícím příkladu je koncový bod generovaného klienta v souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="20392-122">The following example is the generated client endpoint in the App.config file.</span></span>  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 <span data-ttu-id="20392-123">Tato ukázka vyžaduje, že jsou povoleny následující součásti systému Windows:</span><span class="sxs-lookup"><span data-stu-id="20392-123">This sample requires that the following Windows components are enabled:</span></span>  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]<span data-ttu-id="20392-124">Kompatibilita správy metabáze a kompatibilita konfigurace</span><span class="sxs-lookup"><span data-stu-id="20392-124"> Management Compatibility, Metabase, and Configuration Compatibility</span></span>  
  
3.  <span data-ttu-id="20392-125">Webové služby, funkce pro vývoj aplikací a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="20392-125">World Wide Web Services, Application Development Features, and ASP.NET</span></span>  
  
4.  <span data-ttu-id="20392-126">Server Microsoft zpráv fronty (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="20392-126">Microsoft Message Queues (MSMQ) Server</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="20392-127">Jak nastavit a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="20392-127">To set up, and build the sample</span></span>  
  
1.  <span data-ttu-id="20392-128">V [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazový řádek, zaregistrovat ASP.NET tak, že zadáte `aspnet_regiis –I` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="20392-128">At a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by typing `aspnet_regiis –I` and press ENTER.</span></span>  
  
2.  <span data-ttu-id="20392-129">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako správce.</span><span class="sxs-lookup"><span data-stu-id="20392-129">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an Administrator.</span></span>  
  
3.  <span data-ttu-id="20392-130">Otevřete LoanService.sln.</span><span class="sxs-lookup"><span data-stu-id="20392-130">Open LoanService.sln.</span></span>  
  
4.  <span data-ttu-id="20392-131">Když se zobrazí dotaz, pokud chcete vytvořit virtuální adresáře pro LoanService projekt, vyberte **Ano**.</span><span class="sxs-lookup"><span data-stu-id="20392-131">When asked if you would like to create the virtual directories for the LoanService project, select **Yes**.</span></span>  
  
#### <a name="to-set-up-the-service-queues"></a><span data-ttu-id="20392-132">Nastavení fronty služby service</span><span class="sxs-lookup"><span data-stu-id="20392-132">To set up the service queues</span></span>  
  
1.  <span data-ttu-id="20392-133">Stisknutím klávesy F5 spusťte LoanClient aplikace, která vytvoří fronty a aktivuje služby definované v Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="20392-133">Press F5 to run the LoanClient application that creates the queues and activates the service defined in Service1.xamlx.</span></span>  
  
2.  <span data-ttu-id="20392-134">Otevřete **Správa počítače** konzoly spuštěním Compmgmt.msc z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="20392-134">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
3.  <span data-ttu-id="20392-135">V **Správa počítače** rozbalte **služby**, **aplikace**, **služby Řízení front zpráv**, **soukromé fronty** .</span><span class="sxs-lookup"><span data-stu-id="20392-135">In the **Computer Management** console, expand **Service**, **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
4.  <span data-ttu-id="20392-136">Klikněte pravým tlačítkem na fronty loanservice/service1.xamlx a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="20392-136">Right-click the loanservice/service1.xamlx queue and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="20392-137">Vyberte **zabezpečení** a přidejte **Everyone obdrží zprávu**, **prohlížet zprávy** a **odeslat zprávu** oprávnění.</span><span class="sxs-lookup"><span data-stu-id="20392-137">Select the **Security** tab, and add **Everyone Receives Message**, **Peek Message** and **Send Message** permissions.</span></span>  
  
6.  <span data-ttu-id="20392-138">Otevřete [!INCLUDE[iis60](../../../../includes/iis60-md.md)] správce.</span><span class="sxs-lookup"><span data-stu-id="20392-138">Open the [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Manager.</span></span>  
  
7.  <span data-ttu-id="20392-139">Přejděte do **Server**, **lokality**, **výchozí web**, **privátní**, **LoanService** a vyberte  **Rozšířené možnosti**</span><span class="sxs-lookup"><span data-stu-id="20392-139">Browse to **Server**, **Sites**, **Default Web site**, **Private**, **LoanService** and select **Advanced Options**</span></span>  
  
8.  <span data-ttu-id="20392-140">Změna **povolené protokoly** být **http**, **net.msmq**.</span><span class="sxs-lookup"><span data-stu-id="20392-140">Change the **Enabled Protocols** to be **http**, **net.msmq**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="20392-141">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="20392-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="20392-142">Přejděte do http://localhost/private/loanservice/service1.xamlx zajistit, že je služba spuštěná.</span><span class="sxs-lookup"><span data-stu-id="20392-142">Browse to http://localhost/private/loanservice/service1.xamlx to ensure that the service is running.</span></span>  
  
2.  <span data-ttu-id="20392-143">Stisknutím klávesy F5 spusťte aplikaci LoanClient.</span><span class="sxs-lookup"><span data-stu-id="20392-143">Press F5 to run the LoanClient application.</span></span> <span data-ttu-id="20392-144">Po dokončení pracovního postupu by měl být uložen soubor out.txt C:\Inbox obsahující výsledek výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="20392-144">Once the workflow is complete, an out.txt file should be saved to C:\Inbox that contains the result of the message exchange.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="20392-145">Vyčistěte</span><span class="sxs-lookup"><span data-stu-id="20392-145">To clean up</span></span>  
  
1.  <span data-ttu-id="20392-146">Otevřete **Správa počítače** konzoly spuštěním Compmgmt.msc z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="20392-146">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
2.  <span data-ttu-id="20392-147">Rozbalte položku **služby** a **aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="20392-147">Expand **Service** and **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="20392-148">Odstraňte loanservice/service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="20392-148">Delete the loanservice/service1.xamlx queue.</span></span>  
  
4.  <span data-ttu-id="20392-149">Odeberte adresář C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="20392-149">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20392-150">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="20392-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="20392-151">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="20392-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="20392-152">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="20392-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20392-153">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="20392-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
