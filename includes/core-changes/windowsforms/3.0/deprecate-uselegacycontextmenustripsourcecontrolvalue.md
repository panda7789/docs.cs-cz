---
ms.openlocfilehash: df6169289fb96df5f7daf8bd58ccaeebc33ad87c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556156"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="47d13-101">Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="47d13-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="47d13-102">`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`Přepínač kompatibility, který byl představen v .NET Framework 4.7.2, není podporován v model Windows Forms v rozhraní .NET Core nebo .net 5,0 a novějším.</span><span class="sxs-lookup"><span data-stu-id="47d13-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="47d13-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="47d13-103">Change description</span></span>

<span data-ttu-id="47d13-104">Počínaje .NET Framework 4.7.2, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` přepínač kompatibility umožňuje vývojářům, aby se odhlásili od nového chování <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> vlastnosti, který nyní vrací odkaz na správu zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="47d13-104">Starting with .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="47d13-105">Předchozí chování vlastnosti bylo vráceno `null` .</span><span class="sxs-lookup"><span data-stu-id="47d13-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="47d13-106">Další informace naleznete v tématu [ \<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="47d13-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="47d13-107">V rozhraní .NET Core a .NET 5,0 a novějším není `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="47d13-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="47d13-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="47d13-108">Version introduced</span></span>

<span data-ttu-id="47d13-109">3.0</span><span class="sxs-lookup"><span data-stu-id="47d13-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="47d13-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="47d13-110">Recommended action</span></span>

<span data-ttu-id="47d13-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="47d13-111">Remove the switch.</span></span> <span data-ttu-id="47d13-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="47d13-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="47d13-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="47d13-113">Category</span></span>

<span data-ttu-id="47d13-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="47d13-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="47d13-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="47d13-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
