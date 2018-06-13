---
title: Argumenty typu nelze odvodit z delegáta.
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 757483f1e88276dd9db82de1c2a7e47b5c975b0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598238"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="dd87e-102">Argumenty typu nelze odvodit z delegáta.</span><span class="sxs-lookup"><span data-stu-id="dd87e-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="dd87e-103">Pomocí příkazu přiřazení `AddressOf` přiřadit adresu obecný postup delegáta, ale neposkytuje žádné argumenty Typ na obecný postup.</span><span class="sxs-lookup"><span data-stu-id="dd87e-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="dd87e-104">Za normálních okolností při vyvolání obecného typu, můžete zadat typ argumentu pro každý typ parametr, který definuje obecného typu.</span><span class="sxs-lookup"><span data-stu-id="dd87e-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="dd87e-105">Pokud nezadáte žádné argumenty typu, pokusí se kompilátor odvození typy, které mají být předána do parametrů.</span><span class="sxs-lookup"><span data-stu-id="dd87e-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="dd87e-106">Pokud kontext nenabízí dostatek informací pro kompilátor odvození typů, je generována chyba.</span><span class="sxs-lookup"><span data-stu-id="dd87e-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="dd87e-107">**ID chyby:** BC36564</span><span class="sxs-lookup"><span data-stu-id="dd87e-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dd87e-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="dd87e-108">To correct this error</span></span>  
  
-   <span data-ttu-id="dd87e-109">Zadejte argumenty typu pro obecný postup v `AddressOf` výraz.</span><span class="sxs-lookup"><span data-stu-id="dd87e-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd87e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd87e-110">See Also</span></span>  
 [<span data-ttu-id="dd87e-111">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd87e-111">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="dd87e-112">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="dd87e-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="dd87e-113">Obecné procedury v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd87e-113">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [<span data-ttu-id="dd87e-114">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="dd87e-114">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="dd87e-115">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="dd87e-115">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
