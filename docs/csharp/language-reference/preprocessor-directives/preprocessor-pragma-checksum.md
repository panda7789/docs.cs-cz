---
title: '#Direktiva pragma kontrolní součet (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37e06d97b082ba6de75d8efa81723442403e39be
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="bcb61-102">#pragma – kontrolní součet (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bcb61-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="bcb61-103">Generuje kontrolní součty pro zdrojové soubory, které pomáhají s laděním [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="bcb61-103">Generates checksums for source files to aid with debugging [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcb61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcb61-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcb61-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcb61-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="bcb61-106">Název souboru, který vyžaduje monitorování pro změny nebo aktualizace.</span><span class="sxs-lookup"><span data-stu-id="bcb61-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="bcb61-107">Globálně jedinečný identifikátor (GUID) pro algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="bcb61-107">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="bcb61-108">Řetězec šestnáctkových číslic představující bajtů kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="bcb61-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="bcb61-109">Musí být sudé číslo šestnáctkových číslic.</span><span class="sxs-lookup"><span data-stu-id="bcb61-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="bcb61-110">Lichý počet číslic za následek upozornění kompilaci a direktiva se ignorují.</span><span class="sxs-lookup"><span data-stu-id="bcb61-110">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcb61-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcb61-111">Remarks</span></span>  
 <span data-ttu-id="bcb61-112">Ladicí program Visual Studio používá kontrolní součet a ujistěte se, že vždy vyhledá správné zdroje.</span><span class="sxs-lookup"><span data-stu-id="bcb61-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="bcb61-113">Kompilátor vypočítá kontrolní součet u zdrojového souboru a potom vydá výstup do souboru databáze (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="bcb61-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="bcb61-114">Ladicí program pak použije PDB pro porovnání, které vrací pro zdrojový soubor kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="bcb61-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="bcb61-115">Toto řešení nefunguje pro [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projekty, protože počítaný kontrolního součtu je vytvořeném zdrojovém souboru, nikoli soubor .aspx.</span><span class="sxs-lookup"><span data-stu-id="bcb61-115">This solution does not work for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="bcb61-116">Chcete-li vyřešit tento problém `#pragma checksum` poskytuje podporu kontrolního součtu pro [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="bcb61-116">To address this problem, `#pragma checksum` provides checksum support for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
 <span data-ttu-id="bcb61-117">Při vytváření [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projekt v jazyce Visual C#, vytvořeném zdrojovém souboru obsahuje kontrolního součtu pro soubor .aspx, ze které se generuje zdroji.</span><span class="sxs-lookup"><span data-stu-id="bcb61-117">When you create an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="bcb61-118">Kompilátor pak zapíše tyto informace do souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="bcb61-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="bcb61-119">Pokud ne, zaznamená kompilátor `#pragma checksum` direktivy v souboru, se vypočítá kontrolního součtu a zapisuje do souboru PDB hodnota.</span><span class="sxs-lookup"><span data-stu-id="bcb61-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcb61-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcb61-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bcb61-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcb61-121">See Also</span></span>  
 [<span data-ttu-id="bcb61-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bcb61-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bcb61-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bcb61-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bcb61-124">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="bcb61-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
