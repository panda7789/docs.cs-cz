---
ms.openlocfilehash: e128bdb5735b3e4844356ad4807cc092f6f2b105
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062419"
---
### <a name="no-aw-suffix-probing-on-non-windows-platforms"></a><span data-ttu-id="8151a-101">Žádná přípona A/W na platformách jiných než Windows</span><span class="sxs-lookup"><span data-stu-id="8151a-101">No A/W suffix probing on non-Windows platforms</span></span>

<span data-ttu-id="8151a-102">Rozhraní .NET Runtime již nepřidává `A` `W` příponu ani pro export názvů funkcí během zjišťování pro volání nespravovaných platforem na jiných platformách než Windows.</span><span class="sxs-lookup"><span data-stu-id="8151a-102">The .NET runtimes no longer add an `A` or `W` suffix to function export names during probing for P/Invokes on non-Windows platforms.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8151a-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="8151a-103">Version introduced</span></span>

<span data-ttu-id="8151a-104">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="8151a-104">5.0 Preview 4</span></span>

#### <a name="change-description"></a><span data-ttu-id="8151a-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="8151a-105">Change description</span></span>

<span data-ttu-id="8151a-106">[Systém Windows má konvenci](/windows/win32/intl/conventions-for-function-prototypes) pro přidání `A` `W` přípony nebo pro Windows SDK názvů funkcí, které odpovídají znakové stránce systému Windows a verzím Unicode v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8151a-106">[Windows has a convention](/windows/win32/intl/conventions-for-function-prototypes) of adding an `A` or `W` suffix to Windows SDK function names, which correspond to the Windows code page and Unicode versions, respectively.</span></span>

<span data-ttu-id="8151a-107">V předchozích verzích rozhraní .NET `A` `W` během zjišťování exportu pro volání nespravovaného objektu *na všech platformách*přidá do názvu exportu příponu nebo (CoreCLR).</span><span class="sxs-lookup"><span data-stu-id="8151a-107">In previous versions of .NET, both the CoreCLR and Mono runtimes add an `A` or `W` suffix to the export name during export discovery for P/Invokes *on all platforms*.</span></span>

<span data-ttu-id="8151a-108">V rozhraní .NET 5,0 a novějších verzích `A` `W` je přípona nebo přidána do názvu exportu během zjišťování exportu *pouze v systému Windows*.</span><span class="sxs-lookup"><span data-stu-id="8151a-108">In .NET 5.0 and later versions, an `A` or `W` suffix is added to the export name during export discovery *on Windows only*.</span></span> <span data-ttu-id="8151a-109">Na platformách UNIX není přípona přidána.</span><span class="sxs-lookup"><span data-stu-id="8151a-109">On Unix platforms, the suffix is not added.</span></span> <span data-ttu-id="8151a-110">Sémantika obou běhových prostředí v platformě Windows zůstane beze změny.</span><span class="sxs-lookup"><span data-stu-id="8151a-110">The semantics of both runtimes on the Windows platform remain unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8151a-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="8151a-111">Reason for change</span></span>

<span data-ttu-id="8151a-112">Tato změna byla provedena za účelem zjednodušení zjišťování pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="8151a-112">This change was made to simplify cross-platform probing.</span></span> <span data-ttu-id="8151a-113">Má se za to, že by nedocházelo k tomu, že platformy jiné než Windows neobsahují tuto sémantickou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="8151a-113">It's overhead that shouldn't be incurred, given that non-Windows platforms don't contain this semantic.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8151a-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="8151a-114">Recommended action</span></span>

<span data-ttu-id="8151a-115">Chcete-li tuto změnu zmírnit, můžete ručně přidat požadovanou příponu na platformy jiných výrobců než Windows.</span><span class="sxs-lookup"><span data-stu-id="8151a-115">To mitigate the change, you can manually add the desired suffix on non-Windows platforms.</span></span> <span data-ttu-id="8151a-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8151a-116">For example:</span></span>

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

#### <a name="category"></a><span data-ttu-id="8151a-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="8151a-117">Category</span></span>

<span data-ttu-id="8151a-118">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="8151a-118">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8151a-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8151a-119">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

-->
