---
title: 'Postupy: Bezpečné přetypování pomocí operátorů as a is (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: 6e02675a2a895add245d3c2e40305a0417fdf429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325095"
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="321d0-102">Postupy: Bezpečné přetypování pomocí operátorů as a is (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="321d0-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="321d0-103">Protože jsou polymorfní objekty, je možné proměnnou typu základní třídy pro odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="321d0-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="321d0-104">Přístup odvozený typ metodě, je potřeba hodnota zpět do odvozený typ přetypování.</span><span class="sxs-lookup"><span data-stu-id="321d0-104">To access the derived type's method, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="321d0-105">Však k pokusu o jednoduchou cast v těchto případech vytvoří riziko vyvolání <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="321d0-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="321d0-106">To znamená proč C# poskytuje [je](../../../csharp/language-reference/keywords/is.md) a [jako](../../../csharp/language-reference/keywords/as.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="321d0-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="321d0-107">Tyto operátory můžete použít k ověření, zda přetypování bude úspěšné, aniž by docházelo vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="321d0-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="321d0-108">Obecně `as` operátor je efektivnější, protože pokud přetypování můžete provedeny úspěšně ve skutečnosti vrátí hodnotu přetypování.</span><span class="sxs-lookup"><span data-stu-id="321d0-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="321d0-109">`is` Operátor vrací pouze logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="321d0-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="321d0-110">Je proto dá právě chcete určit typ objektu, ale nemají ve skutečnosti vysílat.</span><span class="sxs-lookup"><span data-stu-id="321d0-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="321d0-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="321d0-111">Example</span></span>  
 <span data-ttu-id="321d0-112">Následující příklady ukazují, jak používat `is` a `as` zadejte operátory přetypovat z jeden odkaz na jiný bez riziko došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="321d0-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="321d0-113">Příklad také ukazuje způsob použití `as` operátor s typy hodnot s povolenou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="321d0-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="321d0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="321d0-114">See Also</span></span>  
 [<span data-ttu-id="321d0-115">Typy</span><span class="sxs-lookup"><span data-stu-id="321d0-115">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="321d0-116">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="321d0-116">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="321d0-117">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="321d0-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
