---
title: Z těchto argumentů nelze odvodit datové typy parametrů typu.
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 91ee4bf9242df822890b0a171061f375a3b24cbc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828001"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="ec9c0-102">Z těchto argumentů nelze odvodit datové typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="ec9c0-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>
<span data-ttu-id="ec9c0-103">Z těchto argumentů nelze odvodit datové typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="ec9c0-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="ec9c0-104">Zadání dat explicitně podaří k této chybě.</span><span class="sxs-lookup"><span data-stu-id="ec9c0-104">Specifying the data type(s) explicitly might correct this error.</span></span>  
  
 <span data-ttu-id="ec9c0-105">Tato chyba nastane, pokud řešení přetížení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="ec9c0-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="ec9c0-106">Vyskytuje se jako podřízené zprávu s oznámením, proč se odstranilo kandidát konkrétní přetížení.</span><span class="sxs-lookup"><span data-stu-id="ec9c0-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="ec9c0-107">Chybová zpráva vysvětluje, že kompilátor nelze použít odvození typu najít datové typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="ec9c0-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec9c0-108">Při zadání argumentů není možné zvolit (například pro operátory dotazu ve výrazech dotazů), zobrazí se chybová zpráva bez druhý věty.</span><span class="sxs-lookup"><span data-stu-id="ec9c0-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>  
  
 <span data-ttu-id="ec9c0-109">Následující kód ukazuje chybu.</span><span class="sxs-lookup"><span data-stu-id="ec9c0-109">The following code demonstrates the error.</span></span>  
  
```vb  
Module Module1  
  
    Sub Main()  
  
        '' Not Valid.  
        'OverloadedGenericMethod("Hello", "World")  
  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T)(ByVal x As String,   
                                      ByVal y As InterfaceExample(Of T))  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,   
                                         ByVal y As InterfaceExample(Of R))  
    End Sub  
  
End Module  
  
Interface InterfaceExample(Of T)  
End Interface  
```  
  
 <span data-ttu-id="ec9c0-110">**ID chyby:** BC36647 a BC36644</span><span class="sxs-lookup"><span data-stu-id="ec9c0-110">**Error ID:** BC36647 and BC36644</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ec9c0-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ec9c0-111">To correct this error</span></span>  
  
-   <span data-ttu-id="ec9c0-112">Lze zadat datový typ pro parametr typu nebo parametrů, aniž byste museli spoléhat na odvození typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="ec9c0-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec9c0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec9c0-113">See also</span></span>

- [<span data-ttu-id="ec9c0-114">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="ec9c0-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="ec9c0-115">Obecné procedury v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec9c0-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="ec9c0-116">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec9c0-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
