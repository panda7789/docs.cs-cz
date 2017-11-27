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
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a>Metody & č. 39; System.Nullable (Of T) & č. 39; nelze použít jako operandy & č. 39; AddressOf & č. 39; operátor
Příkaz používá `AddressOf` operátor s operandem, který reprezentuje proceduru z <xref:System.Nullable%601> struktura.  
  
 **ID chyby:** BC32126  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nahraďte název procedury v `AddressOf` klauzule s operandem, který není členem <xref:System.Nullable%601>.  
  
-   Zápis třídu, která zabalí metodě <xref:System.Nullable%601> , kterou chcete použít. V následujícím příkladu `NullableWrapper` třída definuje novou metodu s názvem `GetValueOrDefault`. Protože tato nová metoda není členem <xref:System.Nullable%601>, ho můžete použít k `nullInstance`, instanci typu s povolenou hodnotou null k argumentu `AddressOf`.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Nullable%601>  
 [AddressOf – operátor](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
