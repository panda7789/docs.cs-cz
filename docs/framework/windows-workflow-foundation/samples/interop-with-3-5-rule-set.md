---
title: Zprostředkovatel komunikace s objekty sadou pravidel 3.5
ms.date: 03/30/2017
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
ms.openlocfilehash: 9d42198d336e38c4ad9fc6c686a019814bd571bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517904"
---
# <a name="interop-with-35-rule-set"></a>Zprostředkovatel komunikace s objekty sadou pravidel 3.5
Tento příklad znázorňuje použití <xref:System.Activities.Statements.Interop> aktivity k integraci s vlastní aktivity v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] pomocí <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` a pravidla. Předává data do vlastní aktivita pomocí vytvoření vazby [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] proměnné pro vlastnosti závislosti vystavené vlastní aktivity.  
  
## <a name="requirements"></a>Požadavky  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.Activities.Statements.Interop> Aktivita, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` aktivity v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] s vlastností závislostí  
  
## <a name="discussion"></a>Diskusní  
 Ukázka ukazuje jeden scénáře integrace pro integraci s [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] aktivity. Tato ukázka obsahuje [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] vlastní aktivitu, která volá <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` aktivity.  
  
## <a name="travelrulelibrary"></a>TravelRuleLibrary  
 Otevírání TravelRuleSet.cs v Návrháři zobrazuje vlastní sekvenční aktivity, která obsahuje aktivitu zásad takto  
  
 ![Spolupráce aktivity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")  
  
 Dvakrát klikněte **DiscountPolicy** činnost zásad a zkontrolujte pravidla. Editor pravidla, zobrazí se pravidla.  
  
 ![Pravidlo s editorem sad](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")  
  
 Klikněte pravým tlačítkem myši **DiscountPolicy** aktivitu a vyberte **kód zobrazení** možnost prozkoumat vedle položky kódu C# kód, který přejde k této aktivitě. Sledovat nastavení vlastnosti závislosti `DiscountLevel`. Jde o ekvivalent <xref:System.Activities.Argument> v [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
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
 Toto je [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] projekt sekvenčního pracovního postupu, který používá <xref:System.Activities.Statements.Interop> aktivity k integraci s vlastní sady pravidel, kterou vytvořené v TravelRuleLibrary projektu. Proměnné jsou vytvořené na nejvyšší úrovni <xref:System.Activities.Statements.Sequence> následujícím způsobem.  
  
 ![Proměnné](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")  
  
 ![Průzkumník řešení](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")  
  
 Nakonec <xref:System.Activities.Statements.Interop> aktivita se používá k integraci s TravelRuleSet. Proměnné, které byly dříve na deklarované <xref:System.Activities.Statements.Sequence> slouží k vytvoření vazby na vlastnosti závislosti.  
  
 ![Typ aktivity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")  
  
 ![Šipka](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")  
  
 ![Vlastnosti](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
