---
title: "Absolutní zpoždění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60e3b65851dba68b4d01d6e4195b5faf99b583de
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="absolute-delay"></a><span data-ttu-id="56f46-102">Absolutní zpoždění</span><span class="sxs-lookup"><span data-stu-id="56f46-102">Absolute Delay</span></span>
<span data-ttu-id="56f46-103">Hlavní scénáře pro tato ukázka má počkat, dokud zadané <xref:System.DateTime> pomocí trvanlivý časovačů v aplikaci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="56f46-103">The main scenario for this sample is to delay until a specified <xref:System.DateTime> using durable timers in a workflow application.</span></span> <span data-ttu-id="56f46-104">To se liší od pomocí integrovaných <xref:System.Activities.Statements.Delay> aktivitu jako to bude umožňují pouze zpoždění pro danou <xref:System.TimeSpan> (nebo počet minut nebo sekund).</span><span class="sxs-lookup"><span data-stu-id="56f46-104">This is different from using the built-in <xref:System.Activities.Statements.Delay> activity as this will only allow you to delay for a given <xref:System.TimeSpan> (or number of minutes/seconds).</span></span>  
  
 <span data-ttu-id="56f46-105">Některé reálnými scénáře, ve kterých můžete chtít provést na těchto rozdílech patří:</span><span class="sxs-lookup"><span data-stu-id="56f46-105">Some real-life scenarios in which you may want to make this distinction include the following:</span></span>  
  
1.  <span data-ttu-id="56f46-106">Chcete-li prodleva odesílání pošty po dobu 30 sekund a ujistěte se, že jste nepodali případné chyby.</span><span class="sxs-lookup"><span data-stu-id="56f46-106">You want to delay sending a mail for 30 seconds to make sure you didn’t make any errors.</span></span>  
  
2.  <span data-ttu-id="56f46-107">Jsou nadměrně a chcete všechny vaše e-mailů zpoždění až normální pracovní dobu (například 8: 00).</span><span class="sxs-lookup"><span data-stu-id="56f46-107">You are working overtime and want to delay all of your mails until normal business hours (such as 8 am).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="56f46-108">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="56f46-108">Demonstrates</span></span>  
  
1.  <span data-ttu-id="56f46-109"><xref:System.Activities.Statements.DurableTimerExtension>pro implementaci absolutní zpoždění</span><span class="sxs-lookup"><span data-stu-id="56f46-109"><xref:System.Activities.Statements.DurableTimerExtension> for implementing Absolute Delay</span></span>  
  
2.  <span data-ttu-id="56f46-110">Nastavení pomocí trvalosti <xref:System.Activities.WorkflowApplication> pro odolná časovače</span><span class="sxs-lookup"><span data-stu-id="56f46-110">Setting up persistence using <xref:System.Activities.WorkflowApplication> for Durable Timers</span></span>  
  
3.  <span data-ttu-id="56f46-111">Použití <xref:System.Activities.NativeActivity%601> pro používání body rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="56f46-111">Use of <xref:System.Activities.NativeActivity%601> for using Extensibility points</span></span>  
  
