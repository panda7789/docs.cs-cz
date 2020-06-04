---
title: Obecné parametry použité jako typy volitelného parametru musí mít omezení třídy.
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 273ea592e73be5d76a4ffef077e691014a108347
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402924"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="b080e-102">Obecné parametry použité jako typy volitelného parametru musí mít omezení třídy.</span><span class="sxs-lookup"><span data-stu-id="b080e-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="b080e-103">Procedura je deklarována s volitelným parametrem, který používá parametr typu, který není omezen na typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="b080e-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="b080e-104">Pro každý volitelný parametr je vždy nutné zadat výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b080e-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="b080e-105">Pokud je parametr typu odkazu, musí být volitelná hodnota `Nothing` , což je platná hodnota libovolného typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="b080e-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="b080e-106">Nicméně, pokud je parametr typu hodnoty, tento typ musí být základní datový typ předdefinovaný Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b080e-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="b080e-107">Důvodem je to, že složený typ hodnoty, jako je například uživatelsky definovaná struktura, nemá platnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b080e-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="b080e-108">Použijete-li parametr typu pro volitelný parametr, je nutné zaručit, že se jedná o typ odkazu, aby nedocházelo k možnosti typu hodnoty bez platné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b080e-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="b080e-109">To znamená, že je nutné parametr typu omezit buď pomocí `Class` klíčového slova, nebo s názvem konkrétní třídy.</span><span class="sxs-lookup"><span data-stu-id="b080e-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="b080e-110">**ID chyby:** BC32124</span><span class="sxs-lookup"><span data-stu-id="b080e-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b080e-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b080e-111">To correct this error</span></span>  
  
- <span data-ttu-id="b080e-112">Omezte parametr typu tak, aby přijímal pouze typ odkazu, nebo ho nepoužívejte pro volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="b080e-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b080e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b080e-113">See also</span></span>

- [<span data-ttu-id="b080e-114">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b080e-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="b080e-115">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="b080e-115">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="b080e-116">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="b080e-116">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="b080e-117">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="b080e-117">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="b080e-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="b080e-118">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="b080e-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="b080e-119">Nothing</span></span>](../nothing.md)
