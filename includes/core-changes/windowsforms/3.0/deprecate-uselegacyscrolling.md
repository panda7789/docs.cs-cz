---
ms.openlocfilehash: ee4a27dde9f1e7756401e3d8b709514082f5d3b1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556157"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="e4042-101">Přepínač kompatibility DomainUpDown. UseLegacyScrolling se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="e4042-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="e4042-102">`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`Přepínač kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms v rozhraní .NET Core nebo .net 5,0 a novějším.</span><span class="sxs-lookup"><span data-stu-id="e4042-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e4042-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="e4042-103">Change description</span></span>

<span data-ttu-id="e4042-104">Počínaje .NET Framework 4.7.1 se `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` přepínač kompatibility povolil vývojářům, aby si nezávisle a akce odhlásili <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e4042-104">Starting with .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="e4042-105">Přepínač obnovil chování starší verze, ve kterém se <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ignoruje, pokud je přítomný kontextový text, a vývojář se musí <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> před akcí použít akci na ovládacím prvku <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e4042-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="e4042-106">Další informace naleznete v tématu [ \<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="e4042-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="e4042-107">V rozhraní .NET Core a .NET 5,0 a novějším není `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="e4042-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e4042-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e4042-108">Version introduced</span></span>

<span data-ttu-id="e4042-109">3.0</span><span class="sxs-lookup"><span data-stu-id="e4042-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e4042-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e4042-110">Recommended action</span></span>

<span data-ttu-id="e4042-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="e4042-111">Remove the switch.</span></span> <span data-ttu-id="e4042-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="e4042-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="e4042-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e4042-113">Category</span></span>

<span data-ttu-id="e4042-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4042-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e4042-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e4042-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
