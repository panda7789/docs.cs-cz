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
ms.openlocfilehash: 8ffa4c9919788060dc4524e127c181ee8282e6f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768599"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Postupy: Otevření souboru přetaženého na ovládací prvek RichTextBox
V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, a <xref:System.Windows.Documents.FlowDocument> všechny ovládací prvky mít integrovanou funkci přetažení myší. Integrované funkce umožňuje a přetahování textu v rámci a mezi ovládacími prvky. Však neumožňuje otevírání souboru přetažením souboru na ovládacím prvku. Tyto ovládací prvky přetažení myší události také označit jako zpracování. Ve výchozím nastavení, v důsledku toho nelze přidat svoje vlastní obslužné rutiny události poskytuje funkce pro otevření přetažené soubory.  
  
 Chcete-li přidat další zpracování přetažení myší, události v těchto ovládacích prvků, použijte <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metoda pro přidání obslužné rutiny události pro události přetažení myší. Nastavte `handledEventsToo` parametr `true` mít zadaná obslužná rutina volat pro směrovanou událost, která již byla označena jako stará jiný element na trase události.  
  
> [!TIP]
>  Můžete nahradit vestavěnou funkci přetažení myší <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, a <xref:System.Windows.Documents.FlowDocument> zpracování verze preview událostí přetahování myší a označením události ve verzi preview jako zpracování. Ale to zakáže integrované funkce přetahování myší a nedoporučuje se používat.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat obslužné rutiny pro <xref:System.Windows.DragDrop.DragOver> a <xref:System.Windows.DragDrop.Drop> události <xref:System.Windows.Controls.RichTextBox>. Tento příklad používá <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metoda a nastaví `handledEventsToo` parametr `true` tak, aby obslužné rutiny událostí, který bude vyvolán i když <xref:System.Windows.Controls.RichTextBox> označí tyto události jako zpracované. Kód v obslužné rutině události přidá funkce otevřete textový soubor, který je přesunuta <xref:System.Windows.Controls.RichTextBox>.  
  
 K otestování v tomto příkladu, přetáhněte textový soubor nebo soubor formátovaný text format (RTF) z Průzkumníka Windows <xref:System.Windows.Controls.RichTextBox>. Soubor se otevřou v <xref:System.Windows.Controls.RichTextBox>. Pokud stisknete klávesu SHIFT pokleslo souboru, soubor se otevřou jako prostý text.  
  
 [!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
