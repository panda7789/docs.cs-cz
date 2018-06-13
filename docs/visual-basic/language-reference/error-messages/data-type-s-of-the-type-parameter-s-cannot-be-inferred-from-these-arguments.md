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
ms.openlocfilehash: 6f84df5c9388220e5ca817d95362753df0920534
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586809"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="1a370-102">Z těchto argumentů nelze odvodit datové typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="1a370-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>
<span data-ttu-id="1a370-103">Z těchto argumentů nelze odvodit datové typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="1a370-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="1a370-104">Zadání dat typy explicitně může tuto chybu opravit.</span><span class="sxs-lookup"><span data-stu-id="1a370-104">Specifying the data type(s) explicitly might correct this error.</span></span>  
  
 <span data-ttu-id="1a370-105">K této chybě dojde, když rozlišení přetížení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="1a370-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="1a370-106">K tomu dochází jako podřízené zpráva oznamující, proč se odstranilo kandidátem konkrétní přetížení.</span><span class="sxs-lookup"><span data-stu-id="1a370-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="1a370-107">Chybová zpráva vysvětluje, že kompilátor nelze použít odvození typu najít datové typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="1a370-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a370-108">Při zadání argumentů není možné (například pro operátory dotazu ve výrazech dotazů), zobrazí se chybová zpráva bez druhé věty.</span><span class="sxs-lookup"><span data-stu-id="1a370-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>  
  
 <span data-ttu-id="1a370-109">Následující kód ukazuje chyba.</span><span class="sxs-lookup"><span data-stu-id="1a370-109">The following code demonstrates the error.</span></span>  
  
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
  
 <span data-ttu-id="1a370-110">**ID chyby:** BC36647 a BC36644</span><span class="sxs-lookup"><span data-stu-id="1a370-110">**Error ID:** BC36647 and BC36644</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1a370-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1a370-111">To correct this error</span></span>  
  
-   <span data-ttu-id="1a370-112">Je možné zadat datový typ pro parametr typu nebo parametry, aniž byste museli spoléhat na odvození typu.</span><span class="sxs-lookup"><span data-stu-id="1a370-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a370-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a370-113">See Also</span></span>  
 [<span data-ttu-id="1a370-114">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="1a370-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [<span data-ttu-id="1a370-115">Obecné procedury v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a370-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [<span data-ttu-id="1a370-116">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a370-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
