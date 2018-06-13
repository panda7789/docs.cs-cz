---
title: 'Postupy: Otevření souboru přetaženého na ovládací prvek RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
ms.openlocfilehash: f3c10ae76a9afcc04578c590cc57cd43c3ab7a1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547759"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Postupy: Otevření souboru přetaženého na ovládací prvek RichTextBox
V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, a <xref:System.Windows.Documents.FlowDocument> všechny ovládací prvky mít integrovanou funkci přetažení myší. Integrovanou funkci umožňuje přetažení myší textu v rámci a mezi ovládacími prvky. Však není povolit otevřením souboru umístěním souboru na ovládací prvek. Tyto ovládací prvky přetažení myší události také označit jako zpracování. Ve výchozím nastavení, v důsledku toho nelze přidat svoje vlastní obslužné rutiny událostí nakonfigurovánu otevřete vynechaných soubory.  
  
 Přidat další zpracování pro přetažení myší události v těchto ovládacích prvků, použijte <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metoda pro přidání obslužné rutiny události pro události přetažení myší. Nastavte `handledEventsToo` parametr `true` má být volána pro směrované události, která již byla označena jako zpracované jiný element na trase událostí zadaná obslužná rutina.  
  
> [!TIP]
>  Můžete nahradit integrované funkce přetažení myší <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, a <xref:System.Windows.Documents.FlowDocument> zpracování verze preview událostí přetahování myší a označením události náhledu jako zpracování. Však tato akce zakáže integrovanou funkci přetažení myší a nedoporučuje se používat.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat obslužné rutiny pro <xref:System.Windows.DragDrop.DragOver> a <xref:System.Windows.DragDrop.Drop> události <xref:System.Windows.Controls.RichTextBox>. Tento příklad používá <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metoda a nastaví `handledEventsToo` parametru `true` tak, aby obslužné rutiny události bude volána i když <xref:System.Windows.Controls.RichTextBox> označí tyto události, jako zpracování. Kód obslužné rutiny událostí přidá funkce otevřete textový soubor, který je umístěný na <xref:System.Windows.Controls.RichTextBox>.  
  
 K testování v tomto příkladu, přetáhněte z Průzkumníka Windows na textový soubor nebo soubor formátu RTF formátovaným textem <xref:System.Windows.Controls.RichTextBox>. Soubor se otevřou v <xref:System.Windows.Controls.RichTextBox>. Pokud stisknutím klávesy SHIFT před vyřazování souboru, soubor se otevře jako prostý text.  
  
 [!code-xaml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
