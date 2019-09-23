---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181832"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="a9cd1-101">Přepínač kompatibility. System. Windows. Forms. DomainUpDown. UseLegacyScrolling není podporován.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-101">Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="a9cd1-102">Přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a9cd1-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="a9cd1-103">Change description</span></span>

<span data-ttu-id="a9cd1-104">Počínaje .NET Framework 4.7.1 se přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` kompatibility povolil vývojářům, aby se odhlásili jako nezávisle <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> a <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="a9cd1-105">Přepínač obnovil chování starší verze, ve kterém <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> se ignoruje, pokud je přítomný kontextový text, a vývojář se musí před <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcí <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> použít akci na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="a9cd1-106">Další informace naleznete v tématu [ \<AppContextSwitchOverrides > element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="a9cd1-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="a9cd1-107">V rozhraní .NET Core `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` není přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a9cd1-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a9cd1-108">Version introduced</span></span>

<span data-ttu-id="a9cd1-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="a9cd1-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a9cd1-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a9cd1-110">Recommended action</span></span>

<span data-ttu-id="a9cd1-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-111">Remove the switch.</span></span> <span data-ttu-id="a9cd1-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="a9cd1-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a9cd1-113">Category</span></span>

<span data-ttu-id="a9cd1-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9cd1-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a9cd1-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a9cd1-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
