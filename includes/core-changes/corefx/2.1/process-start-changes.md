---
ms.openlocfilehash: 58cb3580c8701773452ae8338f036a94bbee80c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449390"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="dca22-101">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="dca22-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="dca22-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> má výchozí hodnotu `false` v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dca22-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="dca22-103">V .NET Framework je výchozí hodnota `true`.</span><span class="sxs-lookup"><span data-stu-id="dca22-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="dca22-104">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="dca22-104">Change description</span></span>

<span data-ttu-id="dca22-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> umožňuje spustit aplikaci přímo, například pomocí kódu, jako je například `Process.Start("mspaint.exe")`, který spouští funkci malování.</span><span class="sxs-lookup"><span data-stu-id="dca22-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="dca22-106">Umožňuje vám také nepřímo spustit přidruženou aplikaci, pokud je <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> nastaveno na `true`.</span><span class="sxs-lookup"><span data-stu-id="dca22-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="dca22-107">V .NET Framework je výchozí hodnota pro <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true`, což znamená, že kód, jako je například `Process.Start("mytextfile.txt")`, by spouštěl Poznámkový blok, pokud jste přidružil soubory *. txt* pomocí tohoto editoru.</span><span class="sxs-lookup"><span data-stu-id="dca22-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="dca22-108">Chcete-li zabránit nepřímo spustit aplikaci na .NET Framework, je nutné explicitně nastavit <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> na `false`.</span><span class="sxs-lookup"><span data-stu-id="dca22-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="dca22-109">V .NET Core je výchozí hodnota pro <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`.</span><span class="sxs-lookup"><span data-stu-id="dca22-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="dca22-110">To znamená, že ve výchozím nastavení nejsou přidružené aplikace spouštěny při volání `Process.Start`.</span><span class="sxs-lookup"><span data-stu-id="dca22-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="dca22-111">Tato změna byla představena v rozhraní .NET Core z důvodů výkonu.</span><span class="sxs-lookup"><span data-stu-id="dca22-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="dca22-112">Obvykle se <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> používá ke spuštění aplikace přímo.</span><span class="sxs-lookup"><span data-stu-id="dca22-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="dca22-113">Přímým spouštěním aplikace není nutné zahrnovat prostředí systému Windows a získat související náklady na výkon.</span><span class="sxs-lookup"><span data-stu-id="dca22-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="dca22-114">Aby byl tento výchozí případ rychlejší, .NET Core změní výchozí hodnotu <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> na `false`.</span><span class="sxs-lookup"><span data-stu-id="dca22-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="dca22-115">Pokud ho budete potřebovat, můžete se na pomalejší cestu rozhodnout.</span><span class="sxs-lookup"><span data-stu-id="dca22-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dca22-116">Představená verze</span><span class="sxs-lookup"><span data-stu-id="dca22-116">Version introduced</span></span>

<span data-ttu-id="dca22-117">2.1</span><span class="sxs-lookup"><span data-stu-id="dca22-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="dca22-118">V dřívějších verzích rozhraní .NET Core `UseShellExecute` nebyl implementován pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="dca22-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dca22-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="dca22-119">Recommended action</span></span>

<span data-ttu-id="dca22-120">Pokud vaše aplikace spoléhá na staré chování, zavolejte <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> s <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> nastavenou na `true` na objektu <xref:System.Diagnostics.ProcessStartInfo>.</span><span class="sxs-lookup"><span data-stu-id="dca22-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="dca22-121">Kategorie</span><span class="sxs-lookup"><span data-stu-id="dca22-121">Category</span></span>

<span data-ttu-id="dca22-122">CoreFx</span><span class="sxs-lookup"><span data-stu-id="dca22-122">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dca22-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="dca22-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
