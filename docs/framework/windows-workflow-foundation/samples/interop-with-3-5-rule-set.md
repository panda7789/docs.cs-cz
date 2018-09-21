---
title: Zprostředkovatel komunikace s objekty sadou pravidel 3.5
ms.date: 03/30/2017
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
ms.openlocfilehash: 5ea5454ef80bfd83611ed20392782d99cd8c0c25
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492701"
---
# <a name="interop-with-35-rule-set"></a>Zprostředkovatel komunikace s objekty sadou pravidel 3.5
Tato ukázka demonstruje použití <xref:System.Activities.Statements.Interop> aktivity integrovat vlastní aktivity v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] pomocí <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` a pravidla. Předá data pro vlastní aktivity vazbou [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] proměnné závislosti vlastností vystavovaných třídami vlastní aktivity.  
  
## <a name="requirements"></a>Požadavky  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.Activities.Statements.Interop> Aktivita, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` aktivity v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] prostřednictvím vlastností závislosti  
  
## <a name="discussion"></a>Diskuse  
 Ukázce jednom ze scénářů integrace pro integraci se službou [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] aktivity. Tato ukázka obsahuje [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] vlastní aktivitu, která se vyvolá <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` aktivity.  
  
## <a name="travelrulelibrary"></a>TravelRuleLibrary  
 Otevírání TravelRuleSet.cs v Návrháři ukazuje vlastní sekvenční aktivity, který obsahuje aktivitu zásady takto  
  
 ![Aktivity interoperability](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")  
  
 Dvakrát klikněte **DiscountPolicy** prozkoumat pravidla zásad aktivitou. Chcete-li zobrazit pravidla, zobrazí se editor pravidla.  
  
 ![S editorem sad pravidel](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")  
  
 Klikněte pravým tlačítkem myši **DiscountPolicy** aktivitu a vyberte **zobrazit kód** možnost prozkoumat kód vedle kódu C#, která doprovází této aktivity. Podívejte se na nastavení vlastnosti závislostí pro `DiscountLevel`. To je ekvivalentní <xref:System.Activities.Argument> v [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
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
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 Jde [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] projekt sekvenčního pracovního postupu, který používá <xref:System.Activities.Statements.Interop> aktivity integrovat vlastní pravidlo sadu vytvořenou v projektu TravelRuleLibrary. Proměnné se vytvářejí na nejvyšší úrovni <xref:System.Activities.Statements.Sequence> následujícím způsobem.  
  
 ![Proměnné](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")  
  
 ![Průzkumník řešení](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")  
  
 A konečně <xref:System.Activities.Statements.Interop> aktivity se používají k integraci s TravelRuleSet. Proměnné, které byly předtím deklarován <xref:System.Activities.Statements.Sequence> se používají k vytvoření vazby vlastnosti závislosti.  
  
 ![Typ aktivity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")  
  
 ![Šipka](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")  
  
 ![Vlastnosti](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
