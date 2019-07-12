---
ms.openlocfilehash: 01bbc49cb0febc5a29dafc7c311b848387a4094a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803451"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>Přidejte veřejnou vlastnost SelectionTextBrush výběr – doplněk pro úpravy textového pole a pole pro zadání hesla

|   |   |
|---|---|
|Podrobnosti|V aplikacích WPF pomocí [mimo doplněk pro úpravy na základě výběru textu](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) pro <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.PasswordBox>, vývojáři mohou nyní nastavit vlastnost SelectionTextBrush nově přidané k příkazu alter vykreslení vybraného textu.  Ve výchozím nastavení, tato barva se mění <xref:System.Windows.SystemColors.HighlightTextBrushKey>.  Pokud je založená mimo doplněk pro úpravy není povolen výběr textu, tato vlastnost nemá žádný účinek.|
|Doporučení|Jakmile na základě jiných doplněk pro úpravy je povolen výběr textu, můžete použít <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> vlastnost změnit vzhled vybraného textu. Toho lze dosáhnout pomocí XAML:<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|Scope|Hlavní|
|Version|4.8|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[System.Windows.Controls.TextBox](xref:System.Windows.Controls.TextBox)</li><li>[System.Windows.Controls.PasswordBox](xref:System.Windows.Controls.PasswordBox)</li></ul>|

