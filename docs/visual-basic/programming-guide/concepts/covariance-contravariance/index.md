---
title: Kovariance a kontravariance (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 241b8f5864b6e9b3e1caddde25d032a24e4d0bb7
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850449"
---
# <a name="covariance-and-contravariance-visual-basic"></a>Kovariance a kontravariance (Visual Basic)
V jazyce Visual Basic kovariance a kontravariance povolit implicitní převod odkazu pro typy polí, typy delegátů a argumenty obecného typu. Kompatibility přiřazení zachová kovariance a kontravariance obrátí ho.  
  
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
  
 Kovariance polí umožňuje implicitní převod pole více odvozeného typu na celou řadu méně odvozeného typu. Ale tato operace není typově bezpečný, jak je znázorněno v následujícím příkladu kódu.  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 Kovariance a kontravariance podpora pro metodu skupiny umožňuje, aby pro spárování metod podpisů s typy delegáta. To umožňuje přiřadit delegáty pouze metody, které mají odpovídající podpisy, ale také metody, které vracejí, že více odvozené typy (kovariance) nebo které přijímáte parametry, které mají méně odvozené typy (kontravariance), než je určeno typ delegáta. Další informace najdete v tématu [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [použití odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje kovariance a kontravariance podporu pro skupiny metod.  
  
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
  
 V rozhraní .NET Framework 4 nebo novější Visual Basic podporuje kovariance a kontravariance v obecných rozhraních a delegátech a umožňuje implicitní převod parametrů obecného typu. Další informace najdete v tématu [odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) a [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje implicitní referenční převod pro obecná rozhraní.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 Obecná rozhraní nebo delegát se nazývá *variant* pokud jeho obecné parametry jsou deklarovány kovariantní nebo kontravariantní. Visual Basic umožňuje vytvářet vlastní variant rozhraní a delegátů. Další informace najdete v tématu [vytváření variantních obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) a [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Tento článek popisuje kovariance a kontravariance v obecných rozhraních a obsahuje seznam variantních obecných rozhraní v rozhraní .NET Framework.|  
|[Vytváření variantních obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Ukazuje, jak vytvořit vlastní rozhraní variant.|  
|[Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Ukazuje, jak podporovat kovariance a kontravariance v <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> rozhraní vám umožňují opětovné použití kódu.|  
|[Odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Tento článek popisuje kovariance a kontravariance v obecných a neobecných delegátů a obsahuje seznam variantních obecných delegátů v rozhraní .NET Framework.|  
|[Použití odchylek v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Ukazuje, jak používat podporu kovariance a kontravariance v obecné delegáty tak, aby odpovídaly metod podpisů s typy delegáta.|  
|[Použití odchylek pro delegáty Func a Action obecný (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Ukazuje, jak podporovat kovariance a kontravariance v `Func` a `Action` delegáty umožňují opakované použití kódu.|
