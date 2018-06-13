---
title: Zabalení typů s povolenou hodnotou Null (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
ms.openlocfilehash: e2c7602bf45f1861d3a32a73824e9fedf0a4d29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334753"
---
# <a name="boxing-nullable-types-c-programming-guide"></a><span data-ttu-id="459f2-102">Zabalení typů s povolenou hodnotou Null (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="459f2-102">Boxing Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="459f2-103">Objekty na základě typů s povolenou hodnotou Null se do pouze pole, pokud se objekt nesmí být nulová.</span><span class="sxs-lookup"><span data-stu-id="459f2-103">Objects based on nullable types are only boxed if the object is non-null.</span></span> <span data-ttu-id="459f2-104">Pokud <xref:System.Nullable%601.HasValue%2A> je `false`, odkaz na objekt je přiřazena k `null` místo zabalení.</span><span class="sxs-lookup"><span data-stu-id="459f2-104">If <xref:System.Nullable%601.HasValue%2A> is `false`, the object reference is assigned to `null` instead of boxing.</span></span> <span data-ttu-id="459f2-105">Příklad:</span><span class="sxs-lookup"><span data-stu-id="459f2-105">For example:</span></span>  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 <span data-ttu-id="459f2-106">Pokud se objekt jinou hodnotu než null – Pokud <xref:System.Nullable%601.HasValue%2A> je `true` – pak zabalení dojde, ale jenom základní typ, který je na základě objekt s možnou hodnotou null je zabalená.</span><span class="sxs-lookup"><span data-stu-id="459f2-106">If the object is non-null -- if <xref:System.Nullable%601.HasValue%2A> is `true` -- then boxing occurs, but only the underlying type that the nullable object is based on is boxed.</span></span> <span data-ttu-id="459f2-107">Zabalení typ s možnou hodnotou Null hodnotu než null oknech samostatně, typ hodnoty není <xref:System.Nullable%601?displayProperty=nameWithType> který zabalí typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="459f2-107">Boxing a non-null nullable value type boxes the value type itself, not the <xref:System.Nullable%601?displayProperty=nameWithType> that wraps the value type.</span></span> <span data-ttu-id="459f2-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="459f2-108">For example:</span></span>  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 <span data-ttu-id="459f2-109">Dva zabalené objekty jsou stejné jako ty vytvořené zabalení typů hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="459f2-109">The two boxed objects are identical to those created by boxing non-nullable types.</span></span> <span data-ttu-id="459f2-110">A, stejně jako použití hodnot Null pevně určené typy, může se jednat o nezabalený na typy s možnou hodnotou Null, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="459f2-110">And, just like non-nullable boxed types, they can be unboxed into nullable types, as in the following example:</span></span>  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a><span data-ttu-id="459f2-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="459f2-111">Remarks</span></span>  
 <span data-ttu-id="459f2-112">Chování typy s možnou hodnotou Null, pokud do pole nabízí dvě výhody:</span><span class="sxs-lookup"><span data-stu-id="459f2-112">The behavior of nullable types when boxed provides two advantages:</span></span>  
  
1.  <span data-ttu-id="459f2-113">Null lze testovat s možnou hodnotou Null objekty a jejich zabalené protějšku:</span><span class="sxs-lookup"><span data-stu-id="459f2-113">Nullable objects and their boxed counterpart can be tested for null:</span></span>  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  <span data-ttu-id="459f2-114">Pevně určené typy s možnou hodnotou Null plně podporují funkce základní typ:</span><span class="sxs-lookup"><span data-stu-id="459f2-114">Boxed nullable types fully support the functionality of the underlying type:</span></span>  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="459f2-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="459f2-115">See Also</span></span>  
 [<span data-ttu-id="459f2-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="459f2-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="459f2-117">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="459f2-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="459f2-118">Postupy: Identifikace typu s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="459f2-118">How to: Identify a Nullable Type</span></span>](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
