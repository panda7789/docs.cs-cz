---
title: "Složení základní aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8eb909ce50c5faebf48339b07e8565fcd7afc718
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="basic-activity-composition"></a><span data-ttu-id="da2c4-102">Složení základní aktivity</span><span class="sxs-lookup"><span data-stu-id="da2c4-102">Basic Activity Composition</span></span>
<span data-ttu-id="da2c4-103">Tato ukázka ukazuje, jak vytvořit vlastní aktivity a poskytované systémem aktivit vytvořit více vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="da2c4-103">This sample demonstrates how to compose custom activities and system-provided activities to build more custom activities.</span></span>  
  
 <span data-ttu-id="da2c4-104">Pracovní postup pomocí aktivity průzkum plány průzkum seznam otázky a poté uloží odpovědí přijatých.</span><span class="sxs-lookup"><span data-stu-id="da2c4-104">The workflow using the Survey activity schedules the Survey with a list of questions, and then outputs the responses received.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="da2c4-105">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="da2c4-105">Sample Details</span></span>  
 <span data-ttu-id="da2c4-106">Tato ukázka používá tři vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="da2c4-106">This sample uses three custom activities.</span></span> <span data-ttu-id="da2c4-107">`ReadLine`je jednoduchý <xref:System.Activities.NativeActivity> \<řetězec > vytvářející <xref:System.Activities.Bookmark> při naplánované a nastaví `Return` <xref:System.Activities.OutArgument%601> na hodnotu, se kterým <xref:System.Activities.Bookmark> obnovení.</span><span class="sxs-lookup"><span data-stu-id="da2c4-107">`ReadLine` is a simple <xref:System.Activities.NativeActivity>\<string> that creates a <xref:System.Activities.Bookmark> when scheduled, and then sets the `Return`<xref:System.Activities.OutArgument%601> to the value with which the <xref:System.Activities.Bookmark> is resumed.</span></span> <span data-ttu-id="da2c4-108">`Prompt`je <xref:System.Activities.Activity%601> \<řetězec >, která má <xref:System.Activities.InArgument%601>< řetězec\> s názvem `Text` a vrátí uživatele v odpovědi `Result` <xref:System.Activities.OutArgument%601> \<řetězec >.</span><span class="sxs-lookup"><span data-stu-id="da2c4-108">`Prompt` is an <xref:System.Activities.Activity%601>\<string> that takes an <xref:System.Activities.InArgument%601><string\> named `Text` and returns the users response in the `Result`<xref:System.Activities.OutArgument%601>\<string>.</span></span> <span data-ttu-id="da2c4-109">`Prompt` Používá aktivitu <xref:System.Activities.Statements.Sequence> a <xref:System.Activities.Statements.WriteLine> aktivity, které se dodávají jako součást rozhraní .NET Framework a zahrnuje také vlastní `ReadLine` aktivity pro získání vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="da2c4-109">The `Prompt` activity uses the <xref:System.Activities.Statements.Sequence> and <xref:System.Activities.Statements.WriteLine> activities that ship as part of the .NET Framework, and also incorporates the custom `ReadLine` activity for getting user input.</span></span> <span data-ttu-id="da2c4-110">Poslední vlastní aktivita tvoří `Survey` aktivity.</span><span class="sxs-lookup"><span data-stu-id="da2c4-110">The last custom activity is the `Survey` activity.</span></span> <span data-ttu-id="da2c4-111">Je <xref:System.Activities.Activity>< ICollection\<řetězec >>.</span><span class="sxs-lookup"><span data-stu-id="da2c4-111">It is an <xref:System.Activities.Activity><ICollection\<string>>.</span></span>  <span data-ttu-id="da2c4-112">Tato aktivita přijímá <xref:System.Activities.InArgument%601>< IEnumerable < řetězec\>> s názvem `Questions` a naplní `Result` out argument s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="da2c4-112">This activity takes an <xref:System.Activities.InArgument%601><IEnumerable<string\>> named `Questions` and populates the `Result` out argument with the responses.</span></span> <span data-ttu-id="da2c4-113">`Survey` Aktivita používá <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> a <xref:System.Activities.Statements.AddToCollection%601> z rozhraní .NET Framework a zahrnuje `Prompt` aktivity pro otázkami průzkum a získávání odpovědí.</span><span class="sxs-lookup"><span data-stu-id="da2c4-113">The `Survey` activity uses <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> and <xref:System.Activities.Statements.AddToCollection%601> from the .NET Framework and employs the `Prompt` activity for asking the survey questions and getting responses.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="da2c4-114">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="da2c4-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="da2c4-115">Otevřete **BasicActivityComposition.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da2c4-115">Open the **BasicActivityComposition.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="da2c4-116">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="da2c4-116">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="da2c4-117">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="da2c4-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="da2c4-118">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="da2c4-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="da2c4-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="da2c4-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="da2c4-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="da2c4-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`