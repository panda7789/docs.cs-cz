---
title: Použití proměnných se sadou pravidel rozhraní .NET Framework 3.5
ms.date: 03/30/2017
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
ms.openlocfilehash: 64d47564076e19e152e30b6ab0cb3900ce53cfa1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512851"
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a>Použití proměnných se sadou pravidel rozhraní .NET Framework 3.5
Tato ukázka předvádí, jak vytvořit pracovní postup, který se používá <xref:System.Activities.Statements.Interop> aktivity integrovat vlastní aktivity v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] , která používá zásad a pravidel. Pracovní postup se předá data vlastní aktivity pomocí vazby proměnné na závislost vlastností vystavovaných třídami vlastní aktivity.  
  
## <a name="sample-walkthrough"></a>Ukázkový názorný postup  
  
#### <a name="to-examine-travelrulelibrary"></a>Prozkoumat TravelRuleLibrary  
  
1.  Pomocí sady Visual Studio, otevřete soubor řešení InteropWith35RuleSet.sln.  
  
2.  Otevřete TravelRuleSet.cs v Návrháři pracovních postupů.  
  
     Vlastní sekvenční aktivity, která obsahuje <xref:System.Workflow.Activities.PolicyActivity> se zobrazí.  
  
3.  Dvojitým kliknutím na aktivitu zásad DiscountPolicy zkontrolujte pravidla.  
  
     Editoru pravidel, který otevře zobrazíte pravidla.  
  
4.  Klikněte pravým tlačítkem myši `DiscountPolicy` a vyberte **zobrazit kód** možnosti pro zkoumání kódu vedle kódu jazyka C# pro aktivitu.  
  
     Podívejte se na nastavení vlastnosti závislostí pro `DiscountLevel`. Toto je shodné s argumenty v [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]. Další informace o argumentech najdete v tématu [proměnné a argumenty](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 Toto je projekt sekvenčního pracovního postupu, který používá <xref:System.Activities.Statements.Interop> aktivity integrovat vlastní sadě pravidel, které jsou vytvořené v `TravelRuleLibrary` projektu. Proměnné se vytvářejí na nejvyšší úrovni <xref:System.Activities.Statements.Sequence> aktivity. <xref:System.Activities.Statements.Interop> Aktivity se používají k integraci s `TravelRuleSet` aktivity. Proměnné, které jsou deklarovány na <xref:System.Activities.Statements.Sequence> se používají k vytvoření vazby vlastnosti závislosti.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InteropWith35RuleSet.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`