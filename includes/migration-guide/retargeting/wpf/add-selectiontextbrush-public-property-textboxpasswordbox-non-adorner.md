---
ms.openlocfilehash: aade03c29ff16053a97683499cf719a98ae33f3f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616242"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a><span data-ttu-id="59a7e-101">Přidat veřejnou vlastnost SelectionTextBrush na výběr bez vizuálního textu/PasswordBox</span><span class="sxs-lookup"><span data-stu-id="59a7e-101">Add SelectionTextBrush public property to TextBox/PasswordBox non-adorner selection</span></span>

#### <a name="details"></a><span data-ttu-id="59a7e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="59a7e-102">Details</span></span>

<span data-ttu-id="59a7e-103">V aplikacích WPF, které pro a používají [jiný výběr textu](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> , mohou vývojáři nyní nastavit nově přidanou vlastnost SelectionTextBrush, aby bylo možné změnit vykreslování vybraného textu.</span><span class="sxs-lookup"><span data-stu-id="59a7e-103">In WPF applications using [non-adorner based text selection](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) for <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox>, developers may now set the newly added SelectionTextBrush property in order to alter the rendering of the selected text.</span></span>  <span data-ttu-id="59a7e-104">Ve výchozím nastavení se tato barva změní pomocí <xref:System.Windows.SystemColors.HighlightTextBrushKey> .</span><span class="sxs-lookup"><span data-stu-id="59a7e-104">By default, this color changes with <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span></span>  <span data-ttu-id="59a7e-105">Pokud není výběr textu založený na doplňku není povolený, tato vlastnost neprovede žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="59a7e-105">If non-adorner based text selection is not enabled, this property does nothing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="59a7e-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="59a7e-106">Suggestion</span></span>

<span data-ttu-id="59a7e-107">Když je povolený výběr textu, který není založen na doplňku, můžete <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> použít <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> vlastnost a a změnit vzhled vybraného textu.</span><span class="sxs-lookup"><span data-stu-id="59a7e-107">Once non-adorner based text selection is enabled, you can use the <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> property to change the appearance of the selected text.</span></span> <span data-ttu-id="59a7e-108">Toho lze dosáhnout pomocí XAML:</span><span class="sxs-lookup"><span data-stu-id="59a7e-108">This can be achieved using XAML:</span></span>

<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="59a7e-109">Name</span><span class="sxs-lookup"><span data-stu-id="59a7e-109">Name</span></span>    | <span data-ttu-id="59a7e-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="59a7e-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="59a7e-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="59a7e-111">Scope</span></span>   | <span data-ttu-id="59a7e-112">Hlavní</span><span class="sxs-lookup"><span data-stu-id="59a7e-112">Major</span></span>       |
| <span data-ttu-id="59a7e-113">Verze</span><span class="sxs-lookup"><span data-stu-id="59a7e-113">Version</span></span> | <span data-ttu-id="59a7e-114">4,8</span><span class="sxs-lookup"><span data-stu-id="59a7e-114">4.8</span></span>         |
| <span data-ttu-id="59a7e-115">Typ</span><span class="sxs-lookup"><span data-stu-id="59a7e-115">Type</span></span>    | <span data-ttu-id="59a7e-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="59a7e-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="59a7e-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="59a7e-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType>
- [<span data-ttu-id="59a7e-118">System. Windows. Controls. TextBox</span><span class="sxs-lookup"><span data-stu-id="59a7e-118">System.Windows.Controls.TextBox</span></span>](xref:System.Windows.Controls.TextBox)
- [<span data-ttu-id="59a7e-119">System. Windows. Controls. PasswordBox</span><span class="sxs-lookup"><span data-stu-id="59a7e-119">System.Windows.Controls.PasswordBox</span></span>](xref:System.Windows.Controls.PasswordBox)
