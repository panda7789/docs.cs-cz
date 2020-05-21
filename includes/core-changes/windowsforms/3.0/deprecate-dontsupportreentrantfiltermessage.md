---
ms.openlocfilehash: 55c13aa70a03bcc548ce1d096cca8f40de6cda84
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721447"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="36e21-101">Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="36e21-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="36e21-102">`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`Přepínač kompatibility, který byl představen v .NET Framework 4.6.1, není podporován v model Windows Forms .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="36e21-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="36e21-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="36e21-103">Change description</span></span>

<span data-ttu-id="36e21-104">Počínaje .NET Framework 4.6.1, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` přepínač kompatibility řeší možné <xref:System.IndexOutOfRangeException> výjimky při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volání zprávy s vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementací.</span><span class="sxs-lookup"><span data-stu-id="36e21-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="36e21-105">Další informace naleznete v tématu [zmírňující rizika: Custom IMessageFilter. PreFilterMessage Implements](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span><span class="sxs-lookup"><span data-stu-id="36e21-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="36e21-106">V rozhraní .NET Core není `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="36e21-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="36e21-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="36e21-107">Version introduced</span></span>

<span data-ttu-id="36e21-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="36e21-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="36e21-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="36e21-109">Recommended action</span></span>

<span data-ttu-id="36e21-110">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="36e21-110">Remove the switch.</span></span> <span data-ttu-id="36e21-111">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="36e21-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="36e21-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="36e21-112">Category</span></span>

<span data-ttu-id="36e21-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36e21-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="36e21-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="36e21-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
