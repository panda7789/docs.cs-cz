---
title: Použití aktivity Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 03b9ff7f552ad0cdcfbe9c46121a2f46f35de52a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037871"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="ba6ef-102">Použití aktivity Pick</span><span class="sxs-lookup"><span data-stu-id="ba6ef-102">Using the Pick Activity</span></span>
<span data-ttu-id="ba6ef-103">Tento příklad ukazuje, jak použít <xref:System.Activities.Statements.Pick> aktivitu.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="ba6ef-104"><xref:System.Activities.Statements.Pick> Aktivita poskytuje modelování ovládacího prvku založené na událostech.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="ba6ef-105">Chová se podobně jako C# `switch` příkaz, který spouští pouze jednu z větví v `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="ba6ef-106">Na rozdíl od `switch` příkazu <xref:System.Activities.Statements.Pick> , ve kterém je větev spouštěna na základě hodnoty, aktivita provede větev na základě toho, jak se aktivita dokončí.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="ba6ef-107">Tato ukázka vyzve uživatele k zadání názvu v konzole v daném časovém období.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="ba6ef-108"><xref:System.Activities.Statements.Pick> Aktivita v ukázce má dvě větve, které se spustí na základě toho, jestli uživatel zadá jméno do 5 sekund nebo ne.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="ba6ef-109">Pokud uživatel zadá jméno do 5 sekund, spustí se první větev, která obsahuje vlastní `ReadLine` aktivitu. v opačném případě se spustí druhá větev, která <xref:System.Activities.Statements.Delay> obsahuje aktivitu.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="ba6ef-110">Po zadání jména uživatele v konzole nástroje se v konzole vytiskne jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="ba6ef-111">Pokud vstup není zadán do 5 sekund, vypršel časový limit operace.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ba6ef-112">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="ba6ef-112">Demonstrates</span></span>
 <span data-ttu-id="ba6ef-113"><xref:System.Activities.Statements.Pick>akce.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="ba6ef-114">Účely</span><span class="sxs-lookup"><span data-stu-id="ba6ef-114">Discussion</span></span>
 <span data-ttu-id="ba6ef-115">Ukázka zahrnuje pracovní postup návrháře a kódovaný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="ba6ef-116">Pracovní postup návrháře: verze návrháře ukázky ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="ba6ef-117">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="ba6ef-117">The following files are included:</span></span>

- <span data-ttu-id="ba6ef-118">Program.cs: `Main` Obsahuje funkci, která spustí ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="ba6ef-119">ReadString.cs: Vlastní aktivita, která čte Některé vstupy z konzoly.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="ba6ef-120">Sequence1. XAML: Pracovní postup vytvořený pomocí návrháře, který používá výběr.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="ba6ef-121">Kódovaný pracovní postup: kódovaná verze ukázky ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="ba6ef-122">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="ba6ef-122">The following files are included:</span></span>

- <span data-ttu-id="ba6ef-123">Program.cs: `Main` Obsahuje funkci, která spustí ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="ba6ef-124">ReadString.cs: Vlastní aktivita, která čte Některé vstupy z konzoly.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="ba6ef-125">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="ba6ef-125">To use this sample</span></span>

1. <span data-ttu-id="ba6ef-126">Pomocí sady Visual Studio 2010 otevřete soubor řešení vyskladnit. sln.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="ba6ef-127">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="ba6ef-128">Pokud chcete řešení spustit, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba6ef-129">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ba6ef-130">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-130">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="ba6ef-131">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba6ef-132">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ba6ef-132">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
