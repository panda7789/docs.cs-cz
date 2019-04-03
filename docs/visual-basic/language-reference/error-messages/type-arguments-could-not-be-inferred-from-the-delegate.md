---
title: Argumenty typu nelze odvodit z delegáta.
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 1024cf6f2c1fa112db29cb710eef190a5022d3af
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838596"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="fd353-102">Argumenty typu nelze odvodit z delegáta.</span><span class="sxs-lookup"><span data-stu-id="fd353-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="fd353-103">Přiřazovací příkaz používá `AddressOf` přiřazení adresy obecný postup delegáta, ale neposkytuje žádné argumenty typu pro obecný postup.</span><span class="sxs-lookup"><span data-stu-id="fd353-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="fd353-104">Za normálních okolností při vyvolání obecného typu, zadáte argument typu pro každý z parametrů typu, který definuje obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fd353-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="fd353-105">Pokud nezadáte žádné argumenty typu, kompilátor se pokusí odvodit typy, které se mají předat parametry typu.</span><span class="sxs-lookup"><span data-stu-id="fd353-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="fd353-106">Pokud kontextu neposkytuje dostatek informací pro kompilátor k odvození typů, je vygenerována chyba.</span><span class="sxs-lookup"><span data-stu-id="fd353-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="fd353-107">**ID chyby:** BC36564</span><span class="sxs-lookup"><span data-stu-id="fd353-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fd353-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fd353-108">To correct this error</span></span>  
  
-   <span data-ttu-id="fd353-109">Zadejte argumenty typu pro obecný postup v `AddressOf` výrazu.</span><span class="sxs-lookup"><span data-stu-id="fd353-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd353-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd353-110">See also</span></span>

- [<span data-ttu-id="fd353-111">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd353-111">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="fd353-112">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="fd353-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="fd353-113">Obecné procedury v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd353-113">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="fd353-114">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="fd353-114">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="fd353-115">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="fd353-115">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
