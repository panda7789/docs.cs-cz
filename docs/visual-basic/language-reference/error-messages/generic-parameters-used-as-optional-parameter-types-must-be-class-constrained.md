---
title: Obecné parametry použité jako typy volitelného parametru musí mít omezení třídy.
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 9b0293472f5eda74c2bf8fb215e15ae5cf8d8b98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813896"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="fc508-102">Obecné parametry použité jako typy volitelného parametru musí mít omezení třídy.</span><span class="sxs-lookup"><span data-stu-id="fc508-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="fc508-103">Postup je deklarován s volitelným parametrem, který používá parametr typu, který není omezen na typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="fc508-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="fc508-104">Vždy je nutné zadat výchozí hodnotu pro každý volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="fc508-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="fc508-105">Pokud je parametr typu odkazu, musí být Volitelná hodnota `Nothing`, což je platná hodnota pro jakéhokoliv odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="fc508-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="fc508-106">Ale pokud je parametr typu hodnoty, tento typ musí být typu základní datové předdefinovaná v nástroji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fc508-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="fc508-107">Je to proto složený typ hodnoty, jako je například struktura definovaný uživatelem, nemá platnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fc508-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="fc508-108">Pokud použijete parametr typu pro volitelný parametr, musíte zaručeno, že se typu odkazu, abyste předešli typu hodnoty žádný platný výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fc508-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="fc508-109">To znamená, že musí omezení parametru typu, buď pomocí `Class` – klíčové slovo nebo s názvem určité třídy.</span><span class="sxs-lookup"><span data-stu-id="fc508-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="fc508-110">**ID chyby:** BC32124</span><span class="sxs-lookup"><span data-stu-id="fc508-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fc508-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fc508-111">To correct this error</span></span>  
  
-   <span data-ttu-id="fc508-112">Omezení parametru typu tak, aby přijímal pouze typem odkazu, nebo nepoužívejte ho pro volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="fc508-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc508-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc508-113">See also</span></span>

- [<span data-ttu-id="fc508-114">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fc508-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="fc508-115">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="fc508-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="fc508-116">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="fc508-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="fc508-117">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="fc508-117">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="fc508-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="fc508-118">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="fc508-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="fc508-119">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
