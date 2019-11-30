---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643982"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="2be42-101">Přepínač kompatibility. System. Windows. Forms. DoNotLoadLatestRichEditControl není podporovaný.</span><span class="sxs-lookup"><span data-stu-id="2be42-101">Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="2be42-102">V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.UseLegacyImages`, který byl představen v .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="2be42-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2be42-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="2be42-103">Change description</span></span>

<span data-ttu-id="2be42-104">V .NET Framework 4.6.2 a předchozích verzích by ovládací prvek <xref:System.Windows.Forms.RichTextBox> vytvořil instanci Win32 RichEdit Control v 3.0 a pro aplikace, které cílí .NET Framework 4.7.1, by měl ovládací prvek <xref:System.Windows.Forms.RichTextBox> vytvořit instanci RichEdit v 4.1 (v *Msftedit. dll*).</span><span class="sxs-lookup"><span data-stu-id="2be42-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="2be42-105">Byl zaveden přepínač kompatibility `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`, který umožňuje aplikacím, které cílí na .NET Framework 4.7.1 a novějších verzích, odhlásit nový ovládací prvek RichEdit v 4.1 a místo toho použít starý ovládací prvek RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="2be42-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="2be42-106">V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` podporován.</span><span class="sxs-lookup"><span data-stu-id="2be42-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="2be42-107">Jsou podporovány pouze nové verze <xref:System.Windows.Forms.RichTextBox>ho ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2be42-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2be42-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="2be42-108">Version introduced</span></span>

<span data-ttu-id="2be42-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="2be42-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2be42-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="2be42-110">Recommended action</span></span>

<span data-ttu-id="2be42-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="2be42-111">Remove the switch.</span></span> <span data-ttu-id="2be42-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="2be42-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="2be42-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2be42-113">Category</span></span>

<span data-ttu-id="2be42-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2be42-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2be42-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2be42-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
