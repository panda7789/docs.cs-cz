---
title: Hodnotu typu &#39; &lt;NázevTypu1&gt; &#39; nelze převést na &#39; &lt;NázevTypu2&gt; &#39; (více odkazů na soubor)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 41c18160be9b546f8b525376fa06bc0eca6c117a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603688"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="2c141-102">Hodnotu typu &#39; &lt;NázevTypu1&gt; &#39; nelze převést na &#39; &lt;NázevTypu2&gt; &#39; (více odkazů na soubor)</span><span class="sxs-lookup"><span data-stu-id="2c141-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="2c141-103">Hodnotu typu '\<NázevTypu1 >' nelze převést na '\<NázevTypu2 > ".</span><span class="sxs-lookup"><span data-stu-id="2c141-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="2c141-104">Neshoda typu může být z důvodu kombinování odkazu na soubor '\<filepath1 >' v projektu '\<projectname1 >' s odkazem na soubor '\<filepath2 >' v projektu '\<projectname2 > ".</span><span class="sxs-lookup"><span data-stu-id="2c141-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="2c141-105">Pokud jsou obě sestavení identická, zkuste vyměnit tyto odkazy tak, aby byly oba odkazy ze stejného umístění.</span><span class="sxs-lookup"><span data-stu-id="2c141-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="2c141-106">V situaci, kdy projektu umožňuje více než jeden soubor odkaz na sestavení kompilátor nezaručuje, že jeden typ lze převést na jiný.</span><span class="sxs-lookup"><span data-stu-id="2c141-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="2c141-107">Každý odkaz na soubor Určuje název výstupního souboru projektu (obvykle soubor knihovny DLL) a cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="2c141-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="2c141-108">Kompilátor nemůže zaručit, že výstupní soubory pocházejí z jednoho zdroje, nebo že představují stejnou verzi nástroje do stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c141-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="2c141-109">Proto nemůže zaručit, že typy v různých odkazy jsou stejného typu nebo i než lze převést na druhý.</span><span class="sxs-lookup"><span data-stu-id="2c141-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="2c141-110">Pokud víte, že jsou odkazovaná sestavení mít stejnou identitu sestavení můžete použít jeden soubor odkaz.</span><span class="sxs-lookup"><span data-stu-id="2c141-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="2c141-111">*Identity sestavení* obsahuje název, verzi, veřejný klíč, pokud existuje a jazykovou verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c141-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="2c141-112">Tyto informace jednoznačně identifikuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c141-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="2c141-113">**ID chyby:** BC30961</span><span class="sxs-lookup"><span data-stu-id="2c141-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c141-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2c141-114">To correct this error</span></span>  
  
-   <span data-ttu-id="2c141-115">Pokud jsou odkazovaná sestavení mít stejnou identitu sestavení, odeberte nebo nahraďte jeden z odkazů na soubor tak, aby bylo pouze odkaz na jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="2c141-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="2c141-116">Pokud odkazovaná sestavení nemají stejnou identitu sestavení, pak změňte kód tak, aby se nebude pokoušet o převést na typ v jeden typ v dalších.</span><span class="sxs-lookup"><span data-stu-id="2c141-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c141-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c141-117">See Also</span></span>  
 [<span data-ttu-id="2c141-118">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2c141-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="2c141-119">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="2c141-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 
