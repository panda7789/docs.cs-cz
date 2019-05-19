---
title: '#kontrolního součtu direktivy pragma - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 36e5602f0a0b872a4aa6cdac64b49b1d1c708795
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877525"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="2e097-102">#pragma – kontrolní součet (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2e097-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="2e097-103">Generuje kontrolní součty zdrojových souborů pro usnadnění ladění stránek ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2e097-103">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e097-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e097-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e097-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e097-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="2e097-106">Název souboru, který vyžaduje monitorování pro změny nebo aktualizace.</span><span class="sxs-lookup"><span data-stu-id="2e097-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="2e097-107">Globálně jedinečný identifikátor (GUID) pro algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="2e097-107">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="2e097-108">Řetězec šestnáctkových číslic představující počet bajtů kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="2e097-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="2e097-109">Musí být sudý počet šestnáctkových číslic.</span><span class="sxs-lookup"><span data-stu-id="2e097-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="2e097-110">Lichý počet číslic za následek upozornění kompilace a direktiva se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="2e097-110">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e097-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e097-111">Remarks</span></span>  
 <span data-ttu-id="2e097-112">Ladicí program sady Visual Studio používá kontrolní součet abyste měli jistotu, že vždy najde správný zdroj.</span><span class="sxs-lookup"><span data-stu-id="2e097-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="2e097-113">Kompilátor vypočítá kontrolního součtu pro zdrojový soubor a potom generuje výstup do souboru databáze (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="2e097-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="2e097-114">Ladicí program použije soubor PDB pro porovnání, která vypočítá pro zdrojový soubor kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="2e097-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="2e097-115">Toto řešení pro projekty ASP.NET, nefunguje, protože počítaný kontrolního součtu je vytvořeném zdrojovém souboru, nikoli soubor .aspx.</span><span class="sxs-lookup"><span data-stu-id="2e097-115">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="2e097-116">Chcete-li vyřešit tento problém `#pragma checksum` poskytuje podporu kontrolního součtu pro stránky ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2e097-116">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="2e097-117">Při vytváření projektu aplikace ASP.NET ve Vizuálu C#, obsahuje kontrolní součet souboru .aspx, ze kterého se vygeneruje zdroj vytvořeném zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="2e097-117">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="2e097-118">Kompilátor pak tyto informace zapisuje do souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="2e097-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="2e097-119">Pokud kompilátor narazí ne `#pragma checksum` direktivy v souboru, se vypočítá kontrolního součtu a zapíše hodnoty do souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="2e097-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e097-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e097-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e097-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e097-121">See also</span></span>

- [<span data-ttu-id="2e097-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2e097-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="2e097-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2e097-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2e097-124">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="2e097-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
