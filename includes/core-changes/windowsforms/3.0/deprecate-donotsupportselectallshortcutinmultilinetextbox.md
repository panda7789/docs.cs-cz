---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643989"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="84fdb-101">Přepínač kompatibility. System. Windows. Forms. DoNotSupportSelectAllShortcutInMultilineTextBox není podporovaný.</span><span class="sxs-lookup"><span data-stu-id="84fdb-101">Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="84fdb-102">V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`, který byl představen v .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="84fdb-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="84fdb-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="84fdb-103">Change description</span></span>

<span data-ttu-id="84fdb-104">Počínaje .NET Framework 4.6.1 vybere <kbd>klávesu Ctrl</kbd> <kbd> + </kbd> klávesovou zkratku v ovládacím prvku <xref:System.Windows.Forms.TextBox> vybraný veškerý text.</span><span class="sxs-lookup"><span data-stu-id="84fdb-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="84fdb-105">V .NET Framework 4,6 a předchozích verzích se při výběru <kbd>klávesy Ctrl</kbd> <kbd> + klávesové</kbd> zkratky nepodařilo vybrat veškerý text, pokud jsou vlastnosti [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) a <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> nastaveny na `true`.</span><span class="sxs-lookup"><span data-stu-id="84fdb-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="84fdb-106">Přepínač kompatibility `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` byl představen v .NET Framework 4.6.1 za účelem zachování původního chování.</span><span class="sxs-lookup"><span data-stu-id="84fdb-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="84fdb-107">Další informace najdete v tématu <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84fdb-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="84fdb-108">V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` podporován.</span><span class="sxs-lookup"><span data-stu-id="84fdb-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="84fdb-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="84fdb-109">Version introduced</span></span>

<span data-ttu-id="84fdb-110">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="84fdb-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="84fdb-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="84fdb-111">Recommended action</span></span>

<span data-ttu-id="84fdb-112">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="84fdb-112">Remove the switch.</span></span> <span data-ttu-id="84fdb-113">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="84fdb-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="84fdb-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="84fdb-114">Category</span></span>

<span data-ttu-id="84fdb-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84fdb-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="84fdb-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="84fdb-116">Affected APIs</span></span>

- <span data-ttu-id="84fdb-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="84fdb-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
