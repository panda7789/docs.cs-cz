---
ms.openlocfilehash: 3fb8807a9b6f0bb0d2bc746f5e89eaa8a81d6aa8
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556159"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="6169c-101">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="6169c-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="6169c-102">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Přepínač kompatibility, který byl představen v .NET Framework 4.6.1, není podporován v model Windows Forms v rozhraní .NET Core a .net 5,0 a novějším.</span><span class="sxs-lookup"><span data-stu-id="6169c-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core and .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6169c-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="6169c-103">Change description</span></span>

<span data-ttu-id="6169c-104">Počínaje .NET Framework 4.6.1 vyberete <kbd>klávesovou zkratku CTRL</kbd>  +  <kbd>A</kbd> v <xref:System.Windows.Forms.TextBox> ovládacím prvku vybraný veškerý text.</span><span class="sxs-lookup"><span data-stu-id="6169c-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="6169c-105">V .NET Framework 4,6 a předchozích verzích se při výběru <kbd>klávesy CTRL</kbd>  +  <kbd>a</kbd> klávesové zkratky nepovedlo vybrat veškerý text, pokud by vlastnost [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) a <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> Properties byla obě nastavená na `true` .</span><span class="sxs-lookup"><span data-stu-id="6169c-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="6169c-106">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Přepínač kompatibility byl představen v .NET Framework 4.6.1 za účelem zachování původního chování.</span><span class="sxs-lookup"><span data-stu-id="6169c-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="6169c-107">Další informace naleznete zde <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6169c-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6169c-108">V rozhraní .NET Core a .NET 5,0 a novějších verzích není `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="6169c-108">In .NET Core and .NET 5.0 and later versions, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6169c-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6169c-109">Version introduced</span></span>

<span data-ttu-id="6169c-110">3.0</span><span class="sxs-lookup"><span data-stu-id="6169c-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6169c-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="6169c-111">Recommended action</span></span>

<span data-ttu-id="6169c-112">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="6169c-112">Remove the switch.</span></span> <span data-ttu-id="6169c-113">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="6169c-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="6169c-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="6169c-114">Category</span></span>

<span data-ttu-id="6169c-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6169c-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6169c-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6169c-116">Affected APIs</span></span>

- <span data-ttu-id="6169c-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="6169c-117">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
