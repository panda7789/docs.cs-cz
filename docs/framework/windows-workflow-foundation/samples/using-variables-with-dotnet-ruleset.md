---
title: Pomocí proměnné sada pravidel pro rozhraní .NET Framework 3.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 460f6db9334c2ede7d968e10f9e594c49e806bea
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a>Pomocí proměnné sada pravidel pro rozhraní .NET Framework 3.5
Tento příklad ukazuje, jak vytvořit pracovní postup, který používá <xref:System.Activities.Statements.Interop> aktivity integrovat vlastní aktivity napsané v [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] používající zásady a pravidla. Pracovní postup předá vlastní aktivity dat pomocí vytvoření vazby proměnných pro vlastnosti závislosti vystavené vlastní aktivity.  
  
## <a name="sample-walkthrough"></a>Ukázka návod  
  
#### <a name="to-examine-travelrulelibrary"></a>K prozkoumání TravelRuleLibrary  
  
1.  Pomocí sady Visual Studio, otevřete soubor řešení InteropWith35RuleSet.sln.  
  
2.  Otevřete TravelRuleSet.cs v Návrháři pracovních postupů.  
  
     Vlastní sekvenční aktivita, která obsahuje <xref:System.Workflow.Activities.PolicyActivity> se zobrazí.  
  
3.  Dvojitým kliknutím na aktivitu zásad DiscountPolicy zkontrolujte pravidla.  
  
     Editor pravidla objeví zobrazíte pravidla.  
  
4.  Klikněte pravým tlačítkem `DiscountPolicy` a vyberte **kód zobrazení** možnost prozkoumat kód vedle kódu C# pro aktivitu.  
  
     Sledovat nastavení vlastnosti závislosti `DiscountLevel`. Jde o ekvivalent argumentů [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]. Další informace o argumenty najdete v tématu [proměnné a argumenty](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 Toto je projekt sekvenční pracovní postup, který používá <xref:System.Activities.Statements.Interop> aktivity k integraci s vlastní sady pravidel, které jsou vytvořené v `TravelRuleLibrary` projektu. Proměnné jsou vytvořené na nejvyšší úrovni <xref:System.Activities.Statements.Sequence> aktivity. <xref:System.Activities.Statements.Interop> Aktivita se používá k integraci s `TravelRuleSet` aktivity. Proměnné, které jsou deklarované v <xref:System.Activities.Statements.Sequence> slouží k vytvoření vazby na vlastnosti závislosti.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InteropWith35RuleSet.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`