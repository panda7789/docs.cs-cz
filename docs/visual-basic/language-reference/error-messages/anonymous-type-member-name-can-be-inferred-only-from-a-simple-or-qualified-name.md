---
title: Název člena anonymního typu lze odvodit pouze z jednoduchého nebo kvalifikovaného názvu bez argumentů.
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: 38f669fe183ac79ebed6e5a122bc70aedc9bb753
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701216"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="a38db-102">Název člena anonymního typu lze odvodit pouze z jednoduchého nebo kvalifikovaného názvu bez argumentů.</span><span class="sxs-lookup"><span data-stu-id="a38db-102">Anonymous type member name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="a38db-103">Ze složitých výrazů nelze odvodit název člena anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="a38db-103">You cannot infer an anonymous type member name from a complex expression.</span></span>  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 <span data-ttu-id="a38db-104">Další informace o zdrojích, ze kterých anonymní typy a nemůžou odvodit názvy členů a typy, naleznete v tématu [How to: odvozování názvů a typů vlastností v deklaracích anonymního typu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="a38db-104">For more information about sources from which anonymous types can and cannot infer member names and types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
 <span data-ttu-id="a38db-105">**ID chyby:** BC36556</span><span class="sxs-lookup"><span data-stu-id="a38db-105">**Error ID:** BC36556</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a38db-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a38db-106">To correct this error</span></span>  
  
- <span data-ttu-id="a38db-107">Přiřaďte výraz k názvu členu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="a38db-107">Assign the expression to a member name, as shown in the following code:</span></span>  
  
    ```vb  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a38db-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a38db-108">See also</span></span>

- [<span data-ttu-id="a38db-109">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="a38db-109">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="a38db-110">Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu</span><span class="sxs-lookup"><span data-stu-id="a38db-110">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
