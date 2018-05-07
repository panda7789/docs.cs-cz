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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4b3179333119d1ff516c6176298fa25514a9ba66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje ukázkový kód, který ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vložení textu do jednořádkové textové pole. Poskytuje alternativní metoda pro text Víceřádkový a bohaté ovládací prvky kde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se nedá použít. Pro účely porovnání příklad také ukazuje, jak používat metody Win32 provedete stejné výsledky.  
  
## <a name="example"></a>Příklad  
 Následující příklady kroků pomocí pořadí prvků textu v cílové aplikace. Zjistí, zda je testován každý ovládací prvek text <xref:System.Windows.Automation.ValuePattern> objekt můžete získat pomocí <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metoda. Pokud ovládací prvek text podporuje <xref:System.Windows.Automation.ValuePattern>, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> metoda slouží k vložení řetězec uživatelem definované do ovládacího prvku text. Jinak <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> metoda se používá.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka TextPattern vložení textu](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
