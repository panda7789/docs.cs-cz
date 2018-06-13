---
title: Hodnotu typu &#39; &lt;NázevTypu1&gt; &#39; nelze převést na &#39; &lt;NázevTypu2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 9b3c029ed7bf73ff92dba65438d797b27fa135f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595235"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a><span data-ttu-id="44ca2-102">Hodnotu typu &#39; &lt;NázevTypu1&gt; &#39; nelze převést na &#39; &lt;NázevTypu2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="44ca2-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="44ca2-103">Hodnotu typu '\<NázevTypu1 >' nelze převést na '\<NázevTypu2 > ".</span><span class="sxs-lookup"><span data-stu-id="44ca2-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="44ca2-104">Neshoda typu může být kombinování odkazu na soubor s projektu odkaz na sestavení '\<assemblyname >'.</span><span class="sxs-lookup"><span data-stu-id="44ca2-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="44ca2-105">Zkuste vyměnit odkaz na soubor '\<filepath >' v projektu '\<projectname1 >' s odkaz na projekt se\<projectname2 > ".</span><span class="sxs-lookup"><span data-stu-id="44ca2-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="44ca2-106">V situaci, kdy projektu vytvoří odkaz na projekt a odkaz na soubor kompilátor nezaručuje, že jeden typ lze převést na jiný.</span><span class="sxs-lookup"><span data-stu-id="44ca2-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="44ca2-107">Následující kód pseudo znázorňuje situaci, který může vytvořit tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="44ca2-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
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
  
 <span data-ttu-id="44ca2-108">Projekt `P1` vytváří odkaz nepřímých projektu prostřednictvím projektu `P2` do projektu `P3`a také přímý odkaz na soubor na `P3`.</span><span class="sxs-lookup"><span data-stu-id="44ca2-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="44ca2-109">Prohlášení o `commonObject` používá odkaz na soubor `P3`, při volání `P2.getCommonClass` používá odkaz na projekt `P3`.</span><span class="sxs-lookup"><span data-stu-id="44ca2-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="44ca2-110">Problém v této situaci je, že odkaz na soubor Určuje název pro výstupní soubor a cesta k souboru `P3` (obvykle p3.dll), zatímco odkazů projektu identifikovat zdrojový projekt (`P3`) podle názvu projektu.</span><span class="sxs-lookup"><span data-stu-id="44ca2-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="44ca2-111">Z toho důvodu nelze kompilátor zaručit, že typ `P3.commonClass` pochází z stejný zdrojový kód prostřednictvím dvou různých odkazy.</span><span class="sxs-lookup"><span data-stu-id="44ca2-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="44ca2-112">Tuto situaci obvykle dochází, když projektu odkazy a jsou kombinované odkazů na soubor.</span><span class="sxs-lookup"><span data-stu-id="44ca2-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="44ca2-113">V předchozí ilustraci, nebude problém nastat, pokud `P1` provedené projektu přímý odkaz na `P3` místo odkaz na soubor.</span><span class="sxs-lookup"><span data-stu-id="44ca2-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="44ca2-114">**ID chyby:** BC30955</span><span class="sxs-lookup"><span data-stu-id="44ca2-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="44ca2-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="44ca2-115">To correct this error</span></span>  
  
-   <span data-ttu-id="44ca2-116">Změňte odkaz na soubor odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="44ca2-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ca2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="44ca2-117">See Also</span></span>  
 [<span data-ttu-id="44ca2-118">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="44ca2-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="44ca2-119">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="44ca2-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 