4.  <span data-ttu-id="56f46-112">Použití <xref:System.Activities.CodeActivity%601> v Connectoru aktivitu</span><span class="sxs-lookup"><span data-stu-id="56f46-112">Use of <xref:System.Activities.CodeActivity%601> in the SendEmail activity</span></span>  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  <span data-ttu-id="56f46-113">Pouze XAML pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="56f46-113">XAML-only workflow</span></span>  
  
 <span data-ttu-id="56f46-114">Tento příklad ukazuje, jak vytvořit vlastní aktivitu, která přebírá <xref:System.DateTime> a používá k registraci zpoždění Doba trvání trvanlivý časovače.</span><span class="sxs-lookup"><span data-stu-id="56f46-114">This sample demonstrates how to create a custom activity which takes in a <xref:System.DateTime> and uses durable timers to register the delay duration.</span></span> <span data-ttu-id="56f46-115">Pokud používáte trvanlivý časovače, je nutné použít <xref:System.Activities.NativeActivity> vytvořte záložku, jak budete muset zaregistrovat tuto záložku s příponou časovače.</span><span class="sxs-lookup"><span data-stu-id="56f46-115">When using durable timers, you must use a <xref:System.Activities.NativeActivity> to create a bookmark, as you will need to register this bookmark with the timer extension.</span></span> <span data-ttu-id="56f46-116">V této ukázce, když časovač trvanlivý vyprší `OnTimerExpired` volání metody.</span><span class="sxs-lookup"><span data-stu-id="56f46-116">In this sample, when the durable timer expires, the `OnTimerExpired` method will be called.</span></span> <span data-ttu-id="56f46-117">Ujistěte se, že přidáváte časovače rozšíření v <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> událostí zajistit tím modul runtime s těmito informacemi.</span><span class="sxs-lookup"><span data-stu-id="56f46-117">Make sure that you are adding the timer extension in the <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> event to ensure you are providing the runtime with this information.</span></span> <span data-ttu-id="56f46-118">Jenom jiné implementace podrobností je, že je nutné implementovat logiku pro převod z <xref:System.DateTime> k <xref:System.TimeSpan>, jak trvanlivý časovače trvat jenom <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="56f46-118">The only other implementation detail is that you will need to implement logic to convert from <xref:System.DateTime> to <xref:System.TimeSpan>, as durable timers only take in a <xref:System.DateTime>.</span></span> <span data-ttu-id="56f46-119">Všimněte si, že malé chybě přesnost nástrojem</span><span class="sxs-lookup"><span data-stu-id="56f46-119">Do note that there is a small lapse in accuracy by doing</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56f46-120">Existuje malé ztrátu přesnosti převodem z <xref:System.DateTime> k <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="56f46-120">There is a small loss of accuracy by converting from <xref:System.DateTime> to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="56f46-121">Tento příklad také ukazuje, jak zapnout stálost pro <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="56f46-121">This sample also demonstrates how to turn on persistence for a <xref:System.Activities.WorkflowApplication>.</span></span> <span data-ttu-id="56f46-122">Tato ukázka konkrétní použijeme trvanlivý časovače, ve kterých budou data pracovního postupu uvolněna do databáze trvalost během doby nečinnosti při čekání na časovač vyprší.</span><span class="sxs-lookup"><span data-stu-id="56f46-122">For this particular sample, we will be using durable timers in which the workflow data will be unloaded into the persistence database during the idle time while waiting for timer to expire.</span></span> <span data-ttu-id="56f46-123">Tato implementace mohou sloužit také pro další akce trvalost.</span><span class="sxs-lookup"><span data-stu-id="56f46-123">This implementation can also be used for other persistence actions.</span></span> <span data-ttu-id="56f46-124">Tento příklad ukazuje, jak nastavit připojovací řetězec trvalost s SQL serverem a postup vytvoření instance úložiště s cílem zachovat data instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="56f46-124">This sample shows how to set up the persistence connection string with SQL Server, and how to create the instance store in order to persist the data for workflow instances.</span></span> <span data-ttu-id="56f46-125">Logika je k dispozici o tom, jak obnovit pracovního postupu, jakmile se vyvolá událost, takže je spustitelného k instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="56f46-125">Logic is provided on how to resume the workflow once an event is raised which makes the workflow instance runnable.</span></span>  
  
 <span data-ttu-id="56f46-126">Krocích tuto ukázku, zobrazí se, že čas, ve kterém vestavěnou prodlevu zahájí a dokončení, který pak může způsobit e-mailovou zprávu k odeslání.</span><span class="sxs-lookup"><span data-stu-id="56f46-126">As you step through this sample, you will see the time in which the built-in delay begins and completes, which in turn will cause an email message to be sent.</span></span> <span data-ttu-id="56f46-127">Z tohoto místa se zastaví AbsoluteDelay aktivity do zadané <xref:System.DateTime> (nebo 0 sekund, pokud <xref:System.DateTime> vypršela platnost) který naopak k odeslání e-mailu po vypršení platnosti.</span><span class="sxs-lookup"><span data-stu-id="56f46-127">From there, the AbsoluteDelay activity will halt until a specified <xref:System.DateTime> (or 0 seconds if the <xref:System.DateTime> has expired) which in turn will send out an email upon expiration.</span></span> <span data-ttu-id="56f46-128">Tato rutina ukáže případech předdefinované použití dvou různých <xref:System.Activities.Statements.Delay> funkce a kdy AbsoluteDelay aktivitu.</span><span class="sxs-lookup"><span data-stu-id="56f46-128">This will show the two different use cases of the built-in <xref:System.Activities.Statements.Delay> functionality versus using an AbsoluteDelay activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="56f46-129">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="56f46-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="56f46-130">Ujistěte se, že máte systému SQL Server Express (nebo novější), nainstalovaný na počítači</span><span class="sxs-lookup"><span data-stu-id="56f46-130">Ensure you have SQL Server Express (or higher) installed on your machine</span></span>  
  
2.  <span data-ttu-id="56f46-131">Spustit setup.cmd (z WF/Basic/Services/AbsoluteDelay/CS) [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku AbsoluteDelaySampleDB databázi vytvořit, vytvořit schéma trvalosti a vytvořit logiku trvalost.</span><span class="sxs-lookup"><span data-stu-id="56f46-131">Run setup.cmd (from WF/Basic/Services/AbsoluteDelay/CS) in a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt to create the AbsoluteDelaySampleDB database, create the persistence schema and create the persistence logic.</span></span>  
  
3.  <span data-ttu-id="56f46-132">Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56f46-132">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="56f46-133">Zadejte dobu trvání aktivity zpoždění.</span><span class="sxs-lookup"><span data-stu-id="56f46-133">Specify the Duration in the Delay activity.</span></span>  
  
5.  <span data-ttu-id="56f46-134">Zadejte ExpirationTime AbsoluteDelay aktivity.</span><span class="sxs-lookup"><span data-stu-id="56f46-134">Specify the ExpirationTime in the AbsoluteDelay activity.</span></span>  
  
6.  <span data-ttu-id="56f46-135">Aktualizujte pole SendMailTo, SendMailFrom, SendMailSubject, SendMailBody a SmtpHost SendMail aktivity.</span><span class="sxs-lookup"><span data-stu-id="56f46-135">Update the SendMailTo, SendMailFrom, SendMailSubject, SendMailBody, and SmtpHost fields in the SendMail activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56f46-136">Pokud nezadáte platný hostitel SMTP, vyvolá aplikace SMTP výjimka.</span><span class="sxs-lookup"><span data-stu-id="56f46-136">If you do not enter a valid SMTP host, the application will throw a SMTP exception.</span></span>  
  
7.  <span data-ttu-id="56f46-137">Sestavte řešení výběrem **sestavení**, **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="56f46-137">Build the solution by selecting **Build**, **Build Solution**.</span></span>  
  
8.  <span data-ttu-id="56f46-138">Spuštění řešení stisknutím **F5**.</span><span class="sxs-lookup"><span data-stu-id="56f46-138">Run the solution by pressing **F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="56f46-139">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="56f46-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="56f46-140">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="56f46-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="56f46-141">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="56f46-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="56f46-142">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="56f46-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
