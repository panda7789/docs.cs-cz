---
title: Struktura &#39; &lt;%{structurename/&gt; &#39; musí obsahovat alespoň jednu instanci členské proměnné nebo deklaraci události alespoň jedna instance nesmí být označený &#39;vlastní&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 85a4babc808e274a99f2c9faf08a02abf8aa4e93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594495"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="a8be8-102">Struktura &#39; &lt;%{structurename/&gt; &#39; musí obsahovat alespoň jednu instanci členské proměnné nebo deklaraci události alespoň jedna instance nesmí být označený &#39;vlastní&#39;</span><span class="sxs-lookup"><span data-stu-id="a8be8-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="a8be8-103">Definice struktury nezahrnuje všechny sdíleném proměnné nebo sdíleném nevlastní události.</span><span class="sxs-lookup"><span data-stu-id="a8be8-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="a8be8-104">Proměnné nebo událost, která platí pro každou konkrétní instanci místo (sdíleném) na všechny instance souhrnně musí mít každý struktura ([sdílené](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="a8be8-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="a8be8-105">Sdíleném konstanty, vlastnosti a postupů nevyhovují tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="a8be8-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="a8be8-106">Kromě toho, pokud nejsou žádné sdíleném proměnné a jenom jedna sdíleném událost, že událost nemůže být `Custom` událostí.</span><span class="sxs-lookup"><span data-stu-id="a8be8-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="a8be8-107">**ID chyby:** BC30941</span><span class="sxs-lookup"><span data-stu-id="a8be8-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a8be8-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a8be8-108">To correct this error</span></span>  
  
-   <span data-ttu-id="a8be8-109">Zadejte alespoň jednu proměnnou nebo událost, která není `Shared`.</span><span class="sxs-lookup"><span data-stu-id="a8be8-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="a8be8-110">Pokud definujete jen jednu událost, musí být nevlastní, jakož i sdíleném.</span><span class="sxs-lookup"><span data-stu-id="a8be8-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8be8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8be8-111">See Also</span></span>  
 [<span data-ttu-id="a8be8-112">Struktury</span><span class="sxs-lookup"><span data-stu-id="a8be8-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="a8be8-113">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="a8be8-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="a8be8-114">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="a8be8-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
