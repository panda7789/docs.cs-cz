---
title: Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 71385690c01d261b4ff1b495674bab377232e81d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447257"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje příklad kódu, který ukazuje, jak použít [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pro vložení textu do jednořádkového textového pole. K dispozici je alternativní metoda pro víceřádkové a formátované textové ovládací prvky, kde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nelze použít. Pro účely porovnání příklad také ukazuje, jak použít metody Win32 k dosažení stejných výsledků.  
  
## <a name="example"></a>Příklad  
 Následující příklad postupuje pomocí sekvence textových ovládacích prvků v cílové aplikaci. Každý ovládací prvek textu je testován, aby bylo možné zjistit, zda lze z něj získat <xref:System.Windows.Automation.ValuePattern> objekt pomocí metody <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. Pokud ovládací prvek text podporuje <xref:System.Windows.Automation.ValuePattern>, je metoda <xref:System.Windows.Automation.ValuePattern.SetValue%2A> použita k vložení řetězce definovaného uživatelem do ovládacího prvku text. V opačném případě je použita metoda <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Viz také:

- [Ukázka vložení textu TextPattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
