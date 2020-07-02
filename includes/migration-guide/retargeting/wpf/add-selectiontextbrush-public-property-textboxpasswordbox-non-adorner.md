---
ms.openlocfilehash: aade03c29ff16053a97683499cf719a98ae33f3f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616242"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>Přidat veřejnou vlastnost SelectionTextBrush na výběr bez vizuálního textu/PasswordBox

#### <a name="details"></a>Podrobnosti

V aplikacích WPF, které pro a používají [jiný výběr textu](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> , mohou vývojáři nyní nastavit nově přidanou vlastnost SelectionTextBrush, aby bylo možné změnit vykreslování vybraného textu.  Ve výchozím nastavení se tato barva změní pomocí <xref:System.Windows.SystemColors.HighlightTextBrushKey> .  Pokud není výběr textu založený na doplňku není povolený, tato vlastnost neprovede žádnou akci.

#### <a name="suggestion"></a>Návrh

Když je povolený výběr textu, který není založen na doplňku, můžete <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> použít <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> vlastnost a a změnit vzhled vybraného textu. Toho lze dosáhnout pomocí XAML:

<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4,8         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType>
- [System. Windows. Controls. TextBox](xref:System.Windows.Controls.TextBox)
- [System. Windows. Controls. PasswordBox](xref:System.Windows.Controls.PasswordBox)
