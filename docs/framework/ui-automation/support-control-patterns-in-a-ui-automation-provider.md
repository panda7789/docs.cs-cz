---
title: Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 4daa7f0ec869771e8e7ceb11f6871e4b5791badd
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48029681"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma ukazuje, jak implementovat jednu nebo více vzorů ovládacích prvků ve zprostředkovateli automatizace uživatelského rozhraní tak, aby klientské aplikace můžou manipulace s ovládacími prvky a získání dat z nich.  
  
### <a name="support-control-patterns"></a>Podpora vzorů ovládacích prvků  
  
1.  Implementovat vhodné rozhraní pro vzorů ovládacích prvků, které by měly podporovat element, jako například <xref:System.Windows.Automation.Provider.IInvokeProvider> pro <xref:System.Windows.Automation.InvokePattern>.  
  
2.  Vrátí objekt obsahující vaši implementaci rozhraní každý ovládací prvek ve vaší implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci <xref:System.Windows.Automation.Provider.ISelectionProvider> pro pole s jedním výběrem vlastního seznamu. Vrátí tři vlastnosti a získá aktuálně vybrané položky.  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> , která vrátí implementaci třídy <xref:System.Windows.Automation.Provider.ISelectionProvider>. Většina ovládací prvky seznamu by podporovat další zpracování, stejně, ale v tomto příkladu odkaz s hodnotou null (`Nothing` v aplikaci Microsoft Visual Basic .NET) se vrací pro všechny ostatní identifikátory vzor.  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled zprostředkovatelů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
