---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937057"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="3f67b-101">Přepínač kompatibility DoNotLoadLatestRichEditControl není podporován.</span><span class="sxs-lookup"><span data-stu-id="3f67b-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="3f67b-102">Přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility, který byl zaveden v rozhraní .NET Framework 4.7.1, není ve formulářích Windows v rozhraní .NET Core 3.0 podporován.</span><span class="sxs-lookup"><span data-stu-id="3f67b-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3f67b-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="3f67b-103">Change description</span></span>

<span data-ttu-id="3f67b-104">V rozhraní .NET Framework 4.6.2 a <xref:System.Windows.Forms.RichTextBox> předchozí verze ovládací prvek by vytvořit instanci Ovládací prvek Win32 RichEdit v3.0 <xref:System.Windows.Forms.RichTextBox> a pro aplikace, které se zaměřují na rozhraní .NET Framework 4.7.1, by ovládací prvek vytvořit instanci RichEdit v4.1 (v *msftedit.dll*).</span><span class="sxs-lookup"><span data-stu-id="3f67b-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="3f67b-105">Přepínač `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` kompatibility byl zaveden, aby aplikace, které cílí na rozhraní .NET Framework 4.7.1 a novější verze, odhlásily nový ovládací prvek RichEdit v4.1 a místo toho použily starý ovládací prvek RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="3f67b-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="3f67b-106">V rozhraní .NET `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` Core není přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="3f67b-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="3f67b-107">Podporovány jsou pouze <xref:System.Windows.Forms.RichTextBox> nové verze ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3f67b-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3f67b-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="3f67b-108">Version introduced</span></span>

<span data-ttu-id="3f67b-109">3.0 Náhled 9</span><span class="sxs-lookup"><span data-stu-id="3f67b-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3f67b-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="3f67b-110">Recommended action</span></span>

<span data-ttu-id="3f67b-111">Odstraňte spínač.</span><span class="sxs-lookup"><span data-stu-id="3f67b-111">Remove the switch.</span></span> <span data-ttu-id="3f67b-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="3f67b-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="3f67b-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="3f67b-113">Category</span></span>

<span data-ttu-id="3f67b-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f67b-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3f67b-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3f67b-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
