---
title: Použití aktivity Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 59f99d2e0a69d796c1ec64093cf73e07b88887c9
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2018
ms.locfileid: "48848280"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="8c919-102">Použití aktivity Pick</span><span class="sxs-lookup"><span data-stu-id="8c919-102">Using the Pick Activity</span></span>
<span data-ttu-id="8c919-103">Tato ukázka předvádí, jak používat <xref:System.Activities.Statements.Pick> aktivity.</span><span class="sxs-lookup"><span data-stu-id="8c919-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="8c919-104"><xref:System.Activities.Statements.Pick> Aktivita poskytuje modelování založené na události ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8c919-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="8c919-105">Se chová podobně jako C# `switch` příkazu, který se spustí pouze jeden z větve ve `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8c919-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="8c919-106">Na rozdíl od `switch` příkazu, ve kterém je spuštěn větev na základě na základě hodnot <xref:System.Activities.Statements.Pick> aktivity spustí větev na základě způsobu dokončení aktivity.</span><span class="sxs-lookup"><span data-stu-id="8c919-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="8c919-107">Tato ukázka vyzve uživatele k zadání názvu v konzole v daném časovém období.</span><span class="sxs-lookup"><span data-stu-id="8c919-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="8c919-108"><xref:System.Activities.Statements.Pick> Aktivita v ukázce má dvě větve, které jsou spouštěny na základě Určuje, zda uživatel zadá v jejich názvu do 5 sekund nebo ne.</span><span class="sxs-lookup"><span data-stu-id="8c919-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="8c919-109">Pokud uživatel zadá v jejich názvu do 5 sekund, je proveden první větev, která obsahuje vlastní `ReadLine` aktivity; jinak jiné větve je spuštěn, které se nachází <xref:System.Activities.Statements.Delay> aktivity.</span><span class="sxs-lookup"><span data-stu-id="8c919-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="8c919-110">Jakmile se v konzole je zadali uživatelské jméno, uživatelské jméno je vytištěna v konzole.</span><span class="sxs-lookup"><span data-stu-id="8c919-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="8c919-111">Pokud vstup není zadán do 5 sekund, vypršení časového limitu operace.</span><span class="sxs-lookup"><span data-stu-id="8c919-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8c919-112">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="8c919-112">Demonstrates</span></span>
 <span data-ttu-id="8c919-113"><xref:System.Activities.Statements.Pick> aktivita.</span><span class="sxs-lookup"><span data-stu-id="8c919-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="8c919-114">Diskuse</span><span class="sxs-lookup"><span data-stu-id="8c919-114">Discussion</span></span>
 <span data-ttu-id="8c919-115">Ukázka zahrnuje Návrháře pracovního postupu a programové pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8c919-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="8c919-116">Návrháře návrháři postupu provádění verzi ukázky ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="8c919-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="8c919-117">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="8c919-117">The following files are included:</span></span>

-   <span data-ttu-id="8c919-118">Program.cs: Zahrnuje `Main` funkci, která spustí ukázkového pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8c919-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

-   <span data-ttu-id="8c919-119">ReadString.cs: Vlastní aktivitu, která čte vstupu z konzoly.</span><span class="sxs-lookup"><span data-stu-id="8c919-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

-   <span data-ttu-id="8c919-120">Sequence1.XAML: Pracovní postup vytvořený v Návrháři vyberte používá.</span><span class="sxs-lookup"><span data-stu-id="8c919-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="8c919-121">Programové pracovního postupu programové verzi ukázky ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="8c919-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="8c919-122">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="8c919-122">The following files are included:</span></span>

-   <span data-ttu-id="8c919-123">Program.cs: Zahrnuje `Main` funkci, která spustí ukázkového pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8c919-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

-   <span data-ttu-id="8c919-124">ReadString.cs: Vlastní aktivitu, která čte vstupu z konzoly.</span><span class="sxs-lookup"><span data-stu-id="8c919-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="8c919-125">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="8c919-125">To use this sample</span></span>

1.  <span data-ttu-id="8c919-126">Pomocí sady Visual Studio 2010, otevřete soubor řešení Pick.sln.</span><span class="sxs-lookup"><span data-stu-id="8c919-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2.  <span data-ttu-id="8c919-127">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="8c919-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="8c919-128">Abyste mohli spustit řešení, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="8c919-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="8c919-129">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="8c919-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8c919-130">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8c919-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8c919-131">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8c919-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8c919-132">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8c919-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`