---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643968"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="7f4bb-101">Přepínač kompatibility. System. Windows. Forms. DomainUpDown. UseLegacyScrolling není podporován.</span><span class="sxs-lookup"><span data-stu-id="7f4bb-101">Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="7f4bb-102">V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`, který byl představen v .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="7f4bb-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7f4bb-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="7f4bb-103">Change description</span></span>

<span data-ttu-id="7f4bb-104">Počínaje .NET Framework 4.7.1 se přepínač kompatibility `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` povolil vývojářům, aby se odhlásili od nezávislých <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> a <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcí.</span><span class="sxs-lookup"><span data-stu-id="7f4bb-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="7f4bb-105">Přepínač obnovil chování starší verze, ve kterém se <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ignoruje v případě, že je přítomný kontextový text, a vývojář se musí před akcí <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce použít <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akci ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7f4bb-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="7f4bb-106">Další informace naleznete v tématu [\<AppContextSwitchOverrides > elementu](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="7f4bb-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="7f4bb-107">V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` podporován.</span><span class="sxs-lookup"><span data-stu-id="7f4bb-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7f4bb-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="7f4bb-108">Version introduced</span></span>

<span data-ttu-id="7f4bb-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="7f4bb-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7f4bb-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="7f4bb-110">Recommended action</span></span>

<span data-ttu-id="7f4bb-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="7f4bb-111">Remove the switch.</span></span> <span data-ttu-id="7f4bb-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="7f4bb-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="7f4bb-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="7f4bb-113">Category</span></span>

<span data-ttu-id="7f4bb-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f4bb-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7f4bb-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7f4bb-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
