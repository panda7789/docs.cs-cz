---
title: Kovariance a kontravariance (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1df3b01573ae1a9dc5c106efa5e387927c57c55f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="covariance-and-contravariance-visual-basic"></a>Kovariance a kontravariance (Visual Basic)
Kovariance a kontravariance povolit v jazyce Visual Basic implicitní převod odkazu pro typy polí, typy delegáta a argumenty obecného typu. Kovariance zachovává kompatibility přiřazení a kontravariance obrátí ho.  
  
 Následující kód ukazuje rozdíl mezi kompatibility přiřazení, kovariance a kontravariance.  
  
```vb  
' Assignment compatibility.   
Dim str As String = "test"  
' An object of a more derived type is assigned to an object of a less derived type.   
Dim obj As Object = str  
  
' Covariance.   
Dim strings As IEnumerable(Of String) = New List(Of String)()  
' An object that is instantiated with a more derived type argument   
' is assigned to an object instantiated with a less derived type argument.   
' Assignment compatibility is preserved.   
Dim objects As IEnumerable(Of Object) = strings  
  
' Contravariance.             
' Assume that there is the following method in the class:   
' Shared Sub SetObject(ByVal o As Object)  
' End Sub  
Dim actObject As Action(Of Object) = AddressOf SetObject  
  
' An object that is instantiated with a less derived type argument   
' is assigned to an object instantiated with a more derived type argument.   
' Assignment compatibility is reversed.   
Dim actString As Action(Of String) = actObject  
```  
  
 Kovariance pro pole umožňuje implicitní převod pole více odvozeného typu do pole méně odvozeného typu. Ale tato operace není typově bezpečný, jak je znázorněno v následujícím příkladu kódu.  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 Kovariance a kontravariance podpora pro metodu skupiny umožňuje odpovídající metoda podpisy s typy delegáta. To umožňuje přiřadit delegáty nejen metody, které mají odpovídající podpisy, ale také metody, které vracejí, že informace odvozené typy (kovariance) nebo který přijímáte parametry, které mají méně odvozené typy (kontravariance) než je určeno typ delegáta. Další informace najdete v tématu [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [použití odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje, že kovariance a kontravariance podpora pro metodu skupiny.  
  
```vb  
Shared Function GetObject() As Object  
    Return Nothing  
End Function  
  
Shared Sub SetObject(ByVal obj As Object)  
End Sub  
  
Shared Function GetString() As String  
    Return ""  
End Function  
  
Shared Sub SetString(ByVal str As String)  
  
End Sub  
  
Shared Sub Test()  
    ' Covariance. A delegate specifies a return type as object,  
    ' but you can assign a method that returns a string.  
    Dim del As Func(Of Object) = AddressOf GetString  
  
    ' Contravariance. A delegate specifies a parameter type as string,  
    ' but you can assign a method that takes an object.  
    Dim del2 As Action(Of String) = AddressOf SetObject  
End Sub  
```  
  
 V rozhraní .NET Framework 4 nebo novější Visual Basic podpora kovariance a kontravariance v obecných rozhraní a delegáti a povolit pro implicitní převod parametry obecného typu. Další informace najdete v tématu [odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) a [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje implicitní převod odkazu pro obecná rozhraní.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 Obecná rozhraní nebo delegáta nazývá *variant* pokud jeho obecné parametry jsou deklarovány kovariantní nebo kontravariant. Visual Basic umožňuje vytvářet vlastní variantních rozhraní a delegáti. Další informace najdete v tématu [vytváření variantních obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) a [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Popisuje kovariance a kontravariance v obecných rozhraní a poskytuje seznam variantních obecných rozhraní v rozhraní .NET Framework.|  
|[Vytváření variantních obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Ukazuje, jak vytvořit vlastní variant rozhraní.|  
|[Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Ukazuje, jak podporují kovariance a kontravariance v <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> rozhraní umožňují opakované použití kódu.|  
|[Odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Popisuje kovariance a kontravariance v obecných a neobecnou Delegáti a obsahuje seznam variant obecní delegáti v rozhraní .NET Framework.|  
|[Použití odchylek v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Ukazuje, jak používat podporu kovariance a kontravariance v delegátech neobecnou tak, aby odpovídaly metoda podpisy s typy delegáta.|  
|[Použití odchylek pro Func a akce obecní delegáti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Ukazuje, jak podporují kovariance a kontravariance v `Func` a `Action` Delegáti umožňují opakované použití kódu.|
