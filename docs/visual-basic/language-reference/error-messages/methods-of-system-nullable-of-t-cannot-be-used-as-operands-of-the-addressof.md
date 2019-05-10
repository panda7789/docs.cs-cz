---
title: Metody System.Nullable(Of T) nelze používat jako operandy operátoru 'AddressOf'.
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: e55e561fa20a3740d352537958681b0a66fc381e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592046"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>Metody System.Nullable(Of T) nelze používat jako operandy operátoru 'AddressOf'.
Příkaz používá `AddressOf` operátor s operandem, který představuje postup <xref:System.Nullable%601> struktury.  
  
 **ID chyby:** BC32126  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Nahraďte název procedury v `AddressOf` klauzule s operandem, který není členem <xref:System.Nullable%601>.  
  
- Zápis třídu, která zabalí metodu <xref:System.Nullable%601> , kterou chcete použít. V následujícím příkladu `NullableWrapper` třída definuje novou metodu s názvem `GetValueOrDefault`. Protože tato nová metoda není členem <xref:System.Nullable%601>, lze použít u `nullInstance`, instanci typu s možnou hodnotou Null a vytvoří argument `AddressOf`.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Nullable%601>
- [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
