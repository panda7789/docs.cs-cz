---
ms.openlocfilehash: d21b2e092d460fdfc367d0f490228ed44ad5c6cc
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365640"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="ccde4-101">Integrovaná podpora WinRT se odebere z rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="ccde4-101">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="ccde4-102">Odeberou se Vestavěná podpora pro využití rozhraní API pro [Windows Runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="ccde4-102">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ccde4-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="ccde4-103">Version introduced</span></span>

<span data-ttu-id="ccde4-104">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="ccde4-104">5.0 Preview 6</span></span>

#### <a name="change-description"></a><span data-ttu-id="ccde4-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="ccde4-105">Change description</span></span>

<span data-ttu-id="ccde4-106">Dřív CoreCLR mohl využívat [soubory Windows metadata (WinMD)](/uwp/winrt-cref/winmd-files) k aktivnímu a využívání typů WinRT.</span><span class="sxs-lookup"><span data-stu-id="ccde4-106">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="ccde4-107">Od rozhraní .NET 5,0 nemůže CoreCLR nadále využívat soubory WinMD přímo.</span><span class="sxs-lookup"><span data-stu-id="ccde4-107">Starting in .NET 5.0, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="ccde4-108">Pokud se pokusíte odkazovat na nepodporované sestavení, získáte <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="ccde4-108">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="ccde4-109">Pokud aktivujete třídu WinRT, získáte <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="ccde4-109">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="ccde4-110">Tato změna byla provedena z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="ccde4-110">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="ccde4-111">Takže WinRT se dá vyvíjet a zdokonalovat odděleně od .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="ccde4-111">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="ccde4-112">Pro symetrie se systémy spolupráce, které jsou k dispozici pro jiné operační systémy, jako jsou iOS a Android.</span><span class="sxs-lookup"><span data-stu-id="ccde4-112">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="ccde4-113">Pro využití dalších funkcí rozhraní .NET, jako jsou funkce C#, propojení mezilehlého jazyka (IL) a kompilace před časem (AOT).</span><span class="sxs-lookup"><span data-stu-id="ccde4-113">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="ccde4-114">Pro zjednodušení základu kódu .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="ccde4-114">To simplify the .NET runtime codebase.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ccde4-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="ccde4-115">Recommended action</span></span>

- <span data-ttu-id="ccde4-116">Odeberte odkazy na [balíček Microsoft. Windows. SDK. Contracts](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) a nahraďte je odkazy na [balíček Microsoft.Windows.SDK.NET](https://www.nuget.org/packages/microsoft.windows.sdk.net).</span><span class="sxs-lookup"><span data-stu-id="ccde4-116">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) and replace them with references to the [Microsoft.Windows.SDK.NET package](https://www.nuget.org/packages/microsoft.windows.sdk.net).</span></span>

- <span data-ttu-id="ccde4-117">Použijte řetězec nástroje [C#/WinRT](/windows/uwp/csharp-winrt/) ke generování nebo přizpůsobení rozhraní API a typů WinRT v rozhraní .NET 5,0 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="ccde4-117">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types in .NET 5.0 and later versions.</span></span>

#### <a name="category"></a><span data-ttu-id="ccde4-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="ccde4-118">Category</span></span>

<span data-ttu-id="ccde4-119">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="ccde4-119">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ccde4-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ccde4-120">Affected APIs</span></span>

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
