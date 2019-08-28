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
ms.openlocfilehash: 408d48856362fa8a77a44e2cc97cb2d5ff608dcf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046355"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Postupy: Otevření souboru přetaženého na ovládací prvek RichTextBox

V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]nástrojimají ovládací <xref:System.Windows.Controls.RichTextBox>prvky <xref:System.Windows.Documents.FlowDocument> , a všechny integrované funkce přetahování myší. <xref:System.Windows.Controls.TextBox> Integrovaná funkce umožňuje přetažení textu mezi ovládacími prvky a mezi nimi. Nepovoluje se ale otevírání souboru vyřazením souboru na ovládacím prvku. Tyto ovládací prvky také označují události přetažení jako zpracované. V důsledku toho se ve výchozím nastavení nedají přidat vlastní obslužné rutiny událostí, které by poskytovaly funkce pro otevření vynechaných souborů.

Chcete-li přidat další zpracování pro události přetažení v těchto ovládacích prvcích, použijte <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metodu pro přidání obslužných rutin událostí pro události přetažení. Nastavte parametr na `true` hodnotu pro vyvolání zadané obslužné rutiny pro směrovanou událost, která již byla označena jako zpracována jiným prvkem v rámci trasy události. `handledEventsToo`

> [!TIP]
> Můžete nahradit integrované funkce <xref:System.Windows.Controls.TextBox>přetahování, <xref:System.Windows.Controls.RichTextBox>a <xref:System.Windows.Documents.FlowDocument> tak, že vyřadíte verze Preview událostí přetažení a označíte události verze Preview jako zpracovávané. Tato akce však zakáže integrované funkce přetahování myší a nedoporučuje se.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přidat obslužné rutiny pro <xref:System.Windows.DragDrop.DragOver> události <xref:System.Windows.DragDrop.Drop> a v <xref:System.Windows.Controls.RichTextBox>. Tento příklad používá <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metodu a `handledEventsToo` nastavuje parametr na `true` tak, aby obslužné rutiny <xref:System.Windows.Controls.RichTextBox> událostí byly vyvolány, i když tyto události označí jako zpracovávané. Kód v obslužných rutinách událostí přidává funkce, aby bylo možné otevřít textový soubor, který <xref:System.Windows.Controls.RichTextBox>je umístěn na.

Chcete-li otestovat tento příklad, přetáhněte textový soubor nebo soubor RTF (Rich Text Format) z Průzkumníka Windows na <xref:System.Windows.Controls.RichTextBox>. Soubor bude otevřen v <xref:System.Windows.Controls.RichTextBox>. Pokud stisknete klávesu SHIFT před vyřazením souboru, soubor bude otevřen jako prostý text.

[!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]

[!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
[!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
