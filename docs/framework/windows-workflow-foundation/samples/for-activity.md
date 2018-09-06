---
title: Pro aktivitu
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: 7a7023abb9057ab4b25552fbf9a81cd2ae2b4e88
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881518"
---
# <a name="for-activity"></a><span data-ttu-id="659e4-102">Pro aktivitu</span><span class="sxs-lookup"><span data-stu-id="659e4-102">For Activity</span></span>
<span data-ttu-id="659e4-103">Ukázka pro předvádí, jak vytvořit vlastní aktivitu, která dědí z <xref:System.Activities.NativeActivity>a použít ho v pracovním postupu spustit příklad reálného světa.</span><span class="sxs-lookup"><span data-stu-id="659e4-103">The For sample demonstrates how to build a custom activity that inherits from <xref:System.Activities.NativeActivity>, and use it in a workflow to execute a real world example.</span></span> <span data-ttu-id="659e4-104">Vlastní aktivity, které jsou zahrnuté v této ukázkové funkce, jako je C# `for` příkazu.</span><span class="sxs-lookup"><span data-stu-id="659e4-104">The custom activity included in this sample functions like the C# `for` statement.</span></span> <span data-ttu-id="659e4-105">T</span><span class="sxs-lookup"><span data-stu-id="659e4-105">T</span></span>  
  
 <span data-ttu-id="659e4-106">`For` Vlastní aktivita má vlastnosti s názvem `InitAction`, `IterationAction`, `Condition`, a `Body` , které odpovídají příkaz inicializace, iterativního příkazu, pokračování podmínku a těla příkazu v uvedeném pořadí součástí standard jazyka C# `For` příkazu.</span><span class="sxs-lookup"><span data-stu-id="659e4-106">The `For` custom activity has properties named `InitAction`, `IterationAction`, `Condition`, and `Body` that correspond to the initialization statement, iterative statement, continuation condition, and body statement respectively found in the standard C# `For` statement.</span></span>  
  
 <span data-ttu-id="659e4-107">Následující tabulka popisuje soubory klíčů ve vzorku.</span><span class="sxs-lookup"><span data-stu-id="659e4-107">The following table describes the key files in the sample.</span></span>  
  
|<span data-ttu-id="659e4-108">Soubor</span><span class="sxs-lookup"><span data-stu-id="659e4-108">File</span></span>|<span data-ttu-id="659e4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="659e4-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="659e4-110">For.cs</span><span class="sxs-lookup"><span data-stu-id="659e4-110">For.cs</span></span>|<span data-ttu-id="659e4-111">Třídy definice `For` vlastní aktivitu, která rozšiřuje <xref:System.Activities.NativeActivity> třídy pro zajištění funkcí jazyka C# `For` příkazu.</span><span class="sxs-lookup"><span data-stu-id="659e4-111">Class definition for the `For` custom activity, which extends the <xref:System.Activities.NativeActivity> class to provide the functionality of the C# `For` statement.</span></span>|  
|<span data-ttu-id="659e4-112">Program.cs</span><span class="sxs-lookup"><span data-stu-id="659e4-112">Program.cs</span></span>|<span data-ttu-id="659e4-113">Klientská aplikace, který provádí základní iterativní práci na kolekci pomocí vlastní `For` aktivity.</span><span class="sxs-lookup"><span data-stu-id="659e4-113">A client application that performs basic iterative work on a collection using the custom `For` activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="659e4-114">Při použití `For` vlastní aktivitu, ujistěte se, že `Condition` je nastavena; jinak může dojít k nekonečné smyčce.</span><span class="sxs-lookup"><span data-stu-id="659e4-114">When using the `For` custom activity, ensure that the `Condition` property is set; otherwise an infinite loop could occur.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="659e4-115">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="659e4-115">Demonstrates</span></span>  
 <span data-ttu-id="659e4-116">Vytvořit vlastní aktivitu, která dědí z <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="659e4-116">Create a custom activity that inherits from <xref:System.Activities.NativeActivity>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="659e4-117">Diskuse</span><span class="sxs-lookup"><span data-stu-id="659e4-117">Discussion</span></span>  
 <span data-ttu-id="659e4-118">Následující tabulka popisuje vlastnosti aktivity zahrnuté v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="659e4-118">The following table describes the properties of the activity included in this sample.</span></span>  
  
 <span data-ttu-id="659e4-119">InitAction</span><span class="sxs-lookup"><span data-stu-id="659e4-119">InitAction</span></span>  
 <span data-ttu-id="659e4-120">Inicializace – příkaz</span><span class="sxs-lookup"><span data-stu-id="659e4-120">Initialization statement</span></span>  
  
 <span data-ttu-id="659e4-121">IterationAction</span><span class="sxs-lookup"><span data-stu-id="659e4-121">IterationAction</span></span>  
 <span data-ttu-id="659e4-122">Iterativní – příkaz</span><span class="sxs-lookup"><span data-stu-id="659e4-122">Iterative statement</span></span>  
  
 <span data-ttu-id="659e4-123">Podmínka</span><span class="sxs-lookup"><span data-stu-id="659e4-123">Condition</span></span>  
 <span data-ttu-id="659e4-124">Příkaz pokračování</span><span class="sxs-lookup"><span data-stu-id="659e4-124">Continuation statement</span></span>  
  
 <span data-ttu-id="659e4-125">Text</span><span class="sxs-lookup"><span data-stu-id="659e4-125">Body</span></span>  
 <span data-ttu-id="659e4-126">Text příkazu</span><span class="sxs-lookup"><span data-stu-id="659e4-126">Body statement</span></span>  
  
 <span data-ttu-id="659e4-127">Aktivita dědí z <xref:System.Activities.NativeActivity> k získání přístupu k vlastnosti modulu runtime, jako je plánování další aktivity byste měli spustit, použijte některý `ScheduleActivity` metody <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="659e4-127">The activity inherits from <xref:System.Activities.NativeActivity> to gain access to runtime features such as scheduling additional activities to run, using one of the `ScheduleActivity` methods of <xref:System.Activities.NativeActivityContext>.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="659e4-128">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="659e4-128">To use this sample</span></span>  
  
1.  <span data-ttu-id="659e4-129">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení For.sln.</span><span class="sxs-lookup"><span data-stu-id="659e4-129">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the For.sln solution file.</span></span>  
  
2.  <span data-ttu-id="659e4-130">Sestavte řešení, stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="659e4-130">Build the solution, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="659e4-131">Spuštění řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="659e4-131">Run the solution, by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="659e4-132">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="659e4-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="659e4-133">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="659e4-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="659e4-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="659e4-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="659e4-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="659e4-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`