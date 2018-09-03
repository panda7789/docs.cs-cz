---
title: Absolutní prodleva
ms.date: 03/30/2017
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
ms.openlocfilehash: 30719a4340b738a7462584c4dca00f6d5d90ac72
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486099"
---
# <a name="absolute-delay"></a><span data-ttu-id="9ad39-102">Absolutní prodleva</span><span class="sxs-lookup"><span data-stu-id="9ad39-102">Absolute Delay</span></span>
<span data-ttu-id="9ad39-103">Hlavní scénáře pro tuto ukázku spočívá ve zpoždění až do zadaného <xref:System.DateTime> pomocí časovače odolné aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9ad39-103">The main scenario for this sample is to delay until a specified <xref:System.DateTime> using durable timers in a workflow application.</span></span> <span data-ttu-id="9ad39-104">Tím se liší od použití předdefinované <xref:System.Activities.Statements.Delay> aktivitu jako tento vám pouze umožní, než se dané <xref:System.TimeSpan> (nebo počet minut nebo sekund).</span><span class="sxs-lookup"><span data-stu-id="9ad39-104">This is different from using the built-in <xref:System.Activities.Statements.Delay> activity as this will only allow you to delay for a given <xref:System.TimeSpan> (or number of minutes/seconds).</span></span>  
  
 <span data-ttu-id="9ad39-105">Některé reálné scénáře, ve kterých chcete rozlišit patří následující:</span><span class="sxs-lookup"><span data-stu-id="9ad39-105">Some real-life scenarios in which you may want to make this distinction include the following:</span></span>  
  
1.  <span data-ttu-id="9ad39-106">Chcete-li prodleva odesílání e-mailu pro 30 sekund, ujistěte se, že jste nevytvořili žádné chyby.</span><span class="sxs-lookup"><span data-stu-id="9ad39-106">You want to delay sending a mail for 30 seconds to make sure you didn’t make any errors.</span></span>  
  
2.  <span data-ttu-id="9ad39-107">Jsou pracují a chcete zpoždění všechny vaše e-mailů do normální pracovních hodin (například 8: 00).</span><span class="sxs-lookup"><span data-stu-id="9ad39-107">You are working overtime and want to delay all of your mails until normal business hours (such as 8 am).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9ad39-108">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="9ad39-108">Demonstrates</span></span>  
  
1.  <span data-ttu-id="9ad39-109"><xref:System.Activities.Statements.DurableTimerExtension> pro implementaci absolutní prodleva</span><span class="sxs-lookup"><span data-stu-id="9ad39-109"><xref:System.Activities.Statements.DurableTimerExtension> for implementing Absolute Delay</span></span>  
  
2.  <span data-ttu-id="9ad39-110">Nastavení trvalosti pomocí <xref:System.Activities.WorkflowApplication> pro trvalý časovače</span><span class="sxs-lookup"><span data-stu-id="9ad39-110">Setting up persistence using <xref:System.Activities.WorkflowApplication> for Durable Timers</span></span>  
  
3.  <span data-ttu-id="9ad39-111">Použití <xref:System.Activities.NativeActivity%601> pro používání bodů rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="9ad39-111">Use of <xref:System.Activities.NativeActivity%601> for using Extensibility points</span></span>  
  
