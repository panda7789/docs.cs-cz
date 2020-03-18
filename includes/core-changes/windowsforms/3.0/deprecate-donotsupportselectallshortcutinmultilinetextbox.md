---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937081"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="ff64b-101">Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox není podporován</span><span class="sxs-lookup"><span data-stu-id="ff64b-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="ff64b-102">Přepínač `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` kompatibility, který byl zaveden v rozhraní .NET Framework 4.6.1, není ve formulářích Windows v rozhraní .NET Core 3.0 podporován.</span><span class="sxs-lookup"><span data-stu-id="ff64b-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ff64b-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="ff64b-103">Change description</span></span>

<span data-ttu-id="ff64b-104">Počínaje rozhraním .NET Framework 4.6.1 vyberte klávesovou zkratku <kbd>Ctrl</kbd> + <kbd>A</kbd> v ovládacím prvku vybraný <xref:System.Windows.Forms.TextBox> veškerý text.</span><span class="sxs-lookup"><span data-stu-id="ff64b-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="ff64b-105">V rozhraní .NET Framework 4.6 a předchozích verzích se výběru klávesové zkratky <kbd>Ctrl</kbd> + <kbd>A</kbd> nepodařilo `true`vybrat veškerý text, pokud byly obě [vlastnosti Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) a <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> vlastnosti nastaveny na .</span><span class="sxs-lookup"><span data-stu-id="ff64b-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="ff64b-106">Přepínač `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` kompatibility byl zaveden v rozhraní .NET Framework 4.6.1 zachovat původní chování.</span><span class="sxs-lookup"><span data-stu-id="ff64b-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="ff64b-107">Další informace naleznete zde <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ff64b-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ff64b-108">V rozhraní .NET `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` Core není přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="ff64b-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ff64b-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="ff64b-109">Version introduced</span></span>

<span data-ttu-id="ff64b-110">3.0 Náhled 9</span><span class="sxs-lookup"><span data-stu-id="ff64b-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ff64b-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="ff64b-111">Recommended action</span></span>

<span data-ttu-id="ff64b-112">Odstraňte spínač.</span><span class="sxs-lookup"><span data-stu-id="ff64b-112">Remove the switch.</span></span> <span data-ttu-id="ff64b-113">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="ff64b-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="ff64b-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="ff64b-114">Category</span></span>

<span data-ttu-id="ff64b-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff64b-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ff64b-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ff64b-116">Affected APIs</span></span>

- <span data-ttu-id="ff64b-117">Žádný</span><span class="sxs-lookup"><span data-stu-id="ff64b-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
