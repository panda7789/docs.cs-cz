---
title: Hodnotu typu '<typename1>' nelze převést na typ '<typename2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: f6b35efbc445887c537b94dd299b317a28e5f689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406557"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="1d860-102">Hodnotu typu '\<typename1>' nelze převést na typ '\<typename2>'.</span><span class="sxs-lookup"><span data-stu-id="1d860-102">Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>
<span data-ttu-id="1d860-103">Hodnotu typu \<typename1> nejde převést na \<typename2> .</span><span class="sxs-lookup"><span data-stu-id="1d860-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="1d860-104">Neshoda typů může být způsobena kombinováním odkazu na soubor s odkazem na projekt na sestavení ' \<assemblyname> '.</span><span class="sxs-lookup"><span data-stu-id="1d860-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="1d860-105">Zkuste nahradit odkaz na soubor \<filepath> v projektu ' \<projectname1> ' s odkazem na projekt ' \<projectname2> '.</span><span class="sxs-lookup"><span data-stu-id="1d860-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="1d860-106">V situaci, kdy projekt vytvoří odkaz na projekt i odkaz na soubor, kompilátor nemůže zaručit, že jeden typ lze převést na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="1d860-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="1d860-107">Následující pseudo kód ilustruje situaci, která může tuto chybu vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="1d860-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 <span data-ttu-id="1d860-108">Projekt `P1` vytváří přímý odkaz na projekt prostřednictvím projektu `P2` do projektu `P3` a také přímý odkaz na soubor `P3` .</span><span class="sxs-lookup"><span data-stu-id="1d860-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="1d860-109">Deklarace `commonObject` používá odkaz na soubor `P3` , zatímco volání `P2.getCommonClass` používá odkaz na projekt `P3` .</span><span class="sxs-lookup"><span data-stu-id="1d860-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="1d860-110">Problémem v této situaci je, že odkaz na soubor určuje cestu k souboru a název výstupního souboru `P3` (obvykle P3. dll), zatímco odkazy na projekt identifikují zdrojový projekt ( `P3` ) podle názvu projektu.</span><span class="sxs-lookup"><span data-stu-id="1d860-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="1d860-111">Z tohoto důvodu kompilátor nemůže zaručit, že typ `P3.commonClass` pochází ze stejného zdrojového kódu prostřednictvím dvou různých odkazů.</span><span class="sxs-lookup"><span data-stu-id="1d860-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="1d860-112">K této situaci obvykle dochází, když jsou odkazy na projekt a odkazy na soubory smíšené.</span><span class="sxs-lookup"><span data-stu-id="1d860-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="1d860-113">Na předchozí ilustraci se k problému nestane, pokud `P1` jste vytvořili přímý odkaz na projekt `P3` namísto odkazu na soubor.</span><span class="sxs-lookup"><span data-stu-id="1d860-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="1d860-114">**ID chyby:** BC30955</span><span class="sxs-lookup"><span data-stu-id="1d860-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1d860-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1d860-115">To correct this error</span></span>  
  
- <span data-ttu-id="1d860-116">Změňte odkaz na soubor na odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="1d860-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d860-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d860-117">See also</span></span>

- [<span data-ttu-id="1d860-118">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d860-118">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="1d860-119">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="1d860-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
