---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937057"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="20f7e-101">Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="20f7e-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="20f7e-102">Přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="20f7e-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="20f7e-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="20f7e-103">Change description</span></span>

<span data-ttu-id="20f7e-104">V .NET Framework 4.6.2 a předchozích verzích může <xref:System.Windows.Forms.RichTextBox> ovládací prvek vytvořit instanci systému Win32 RichEdit Control v 3.0 a pro aplikace, které cílí na .NET Framework 4.7.1, by měl <xref:System.Windows.Forms.RichTextBox> ovládací prvek vytvořit instanci RichEdit v 4.1 (v *Msftedit. dll*).</span><span class="sxs-lookup"><span data-stu-id="20f7e-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="20f7e-105">Byl `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` zaveden přepínač kompatibility, který umožňuje aplikacím, které cílí na .NET Framework 4.7.1 a novějších verzí, odhlásit nový ovládací prvek RichEdit v 4.1 a místo toho použít starý ovládací prvek RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="20f7e-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="20f7e-106">V rozhraní .NET Core není `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="20f7e-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="20f7e-107">Jsou podporovány pouze nové verze <xref:System.Windows.Forms.RichTextBox> tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="20f7e-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="20f7e-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="20f7e-108">Version introduced</span></span>

<span data-ttu-id="20f7e-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="20f7e-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="20f7e-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="20f7e-110">Recommended action</span></span>

<span data-ttu-id="20f7e-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="20f7e-111">Remove the switch.</span></span> <span data-ttu-id="20f7e-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="20f7e-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="20f7e-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="20f7e-113">Category</span></span>

<span data-ttu-id="20f7e-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20f7e-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="20f7e-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="20f7e-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
