---
ms.openlocfilehash: 9c9c4ec55143ef991e9b69a389e0f3368263bb4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614555"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a><span data-ttu-id="3d976-101">NullReferenceException v kódu pro zpracování výjimek z ImageSourceConverter. ConvertFrom</span><span class="sxs-lookup"><span data-stu-id="3d976-101">NullReferenceException in exception handling code from ImageSourceConverter.ConvertFrom</span></span>

#### <a name="details"></a><span data-ttu-id="3d976-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3d976-102">Details</span></span>

<span data-ttu-id="3d976-103">Chyba v kódu zpracování výjimky pro <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> způsobila nesprávnou <xref:System.NullReferenceException?displayProperty=fullName> výjimku namísto zamýšlené výjimky ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> nebo <xref:System.IO.FileNotFoundException?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="3d976-103">An error in the exception handling code for <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> caused an incorrect <xref:System.NullReferenceException?displayProperty=fullName> to be thrown instead of the intended exception ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> or <xref:System.IO.FileNotFoundException?displayProperty=fullName>).</span></span> <span data-ttu-id="3d976-104">Tato změna opravuje tuto chybu tak, aby metoda nyní vyvolala správnou výjimku.</span><span class="sxs-lookup"><span data-stu-id="3d976-104">This change corrects that error so that the method now throws the right exception.</span></span> <p/><span data-ttu-id="3d976-105">Ve výchozím nastavení všechny aplikace cílené .NET Framework 4.6.2 a starší pokračují <xref:System.NullReferenceException?displayProperty=fullName> v vyvolání kompatibility.</span><span class="sxs-lookup"><span data-stu-id="3d976-105">By default all applications targeting .NET Framework 4.6.2 and earlier continue to throw <xref:System.NullReferenceException?displayProperty=fullName> for compatibility.</span></span> <span data-ttu-id="3d976-106">Vývojáři, kteří cílí na .NET Framework 4,7 a vyšší, by měli vidět správné výjimky.</span><span class="sxs-lookup"><span data-stu-id="3d976-106">Developers targeting .NET Framework 4.7 and above should see the right exceptions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3d976-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="3d976-107">Suggestion</span></span>

<span data-ttu-id="3d976-108">Vývojáři, kteří se chtějí vrátit k získání, <xref:System.NullReferenceException?displayProperty=fullName> když cílí na .NET Framework 4,7 nebo novější, můžou do souboru App.config aplikace přidat nebo sloučit následující:</span><span class="sxs-lookup"><span data-stu-id="3d976-108">Developers who wish to revert to getting <xref:System.NullReferenceException?displayProperty=fullName> when targeting .NET Framework 4.7 or later can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="3d976-109">Name</span><span class="sxs-lookup"><span data-stu-id="3d976-109">Name</span></span>    | <span data-ttu-id="3d976-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3d976-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3d976-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3d976-111">Scope</span></span>   | <span data-ttu-id="3d976-112">Edge</span><span class="sxs-lookup"><span data-stu-id="3d976-112">Edge</span></span>        |
| <span data-ttu-id="3d976-113">Verze</span><span class="sxs-lookup"><span data-stu-id="3d976-113">Version</span></span> | <span data-ttu-id="3d976-114">4,7</span><span class="sxs-lookup"><span data-stu-id="3d976-114">4.7</span></span>         |
| <span data-ttu-id="3d976-115">Typ</span><span class="sxs-lookup"><span data-stu-id="3d976-115">Type</span></span>    | <span data-ttu-id="3d976-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="3d976-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3d976-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3d976-117">Affected APIs</span></span>

- <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType>
