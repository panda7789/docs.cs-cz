---
title: 'Postupy: Bezpečné přetypování pomocí operátorů as a is (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: de59fb49ca5dbe1282cd828f7d6995dda449d31b
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257298"
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="6a8b1-102">Postupy: Bezpečné přetypování pomocí operátorů as a is (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6a8b1-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="6a8b1-103">Protože objekty jsou polymorfní, je možné pro proměnné typu základní třídy pro uložení odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="6a8b1-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="6a8b1-104">Pro přístup k metodám instance odvozeného typu, je nezbytné převést hodnotu zpět na odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="6a8b1-104">To access the derived type's instance methods, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="6a8b1-105">Však pokusu o jednoduchý přetypování v těchto případech vytvoří riziko vyvolání <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="6a8b1-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="6a8b1-106">To znamená proč C# poskytuje [je](../../../csharp/language-reference/keywords/is.md) a [jako](../../../csharp/language-reference/keywords/as.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="6a8b1-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="6a8b1-107">Tyto operátory můžete použít k ověření, zda přetypování proběhne úspěšně, aniž by to způsobilo vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="6a8b1-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="6a8b1-108">Obecně platí `as` operátor je mnohem efektivnější, protože je ve skutečnosti vrací hodnotu přetypování, pokud přetypování lze provést úspěšně.</span><span class="sxs-lookup"><span data-stu-id="6a8b1-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="6a8b1-109">`is` Operátor vrátí logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6a8b1-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="6a8b1-110">Může být proto použita, když pouze k určení typu objektu, ale nemají skutečně přetypovat.</span><span class="sxs-lookup"><span data-stu-id="6a8b1-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a8b1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a8b1-111">Example</span></span>  
 <span data-ttu-id="6a8b1-112">Následující příklady ukazují, jak používat `is` a `as` operátory přetypování z jednoho odkazu typu na jiný bez rizika došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="6a8b1-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="6a8b1-113">Tento příklad také ukazuje způsob použití `as` operátor s typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="6a8b1-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6a8b1-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a8b1-114">See Also</span></span>  
 [<span data-ttu-id="6a8b1-115">Typy</span><span class="sxs-lookup"><span data-stu-id="6a8b1-115">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="6a8b1-116">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="6a8b1-116">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="6a8b1-117">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="6a8b1-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
