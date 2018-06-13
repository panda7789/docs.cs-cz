---
title: 'Postupy: Povolení ořezávání textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 97bc88b298500892fcc7d26e61f8052a05d9e593
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543537"
---
# <a name="how-to-enable-text-trimming"></a>Postupy: Povolení ořezávání textu
Tento příklad ukazuje použití a důsledků hodnoty, které jsou k dispozici v <xref:System.Windows.TextTrimming> výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje <xref:System.Windows.Controls.TextBlock> element s <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> nastaven atribut.  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a>Příklad  
 Nastavení odpovídající <xref:System.Windows.TextTrimming> je znázorněn vlastností v kódu.  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 Jsou aktuálně tři možnosti pro text oříznutí: **CharacterEllipsis**, **WordEllipsis**, a **žádné**.  
  
 Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastaven na **CharacterEllipsis**, text je oříznut a dál se třemi tečkami na nejbližší okraj oříznutí znaků.  Toto nastavení se obvykle trim přizpůsobení přesněji na hranici oříznutí textu, ale může mít za následek slova částečně oříznuty.  Následující obrázek znázorňuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> podobné definované výše.  
  
 ![Příklad: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")  
  
 Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastaven na **WordEllipsis**, text je oříznut a dál se třemi tečkami na konci prvního úplné slova nejbližší okraj oříznutí.  Toto nastavení nebude zobrazit částečně oříznutý slova, ale obvykle není trim co nejvíce oříznutí okraj jako text **CharacterEllipsis** nastavení.  Následující obrázek znázorňuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> definované výše.  
  
 ![Příklad: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")  
  
 Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastaven na **žádné**, se provádí bez oříznutí text.  V takovém případě text jednoduše oříznout na hranici nadřazený kontejner textu.  Následující obrázek znázorňuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> podobné definované výše.  
  
 ![Příklad: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")
