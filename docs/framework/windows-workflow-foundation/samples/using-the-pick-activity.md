---
title: Pomocí aktivity vybrat
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 9617949d72fb1489f66fec205b260b807d011177
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516939"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="a38ec-102">Pomocí aktivity vybrat</span><span class="sxs-lookup"><span data-stu-id="a38ec-102">Using the Pick Activity</span></span>
<span data-ttu-id="a38ec-103">Tento příklad znázorňuje způsob použití <xref:System.Activities.Statements.Pick> aktivity.</span><span class="sxs-lookup"><span data-stu-id="a38ec-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>  
  
 <span data-ttu-id="a38ec-104"><xref:System.Activities.Statements.Pick> Aktivity poskytuje modelování řízení na základě událostí.</span><span class="sxs-lookup"><span data-stu-id="a38ec-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="a38ec-105">Se chová podobně jako jazyka C# `switch` příkaz, který se spustí pouze jeden z poboček v `switch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a38ec-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="a38ec-106">Na rozdíl od `switch` příkaz, ve kterém se spustí větev na základě na hodnotu, <xref:System.Activities.Statements.Pick> aktivita provede větev podle jak dokončení aktivity.</span><span class="sxs-lookup"><span data-stu-id="a38ec-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>  
  
 <span data-ttu-id="a38ec-107">Tato ukázka vyzve uživatele k zadání v názvu v konzole a v daném časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="a38ec-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="a38ec-108"><xref:System.Activities.Statements.Pick> Aktivita v ukázce má dvě větve, které jsou spouštěny podle o tom, jestli uživatel zadá v názvu během 5 sekund nebo ne.</span><span class="sxs-lookup"><span data-stu-id="a38ec-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="a38ec-109">Pokud uživatel zadá v názvu během 5 sekund, je proveden první větve, který obsahuje vlastní `ReadLine` aktivity; v opačném případě jiné větev proveden, který obsahuje <xref:System.Activities.Statements.Delay> aktivity.</span><span class="sxs-lookup"><span data-stu-id="a38ec-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="a38ec-110">Jakmile uživatelské jméno je zadán v v konzole, uživatelské jméno je vytištěno na konzole.</span><span class="sxs-lookup"><span data-stu-id="a38ec-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="a38ec-111">Pokud vstup není zadán v rámci 5 sekund, je operace vypršel.</span><span class="sxs-lookup"><span data-stu-id="a38ec-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a38ec-112">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="a38ec-112">Demonstrates</span></span>  
 <span data-ttu-id="a38ec-113"><xref:System.Activities.Statements.Pick> aktivita.</span><span class="sxs-lookup"><span data-stu-id="a38ec-113"><xref:System.Activities.Statements.Pick> activity.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="a38ec-114">Diskusní</span><span class="sxs-lookup"><span data-stu-id="a38ec-114">Discussion</span></span>  
 <span data-ttu-id="a38ec-115">Ukázka zahrnuje Návrháře pracovního postupu a programové pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a38ec-115">The sample includes a Designer workflow and coded workflow.</span></span>  
  
 <span data-ttu-id="a38ec-116">Návrháře pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a38ec-116">Designer Workflow</span></span>  
 <span data-ttu-id="a38ec-117">Návrhář verzi příkladu ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="a38ec-117">The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="a38ec-118">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="a38ec-118">The following files are included:</span></span>  
  
-   <span data-ttu-id="a38ec-119">Program.cs: Zahrnuje `Main` funkce, která spustí ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="a38ec-119">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="a38ec-120">ReadString.cs: Vlastní aktivitu, která čte některé vstup z konzoly.</span><span class="sxs-lookup"><span data-stu-id="a38ec-120">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
-   <span data-ttu-id="a38ec-121">Sequence1.XAML: Pracovní postup vytvořený pomocí návrháře, který používá vyberte.</span><span class="sxs-lookup"><span data-stu-id="a38ec-121">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>  
  
 <span data-ttu-id="a38ec-122">Programové pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a38ec-122">Coded Workflow</span></span>  
 <span data-ttu-id="a38ec-123">Programové verzi příkladu ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="a38ec-123">The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="a38ec-124">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="a38ec-124">The following files are included:</span></span>  
  
-   <span data-ttu-id="a38ec-125">Program.cs: Zahrnuje `Main` funkce, která spustí ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="a38ec-125">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="a38ec-126">ReadString.cs: Vlastní aktivitu, která čte některé vstup z konzoly.</span><span class="sxs-lookup"><span data-stu-id="a38ec-126">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a38ec-127">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="a38ec-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="a38ec-128">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení Pick.sln.</span><span class="sxs-lookup"><span data-stu-id="a38ec-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Pick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a38ec-129">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a38ec-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a38ec-130">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="a38ec-130">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a38ec-131">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="a38ec-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a38ec-132">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a38ec-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a38ec-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a38ec-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a38ec-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a38ec-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`