---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181730"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="5c7c9-101">Přepínač kompatibility. System. Windows. Forms. UseLegacyContextMenuStripSourceControlValue není podporovaný.</span><span class="sxs-lookup"><span data-stu-id="5c7c9-101">Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="5c7c9-102">Přepínač `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` kompatibility, který byl představen v .NET Framework 4.7.2, není podporován v model Windows Forms .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="5c7c9-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5c7c9-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="5c7c9-103">Change description</span></span>

<span data-ttu-id="5c7c9-104">Počínaje .NET Framework 4.7.2, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` přepínač kompatibility umožňuje vývojářům, aby se odhlásili od nového chování <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> vlastnosti, který nyní vrací odkaz na správu zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="5c7c9-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="5c7c9-105">Předchozí chování vlastnosti bylo vráceno `null`.</span><span class="sxs-lookup"><span data-stu-id="5c7c9-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="5c7c9-106">Další informace naleznete v tématu [ \<AppContextSwitchOverrides > element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="5c7c9-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="5c7c9-107">V rozhraní .NET Core `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` není přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="5c7c9-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5c7c9-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5c7c9-108">Version introduced</span></span>

<span data-ttu-id="5c7c9-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="5c7c9-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5c7c9-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5c7c9-110">Recommended action</span></span>

<span data-ttu-id="5c7c9-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="5c7c9-111">Remove the switch.</span></span> <span data-ttu-id="5c7c9-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="5c7c9-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="5c7c9-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5c7c9-113">Category</span></span>

<span data-ttu-id="5c7c9-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c7c9-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5c7c9-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5c7c9-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
