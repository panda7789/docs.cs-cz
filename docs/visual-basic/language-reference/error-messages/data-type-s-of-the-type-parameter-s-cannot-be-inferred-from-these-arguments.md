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
ms.openlocfilehash: b278dcc10a8a4e9e67aacdb16dca2588d2ebd0f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409778"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="ec3fa-102">Z těchto argumentů nelze odvodit datové typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="ec3fa-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>

<span data-ttu-id="ec3fa-103">Z těchto argumentů nelze odvodit datové typy parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="ec3fa-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="ec3fa-104">Je možné, že se chybu podaří odstranit explicitním zadáním datových typů.</span><span class="sxs-lookup"><span data-stu-id="ec3fa-104">Specifying the data type(s) explicitly might correct this error.</span></span>

<span data-ttu-id="ec3fa-105">K této chybě dojde v případě, že se nepovedlo vyřešit přetížení.</span><span class="sxs-lookup"><span data-stu-id="ec3fa-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="ec3fa-106">K tomu dochází jako podřízená zpráva, která uvádí, proč byl vyloučen konkrétní kandidát na přetížení.</span><span class="sxs-lookup"><span data-stu-id="ec3fa-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="ec3fa-107">Chybová zpráva vysvětluje, že kompilátor nemůže použít odvození typu k nalezení datových typů pro parametry typu.</span><span class="sxs-lookup"><span data-stu-id="ec3fa-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="ec3fa-108">Pokud se zadáním argumentů nejedná o možnost (například pro operátory dotazu ve výrazech dotazu), zobrazí se chybová zpráva bez druhé věty.</span><span class="sxs-lookup"><span data-stu-id="ec3fa-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>

<span data-ttu-id="ec3fa-109">Následující kód demonstruje chybu.</span><span class="sxs-lookup"><span data-stu-id="ec3fa-109">The following code demonstrates the error.</span></span>

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

<span data-ttu-id="ec3fa-110">**ID chyby:** BC36647 a BC36644</span><span class="sxs-lookup"><span data-stu-id="ec3fa-110">**Error ID:** BC36647 and BC36644</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ec3fa-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ec3fa-111">To correct this error</span></span>

<span data-ttu-id="ec3fa-112">Možná budete moct zadat datový typ pro parametr typu nebo parametry a nemusíte se spoléhat na odvození typu.</span><span class="sxs-lookup"><span data-stu-id="ec3fa-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec3fa-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec3fa-113">See also</span></span>

- [<span data-ttu-id="ec3fa-114">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="ec3fa-114">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="ec3fa-115">Obecné procedury v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec3fa-115">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="ec3fa-116">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec3fa-116">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
