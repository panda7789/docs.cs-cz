---
ms.openlocfilehash: 811b1a91169eeebfa056d9ecdb07d342d3b32d85
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615717"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a><span data-ttu-id="312f2-101">Icon. ToBitmap úspěšně převádí ikony s snímky PNG na bitmapové objekty.</span><span class="sxs-lookup"><span data-stu-id="312f2-101">Icon.ToBitmap successfully converts icons with PNG frames into Bitmap objects</span></span>

#### <a name="details"></a><span data-ttu-id="312f2-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="312f2-102">Details</span></span>

<span data-ttu-id="312f2-103">Počínaje aplikacemi, které cílí na .NET Framework 4,6, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Metoda úspěšně převede ikony s snímky PNG na bitmapové objekty.</span><span class="sxs-lookup"><span data-stu-id="312f2-103">Starting with the apps that target the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into Bitmap objects.</span></span><p/><span data-ttu-id="312f2-104">V aplikacích, které cílí na .NET Framework 4.5.2 a starší verze, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> vyvolá metoda <xref:System.ArgumentOutOfRangeException> výjimku, pokud objekt Icon obsahuje snímky PNG.</span><span class="sxs-lookup"><span data-stu-id="312f2-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the  <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the Icon object has PNG frames.</span></span><p/><span data-ttu-id="312f2-105">Tato změna ovlivní aplikace, které jsou znovu zkompilovány pro cílení na .NET Framework 4,6 a které implementují speciální zpracování pro <xref:System.ArgumentOutOfRangeException> výjimku, která je vyvolána, když objekt Icon má snímky PNG.</span><span class="sxs-lookup"><span data-stu-id="312f2-105">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an Icon object has PNG frames.</span></span> <span data-ttu-id="312f2-106">Při spuštění pod .NET Framework 4,6 je převod úspěšný, <xref:System.ArgumentOutOfRangeException> již není vyvolán, a proto obslužná rutina výjimky již není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="312f2-106">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="312f2-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="312f2-107">Suggestion</span></span>

<span data-ttu-id="312f2-108">Pokud je toto chování nežádoucí, můžete předchozí chování zachovat přidáním následujícího elementu do `<runtime>` části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="312f2-108">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the `<runtime>` section of your app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>

<span data-ttu-id="312f2-109">Pokud app.config soubor již obsahuje `AppContextSwitchOverrides` element, nová hodnota by měla být sloučena s atributem value takto:</span><span class="sxs-lookup"><span data-stu-id="312f2-109">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the value attribute like this:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="312f2-110">Name</span><span class="sxs-lookup"><span data-stu-id="312f2-110">Name</span></span>    | <span data-ttu-id="312f2-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="312f2-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="312f2-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="312f2-112">Scope</span></span>   | <span data-ttu-id="312f2-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="312f2-113">Minor</span></span>       |
| <span data-ttu-id="312f2-114">Verze</span><span class="sxs-lookup"><span data-stu-id="312f2-114">Version</span></span> | <span data-ttu-id="312f2-115">4.6</span><span class="sxs-lookup"><span data-stu-id="312f2-115">4.6</span></span>         |
| <span data-ttu-id="312f2-116">Typ</span><span class="sxs-lookup"><span data-stu-id="312f2-116">Type</span></span>    | <span data-ttu-id="312f2-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="312f2-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="312f2-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="312f2-118">Affected APIs</span></span>

- <xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType>
