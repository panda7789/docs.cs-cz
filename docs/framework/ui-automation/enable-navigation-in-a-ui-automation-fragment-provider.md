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
ms.openlocfilehash: 729d8c117599ca6d9aa011de6b3cf0e9a86cbea3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043825"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a>Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje příklad kódu, který ukazuje, jak povolit navigaci v poskytovateli automatizace uživatelského rozhraní pro prvek, který je v rámci fragmentu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> pro položku seznamu v rámci seznamu. Nadřazený prvek je prvek pole se seznamem a prvky na stejné úrovni jsou jiné položky v kolekci seznamu. Metoda vrátí `null` (`Nothing` v Visual Basic) pokyny, které nejsou platné <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> ; v tomto případě a <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, protože element nemá žádné podřízené položky.  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled zprostředkovatelů automatizace uživatelského rozhraní](ui-automation-providers-overview.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