4.  <span data-ttu-id="9ad39-112">Použití <xref:System.Activities.CodeActivity%601> v Connectoru aktivitu</span><span class="sxs-lookup"><span data-stu-id="9ad39-112">Use of <xref:System.Activities.CodeActivity%601> in the SendEmail activity</span></span>  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  <span data-ttu-id="9ad39-113">Pracovní postup pouze pro XAML</span><span class="sxs-lookup"><span data-stu-id="9ad39-113">XAML-only workflow</span></span>  
  
 <span data-ttu-id="9ad39-114">Tento příklad ukazuje, jak vytvořit vlastní aktivitu, která přijímá <xref:System.DateTime> a trvalý časovače používá k registraci doba zpoždění.</span><span class="sxs-lookup"><span data-stu-id="9ad39-114">This sample demonstrates how to create a custom activity which takes in a <xref:System.DateTime> and uses durable timers to register the delay duration.</span></span> <span data-ttu-id="9ad39-115">Při použití trvalý časovače, je nutné použít <xref:System.Activities.NativeActivity> vytvořte záložku, jak budete muset zaregistrovat tuto záložku pomocí časovače rozšíření.</span><span class="sxs-lookup"><span data-stu-id="9ad39-115">When using durable timers, you must use a <xref:System.Activities.NativeActivity> to create a bookmark, as you will need to register this bookmark with the timer extension.</span></span> <span data-ttu-id="9ad39-116">V této ukázce, když vyprší platnost trvalý časovač `OnTimerExpired` metoda bude volána.</span><span class="sxs-lookup"><span data-stu-id="9ad39-116">In this sample, when the durable timer expires, the `OnTimerExpired` method will be called.</span></span> <span data-ttu-id="9ad39-117">Ujistěte se, že přidáváte časovače rozšíření v <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> událostí, aby pomocí těchto informací poskytujete modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9ad39-117">Make sure that you are adding the timer extension in the <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> event to ensure you are providing the runtime with this information.</span></span> <span data-ttu-id="9ad39-118">Jenom další podrobnosti implementace je, že budete muset implementovat logiku pro převod z <xref:System.DateTime> k <xref:System.TimeSpan>, protože trvalého časovače trvat pouze <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="9ad39-118">The only other implementation detail is that you will need to implement logic to convert from <xref:System.DateTime> to <xref:System.TimeSpan>, as durable timers only take in a <xref:System.DateTime>.</span></span> <span data-ttu-id="9ad39-119">Mějte na paměti, že existuje malé zachytí přesnost prováděním</span><span class="sxs-lookup"><span data-stu-id="9ad39-119">Do note that there is a small lapse in accuracy by doing</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ad39-120">Existuje malé ztrátou přesnosti převodem z <xref:System.DateTime> k <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="9ad39-120">There is a small loss of accuracy by converting from <xref:System.DateTime> to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="9ad39-121">Tento příklad také ukazuje, jak zapnout stálost pro <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="9ad39-121">This sample also demonstrates how to turn on persistence for a <xref:System.Activities.WorkflowApplication>.</span></span> <span data-ttu-id="9ad39-122">V tomto konkrétním příkladu použijeme trvalý časovače, ve kterých se data pracovního postupu uvolněných do databáze trvalosti během doby nečinnosti při čekání na časovač vypršení platnosti.</span><span class="sxs-lookup"><span data-stu-id="9ad39-122">For this particular sample, we will be using durable timers in which the workflow data will be unloaded into the persistence database during the idle time while waiting for timer to expire.</span></span> <span data-ttu-id="9ad39-123">Tato implementace lze použít také pro další akce trvalosti.</span><span class="sxs-lookup"><span data-stu-id="9ad39-123">This implementation can also be used for other persistence actions.</span></span> <span data-ttu-id="9ad39-124">Tento příklad ukazuje, jak nastavit připojovací řetězec trvalost s SQL serverem a tom, jak vytvořit v úložišti instancí, aby bylo možné zachovat data instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9ad39-124">This sample shows how to set up the persistence connection string with SQL Server, and how to create the instance store in order to persist the data for workflow instances.</span></span> <span data-ttu-id="9ad39-125">Logika je k dispozici na tom, jak obnovit pracovní postup po vyvolá událost, díky spustitelné instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9ad39-125">Logic is provided on how to resume the workflow once an event is raised which makes the workflow instance runnable.</span></span>  
  
 <span data-ttu-id="9ad39-126">Krocích této ukázce uvidíte, že čas, ve kterém integrované zpoždění zahájí a dokončí, která zase způsobí, že e-mailové zprávy k odeslání.</span><span class="sxs-lookup"><span data-stu-id="9ad39-126">As you step through this sample, you will see the time in which the built-in delay begins and completes, which in turn will cause an email message to be sent.</span></span> <span data-ttu-id="9ad39-127">Odtud se zastaví aktivity AbsoluteDelay až do zadaného <xref:System.DateTime> (nebo 0 sekund, pokud <xref:System.DateTime> vypršela platnost) který pak se rozešle e-mail po vypršení platnosti.</span><span class="sxs-lookup"><span data-stu-id="9ad39-127">From there, the AbsoluteDelay activity will halt until a specified <xref:System.DateTime> (or 0 seconds if the <xref:System.DateTime> has expired) which in turn will send out an email upon expiration.</span></span> <span data-ttu-id="9ad39-128">Tím se zobrazí dvě různé případy integrovaných použití <xref:System.Activities.Statements.Delay> funkce oproti použití AbsoluteDelay aktivity.</span><span class="sxs-lookup"><span data-stu-id="9ad39-128">This will show the two different use cases of the built-in <xref:System.Activities.Statements.Delay> functionality versus using an AbsoluteDelay activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9ad39-129">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="9ad39-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9ad39-130">Ujistěte se, že máte SQL Server Express (nebo vyšší) na vašem počítači nainstalovaná</span><span class="sxs-lookup"><span data-stu-id="9ad39-130">Ensure you have SQL Server Express (or higher) installed on your machine</span></span>  
  
