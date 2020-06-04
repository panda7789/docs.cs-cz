---
title: Metody System.Nullable(Of T) nelze používat jako operandy operátoru 'AddressOf'.
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 61c6fe7c33b3292066e653304ded43a863413723
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397217"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>Metody System.Nullable(Of T) nelze používat jako operandy operátoru 'AddressOf'.
Příkaz používá `AddressOf` operátor s operandem, který představuje proceduru <xref:System.Nullable%601> struktury.  
  
 **ID chyby:** BC32126  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Nahraďte název procedury v `AddressOf` klauzuli operandem, který není členem <xref:System.Nullable%601> .  
  
- Napište třídu, která zabalí metodu, kterou chcete <xref:System.Nullable%601> použít. V následujícím příkladu `NullableWrapper` Třída definuje novou metodu s názvem `GetValueOrDefault` . Vzhledem k tomu, že tato nová metoda není členem <xref:System.Nullable%601> , lze ji použít pro `nullInstance` instanci typu s možnou hodnotou null a vytvořit argument pro `AddressOf` .  
  
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

- <xref:System.Nullable%601>
- [AddressOf – operátor](../operators/addressof-operator.md)
- [Typy hodnot s možnou hodnotou null](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
