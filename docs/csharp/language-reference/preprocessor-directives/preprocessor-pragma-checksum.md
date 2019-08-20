---
title: '#pragma Checksum – C# reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 4103b6262fc5085c1204f423a36c9c5c2053b497
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605649"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="d53ea-102">#pragma – kontrolní součet (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d53ea-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="d53ea-103">Vygeneruje kontrolní součty pro zdrojové soubory, které pomáhají s laděním ASP.NET stránek.</span><span class="sxs-lookup"><span data-stu-id="d53ea-103">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d53ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d53ea-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="d53ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d53ea-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="d53ea-106">Název souboru, který vyžaduje monitorování pro změny nebo aktualizace.</span><span class="sxs-lookup"><span data-stu-id="d53ea-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="d53ea-107">Globálně jedinečný identifikátor (GUID) pro algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="d53ea-107">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="d53ea-108">Řetězec hexadecimálních číslic reprezentujících bajty kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="d53ea-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="d53ea-109">Musí se jednat o sudý počet šestnáctkových číslic.</span><span class="sxs-lookup"><span data-stu-id="d53ea-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="d53ea-110">Lichý počet číslic má za následek upozornění v době kompilace a direktiva se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="d53ea-110">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d53ea-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d53ea-111">Remarks</span></span>  
 <span data-ttu-id="d53ea-112">Ladicí program sady Visual Studio používá kontrolní součet k tomu, aby se ujistil, že vždy najde správný zdroj.</span><span class="sxs-lookup"><span data-stu-id="d53ea-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="d53ea-113">Kompilátor vypočítá kontrolní součet pro zdrojový soubor a poté vygeneruje výstup do souboru programu databáze (PDB).</span><span class="sxs-lookup"><span data-stu-id="d53ea-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="d53ea-114">Ladicí program pak pomocí PDB porovná s kontrolním součtem, který počítá pro zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="d53ea-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="d53ea-115">Toto řešení nefunguje pro projekty ASP.NET, protože vypočtený kontrolní součet je pro generovaný zdrojový soubor, nikoli soubor. aspx.</span><span class="sxs-lookup"><span data-stu-id="d53ea-115">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="d53ea-116">Pro vyřešení tohoto problému `#pragma checksum` poskytuje podporu kontrolního součtu pro stránky ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d53ea-116">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="d53ea-117">Při vytváření projektu ASP.NET ve vizuálu C#obsahuje generovaný zdrojový soubor kontrolní součet pro soubor. aspx, ze kterého se zdroj vygeneroval.</span><span class="sxs-lookup"><span data-stu-id="d53ea-117">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="d53ea-118">Kompilátor potom tyto informace zapíše do souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="d53ea-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="d53ea-119">Pokud kompilátor v souboru nenalezne žádnou `#pragma checksum` direktivu, vypočítá kontrolní součet a zapíše hodnotu do souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="d53ea-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d53ea-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="d53ea-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d53ea-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d53ea-121">See also</span></span>

- [<span data-ttu-id="d53ea-122">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="d53ea-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d53ea-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d53ea-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d53ea-124">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="d53ea-124">C# Preprocessor Directives</span></span>](./index.md)
