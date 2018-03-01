---
title: "#Direktiva pragma kontrolní součet (referenční dokumentace jazyka C#)"
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0604a559be25c300fcdc6041975306b465fc595f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="57769-102">#pragma – kontrolní součet (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="57769-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="57769-103">Generuje kontrolní součty pro zdrojové soubory, které pomáhají s laděním [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="57769-103">Generates checksums for source files to aid with debugging [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57769-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57769-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57769-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57769-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="57769-106">Název souboru, který vyžaduje monitorování pro změny nebo aktualizace.</span><span class="sxs-lookup"><span data-stu-id="57769-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="57769-107">Globálně jedinečný identifikátor (GUID) pro soubor.</span><span class="sxs-lookup"><span data-stu-id="57769-107">The Globally Unique Identifier (GUID) for the file.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="57769-108">Řetězec šestnáctkových číslic představující bajtů kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="57769-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="57769-109">Musí být sudé číslo šestnáctkových číslic.</span><span class="sxs-lookup"><span data-stu-id="57769-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="57769-110">Lichý počet číslic za následek upozornění kompilaci a direktiva se ignorují.</span><span class="sxs-lookup"><span data-stu-id="57769-110">An odd number of digits results in a compile-time warning, and the directive are  ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57769-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57769-111">Remarks</span></span>  
 <span data-ttu-id="57769-112">Ladicí program Visual Studio používá kontrolní součet a ujistěte se, že vždy vyhledá správné zdroje.</span><span class="sxs-lookup"><span data-stu-id="57769-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="57769-113">Kompilátor vypočítá kontrolní součet u zdrojového souboru a potom vydá výstup do souboru databáze (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="57769-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="57769-114">Ladicí program pak použije PDB pro porovnání, které vrací pro zdrojový soubor kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="57769-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="57769-115">Toto řešení nefunguje pro [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projekty, protože počítaný kontrolního součtu je vytvořeném zdrojovém souboru, nikoli soubor .aspx.</span><span class="sxs-lookup"><span data-stu-id="57769-115">This solution does not work for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="57769-116">Chcete-li vyřešit tento problém `#pragma checksum` poskytuje podporu kontrolního součtu pro [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="57769-116">To address this problem, `#pragma checksum` provides checksum support for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
 <span data-ttu-id="57769-117">Při vytváření [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projektu v [!INCLUDE[csprcs](~/includes/csprcs-md.md)], vytvořeném zdrojovém souboru obsahuje kontrolního součtu pro soubor .aspx, ze které se generuje zdroji.</span><span class="sxs-lookup"><span data-stu-id="57769-117">When you create an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] project in [!INCLUDE[csprcs](~/includes/csprcs-md.md)], the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="57769-118">Kompilátor pak zapíše tyto informace do souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="57769-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="57769-119">Pokud ne, zaznamená kompilátor `#pragma checksum` direktivy v souboru, se vypočítá kontrolního součtu a zapisuje do souboru PDB hodnota.</span><span class="sxs-lookup"><span data-stu-id="57769-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57769-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="57769-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="57769-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="57769-121">See Also</span></span>  
 [<span data-ttu-id="57769-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="57769-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="57769-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="57769-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="57769-124">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="57769-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
