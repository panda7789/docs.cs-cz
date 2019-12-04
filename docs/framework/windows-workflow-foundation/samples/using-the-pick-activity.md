---
title: Použití aktivity Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: b0997254615ca962fd386dea70c67a8edb36c90a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715531"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="3903a-102">Použití aktivity Pick</span><span class="sxs-lookup"><span data-stu-id="3903a-102">Using the Pick Activity</span></span>
<span data-ttu-id="3903a-103">Tato ukázka demonstruje použití aktivity <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="3903a-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="3903a-104">Aktivita <xref:System.Activities.Statements.Pick> poskytuje modelování ovládacího prvku založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="3903a-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="3903a-105">Chová se podobně jako příkaz C# `switch`, který spouští pouze jednu z větví v příkazu `switch`.</span><span class="sxs-lookup"><span data-stu-id="3903a-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="3903a-106">Na rozdíl od příkazu `switch`, ve kterém je větev spouštěna na základě hodnoty, aktivita <xref:System.Activities.Statements.Pick> spustí větev na základě toho, jak se aktivita dokončí.</span><span class="sxs-lookup"><span data-stu-id="3903a-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="3903a-107">Tato ukázka vyzve uživatele k zadání názvu v konzole v daném časovém období.</span><span class="sxs-lookup"><span data-stu-id="3903a-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="3903a-108">Aktivita <xref:System.Activities.Statements.Pick> v ukázce má dvě větve, které jsou spuštěny na základě toho, zda uživatel zadá jméno do 5 sekund nebo ne.</span><span class="sxs-lookup"><span data-stu-id="3903a-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="3903a-109">Pokud uživatel zadá jméno do 5 sekund, spustí se první větev, která obsahuje vlastní aktivitu `ReadLine`; v opačném případě se spustí druhá větev, která obsahuje aktivitu <xref:System.Activities.Statements.Delay>.</span><span class="sxs-lookup"><span data-stu-id="3903a-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="3903a-110">Po zadání jména uživatele v konzole nástroje se v konzole vytiskne jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="3903a-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="3903a-111">Pokud vstup není zadán do 5 sekund, vypršel časový limit operace.</span><span class="sxs-lookup"><span data-stu-id="3903a-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3903a-112">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="3903a-112">Demonstrates</span></span>
 <span data-ttu-id="3903a-113"><xref:System.Activities.Statements.Pick> aktivita</span><span class="sxs-lookup"><span data-stu-id="3903a-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="3903a-114">Účely</span><span class="sxs-lookup"><span data-stu-id="3903a-114">Discussion</span></span>
 <span data-ttu-id="3903a-115">Ukázka zahrnuje pracovní postup návrháře a kódovaný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="3903a-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="3903a-116">Pracovní postup návrháře: verze návrháře ukázky ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="3903a-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="3903a-117">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="3903a-117">The following files are included:</span></span>

- <span data-ttu-id="3903a-118">Program.cs: obsahuje funkci `Main`, která spustí ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="3903a-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="3903a-119">ReadString.cs: vlastní aktivita, která čte Některé vstupy z konzoly.</span><span class="sxs-lookup"><span data-stu-id="3903a-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="3903a-120">Sequence1. XAML: pracovní postup vytvořený pomocí návrháře, který používá vybrat.</span><span class="sxs-lookup"><span data-stu-id="3903a-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="3903a-121">Kódovaný pracovní postup: kódovaná verze ukázky ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="3903a-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="3903a-122">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="3903a-122">The following files are included:</span></span>

- <span data-ttu-id="3903a-123">Program.cs: obsahuje funkci `Main`, která spustí ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="3903a-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="3903a-124">ReadString.cs: vlastní aktivita, která čte Některé vstupy z konzoly.</span><span class="sxs-lookup"><span data-stu-id="3903a-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="3903a-125">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="3903a-125">To use this sample</span></span>

1. <span data-ttu-id="3903a-126">Pomocí sady Visual Studio 2010 otevřete soubor řešení vyskladnit. sln.</span><span class="sxs-lookup"><span data-stu-id="3903a-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="3903a-127">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="3903a-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="3903a-128">Pokud chcete řešení spustit, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="3903a-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3903a-129">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="3903a-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3903a-130">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="3903a-130">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="3903a-131">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="3903a-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3903a-132">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3903a-132">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
