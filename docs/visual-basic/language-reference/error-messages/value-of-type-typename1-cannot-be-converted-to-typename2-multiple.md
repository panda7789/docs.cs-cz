---
title: Hodnotu typu &#39; &lt;NázevTypu1&gt; &#39; nelze převést na &#39; &lt;NázevTypu2&gt; &#39; (odkazy na více souborů)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 943b9612a9217b90c19f34285e812c4e1cccf81a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691370"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="209b4-102">Hodnotu typu &#39; &lt;NázevTypu1&gt; &#39; nelze převést na &#39; &lt;NázevTypu2&gt; &#39; (odkazy na více souborů)</span><span class="sxs-lookup"><span data-stu-id="209b4-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="209b4-103">Hodnotu typu '\<NázevTypu1 >' nelze převést na "\<NázevTypu2 >'.</span><span class="sxs-lookup"><span data-stu-id="209b4-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="209b4-104">Neshody typů může být způsobena kombinováním odkazu na soubor "\<filepath1 >' v projektu"\<projectname1 >' s odkazem na soubor "\<filepath2 >' v projektu"\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="209b4-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="209b4-105">Pokud jsou obě sestavení identická, zkuste, nahraďte tyto odkazy tak, aby oba odkazy byly ze stejného umístění.</span><span class="sxs-lookup"><span data-stu-id="209b4-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="209b4-106">V situaci, kdy projekt vytvoří více než jeden soubor odkaz na sestavení kompilátor zaručit, že jeden typ lze převést na jiný.</span><span class="sxs-lookup"><span data-stu-id="209b4-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="209b4-107">Každý odkaz na soubor Určuje název výstupního souboru projektu (obvykle souboru knihovny DLL) a cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="209b4-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="209b4-108">Kompilátor nemůže zaručit, že výstupní soubory pocházejí ze stejného zdroje, nebo že představují stejné verze téhož sestavení.</span><span class="sxs-lookup"><span data-stu-id="209b4-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="209b4-109">Proto nemůže zaručit, že typy v jiné odkazy jsou stejného typu nebo ještě, že jedna může být převeden na druhý.</span><span class="sxs-lookup"><span data-stu-id="209b4-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="209b4-110">Pokud víte, že odkazovaná sestavení mají stejnou identitu sestavení, můžete použít odkaz na jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="209b4-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="209b4-111">*Identita sestavení* obsahuje název sestavení, verze, veřejného klíče, pokud existuje a jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="209b4-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="209b4-112">Tyto informace jednoznačně identifikuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="209b4-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="209b4-113">**ID chyby:** BC30961</span><span class="sxs-lookup"><span data-stu-id="209b4-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="209b4-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="209b4-114">To correct this error</span></span>  
  
-   <span data-ttu-id="209b4-115">Pokud odkazovaná sestavení mají stejnou identitu sestavení, odebrat nebo nahradit jeden z odkazů na soubory tak, aby se pouze odkaz na jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="209b4-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="209b4-116">Pokud odkazovaná sestavení nemají stejnou identitu sestavení, pak změňte kód tak, aby se nebude pokoušet o převod typu v jednom typu v jiném.</span><span class="sxs-lookup"><span data-stu-id="209b4-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="209b4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="209b4-117">See also</span></span>
- [<span data-ttu-id="209b4-118">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="209b4-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="209b4-119">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="209b4-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)

