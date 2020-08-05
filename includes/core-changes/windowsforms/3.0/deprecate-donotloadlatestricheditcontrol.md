---
ms.openlocfilehash: e10b5168d59edd56ff549a3a1e3a09d023fe5e28
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556154"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="b06a1-101">Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="b06a1-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="b06a1-102">`Switch.System.Windows.Forms.UseLegacyImages`Přepínač kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms v rozhraní .NET Core nebo .net 5,0 a novějším.</span><span class="sxs-lookup"><span data-stu-id="b06a1-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b06a1-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="b06a1-103">Change description</span></span>

<span data-ttu-id="b06a1-104">V .NET Framework 4.6.2 a předchozích verzích <xref:System.Windows.Forms.RichTextBox> řídí ovládací prvek Win32 RichEdit Control v 3.0 a pro aplikace, které cílí na .NET Framework 4.7.1, <xref:System.Windows.Forms.RichTextBox> ovládací prvek vytváří instance RichEdit v 4.1 (v *msftedit.dll*).</span><span class="sxs-lookup"><span data-stu-id="b06a1-104">In .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control instantiates the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control instantiates RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="b06a1-105">`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`Byl zaveden přepínač kompatibility, který umožňuje aplikacím, které cílí na .NET Framework 4.7.1 a novějších verzí, odhlásit nový ovládací prvek RichEdit v 4.1 a místo toho použít starý ovládací prvek RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="b06a1-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="b06a1-106">V rozhraní .NET Core a .NET 5,0 a novějších verzích není `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="b06a1-106">In .NET Core and .NET 5.0 and later versions, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="b06a1-107">Jsou podporovány pouze nové verze tohoto <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b06a1-107">Only new versions of the <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b06a1-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b06a1-108">Version introduced</span></span>

<span data-ttu-id="b06a1-109">3.0</span><span class="sxs-lookup"><span data-stu-id="b06a1-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b06a1-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b06a1-110">Recommended action</span></span>

<span data-ttu-id="b06a1-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="b06a1-111">Remove the switch.</span></span> <span data-ttu-id="b06a1-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="b06a1-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="b06a1-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b06a1-113">Category</span></span>

<span data-ttu-id="b06a1-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b06a1-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b06a1-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b06a1-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
