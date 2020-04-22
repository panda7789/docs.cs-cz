---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021789"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="fd42e-101">Změna výchozí hodnoty useShellExecute</span><span class="sxs-lookup"><span data-stu-id="fd42e-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="fd42e-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>má výchozí hodnotu `false` na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd42e-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="fd42e-103">V rozhraní .NET Framework `true`je jeho výchozí hodnota .</span><span class="sxs-lookup"><span data-stu-id="fd42e-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fd42e-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="fd42e-104">Change description</span></span>

<span data-ttu-id="fd42e-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>umožňuje spustit aplikaci přímo, například s `Process.Start("mspaint.exe")` kódem, jako je například spuštění programu Malování.</span><span class="sxs-lookup"><span data-stu-id="fd42e-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="fd42e-106">Umožňuje také nepřímo spustit přidruženou aplikaci, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true`pokud je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="fd42e-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="fd42e-107">V rozhraní .NET Framework <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> je `true`výchozí hodnota pro `Process.Start("mytextfile.txt")` , což znamená, že kód, jako je spuštění programu Poznámkový blok, pokud jste k tomuto editoru přidružili soubory *TXT.*</span><span class="sxs-lookup"><span data-stu-id="fd42e-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="fd42e-108">Chcete-li zabránit nepřímému spuštění aplikace v <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> rozhraní `false`.NET Framework, musíte explicitně nastavit .</span><span class="sxs-lookup"><span data-stu-id="fd42e-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="fd42e-109">Na .NET Core je <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`výchozí hodnota pro .</span><span class="sxs-lookup"><span data-stu-id="fd42e-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="fd42e-110">To znamená, že ve výchozím nastavení nejsou `Process.Start`přidružené aplikace spuštěny při volání .</span><span class="sxs-lookup"><span data-stu-id="fd42e-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="fd42e-111">Tato změna byla zavedena v .NET Core z důvodů výkonu.</span><span class="sxs-lookup"><span data-stu-id="fd42e-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="fd42e-112">Obvykle se <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> používá ke spuštění aplikace přímo.</span><span class="sxs-lookup"><span data-stu-id="fd42e-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="fd42e-113">Spuštění aplikace přímo nemusí zahrnovat prostředí Windows a vznikají související náklady na výkon.</span><span class="sxs-lookup"><span data-stu-id="fd42e-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="fd42e-114">Chcete-li tento výchozí případ urychlit, změní <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> jádro `false`.NET výchozí hodnotu na .</span><span class="sxs-lookup"><span data-stu-id="fd42e-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="fd42e-115">Můžete se přihlásit do pomalejší cesty, pokud ji potřebujete.</span><span class="sxs-lookup"><span data-stu-id="fd42e-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fd42e-116">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="fd42e-116">Version introduced</span></span>

<span data-ttu-id="fd42e-117">2.1</span><span class="sxs-lookup"><span data-stu-id="fd42e-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="fd42e-118">V dřívějších verzích rozhraní `UseShellExecute` .NET Core nebyla implementována pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="fd42e-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fd42e-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="fd42e-119">Recommended action</span></span>

<span data-ttu-id="fd42e-120">Pokud vaše aplikace závisí na staré <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> chování, `true` volání <xref:System.Diagnostics.ProcessStartInfo> s nastavenou na objekt.</span><span class="sxs-lookup"><span data-stu-id="fd42e-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="fd42e-121">Kategorie</span><span class="sxs-lookup"><span data-stu-id="fd42e-121">Category</span></span>

<span data-ttu-id="fd42e-122">Základní knihovny .NET</span><span class="sxs-lookup"><span data-stu-id="fd42e-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fd42e-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="fd42e-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
