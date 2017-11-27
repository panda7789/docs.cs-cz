---
title: "Pomocí aktivity vybrat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5a95567afd955848b81bc343109acfe3fd138c7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="b2555-102">Pomocí aktivity vybrat</span><span class="sxs-lookup"><span data-stu-id="b2555-102">Using the Pick Activity</span></span>
<span data-ttu-id="b2555-103">Tento příklad znázorňuje způsob použití <xref:System.Activities.Statements.Pick> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b2555-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>  
  
 <span data-ttu-id="b2555-104"><xref:System.Activities.Statements.Pick> Aktivity poskytuje modelování řízení na základě událostí.</span><span class="sxs-lookup"><span data-stu-id="b2555-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="b2555-105">Se chová podobně jako jazyka C# `switch` příkaz, který se spustí pouze jeden z poboček v `switch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="b2555-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="b2555-106">Na rozdíl od `switch` příkaz, ve kterém se spustí větev na základě na hodnotu, <xref:System.Activities.Statements.Pick> aktivita provede větev podle jak dokončení aktivity.</span><span class="sxs-lookup"><span data-stu-id="b2555-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>  
  
 <span data-ttu-id="b2555-107">Tato ukázka vyzve uživatele k zadání v názvu v konzole a v daném časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="b2555-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="b2555-108"><xref:System.Activities.Statements.Pick> Aktivita v ukázce má dvě větve, které jsou spouštěny podle o tom, jestli uživatel zadá v názvu během 5 sekund nebo ne.</span><span class="sxs-lookup"><span data-stu-id="b2555-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="b2555-109">Pokud uživatel zadá v názvu během 5 sekund, je proveden první větve, který obsahuje vlastní `ReadLine` aktivity; v opačném případě jiné větev proveden, který obsahuje <xref:System.Activities.Statements.Delay> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b2555-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="b2555-110">Jakmile uživatelské jméno je zadán v v konzole, uživatelské jméno je vytištěno na konzole.</span><span class="sxs-lookup"><span data-stu-id="b2555-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="b2555-111">Pokud vstup není zadán v rámci 5 sekund, je operace vypršel.</span><span class="sxs-lookup"><span data-stu-id="b2555-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b2555-112">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="b2555-112">Demonstrates</span></span>  
 <span data-ttu-id="b2555-113"><xref:System.Activities.Statements.Pick>aktivita.</span><span class="sxs-lookup"><span data-stu-id="b2555-113"><xref:System.Activities.Statements.Pick> activity.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b2555-114">Diskusní</span><span class="sxs-lookup"><span data-stu-id="b2555-114">Discussion</span></span>  
 <span data-ttu-id="b2555-115">Ukázka zahrnuje Návrháře pracovního postupu a programové pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b2555-115">The sample includes a Designer workflow and coded workflow.</span></span>  
  
 <span data-ttu-id="b2555-116">Návrháře pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b2555-116">Designer Workflow</span></span>  
 <span data-ttu-id="b2555-117">Návrhář verzi příkladu ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="b2555-117">The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="b2555-118">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="b2555-118">The following files are included:</span></span>  
  
-   <span data-ttu-id="b2555-119">Program.cs: Zahrnuje `Main` funkce, která spustí ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="b2555-119">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="b2555-120">ReadString.cs: Vlastní aktivitu, která čte některé vstup z konzoly.</span><span class="sxs-lookup"><span data-stu-id="b2555-120">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
-   <span data-ttu-id="b2555-121">Sequence1.XAML: Pracovní postup vytvořený pomocí návrháře, který používá vyberte.</span><span class="sxs-lookup"><span data-stu-id="b2555-121">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>  
  
 <span data-ttu-id="b2555-122">Programové pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b2555-122">Coded Workflow</span></span>  
 <span data-ttu-id="b2555-123">Programové verzi příkladu ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="b2555-123">The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="b2555-124">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="b2555-124">The following files are included:</span></span>  
  
-   <span data-ttu-id="b2555-125">Program.cs: Zahrnuje `Main` funkce, která spustí ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="b2555-125">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="b2555-126">ReadString.cs: Vlastní aktivitu, která čte některé vstup z konzoly.</span><span class="sxs-lookup"><span data-stu-id="b2555-126">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b2555-127">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="b2555-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="b2555-128">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení Pick.sln.</span><span class="sxs-lookup"><span data-stu-id="b2555-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Pick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b2555-129">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b2555-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b2555-130">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="b2555-130">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b2555-131">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="b2555-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b2555-132">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b2555-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b2555-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b2555-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b2555-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b2555-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`  
  
## <a name="see-also"></a><span data-ttu-id="b2555-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2555-135">See Also</span></span>
