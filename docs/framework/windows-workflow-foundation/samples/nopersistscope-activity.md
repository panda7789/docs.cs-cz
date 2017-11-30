---
title: NoPersistScope aktivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f0dae84428f079dc3efb0c7ee620fa8c6ff87a8f
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="nopersistscope-activity"></a><span data-ttu-id="b9ee0-102">NoPersistScope aktivity</span><span class="sxs-lookup"><span data-stu-id="b9ee0-102">NoPersistScope Activity</span></span>
<span data-ttu-id="b9ee0-103">Tento příklad ukazuje, jak k manipulaci s neserializovatelných a na jedno použití stavu v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-103">This sample shows how to manipulate a non-serializable and disposable state within a workflow.</span></span> <span data-ttu-id="b9ee0-104">Je důležité, aby pracovní postupy Nepokoušejte se zachovat neserializovatelných stavu a je také důležité pro uvolnitelné objekty, které chcete vymazat, jakmile se používají v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-104">It is important that workflows do not attempt to persist non-serializable state and it is also important for disposable objects to be cleaned up after they are used in workflow.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b9ee0-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="b9ee0-105">Demonstrates</span></span>  
 <span data-ttu-id="b9ee0-106">`NoPersistScope`vlastní aktivity a návrháři.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-106">`NoPersistScope` custom activity and designer.</span></span>  
  
## <a name="using-the-nopersistzone-activity"></a><span data-ttu-id="b9ee0-107">Pomocí aktivity NoPersistZone</span><span class="sxs-lookup"><span data-stu-id="b9ee0-107">Using the NoPersistZone activity</span></span>  
 <span data-ttu-id="b9ee0-108">Pokud ukázkový pracovní postup běží, vlastní aktivity volat `CreateTextWriter` vytvoří objekt typu <xref:System.IO.TextWriter> a ukládá je do proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-108">When the sample workflow runs, a custom activity called `CreateTextWriter` creates an object of type <xref:System.IO.TextWriter> and saves it into a workflow variable.</span></span> <span data-ttu-id="b9ee0-109"><xref:System.IO.TextWriter>je <xref:System.IDisposable> objektu.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-109"><xref:System.IO.TextWriter> is an <xref:System.IDisposable> object.</span></span> <span data-ttu-id="b9ee0-110">To <xref:System.IO.TextWriter>, je používána k zápisu do souboru s názvem 'out.txt' v adresáři, ve kterém běží ukázku, která je nakonfigurována <xref:System.Activities.Statements.WriteLine> aktivitu jako ho vrátí jakýkoli text, kterou zadáte v konzole.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-110">This <xref:System.IO.TextWriter>, which is configured to write to a file named ‘out.txt’ in the directory in which the sample runs, is used by a <xref:System.Activities.Statements.WriteLine> activity as it echoes any text you type in at the console.</span></span>  
  
 <span data-ttu-id="b9ee0-111">Echo logiku běží v rámci `NoPersistScope` aktivity (kód, pro který je také součástí této ukázce), což zabraňuje pracovního postupu byly trvalé.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-111">The echo logic runs within a `NoPersistScope` activity (the code for which is also part of this sample), which prevents the workflow from being persisted.</span></span> <span data-ttu-id="b9ee0-112">Pokud zadáte v `unload` v konzole, hostitel pokusí uložit instanci pracovního postupu, ale vyprší tuto operaci, protože pracovní postup pořád v rámci `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-112">If you type in `unload` at the console, the host attempts to persist the workflow instance but this operation times out because the workflow remains within a `NoPersistScope`.</span></span> <span data-ttu-id="b9ee0-113">Pracovní postup také využívá vlastní aktivity volá `Dispose` k uvolnění <xref:System.IO.TextWriter> objektu až po dokončení pracovního postupu pomocí ho.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-113">The workflow also utilizes a custom activity called `Dispose` to dispose the <xref:System.IO.TextWriter> object when the workflow is finished using it.</span></span> <span data-ttu-id="b9ee0-114">`Dispose` Aktivity je umístěn v rámci <xref:System.Activities.Statements.TryCatch.Finally%2A> blokovat z <xref:System.Activities.Statements.TryCatch> činnosti, ve kterých <xref:System.IO.TextWriter> proměnné je deklarovaná zajistit, aby byl spouštěn i v případě, že k během provádění bloku Try by mělo dojít k výjimce.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-114">The `Dispose` activity is placed within the <xref:System.Activities.Statements.TryCatch.Finally%2A> block of the <xref:System.Activities.Statements.TryCatch> activity in which the <xref:System.IO.TextWriter> variable is declared, to ensure that it runs even if an exception should occur during execution of the Try block.</span></span>  
  
 <span data-ttu-id="b9ee0-115">Můžete zadat v `exit` dokončit k instanci pracovního postupu a ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-115">You can type in `exit` to complete the workflow instance and exit the program.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="b9ee0-116">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="b9ee0-116">To run the sample</span></span>  
  
1.  <span data-ttu-id="b9ee0-117">Otevřete řešení NoPersistZone.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b9ee0-117">Open the NoPersistZone.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="b9ee0-118">Sestavte řešení, stiskněte CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-118">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="b9ee0-119">Po sestavení proběhla úspěšně, stiskněte klávesu F5, nebo vyberte **spustit ladění** z **ladění** nabídky můžete alternativně stiskněte klávesy CTRL + F5 nebo vybrat **spustit bez ladění** z **Ladění** nabídku spustit bez ladění.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-119">Once the build has succeeded, press F5 or select **Start Debugging** from the **Debug** menu alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="b9ee0-120">Pro čištění (volitelné)</span><span class="sxs-lookup"><span data-stu-id="b9ee0-120">To cleanup (optional)</span></span>  
  
1.  <span data-ttu-id="b9ee0-121">Chcete-li odebrat úložiště Instance SQL, spusťte Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-121">To remove the SQL Instance Store, run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b9ee0-122">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b9ee0-123">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b9ee0-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b9ee0-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b9ee0-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b9ee0-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`