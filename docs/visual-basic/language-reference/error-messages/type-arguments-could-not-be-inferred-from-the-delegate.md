---
title: "Argumenty typu nelze odvodit z delegáta."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords: BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 57a3a24af32d9eb85a0f905aa3a73a956723b6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="0cafb-102">Argumenty typu nelze odvodit z delegáta.</span><span class="sxs-lookup"><span data-stu-id="0cafb-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="0cafb-103">Pomocí příkazu přiřazení `AddressOf` přiřadit adresu obecný postup delegáta, ale neposkytuje žádné argumenty Typ na obecný postup.</span><span class="sxs-lookup"><span data-stu-id="0cafb-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="0cafb-104">Za normálních okolností při vyvolání obecného typu, můžete zadat typ argumentu pro každý typ parametr, který definuje obecného typu.</span><span class="sxs-lookup"><span data-stu-id="0cafb-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="0cafb-105">Pokud nezadáte žádné argumenty typu, pokusí se kompilátor odvození typy, které mají být předána do parametrů.</span><span class="sxs-lookup"><span data-stu-id="0cafb-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="0cafb-106">Pokud kontext nenabízí dostatek informací pro kompilátor odvození typů, je generována chyba.</span><span class="sxs-lookup"><span data-stu-id="0cafb-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="0cafb-107">**ID chyby:** BC36564</span><span class="sxs-lookup"><span data-stu-id="0cafb-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0cafb-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0cafb-108">To correct this error</span></span>  
  
-   <span data-ttu-id="0cafb-109">Zadejte argumenty typu pro obecný postup v `AddressOf` výraz.</span><span class="sxs-lookup"><span data-stu-id="0cafb-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cafb-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cafb-110">See Also</span></span>  
 [<span data-ttu-id="0cafb-111">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cafb-111">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="0cafb-112">AddressOf – operátor</span><span class="sxs-lookup"><span data-stu-id="0cafb-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="0cafb-113">Obecné procedury v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cafb-113">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [<span data-ttu-id="0cafb-114">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="0cafb-114">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="0cafb-115">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="0cafb-115">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
