---
title: 'Postupy: Povolení ořezávání textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimming text
- trimming text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 25fff566868e792004a915fee195485c4a1f385f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776103"
---
# <a name="how-to-enable-text-trimming"></a>Postupy: Povolení ořezávání textu

Tento příklad ukazuje použití a efekty hodnot, které jsou k dispozici v <xref:System.Windows.TextTrimming> výčtu.

## <a name="example"></a>Příklad

Následující příklad definuje <xref:System.Windows.Controls.TextBlock> křížkem <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> sadu atributů.

[!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]

Nastavení odpovídající <xref:System.Windows.TextTrimming> vlastností v kódu je znázorněno níže.

[!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
[!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]

Jsou nyní tři možnosti pro oříznutí textu: **CharacterEllipsis**, **WordEllipsis**, a **žádný**.

Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastavena na **CharacterEllipsis**, text je oříznut a pokračuje se třemi tečkami na znak, který je nejblíž k oříznutí edge.  Toto nastavení obvykle mají být odebrány text, který lépe přizpůsobit na hranici ořezávání, ale může vést k slov, který částečně má být oříznut.  Následující obrázek ukazuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> podobně jako výše.

![Příklad: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")

Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastavena na **WordEllipsis**, text je oříznut a pokračovat tři tečky na konci prvního úplné slovo nejbližší na hraničních zařízeních oříznutí.  Toto nastavení částečně oříznutý slova se nezobrazí, ale obvykle nechcete trim co nejvíce oříznutí edge jako text **CharacterEllipsis** nastavení.  Následující obrázek ukazuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> výše.

![Příklad: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")

Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastavena na **žádný**, se provádí bez ořezávání textu.  V takovém případě text jednoduše ořízne na hranici jeho nadřazeného kontejneru text.  Následující obrázek ukazuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> podobně jako výše.

![Příklad: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")
