---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181867"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="9bf79-101">Přepínač kompatibility. System. Windows. Forms. DontSupportReentrantFilterMessage není podporovaný.</span><span class="sxs-lookup"><span data-stu-id="9bf79-101">Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="9bf79-102">Přepínač `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` kompatibility, který byl představen v .NET Framework 4.6.1, není podporován v model Windows Forms .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="9bf79-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9bf79-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="9bf79-103">Change description</span></span>

<span data-ttu-id="9bf79-104">Počínaje .NET Framework 4.6.1 `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` , přepínač kompatibility řeší možné <xref:System.IndexOutOfRangeException> výjimky při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volání zprávy s vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementací.</span><span class="sxs-lookup"><span data-stu-id="9bf79-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="9bf79-105">Další informace najdete v tématu [zmírnění rizika: Vlastní implementace](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)IMessageFilter. PreFilterMessage.</span><span class="sxs-lookup"><span data-stu-id="9bf79-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="9bf79-106">V rozhraní .NET Core `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` není přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="9bf79-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9bf79-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="9bf79-107">Version introduced</span></span>

<span data-ttu-id="9bf79-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="9bf79-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9bf79-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="9bf79-109">Recommended action</span></span>

<span data-ttu-id="9bf79-110">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="9bf79-110">Remove the switch.</span></span> <span data-ttu-id="9bf79-111">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="9bf79-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="9bf79-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="9bf79-112">Category</span></span>

<span data-ttu-id="9bf79-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9bf79-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9bf79-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9bf79-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
