---
ms.openlocfilehash: e04134ec731c5e7bede3388621078c6518805ec2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803451"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>Přidat selectionTextBrush veřejnou vlastnost do výběru TextBox/PasswordBox non-adorner

|   |   |
|---|---|
|Podrobnosti|V aplikacích WPF pomocí [non-adorner na výběr textu](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) pro <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.PasswordBox>vývojáři mohou nyní nastavit nově přidané SelectionTextBrush vlastnost změnit vykreslování vybraného textu.  Ve výchozím nastavení se <xref:System.Windows.SystemColors.HighlightTextBrushKey>tato barva mění pomocí aplikace .  Pokud není povolen výběr textu na bázi adorner, tato vlastnost neprovede žádné.|
|Návrh|Jakmile je povolen výběr textu na bázi adorner, můžete použít vlastnost <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> ke změně vzhledu vybraného textu. Toho lze dosáhnout pomocí XAML:<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|Rozsah|Hlavní|
|Version|4.8|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[System.Windows.Controls.Textové pole](xref:System.Windows.Controls.TextBox)</li><li>[System.Windows.Controls.PasswordBox](xref:System.Windows.Controls.PasswordBox)</li></ul>|
