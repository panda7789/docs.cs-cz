---
title: 'Postupy: Identifikace typu s povolenou hodnotou Null (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: f3ac4ebd77fc92a133eb326919d5ba55264ced97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333180"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="3c1ee-102">Postupy: Identifikace typu s povolenou hodnotou Null (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="3c1ee-102">How to: Identify a Nullable Type (C# Programming Guide)</span></span>
<span data-ttu-id="3c1ee-103">Můžete použít jazyka C# [typeof](../../../csharp/language-reference/keywords/typeof.md) operátor k vytvoření <xref:System.Type> objekt, který představuje typ s možnou hodnotou NULL:</span><span class="sxs-lookup"><span data-stu-id="3c1ee-103">You can use the C# [typeof](../../../csharp/language-reference/keywords/typeof.md) operator to create a <xref:System.Type> object that represents a Nullable type:</span></span>  
  
```  
System.Type type = typeof(int?);  
```  
  
 <span data-ttu-id="3c1ee-104">Můžete také použít třídy a metody <xref:System.Reflection> obor názvů pro generování <xref:System.Type> objekty, které reprezentují typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="3c1ee-104">You can also use the classes and methods of the <xref:System.Reflection> namespace to generate <xref:System.Type> objects that represent Nullable types.</span></span> <span data-ttu-id="3c1ee-105">Ale pokud pokusí získat informace o typu ze s možnou hodnotou Null proměnné za běhu pomocí <xref:System.Object.GetType%2A> metoda nebo `is` operátor, výsledkem je, <xref:System.Type> typ objektu, který představuje základní typ, není Nullable sám sebe.</span><span class="sxs-lookup"><span data-stu-id="3c1ee-105">However, if you try to obtain type information from Nullable variables at runtime by using the <xref:System.Object.GetType%2A> method or the `is` operator, the result is a <xref:System.Type> object that represents the underlying type, not the Nullable type itself.</span></span>  
  
 <span data-ttu-id="3c1ee-106">Volání metody `GetType` v Nullable typ způsobí, že zabalení operaci provést, když je typ implicitně převést na <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="3c1ee-106">Calling `GetType` on a Nullable type causes a boxing operation to be performed when the type is implicitly converted to <xref:System.Object>.</span></span> <span data-ttu-id="3c1ee-107">Proto <xref:System.Object.GetType%2A> vždy vrátí hodnotu <xref:System.Type> objekt, který představuje základní typ, není typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="3c1ee-107">Therefore <xref:System.Object.GetType%2A> always returns a <xref:System.Type> object that represents the underlying type, not the Nullable type.</span></span>  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 <span data-ttu-id="3c1ee-108">C# [je](../../../csharp/language-reference/keywords/is.md) operátor taky pracuje Nullable podkladovým typem.</span><span class="sxs-lookup"><span data-stu-id="3c1ee-108">The C# [is](../../../csharp/language-reference/keywords/is.md) operator also operates on a Nullable's underlying type.</span></span> <span data-ttu-id="3c1ee-109">Proto nelze použít `is` k určení, zda je proměnná typu s povolenou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="3c1ee-109">Therefore you cannot use `is` to determine whether a variable is a Nullable type.</span></span> <span data-ttu-id="3c1ee-110">Následující příklad ukazuje, že `is` operátor považuje Nullable\<int > proměnné jako typ int.</span><span class="sxs-lookup"><span data-stu-id="3c1ee-110">The following example shows that the `is` operator treats a Nullable\<int> variable as an int.</span></span>  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a><span data-ttu-id="3c1ee-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c1ee-111">Example</span></span>  
 <span data-ttu-id="3c1ee-112">Pomocí následujícího kódu rozhodnout, jestli <xref:System.Type> objekt představuje typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="3c1ee-112">Use the following code to determine whether a <xref:System.Type> object represents a Nullable type.</span></span> <span data-ttu-id="3c1ee-113">Mějte na paměti, že tento kód vždy vrátí hodnotu false, pokud `Type` volání byl vrácen objekt <xref:System.Object.GetType%2A>, jak je popsáno výše v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="3c1ee-113">Remember that this code always returns false if the `Type` object was returned from a call to <xref:System.Object.GetType%2A>, as explained earlier in this topic.</span></span>  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c1ee-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c1ee-114">See Also</span></span>  
 [<span data-ttu-id="3c1ee-115">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="3c1ee-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="3c1ee-116">Zabalení typů s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="3c1ee-116">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
