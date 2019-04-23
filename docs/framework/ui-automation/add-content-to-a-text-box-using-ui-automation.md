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
ms.openlocfilehash: 9183aecdc47d54aef26d5cdca8ea11d8398be732
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226505"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje ukázkový kód, který ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vložení textu do pole jedním řádkem textu. Alternativní metoda pro více řádků a funkčně bohaté textových ovládacích prvků neposkytujeme kde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se nedá použít. Pro účely porovnání v příkladu také ukazuje, jak dosáhnout stejných výsledků pomocí metod Win32.  
  
## <a name="example"></a>Příklad  
 Následující příklad vás provede sekvenci textových ovládacích prvků v cílové aplikaci. Každý ovládací prvek text je testován a zjistěte, jestli <xref:System.Windows.Automation.ValuePattern> objektu můžete získat pomocí <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody. Pokud ovládací prvek textu nepodporuje <xref:System.Windows.Automation.ValuePattern>, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> metoda se používá k vložení do textu ovládacího prvku uživatelem definovaný řetězec. V opačném případě <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> metoda se používá.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Viz také:

- [Ukázka vložení prvku TextPattern textu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
