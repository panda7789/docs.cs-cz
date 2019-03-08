---
title: Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: f5a6de0df834a2dc0c80801c141e3d0793a859ed
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680097"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a>Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje ukázkový kód, který ukazuje, jak k povolení navigace u zprostředkovatele automatizace uživatelského rozhraní pro element, který je v rámci fragment.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> pro položku seznamu v rámci seznamu. Nadřazeným elementem je element seznamu pole a dalších položek v kolekci seznamu jsou prvky na stejné úrovni. Metoda vrátí `null` (`Nothing` v jazyce Visual Basic) pro pokyny, které nejsou platné; v takovém případě <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> a <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, protože nemá žádné podřízené položky elementu.  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled zprostředkovatelů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
