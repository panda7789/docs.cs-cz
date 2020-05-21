---
ms.openlocfilehash: cb8c0532bb2bcfbcd619cd382f3d236b431c3480
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721723"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="68173-101">Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="68173-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="68173-102">`Switch.System.Windows.Forms.UseLegacyImages`Přepínač kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="68173-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="68173-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="68173-103">Change description</span></span>

<span data-ttu-id="68173-104">V .NET Framework 4.6.2 a předchozích verzích může <xref:System.Windows.Forms.RichTextBox> ovládací prvek vytvořit instanci systému Win32 RichEdit Control v 3.0 a pro aplikace, které cílí na .NET Framework 4.7.1, <xref:System.Windows.Forms.RichTextBox> by měl ovládací prvek vytvořit instanci RichEdit v 4.1 (v *Msftedit. dll*).</span><span class="sxs-lookup"><span data-stu-id="68173-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="68173-105">`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`Byl zaveden přepínač kompatibility, který umožňuje aplikacím, které cílí na .NET Framework 4.7.1 a novějších verzí, odhlásit nový ovládací prvek RichEdit v 4.1 a místo toho použít starý ovládací prvek RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="68173-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="68173-106">V rozhraní .NET Core není `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="68173-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="68173-107">Jsou podporovány pouze nové verze tohoto <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="68173-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="68173-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="68173-108">Version introduced</span></span>

<span data-ttu-id="68173-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="68173-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="68173-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="68173-110">Recommended action</span></span>

<span data-ttu-id="68173-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="68173-111">Remove the switch.</span></span> <span data-ttu-id="68173-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="68173-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="68173-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="68173-113">Category</span></span>

<span data-ttu-id="68173-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="68173-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="68173-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="68173-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
