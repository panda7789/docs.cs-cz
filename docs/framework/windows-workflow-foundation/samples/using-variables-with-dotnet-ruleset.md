---
title: Pomocí proměnné sada pravidel pro rozhraní .NET Framework 3.5
ms.date: 03/30/2017
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
ms.openlocfilehash: 9fa6eaf58aaddc4673f08ec9a9001647a494877d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516853"
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a><span data-ttu-id="94a15-102">Pomocí proměnné sada pravidel pro rozhraní .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="94a15-102">Using Variables with a .NET Framework 3.5 Ruleset</span></span>
<span data-ttu-id="94a15-103">Tento příklad ukazuje, jak vytvořit pracovní postup, který používá <xref:System.Activities.Statements.Interop> aktivity integrovat vlastní aktivity napsané v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] používající zásady a pravidla.</span><span class="sxs-lookup"><span data-stu-id="94a15-103">This sample demonstrates how to create a workflow that uses the <xref:System.Activities.Statements.Interop> activity to integrate a custom activity written in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] that uses policy and rules.</span></span> <span data-ttu-id="94a15-104">Pracovní postup předá vlastní aktivity dat pomocí vytvoření vazby proměnných pro vlastnosti závislosti vystavené vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="94a15-104">The workflow passes data to the custom activity by binding variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="sample-walkthrough"></a><span data-ttu-id="94a15-105">Ukázka návod</span><span class="sxs-lookup"><span data-stu-id="94a15-105">Sample walkthrough</span></span>  
  
#### <a name="to-examine-travelrulelibrary"></a><span data-ttu-id="94a15-106">K prozkoumání TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="94a15-106">To examine TravelRuleLibrary</span></span>  
  
1.  <span data-ttu-id="94a15-107">Pomocí sady Visual Studio, otevřete soubor řešení InteropWith35RuleSet.sln.</span><span class="sxs-lookup"><span data-stu-id="94a15-107">Using Visual Studio, open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="94a15-108">Otevřete TravelRuleSet.cs v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="94a15-108">Open the TravelRuleSet.cs in the workflow designer.</span></span>  
  
     <span data-ttu-id="94a15-109">Vlastní sekvenční aktivita, která obsahuje <xref:System.Workflow.Activities.PolicyActivity> se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="94a15-109">A custom sequential activity that contains a <xref:System.Workflow.Activities.PolicyActivity> is displayed.</span></span>  
  
3.  <span data-ttu-id="94a15-110">Dvojitým kliknutím na aktivitu zásad DiscountPolicy zkontrolujte pravidla.</span><span class="sxs-lookup"><span data-stu-id="94a15-110">Double-click the DiscountPolicy policy activity to examine the rules.</span></span>  
  
     <span data-ttu-id="94a15-111">Editor pravidla objeví zobrazíte pravidla.</span><span class="sxs-lookup"><span data-stu-id="94a15-111">The Rules editor pops up to show the rules.</span></span>  
  
4.  <span data-ttu-id="94a15-112">Klikněte pravým tlačítkem `DiscountPolicy` a vyberte **kód zobrazení** možnost prozkoumat kód vedle kódu C# pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="94a15-112">Right click the `DiscountPolicy` and select the **View Code** option to examine the code beside C# code for the activity.</span></span>  
  
     <span data-ttu-id="94a15-113">Sledovat nastavení vlastnosti závislosti `DiscountLevel`.</span><span class="sxs-lookup"><span data-stu-id="94a15-113">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="94a15-114">Jde o ekvivalent argumentů [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="94a15-114">This is equivalent to arguments in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="94a15-115">Další informace o argumenty najdete v tématu [proměnné a argumenty](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="94a15-115">For more information about arguments, see [Variables and Arguments](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span></span>  
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="94a15-116">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="94a15-116">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="94a15-117">Toto je projekt sekvenční pracovní postup, který používá <xref:System.Activities.Statements.Interop> aktivity k integraci s vlastní sady pravidel, které jsou vytvořené v `TravelRuleLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="94a15-117">This is a sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom Rule set created in the `TravelRuleLibrary` project.</span></span> <span data-ttu-id="94a15-118">Proměnné jsou vytvořené na nejvyšší úrovni <xref:System.Activities.Statements.Sequence> aktivity.</span><span class="sxs-lookup"><span data-stu-id="94a15-118">Variables are created on the top level <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="94a15-119"><xref:System.Activities.Statements.Interop> Aktivita se používá k integraci s `TravelRuleSet` aktivity.</span><span class="sxs-lookup"><span data-stu-id="94a15-119">The <xref:System.Activities.Statements.Interop> activity is used to integrate with the `TravelRuleSet` activity.</span></span> <span data-ttu-id="94a15-120">Proměnné, které jsou deklarované v <xref:System.Activities.Statements.Sequence> slouží k vytvoření vazby na vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="94a15-120">The variables that are declared on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="94a15-121">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="94a15-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="94a15-122">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InteropWith35RuleSet.sln.</span><span class="sxs-lookup"><span data-stu-id="94a15-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="94a15-123">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="94a15-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="94a15-124">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="94a15-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="94a15-125">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="94a15-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94a15-126">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="94a15-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="94a15-127">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="94a15-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94a15-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="94a15-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`