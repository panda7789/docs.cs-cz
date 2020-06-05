---
title: Argumenty typu nelze odvodit z delegáta.
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: f29e92c8245e33c0418d9a387070b03f645c331e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362745"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="35615-102">Argumenty typu nelze odvodit z delegáta.</span><span class="sxs-lookup"><span data-stu-id="35615-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="35615-103">Příkaz přiřazení používá `AddressOf` k přiřazení adresy obecného postupu delegátovi, ale neposkytuje žádné argumenty typu pro obecný postup.</span><span class="sxs-lookup"><span data-stu-id="35615-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="35615-104">Při vyvolání obecného typu obvykle zadáte argument typu pro každý parametr typu, který definuje obecný typ.</span><span class="sxs-lookup"><span data-stu-id="35615-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="35615-105">Pokud nezadáte žádné argumenty typu, kompilátor se pokusí odvodit typy, které mají být předány do parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="35615-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="35615-106">Pokud kontext neposkytne dostatek informací pro kompilátor k odvození typů, je vygenerována chyba.</span><span class="sxs-lookup"><span data-stu-id="35615-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="35615-107">**ID chyby:** BC36564</span><span class="sxs-lookup"><span data-stu-id="35615-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="35615-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="35615-108">To correct this error</span></span>  
  
- <span data-ttu-id="35615-109">Zadejte argumenty typu pro obecný postup ve `AddressOf` výrazu.</span><span class="sxs-lookup"><span data-stu-id="35615-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35615-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="35615-110">See also</span></span>

- [<span data-ttu-id="35615-111">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35615-111">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="35615-112">AddressOf – operátor</span><span class="sxs-lookup"><span data-stu-id="35615-112">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="35615-113">Obecné procedury v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35615-113">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="35615-114">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="35615-114">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="35615-115">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="35615-115">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
