---
title: "Metody & č. 39; System.Nullable (Of T) & č. 39; nelze použít jako operandy & č. 39; AddressOf & č. 39; operátor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords: BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce0e9bc6abd71f22e3f6c3486ef40493e74d820f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a><span data-ttu-id="c2044-102">Metody & č. 39; System.Nullable (Of T) & č. 39; nelze použít jako operandy & č. 39; AddressOf & č. 39; operátor</span><span class="sxs-lookup"><span data-stu-id="c2044-102">Methods of &#39;System.Nullable(Of T)&#39; cannot be used as operands of the &#39;AddressOf&#39; operator</span></span>
<span data-ttu-id="c2044-103">Příkaz používá `AddressOf` operátor s operandem, který reprezentuje proceduru z <xref:System.Nullable%601> struktura.</span><span class="sxs-lookup"><span data-stu-id="c2044-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="c2044-104">**ID chyby:** BC32126</span><span class="sxs-lookup"><span data-stu-id="c2044-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c2044-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c2044-105">To correct this error</span></span>  
  
-   <span data-ttu-id="c2044-106">Nahraďte název procedury v `AddressOf` klauzule s operandem, který není členem <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="c2044-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
-   <span data-ttu-id="c2044-107">Zápis třídu, která zabalí metodě <xref:System.Nullable%601> , kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="c2044-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="c2044-108">V následujícím příkladu `NullableWrapper` třída definuje novou metodu s názvem `GetValueOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="c2044-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="c2044-109">Protože tato nová metoda není členem <xref:System.Nullable%601>, ho můžete použít k `nullInstance`, instanci typu s povolenou hodnotou null k argumentu `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="c2044-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2044-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2044-110">See Also</span></span>  
 <xref:System.Nullable%601>  
 [<span data-ttu-id="c2044-111">AddressOf – operátor</span><span class="sxs-lookup"><span data-stu-id="c2044-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="c2044-112">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="c2044-112">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="c2044-113">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2044-113">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