2.  <span data-ttu-id="9ad39-131">Spustit setup.cmd (z WF/Basic/Services/AbsoluteDelay/CS) [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku vytvořit AbsoluteDelaySampleDB databázi, vytvoření schématu trvalosti a vytvoření logiky trvalosti.</span><span class="sxs-lookup"><span data-stu-id="9ad39-131">Run setup.cmd (from WF/Basic/Services/AbsoluteDelay/CS) in a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt to create the AbsoluteDelaySampleDB database, create the persistence schema and create the persistence logic.</span></span>  
  
3.  <span data-ttu-id="9ad39-132">Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9ad39-132">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="9ad39-133">V aktivitě Delay určete dobu trvání.</span><span class="sxs-lookup"><span data-stu-id="9ad39-133">Specify the Duration in the Delay activity.</span></span>  
  
5.  <span data-ttu-id="9ad39-134">Zadejte ExpirationTime AbsoluteDelay aktivity.</span><span class="sxs-lookup"><span data-stu-id="9ad39-134">Specify the ExpirationTime in the AbsoluteDelay activity.</span></span>  
  
6.  <span data-ttu-id="9ad39-135">Aktualizují se pole SendMailTo SendMailFrom, SendMailSubject, SendMailBody a SmtpHost v aktivita SendMail.</span><span class="sxs-lookup"><span data-stu-id="9ad39-135">Update the SendMailTo, SendMailFrom, SendMailSubject, SendMailBody, and SmtpHost fields in the SendMail activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9ad39-136">Pokud se platný hostitel SMTP nezadáte, aplikace vyvolá výjimka SMTP.</span><span class="sxs-lookup"><span data-stu-id="9ad39-136">If you do not enter a valid SMTP host, the application will throw a SMTP exception.</span></span>  
  
7.  <span data-ttu-id="9ad39-137">Sestavte řešení tak, že vyberete **sestavení**, **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="9ad39-137">Build the solution by selecting **Build**, **Build Solution**.</span></span>  
  
8.  <span data-ttu-id="9ad39-138">Spuštění řešení stisknutím kombinace kláves **F5**.</span><span class="sxs-lookup"><span data-stu-id="9ad39-138">Run the solution by pressing **F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9ad39-139">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="9ad39-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9ad39-140">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9ad39-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9ad39-141">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9ad39-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ad39-142">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9ad39-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
