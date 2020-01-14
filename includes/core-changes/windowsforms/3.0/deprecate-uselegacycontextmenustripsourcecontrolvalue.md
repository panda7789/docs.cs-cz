---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937079"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="05735-101">Přepínač kompatibility UseLegacyContextMenuStripSourceControlValue se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="05735-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="05735-102">V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`, který byl představen v .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="05735-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="05735-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="05735-103">Change description</span></span>

<span data-ttu-id="05735-104">Počínaje .NET Framework 4.7.2, přepínač kompatibility `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` umožňuje vývojářům, aby se odhlásili od nového chování vlastnosti <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>, která nyní vrací odkaz na správu zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="05735-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="05735-105">Předchozí chování vlastnosti vrátilo `null`.</span><span class="sxs-lookup"><span data-stu-id="05735-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="05735-106">Další informace naleznete v tématu [\<AppContextSwitchOverrides > elementu](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="05735-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="05735-107">V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` podporován.</span><span class="sxs-lookup"><span data-stu-id="05735-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="05735-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="05735-108">Version introduced</span></span>

<span data-ttu-id="05735-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="05735-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="05735-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="05735-110">Recommended action</span></span>

<span data-ttu-id="05735-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="05735-111">Remove the switch.</span></span> <span data-ttu-id="05735-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="05735-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="05735-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="05735-113">Category</span></span>

<span data-ttu-id="05735-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05735-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="05735-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="05735-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
