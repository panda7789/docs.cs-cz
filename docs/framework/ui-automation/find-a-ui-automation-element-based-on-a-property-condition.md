---
title: "Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cafd84ce3acea80905d686f33f23338e3581a9c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje ukázkový kód, který ukazuje, jak najít prvek v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu podle určitou vlastnost nebo vlastnosti.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu sadu podmínek vlastností jsou určené, identifikovat určité elementu (nebo elementy) zájmu v <xref:System.Windows.Automation.AutomationElement> stromu. Vyhledejte všechny odpovídající elementy se pak provádí pomocí <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metoda, která zahrnuje řadu <xref:System.Windows.Automation.AndCondition> logických operací omezit počet elementů odpovídající.  
  
> [!NOTE]
>  Při hledání z <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, pokuste se získat jen přímé podřízené objekty. Vyhledejte následníky může iterovat stovky nebo dokonce tisíce elementy, což může způsobit k přetečení zásobníku. Pokud se pokoušíte získat konkrétní element na nižší úrovni, měli byste začít vyhledávání z okna aplikace nebo z kontejneru na nižší úrovni.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Viz také  
 [Vlastnost InvokePattern a ukázkové položky nabídky ExpandCollapsePattern](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [Získání elementů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [Používání vlastnosti AutomationID](../../../docs/framework/ui-automation/use-the-automationid-property.md)
