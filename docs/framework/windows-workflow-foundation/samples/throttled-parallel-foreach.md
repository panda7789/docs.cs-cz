---
title: Aktivita ThrottledParallelForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 340e4ff154b63221ec911c872a1154bdb672cf8c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715911"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="38286-102">Aktivita ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="38286-102">Throttled Parallel ForEach</span></span>

<span data-ttu-id="38286-103">Aktivita `ThrottleParallelForEach` je podobná aktivitě <xref:System.Activities.Statements.ParallelForEach%601> s jednou výjimkou, kterou umožňuje nastavit faktor souběžnosti, aby se omezil počet souběžných větví, které se mají spustit.</span><span class="sxs-lookup"><span data-stu-id="38286-103">The `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="38286-104">Aktivita `ThrottleParallelForEach` je odvozena z <xref:System.Activities.NativeActivity>, protože potřebuje naplánovat jiné aktivity (podřízené aktivity) a je přístupná pouze prostřednictvím třídy <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="38286-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>

## <a name="projects"></a><span data-ttu-id="38286-105">Projekty</span><span class="sxs-lookup"><span data-stu-id="38286-105">Projects</span></span>

|<span data-ttu-id="38286-106">**Názevprojektu**</span><span class="sxs-lookup"><span data-stu-id="38286-106">**ProjectName**</span></span>|<span data-ttu-id="38286-107">**Popis**</span><span class="sxs-lookup"><span data-stu-id="38286-107">**Description**</span></span>|<span data-ttu-id="38286-108">**Hlavní soubory**</span><span class="sxs-lookup"><span data-stu-id="38286-108">**Main Files**</span></span>|
|-|-|-|
|<span data-ttu-id="38286-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="38286-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="38286-110">Obsahuje aktivitu `ThrottledParallelForEach` a její Návrhář.</span><span class="sxs-lookup"><span data-stu-id="38286-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="38286-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="38286-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="38286-112">Definice aktivity `ThrottledParallelForEach`.</span><span class="sxs-lookup"><span data-stu-id="38286-112">The `ThrottledParallelForEach` activity definition.</span></span>|
|<span data-ttu-id="38286-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="38286-113">CodeTestClient</span></span>|<span data-ttu-id="38286-114">Ukázková klientská aplikace, která konfiguruje a spustí pracovní postup s `ThrottledParallelForEach` pomocí imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="38286-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="38286-115">Program.cs</span><span class="sxs-lookup"><span data-stu-id="38286-115">Program.cs</span></span><br /><br /> <span data-ttu-id="38286-116">Definuje a spustí instanci ukázkového pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="38286-116">Defines and runs an instance of the sample workflow.</span></span>|

## <a name="to-use-this-sample"></a><span data-ttu-id="38286-117">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="38286-117">To use this sample</span></span>

1. <span data-ttu-id="38286-118">Pomocí sady Visual Studio 2010 otevřete soubor ThrottledParallelForEach. sln.</span><span class="sxs-lookup"><span data-stu-id="38286-118">Using Visual Studio 2010, open the ThrottledParallelForEach.sln file.</span></span>

2. <span data-ttu-id="38286-119">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="38286-119">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="38286-120">Pokud chcete řešení spustit, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="38286-120">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38286-121">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="38286-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="38286-122">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="38286-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="38286-123">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="38286-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38286-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="38286-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
