---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937116"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="51053-101">Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="51053-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="51053-102">Přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="51053-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="51053-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="51053-103">Change description</span></span>

<span data-ttu-id="51053-104">Počínaje .NET Framework 4.7.1 se přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` kompatibility povolil vývojářům, aby se odhlásili jako nezávisle <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> a <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce.</span><span class="sxs-lookup"><span data-stu-id="51053-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="51053-105">Přepínač obnovil chování starší verze, ve kterém <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> se ignoruje, pokud je přítomný kontextový text, a vývojář se musí před <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcí použít akci na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="51053-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="51053-106">Další informace naleznete v tématu [ \<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="51053-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="51053-107">V rozhraní .NET Core není `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="51053-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="51053-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="51053-108">Version introduced</span></span>

<span data-ttu-id="51053-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="51053-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="51053-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="51053-110">Recommended action</span></span>

<span data-ttu-id="51053-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="51053-111">Remove the switch.</span></span> <span data-ttu-id="51053-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="51053-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="51053-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="51053-113">Category</span></span>

<span data-ttu-id="51053-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51053-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="51053-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="51053-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
