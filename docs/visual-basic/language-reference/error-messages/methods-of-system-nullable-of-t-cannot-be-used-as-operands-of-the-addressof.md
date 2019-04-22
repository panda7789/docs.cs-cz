---
title: Metody System.Nullable(Of T) nelze používat jako operandy operátoru 'AddressOf'.
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 54d66a60d20a6add4c2b4a160f87b58b5a1d00e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817263"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a><span data-ttu-id="6d59a-102">Metody System.Nullable(Of T) nelze používat jako operandy operátoru 'AddressOf'.</span><span class="sxs-lookup"><span data-stu-id="6d59a-102">Methods of 'System.Nullable(Of T)' cannot be used as operands of the 'AddressOf' operator</span></span>
<span data-ttu-id="6d59a-103">Příkaz používá `AddressOf` operátor s operandem, který představuje postup <xref:System.Nullable%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="6d59a-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="6d59a-104">**ID chyby:** BC32126</span><span class="sxs-lookup"><span data-stu-id="6d59a-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6d59a-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="6d59a-105">To correct this error</span></span>  
  
-   <span data-ttu-id="6d59a-106">Nahraďte název procedury v `AddressOf` klauzule s operandem, který není členem <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="6d59a-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
-   <span data-ttu-id="6d59a-107">Zápis třídu, která zabalí metodu <xref:System.Nullable%601> , kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="6d59a-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="6d59a-108">V následujícím příkladu `NullableWrapper` třída definuje novou metodu s názvem `GetValueOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="6d59a-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="6d59a-109">Protože tato nová metoda není členem <xref:System.Nullable%601>, lze použít u `nullInstance`, instanci typu s možnou hodnotou Null a vytvoří argument `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="6d59a-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d59a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d59a-110">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="6d59a-111">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="6d59a-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="6d59a-112">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="6d59a-112">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="6d59a-113">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d59a-113">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
