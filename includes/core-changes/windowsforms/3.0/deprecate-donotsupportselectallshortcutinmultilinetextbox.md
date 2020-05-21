---
ms.openlocfilehash: bba74f26eafd52b966928835d5003d03af1eabdc
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721403"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="775c4-101">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="775c4-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="775c4-102">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Přepínač kompatibility, který byl představen v .NET Framework 4.6.1, není podporován v model Windows Forms .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="775c4-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="775c4-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="775c4-103">Change description</span></span>

<span data-ttu-id="775c4-104">Počínaje .NET Framework 4.6.1 vyberete <kbd>klávesovou zkratku CTRL</kbd>  +  <kbd>A</kbd> v <xref:System.Windows.Forms.TextBox> ovládacím prvku vybraný veškerý text.</span><span class="sxs-lookup"><span data-stu-id="775c4-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="775c4-105">V .NET Framework 4,6 a předchozích verzích se při výběru <kbd>klávesy CTRL</kbd>  +  <kbd>a</kbd> klávesové zkratky nepovedlo vybrat veškerý text, pokud by vlastnost [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) a <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> Properties byla obě nastavená na `true` .</span><span class="sxs-lookup"><span data-stu-id="775c4-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="775c4-106">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Přepínač kompatibility byl představen v .NET Framework 4.6.1 za účelem zachování původního chování.</span><span class="sxs-lookup"><span data-stu-id="775c4-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="775c4-107">Další informace naleznete zde <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="775c4-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="775c4-108">V rozhraní .NET Core není `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="775c4-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="775c4-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="775c4-109">Version introduced</span></span>

<span data-ttu-id="775c4-110">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="775c4-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="775c4-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="775c4-111">Recommended action</span></span>

<span data-ttu-id="775c4-112">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="775c4-112">Remove the switch.</span></span> <span data-ttu-id="775c4-113">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="775c4-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="775c4-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="775c4-114">Category</span></span>

<span data-ttu-id="775c4-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="775c4-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="775c4-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="775c4-116">Affected APIs</span></span>

- <span data-ttu-id="775c4-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="775c4-117">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
