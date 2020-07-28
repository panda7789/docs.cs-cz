---
title: 'Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox'
description: Naučte se používat událost TextChanged ke spuštění metody vždy, když se text v ovládacím prvku TextBox změní v Windows Presentation Foundation aplikaci.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166227"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox

Tento příklad ukazuje jeden ze způsobů, jak použít <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> událost ke spuštění metody pokaždé, když se <xref:System.Windows.Controls.TextBox> změní text v ovládacím prvku.

V třídě kódu na pozadí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ovládacího prvku, který obsahuje <xref:System.Windows.Controls.TextBox> ovládací prvek, který chcete monitorovat, vložte metodu, která bude volána vždy, když se <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> událost aktivuje.  Tato metoda musí mít signaturu, která odpovídá tomu, co očekává <xref:System.Windows.Controls.TextChangedEventHandler> delegát.

Obslužná rutina události se volá vždycky, když se <xref:System.Windows.Controls.TextBox> změní obsah ovládacího prvku, a to buď uživatelem, nebo programově.

> [!NOTE]
> Tato událost je aktivována při <xref:System.Windows.Controls.TextBox> vytvoření ovládacího prvku a jeho prvotním vyplnění textem.

## <a name="example"></a>Příklad

V ovládacím [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] prvku definujícího <xref:System.Windows.Controls.TextBox> ovládací prvek zadejte <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atribut s hodnotou, která odpovídá názvu metody obslužné rutiny události.

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>Příklad

V třídě kódu na pozadí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ovládacího prvku, který obsahuje <xref:System.Windows.Controls.TextBox> ovládací prvek, který chcete monitorovat, vložte metodu, která bude volána vždy, když se <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> událost aktivuje.  Tato metoda musí mít signaturu, která odpovídá tomu, co očekává <xref:System.Windows.Controls.TextChangedEventHandler> delegát.

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

Obslužná rutina události se volá vždycky, když se <xref:System.Windows.Controls.TextBox> změní obsah ovládacího prvku, a to buď uživatelem, nebo programově.

> [!NOTE]
> Tato událost je aktivována při <xref:System.Windows.Controls.TextBox> vytvoření ovládacího prvku a jeho prvotním vyplnění textem.

Komentáře

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
