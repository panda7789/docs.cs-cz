---
title: Použití aktivity Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 7ca4527cc1d5bc90ed1ec4df3eef6cf2d8b93b4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142612"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="34088-102">Použití aktivity Pick</span><span class="sxs-lookup"><span data-stu-id="34088-102">Using the Pick Activity</span></span>
<span data-ttu-id="34088-103">Tato ukázka ukazuje, <xref:System.Activities.Statements.Pick> jak použít aktivitu.</span><span class="sxs-lookup"><span data-stu-id="34088-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="34088-104">Aktivita <xref:System.Activities.Statements.Pick> poskytuje modelování řízení založené na událostech.</span><span class="sxs-lookup"><span data-stu-id="34088-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="34088-105">Chová se podobně jako příkaz `switch` C#, který provede pouze jednu `switch` z větví v příkazu.</span><span class="sxs-lookup"><span data-stu-id="34088-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="34088-106">Na `switch` rozdíl od příkazu, ve kterém je větev spuštěna na základě hodnoty, aktivita <xref:System.Activities.Statements.Pick> provede větev na základě toho, jak se aktivita dokončí.</span><span class="sxs-lookup"><span data-stu-id="34088-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="34088-107">Tato ukázka vyzve uživatele k zadání jejich jména na konzoli v daném časovém období.</span><span class="sxs-lookup"><span data-stu-id="34088-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="34088-108">Aktivita <xref:System.Activities.Statements.Pick> v ukázce má dvě větve, které jsou provedeny na základě toho, zda uživatel zadá v jejich názvu do 5 sekund nebo ne.</span><span class="sxs-lookup"><span data-stu-id="34088-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="34088-109">Pokud uživatel zadá v jejich názvu do 5 sekund, první `ReadLine` větev je spuštěna, která obsahuje vlastní aktivitu; jinak je spuštěna druhá větev, která obsahuje aktivitu. <xref:System.Activities.Statements.Delay></span><span class="sxs-lookup"><span data-stu-id="34088-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="34088-110">Jakmile je jméno uživatele zadáno do konzole, je na konzoli vytištěno jeho jméno.</span><span class="sxs-lookup"><span data-stu-id="34088-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="34088-111">Pokud vstup není zadán do 5 sekund, operace je časový rozsah.</span><span class="sxs-lookup"><span data-stu-id="34088-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="34088-112">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="34088-112">Demonstrates</span></span>
 <span data-ttu-id="34088-113"><xref:System.Activities.Statements.Pick>Činnosti.</span><span class="sxs-lookup"><span data-stu-id="34088-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="34088-114">Diskuse</span><span class="sxs-lookup"><span data-stu-id="34088-114">Discussion</span></span>
 <span data-ttu-id="34088-115">Ukázka obsahuje pracovní postup návrháře a kódovaný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="34088-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="34088-116">Pracovní postup návrháře Verze ukázky návrháře ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="34088-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="34088-117">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="34088-117">The following files are included:</span></span>

- <span data-ttu-id="34088-118">Program.cs : `Main` Zahrnuje funkci, která spustí ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="34088-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="34088-119">ReadString.cs: Vlastní aktivita, která čte některé vstupy z konzoly.</span><span class="sxs-lookup"><span data-stu-id="34088-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="34088-120">Sequence1.xaml: Pracovní postup vytvořený pomocí návrháře, který používá vyskladnění.</span><span class="sxs-lookup"><span data-stu-id="34088-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="34088-121">Kódovaný pracovní postup Kódovaná verze ukázky ukazuje, jak vytvořit pracovní postup v návrháři.</span><span class="sxs-lookup"><span data-stu-id="34088-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="34088-122">Jsou zahrnuty následující soubory:</span><span class="sxs-lookup"><span data-stu-id="34088-122">The following files are included:</span></span>

- <span data-ttu-id="34088-123">Program.cs : `Main` Zahrnuje funkci, která spustí ukázkový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="34088-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="34088-124">ReadString.cs: Vlastní aktivita, která čte některé vstupy z konzoly.</span><span class="sxs-lookup"><span data-stu-id="34088-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="34088-125">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="34088-125">To use this sample</span></span>

1. <span data-ttu-id="34088-126">Pomocí sady Visual Studio 2010 otevřete soubor řešení Pick.sln.</span><span class="sxs-lookup"><span data-stu-id="34088-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="34088-127">Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="34088-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="34088-128">Chcete-li řešení spustit, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="34088-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34088-129">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="34088-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="34088-130">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="34088-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="34088-131">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="34088-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34088-132">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="34088-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
