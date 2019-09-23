---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181794"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="d417a-101">Přepínač kompatibility. System. Windows. Forms. DoNotLoadLatestRichEditControl není podporovaný.</span><span class="sxs-lookup"><span data-stu-id="d417a-101">Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="d417a-102">Přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d417a-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d417a-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="d417a-103">Change description</span></span>

<span data-ttu-id="d417a-104">V .NET Framework 4.6.2 a předchozích verzích <xref:System.Windows.Forms.RichTextBox> by ovládací prvek vytvořil instanci Win32 RichEdit Control v 3.0 a pro aplikace, které cílí na .NET Framework 4.7.1 <xref:System.Windows.Forms.RichTextBox> , by měl ovládací prvek vytvořit instanci RichEdit v 4.1 (v  *Msftedit. dll*).</span><span class="sxs-lookup"><span data-stu-id="d417a-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="d417a-105">Byl zaveden přepínač kompatibility, který umožňuje aplikacím, které cílí na .NET Framework 4.7.1 a novějších verzí, odhlásit nový ovládací prvek RichEdit v 4.1 a místo toho použít starý ovládací prvek RichEdit v3. `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`</span><span class="sxs-lookup"><span data-stu-id="d417a-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="d417a-106">V rozhraní .NET Core `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` není přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="d417a-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="d417a-107">Jsou podporovány pouze nové verze <xref:System.Windows.Forms.RichTextBox> tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d417a-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d417a-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="d417a-108">Version introduced</span></span>

<span data-ttu-id="d417a-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="d417a-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d417a-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="d417a-110">Recommended action</span></span>

<span data-ttu-id="d417a-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="d417a-111">Remove the switch.</span></span> <span data-ttu-id="d417a-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="d417a-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d417a-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d417a-113">Category</span></span>

<span data-ttu-id="d417a-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d417a-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d417a-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d417a-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
