---
ms.openlocfilehash: e04134ec731c5e7bede3388621078c6518805ec2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982280"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>Přidejte veřejnou vlastnost SelectionTextBrush výběr – doplněk pro úpravy textového pole a pole pro zadání hesla

|   |   |
|---|---|
|Podrobnosti|V aplikacích WPF pomocí [mimo doplněk pro úpravy na základě výběru textu](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) pro <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.PasswordBox>, vývojáři mohou nyní nastavit vlastnost SelectionTextBrush nově přidané k příkazu alter vykreslení vybraného textu.  Ve výchozím nastavení, tato barva se mění <xref:System.Windows.SystemColors.HighlightTextBrushKey>.  Pokud je založená mimo doplněk pro úpravy není povolen výběr textu, tato vlastnost nemá žádný účinek.|
|Doporučení|Jakmile na základě jiných doplněk pro úpravy je povolen výběr textu, můžete použít <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> vlastnost změnit vzhled vybraného textu. Toho lze dosáhnout pomocí XAML:<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|Rozsah|Hlavní|
|Version|4.8|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[System.Windows.Controls.TextBox](xref:System.Windows.Controls.TextBox)</li><li>[System.Windows.Controls.PasswordBox](xref:System.Windows.Controls.PasswordBox)</li></ul>|
