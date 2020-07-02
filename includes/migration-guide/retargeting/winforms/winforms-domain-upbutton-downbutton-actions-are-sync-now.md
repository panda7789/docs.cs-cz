---
ms.openlocfilehash: f75a652f15be6b0d184db20dc5cd8aafd80539fe
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614581"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a><span data-ttu-id="7685e-101">DataGridView a akce DownButton v doméně se teď synchronizují.</span><span class="sxs-lookup"><span data-stu-id="7685e-101">WinForm's Domain upbutton and downbutton actions are in sync now</span></span>

#### <a name="details"></a><span data-ttu-id="7685e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7685e-102">Details</span></span>

<span data-ttu-id="7685e-103">V .NET Framework 4.7.1 a předchozích verzích <xref:System.Windows.Forms.DomainUpDown> se akce ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ignoruje, když je přítomen text ovládacího prvku a vývojář je <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> před použitím akce nutný k použití akce na ovládacím prvku <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7685e-103">In the .NET Framework 4.7.1 and previous versions the <xref:System.Windows.Forms.DomainUpDown> control's <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action is ignored when control text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before using <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="7685e-104">Počínaje .NET Framework 4.7.2 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akce a pracují nezávisle v tomto scénáři a zůstanou synchronizované.</span><span class="sxs-lookup"><span data-stu-id="7685e-104">Starting with the .NET Framework 4.7.2 both the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions work independently in this scenario and remain in sync.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7685e-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="7685e-105">Suggestion</span></span>

<span data-ttu-id="7685e-106">Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4.7.2 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="7685e-106">In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="7685e-107">Aplikace může tyto změny využít v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="7685e-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="7685e-108">Zkompiluje se znovu a zacílí na .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="7685e-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="7685e-109">Tato změna je ve výchozím nastavení povolená v aplikacích model Windows Forms, které cílí na .NET Framework 4.7.2 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="7685e-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="7685e-110">Výslovný se starším chováním posouvání přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do `<runtime>` oddílu konfiguračního souboru aplikace a jeho nastavením na `false` , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="7685e-110">It opts out of the legacy scrolling behavior by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="7685e-111">Name</span><span class="sxs-lookup"><span data-stu-id="7685e-111">Name</span></span>    | <span data-ttu-id="7685e-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7685e-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7685e-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="7685e-113">Scope</span></span>   | <span data-ttu-id="7685e-114">Edge</span><span class="sxs-lookup"><span data-stu-id="7685e-114">Edge</span></span>        |
| <span data-ttu-id="7685e-115">Verze</span><span class="sxs-lookup"><span data-stu-id="7685e-115">Version</span></span> | <span data-ttu-id="7685e-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="7685e-116">4.7.2</span></span>       |
| <span data-ttu-id="7685e-117">Typ</span><span class="sxs-lookup"><span data-stu-id="7685e-117">Type</span></span>    | <span data-ttu-id="7685e-118">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="7685e-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7685e-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7685e-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
