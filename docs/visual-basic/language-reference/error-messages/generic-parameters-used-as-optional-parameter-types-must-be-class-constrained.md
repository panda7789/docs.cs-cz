---
title: Obecné parametry použité jako typy volitelného parametru musí mít omezení třídy.
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 7e2b59f758ef236717a912694576b514e2ae8a60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590036"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="7834b-102">Obecné parametry použité jako typy volitelného parametru musí mít omezení třídy.</span><span class="sxs-lookup"><span data-stu-id="7834b-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="7834b-103">Postup je deklarovaný s volitelný parametr, který používá parametr typu, který není omezen být odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="7834b-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="7834b-104">Vždy je třeba zadat výchozí hodnotu pro každý volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="7834b-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="7834b-105">Pokud má parametr hodnotu typu odkaz, volitelná hodnota musí být `Nothing`, což je platná hodnota pro jakýkoli typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="7834b-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="7834b-106">Ale pokud je parametr typu hodnoty, tento typ musí být typu základní datové předdefinovaná v nástroji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7834b-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="7834b-107">Je to proto, že hodnota kompozitního typu, například do vlastní struktury nemá žádný platný výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7834b-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="7834b-108">Použijete-li parametr typu pro volitelný parametr, musí zaručit, že je typu odkazu. aby se zabránilo možnost Typ hodnoty žádný platný výchozí hodnotou.</span><span class="sxs-lookup"><span data-stu-id="7834b-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="7834b-109">To znamená, že je parametr typu omezit buď pomocí `Class` – klíčové slovo nebo s názvem určité třídy.</span><span class="sxs-lookup"><span data-stu-id="7834b-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="7834b-110">**ID chyby:** BC32124</span><span class="sxs-lookup"><span data-stu-id="7834b-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7834b-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7834b-111">To correct this error</span></span>  
  
-   <span data-ttu-id="7834b-112">Omezit parametr typu tak, aby přijímal pouze odkaz na typ, nebo nepoužívejte ho pro volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="7834b-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7834b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7834b-113">See Also</span></span>  
 [<span data-ttu-id="7834b-114">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7834b-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="7834b-115">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="7834b-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="7834b-116">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="7834b-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="7834b-117">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="7834b-117">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [<span data-ttu-id="7834b-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="7834b-118">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="7834b-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="7834b-119">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
