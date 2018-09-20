---
title: Zprostředkovatel komunikace s objekty sadou pravidel 3.5
ms.date: 03/30/2017
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
ms.openlocfilehash: 5ea5454ef80bfd83611ed20392782d99cd8c0c25
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324289"
---
# <a name="interop-with-35-rule-set"></a><span data-ttu-id="60095-102">Zprostředkovatel komunikace s objekty sadou pravidel 3.5</span><span class="sxs-lookup"><span data-stu-id="60095-102">Interop with 3.5 Rule Set</span></span>
<span data-ttu-id="60095-103">Tato ukázka demonstruje použití <xref:System.Activities.Statements.Interop> aktivity integrovat vlastní aktivity v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] pomocí <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` a pravidla.</span><span class="sxs-lookup"><span data-stu-id="60095-103">This sample demonstrates the use of the <xref:System.Activities.Statements.Interop> activity to integrate with a custom activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] using <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` and rules.</span></span> <span data-ttu-id="60095-104">Předá data pro vlastní aktivity vazbou [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] proměnné závislosti vlastností vystavovaných třídami vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="60095-104">It passes data to the custom activity by binding [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60095-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60095-105">Requirements</span></span>  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a><span data-ttu-id="60095-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="60095-106">Demonstrates</span></span>  
 <span data-ttu-id="60095-107"><xref:System.Activities.Statements.Interop> Aktivita, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` aktivity v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] prostřednictvím vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="60095-107"><xref:System.Activities.Statements.Interop> activity, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] with dependency properties</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="60095-108">Diskuse</span><span class="sxs-lookup"><span data-stu-id="60095-108">Discussion</span></span>  
 <span data-ttu-id="60095-109">Ukázce jednom ze scénářů integrace pro integraci se službou [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] aktivity.</span><span class="sxs-lookup"><span data-stu-id="60095-109">The sample demonstrates one of the integration scenarios for integrating with a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] activity.</span></span> <span data-ttu-id="60095-110">Tato ukázka obsahuje [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] vlastní aktivitu, která se vyvolá <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` aktivity.</span><span class="sxs-lookup"><span data-stu-id="60095-110">This sample includes a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] custom activity that invokes a <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity.</span></span>  
  
## <a name="travelrulelibrary"></a><span data-ttu-id="60095-111">TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="60095-111">TravelRuleLibrary</span></span>  
 <span data-ttu-id="60095-112">Otevírání TravelRuleSet.cs v Návrháři ukazuje vlastní sekvenční aktivity, který obsahuje aktivitu zásady takto</span><span class="sxs-lookup"><span data-stu-id="60095-112">Opening TravelRuleSet.cs in the designer shows a custom sequential activity that contains a Policy activity as follows</span></span>  
  
 <span data-ttu-id="60095-113">![Aktivity interoperability](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span><span class="sxs-lookup"><span data-stu-id="60095-113">![Interop Activity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span></span>  
  
 <span data-ttu-id="60095-114">Dvakrát klikněte **DiscountPolicy** prozkoumat pravidla zásad aktivitou.</span><span class="sxs-lookup"><span data-stu-id="60095-114">Double-click the **DiscountPolicy** policy activity to examine the rules.</span></span> <span data-ttu-id="60095-115">Chcete-li zobrazit pravidla, zobrazí se editor pravidla.</span><span class="sxs-lookup"><span data-stu-id="60095-115">The Rules editor appears to show the rules.</span></span>  
  
 <span data-ttu-id="60095-116">![S editorem sad pravidel](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span><span class="sxs-lookup"><span data-stu-id="60095-116">![Rule Set Editor](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span></span>  
  
 <span data-ttu-id="60095-117">Klikněte pravým tlačítkem myši **DiscountPolicy** aktivitu a vyberte **zobrazit kód** možnost prozkoumat kód vedle kódu C#, která doprovází této aktivity.</span><span class="sxs-lookup"><span data-stu-id="60095-117">Right-click the **DiscountPolicy** activity and select the **View Code** option to examine the code-beside C# code that goes with this activity.</span></span> <span data-ttu-id="60095-118">Podívejte se na nastavení vlastnosti závislostí pro `DiscountLevel`.</span><span class="sxs-lookup"><span data-stu-id="60095-118">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="60095-119">To je ekvivalentní <xref:System.Activities.Argument> v [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60095-119">This is equivalent to an <xref:System.Activities.Argument> in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span>  
  
```  
public static DependencyProperty DiscountLevelProperty = DependencyProperty.Register("DiscountLevel", typeof(int), typeof(TravelRuleSet));  
  
[DescriptionAttribute("DiscountLevel")]  
[CategoryAttribute("DiscountLevel Category")]  
[BrowsableAttribute(true)]  
[DesignerSerializationVisibilityAttribute(DesignerSerializationVisibility.Visible)]  
public int DiscountLevel  
{  
   get  
   {  
return ((int)base.GetValue(TravelRuleSet.DiscountLevelProperty)));  
   }  
   set  
   {  
base.SetValue(TravelRuleSet.DiscountLevelProperty, value);  
   }  
}  
```  
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="60095-120">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="60095-120">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="60095-121">Jde [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] projekt sekvenčního pracovního postupu, který používá <xref:System.Activities.Statements.Interop> aktivity integrovat vlastní pravidlo sadu vytvořenou v projektu TravelRuleLibrary.</span><span class="sxs-lookup"><span data-stu-id="60095-121">This is a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom rule set created in the TravelRuleLibrary project.</span></span> <span data-ttu-id="60095-122">Proměnné se vytvářejí na nejvyšší úrovni <xref:System.Activities.Statements.Sequence> následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="60095-122">Variables are created on the top-level <xref:System.Activities.Statements.Sequence> as follows.</span></span>  
  
 <span data-ttu-id="60095-123">![Proměnné](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span><span class="sxs-lookup"><span data-stu-id="60095-123">![Variables](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span></span>  
  
 <span data-ttu-id="60095-124">![Průzkumník řešení](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span><span class="sxs-lookup"><span data-stu-id="60095-124">![Solution Explorer](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span></span>  
  
 <span data-ttu-id="60095-125">A konečně <xref:System.Activities.Statements.Interop> aktivity se používají k integraci s TravelRuleSet.</span><span class="sxs-lookup"><span data-stu-id="60095-125">Lastly, the <xref:System.Activities.Statements.Interop> activity is used to integrate with the TravelRuleSet.</span></span> <span data-ttu-id="60095-126">Proměnné, které byly předtím deklarován <xref:System.Activities.Statements.Sequence> se používají k vytvoření vazby vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="60095-126">The variables that were declared earlier on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
 <span data-ttu-id="60095-127">![Typ aktivity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span><span class="sxs-lookup"><span data-stu-id="60095-127">![Activity Type](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span></span>  
  
 <span data-ttu-id="60095-128">![Šipka](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span><span class="sxs-lookup"><span data-stu-id="60095-128">![Arrow](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span></span>  
  
 <span data-ttu-id="60095-129">![Vlastnosti](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span><span class="sxs-lookup"><span data-stu-id="60095-129">![Properties](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="60095-130">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="60095-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="60095-131">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="60095-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="60095-132">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="60095-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="60095-133">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="60095-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
