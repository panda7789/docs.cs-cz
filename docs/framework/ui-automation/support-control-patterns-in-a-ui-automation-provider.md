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
ms.openlocfilehash: 1200ebd42884220d2611729b87f4bf51e7a903a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446829"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní

> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).

Toto téma ukazuje, jak implementovat jeden nebo více vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní, aby klientské aplikace mohly manipulovat s ovládacími prvky a získávat z nich data.

## <a name="support-control-patterns"></a>Podpora vzorů ovládacích prvků

1. Implementujte vhodná rozhraní pro vzory ovládacích prvků, které by měl element podporovat, například <xref:System.Windows.Automation.Provider.IInvokeProvider> pro <xref:System.Windows.Automation.InvokePattern>.

2. Vrátí objekt, který obsahuje implementaci každého rozhraní ovládacího prvku v implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>

## <a name="example"></a>Příklad

Následující příklad ukazuje implementaci <xref:System.Windows.Automation.Provider.ISelectionProvider> pro vlastní seznam s jedním výběrem. Vrátí tři vlastnosti a získá aktuálně vybranou položku.

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a>Příklad

Následující příklad ukazuje implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>, která vrací třídu implementující <xref:System.Windows.Automation.Provider.ISelectionProvider>. Většina ovládacích prvků pole se seznamem podporuje i další vzory, ale v tomto příkladu se vrátí odkaz s hodnotou null (`Nothing` v Microsoft Visual Basic .NET) pro všechny ostatní identifikátory vzoru.

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a>Viz také:

- [Přehled zprostředkovatelů automatizace uživatelského rozhraní](ui-automation-providers-overview.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
