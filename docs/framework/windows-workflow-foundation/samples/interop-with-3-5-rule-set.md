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
ms.openlocfilehash: 5f5d8dd02d325d196cdceccea37624c9b2c1a01d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="interop-with-35-rule-set"></a>Zprostředkovatel komunikace s objekty sadou pravidel 3.5
Tento příklad znázorňuje použití <xref:System.Activities.Statements.Interop> aktivity k integraci s vlastní aktivity v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] pomocí <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` a pravidla. Předává data do vlastní aktivita pomocí vytvoření vazby [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] proměnné pro vlastnosti závislosti vystavené vlastní aktivity.  
  
## <a name="requirements"></a>Požadavky  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.Activities.Statements.Interop>Aktivita, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` aktivity v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] s vlastností závislostí  
  
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
