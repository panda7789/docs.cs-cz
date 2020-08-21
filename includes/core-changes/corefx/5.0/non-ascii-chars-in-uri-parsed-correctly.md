---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720184"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a><span data-ttu-id="56576-101">Cesty URI bez znaků, které nejsou ASCII, se v systému UNIX analyzují správně</span><span class="sxs-lookup"><span data-stu-id="56576-101">URI paths with non-ASCII characters parse correctly on Unix</span></span>

<span data-ttu-id="56576-102">Ve třídě byla opravena chyba <xref:System.Uri?displayProperty=fullName> tak, že absolutní cesty URI, které obsahují znaky jiné než ASCII, se teď na platformách UNIX analyzují správně.</span><span class="sxs-lookup"><span data-stu-id="56576-102">A bug was fixed in the <xref:System.Uri?displayProperty=fullName> class such that absolute URI paths that contain non-ASCII characters now parse correctly on Unix platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="56576-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="56576-103">Change description</span></span>

<span data-ttu-id="56576-104">V předchozích verzích rozhraní .NET se absolutní cesty URI, které obsahují znaky jiné než ASCII, nesprávně analyzují na platformách UNIX a segmenty cesty jsou duplicitní.</span><span class="sxs-lookup"><span data-stu-id="56576-104">In previous versions of .NET, absolute URI paths that contain non-ASCII characters are parsed incorrectly on Unix platforms, and segments of the path are duplicated.</span></span> <span data-ttu-id="56576-105">(Absolutní cesty jsou ty, které začínají znakem "/".) Problém s analýzou byl vyřešen pro .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="56576-105">(Absolute paths are those that start with "/".) The parsing issue has been fixed for .NET 5.0.</span></span> <span data-ttu-id="56576-106">Pokud přejdete z předchozí verze rozhraní .NET na .NET 5,0 nebo novější, získáte různé hodnoty vytvářené pomocí <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> , <xref:System.Uri.ToString?displayProperty=nameWithType> a dalších <xref:System.Uri> členů.</span><span class="sxs-lookup"><span data-stu-id="56576-106">If you move from a previous version of .NET to .NET 5.0 or later, you'll get different values produced by <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType>, and other <xref:System.Uri> members.</span></span>

<span data-ttu-id="56576-107">Při spuštění v systému UNIX zvažte výstup následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="56576-107">Consider the output of the following code when run on Unix.</span></span>

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

<span data-ttu-id="56576-108">Výstup na předchozí verzi rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="56576-108">Output on previous .NET version:</span></span>

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

<span data-ttu-id="56576-109">Výstup v rozhraní .NET 5,0 nebo novější verzi:</span><span class="sxs-lookup"><span data-stu-id="56576-109">Output on .NET 5.0 or later version:</span></span>

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

#### <a name="version-introduced"></a><span data-ttu-id="56576-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="56576-110">Version introduced</span></span>

<span data-ttu-id="56576-111">5,0</span><span class="sxs-lookup"><span data-stu-id="56576-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="56576-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="56576-112">Recommended action</span></span>

<span data-ttu-id="56576-113">Pokud máte kód, který očekává a účty pro duplicitní segmenty cesty, můžete tento kód odebrat.</span><span class="sxs-lookup"><span data-stu-id="56576-113">If you have code that expects and accounts for the duplicated path segments, you can remove that code.</span></span>

#### <a name="category"></a><span data-ttu-id="56576-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="56576-114">Category</span></span>

<span data-ttu-id="56576-115">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="56576-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56576-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="56576-116">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
