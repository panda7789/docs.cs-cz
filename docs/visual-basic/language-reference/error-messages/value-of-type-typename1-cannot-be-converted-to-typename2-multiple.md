---
title: "Hodnota typu č. 39; &lt;NázevTypu1&gt;& č. 39; nelze převést na & č. 39;&lt; NázevTypu2&gt;& č. 39; (Více odkazů na soubor)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords: BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc6138c7a7ca7d50a56fdd1f536e8d2dc3462a08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="fb5b8-102">Hodnota typu č. 39; &lt;NázevTypu1&gt;& č. 39; nelze převést na & č. 39;&lt; NázevTypu2&gt;& č. 39; (Více odkazů na soubor)</span><span class="sxs-lookup"><span data-stu-id="fb5b8-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="fb5b8-103">Hodnotu typu '\<NázevTypu1 >' nelze převést na '\<NázevTypu2 > ".</span><span class="sxs-lookup"><span data-stu-id="fb5b8-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="fb5b8-104">Neshoda typu může být z důvodu kombinování odkazu na soubor '\<filepath1 >' v projektu '\<projectname1 >' s odkazem na soubor '\<filepath2 >' v projektu '\<projectname2 > ".</span><span class="sxs-lookup"><span data-stu-id="fb5b8-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="fb5b8-105">Pokud jsou obě sestavení identická, zkuste vyměnit tyto odkazy tak, aby byly oba odkazy ze stejného umístění.</span><span class="sxs-lookup"><span data-stu-id="fb5b8-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="fb5b8-106">V situaci, kdy projektu umožňuje více než jeden soubor odkaz na sestavení kompilátor nezaručuje, že jeden typ lze převést na jiný.</span><span class="sxs-lookup"><span data-stu-id="fb5b8-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="fb5b8-107">Každý odkaz na soubor Určuje název výstupního souboru projektu (obvykle soubor knihovny DLL) a cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="fb5b8-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="fb5b8-108">Kompilátor nemůže zaručit, že výstupní soubory pocházejí z jednoho zdroje, nebo že představují stejnou verzi nástroje do stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="fb5b8-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="fb5b8-109">Proto nemůže zaručit, že typy v různých odkazy jsou stejného typu nebo i než lze převést na druhý.</span><span class="sxs-lookup"><span data-stu-id="fb5b8-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="fb5b8-110">Pokud víte, že jsou odkazovaná sestavení mít stejnou identitu sestavení můžete použít jeden soubor odkaz.</span><span class="sxs-lookup"><span data-stu-id="fb5b8-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="fb5b8-111">*Identity sestavení* obsahuje název, verzi, veřejný klíč, pokud existuje a jazykovou verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="fb5b8-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="fb5b8-112">Tyto informace jednoznačně identifikuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="fb5b8-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="fb5b8-113">**ID chyby:** BC30961</span><span class="sxs-lookup"><span data-stu-id="fb5b8-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fb5b8-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fb5b8-114">To correct this error</span></span>  
  
-   <span data-ttu-id="fb5b8-115">Pokud jsou odkazovaná sestavení mít stejnou identitu sestavení, odeberte nebo nahraďte jeden z odkazů na soubor tak, aby bylo pouze odkaz na jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="fb5b8-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="fb5b8-116">Pokud odkazovaná sestavení nemají stejnou identitu sestavení, pak změňte kód tak, aby se nebude pokoušet o převést na typ v jeden typ v dalších.</span><span class="sxs-lookup"><span data-stu-id="fb5b8-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb5b8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb5b8-117">See Also</span></span>  
 [<span data-ttu-id="fb5b8-118">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb5b8-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="fb5b8-119">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="fb5b8-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="fb5b8-120">NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="fb5b8-120">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
