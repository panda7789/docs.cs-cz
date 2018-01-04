---
title: "Zprostředkovatel komunikace s objekty sadou pravidel 3.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 854aeac936d3f911f2613c6e315ab81347f64a25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="interop-with-35-rule-set"></a><span data-ttu-id="bab54-102">Zprostředkovatel komunikace s objekty sadou pravidel 3.5</span><span class="sxs-lookup"><span data-stu-id="bab54-102">Interop with 3.5 Rule Set</span></span>
<span data-ttu-id="bab54-103">Tento příklad znázorňuje použití <xref:System.Activities.Statements.Interop> aktivity k integraci s vlastní aktivity v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] pomocí <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` a pravidla.</span><span class="sxs-lookup"><span data-stu-id="bab54-103">This sample demonstrates the use of the <xref:System.Activities.Statements.Interop> activity to integrate with a custom activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] using <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` and rules.</span></span> <span data-ttu-id="bab54-104">Předává data do vlastní aktivita pomocí vytvoření vazby [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] proměnné pro vlastnosti závislosti vystavené vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="bab54-104">It passes data to the custom activity by binding [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bab54-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bab54-105">Requirements</span></span>  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a><span data-ttu-id="bab54-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="bab54-106">Demonstrates</span></span>  
 <span data-ttu-id="bab54-107"><xref:System.Activities.Statements.Interop>Aktivita, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` aktivity v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] s vlastností závislostí</span><span class="sxs-lookup"><span data-stu-id="bab54-107"><xref:System.Activities.Statements.Interop> activity, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] with dependency properties</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="bab54-108">Diskusní</span><span class="sxs-lookup"><span data-stu-id="bab54-108">Discussion</span></span>  
 <span data-ttu-id="bab54-109">Ukázka ukazuje jeden scénáře integrace pro integraci s [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] aktivity.</span><span class="sxs-lookup"><span data-stu-id="bab54-109">The sample demonstrates one of the integration scenarios for integrating with a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] activity.</span></span> <span data-ttu-id="bab54-110">Tato ukázka obsahuje [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] vlastní aktivitu, která volá <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` aktivity.</span><span class="sxs-lookup"><span data-stu-id="bab54-110">This sample includes a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] custom activity that invokes a <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity.</span></span>  
  
## <a name="travelrulelibrary"></a><span data-ttu-id="bab54-111">TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="bab54-111">TravelRuleLibrary</span></span>  
 <span data-ttu-id="bab54-112">Otevírání TravelRuleSet.cs v Návrháři zobrazuje vlastní sekvenční aktivity, která obsahuje aktivitu zásad takto</span><span class="sxs-lookup"><span data-stu-id="bab54-112">Opening TravelRuleSet.cs in the designer shows a custom sequential activity that contains a Policy activity as follows</span></span>  
  
 <span data-ttu-id="bab54-113">![Spolupráce aktivity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span><span class="sxs-lookup"><span data-stu-id="bab54-113">![Interop Activity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span></span>  
  
 <span data-ttu-id="bab54-114">Dvakrát klikněte **DiscountPolicy** činnost zásad a zkontrolujte pravidla.</span><span class="sxs-lookup"><span data-stu-id="bab54-114">Double-click the **DiscountPolicy** policy activity to examine the rules.</span></span> <span data-ttu-id="bab54-115">Editor pravidla, zobrazí se pravidla.</span><span class="sxs-lookup"><span data-stu-id="bab54-115">The Rules editor appears to show the rules.</span></span>  
  
 <span data-ttu-id="bab54-116">![Pravidlo s editorem sad](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span><span class="sxs-lookup"><span data-stu-id="bab54-116">![Rule Set Editor](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span></span>  
  
 <span data-ttu-id="bab54-117">Klikněte pravým tlačítkem myši **DiscountPolicy** aktivitu a vyberte **kód zobrazení** možnost prozkoumat vedle položky kódu C# kód, který přejde k této aktivitě.</span><span class="sxs-lookup"><span data-stu-id="bab54-117">Right-click the **DiscountPolicy** activity and select the **View Code** option to examine the code-beside C# code that goes with this activity.</span></span> <span data-ttu-id="bab54-118">Sledovat nastavení vlastnosti závislosti `DiscountLevel`.</span><span class="sxs-lookup"><span data-stu-id="bab54-118">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="bab54-119">Jde o ekvivalent <xref:System.Activities.Argument> v [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bab54-119">This is equivalent to an <xref:System.Activities.Argument> in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span>  
  
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
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="bab54-120">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="bab54-120">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="bab54-121">Toto je [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] projekt sekvenčního pracovního postupu, který používá <xref:System.Activities.Statements.Interop> aktivity k integraci s vlastní sady pravidel, kterou vytvořené v TravelRuleLibrary projektu.</span><span class="sxs-lookup"><span data-stu-id="bab54-121">This is a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom rule set created in the TravelRuleLibrary project.</span></span> <span data-ttu-id="bab54-122">Proměnné jsou vytvořené na nejvyšší úrovni <xref:System.Activities.Statements.Sequence> následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="bab54-122">Variables are created on the top-level <xref:System.Activities.Statements.Sequence> as follows.</span></span>  
  
 <span data-ttu-id="bab54-123">![Proměnné](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span><span class="sxs-lookup"><span data-stu-id="bab54-123">![Variables](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span></span>  
  
 <span data-ttu-id="bab54-124">![Průzkumník řešení](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span><span class="sxs-lookup"><span data-stu-id="bab54-124">![Solution Explorer](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span></span>  
  
 <span data-ttu-id="bab54-125">Nakonec <xref:System.Activities.Statements.Interop> aktivita se používá k integraci s TravelRuleSet.</span><span class="sxs-lookup"><span data-stu-id="bab54-125">Lastly, the <xref:System.Activities.Statements.Interop> activity is used to integrate with the TravelRuleSet.</span></span> <span data-ttu-id="bab54-126">Proměnné, které byly dříve na deklarované <xref:System.Activities.Statements.Sequence> slouží k vytvoření vazby na vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="bab54-126">The variables that were declared earlier on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
 <span data-ttu-id="bab54-127">![Typ aktivity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span><span class="sxs-lookup"><span data-stu-id="bab54-127">![Activity Type](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span></span>  
  
 <span data-ttu-id="bab54-128">![Šipka](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span><span class="sxs-lookup"><span data-stu-id="bab54-128">![Arrow](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span></span>  
  
 <span data-ttu-id="bab54-129">![Vlastnosti](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span><span class="sxs-lookup"><span data-stu-id="bab54-129">![Properties](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bab54-130">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="bab54-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bab54-131">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bab54-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bab54-132">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bab54-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bab54-133">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bab54-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
