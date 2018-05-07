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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1f4dea321ba4a4242af0766a367731222368372e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a>Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje ukázkový kód, který ukazuje, jak k povolení navigace u zprostředkovatele automatizace uživatelského rozhraní pro element, který je v rámci fragment.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> položky seznamu v seznamu. Nadřazeným elementem je element seznamu pole a prvků jsou ostatní položky v seznamu kolekci. Vrátí metoda `null` (`Nothing` v jazyce Visual Basic) pro pokynů, které nejsou platné; v tomto případě <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> a <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, protože element nemá žádné podřízené objekty.  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled zprostředkovatelů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
