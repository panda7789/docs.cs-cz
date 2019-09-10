---
title: 'Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 8c7744e9e61b8ba796802e54435c0bf9fdbee50e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855619"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox

Tento příklad ukazuje jeden ze <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> způsobů, jak použít událost ke spuštění metody pokaždé, když se změní text <xref:System.Windows.Controls.TextBox> v ovládacím prvku.

V třídě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódu na pozadí <xref:System.Windows.Controls.TextBox> ovládacího prvku, který obsahuje ovládací prvek, který chcete monitorovat, vložte metodu, která bude volána vždy, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se událost aktivuje.  Tato metoda musí mít signaturu, která odpovídá tomu, co očekává <xref:System.Windows.Controls.TextChangedEventHandler> delegát.

Obslužná rutina události se volá vždycky, když se <xref:System.Windows.Controls.TextBox> změní obsah ovládacího prvku, a to buď uživatelem, nebo programově.

> [!NOTE]
> Tato událost je aktivována při <xref:System.Windows.Controls.TextBox> vytvoření ovládacího prvku a jeho prvotním vyplnění textem.

## <a name="example"></a>Příklad

V ovládacím <xref:System.Windows.Controls.TextBox> prvku definujícího ovládací prvek zadejte <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atribut s hodnotou, která odpovídá názvu metody obslužné rutiny události. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>Příklad

V třídě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódu na pozadí <xref:System.Windows.Controls.TextBox> ovládacího prvku, který obsahuje ovládací prvek, který chcete monitorovat, vložte metodu, která bude volána vždy, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se událost aktivuje.  Tato metoda musí mít signaturu, která odpovídá tomu, co očekává <xref:System.Windows.Controls.TextChangedEventHandler> delegát.

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

Obslužná rutina události se volá vždycky, když se <xref:System.Windows.Controls.TextBox> změní obsah ovládacího prvku, a to buď uživatelem, nebo programově.

> [!NOTE]
> Tato událost je aktivována při <xref:System.Windows.Controls.TextBox> vytvoření ovládacího prvku a jeho prvotním vyplnění textem.

Komentáře

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
