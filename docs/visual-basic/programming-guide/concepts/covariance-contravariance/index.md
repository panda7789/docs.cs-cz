---
title: Kovariance a kontravariance (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1df3b01573ae1a9dc5c106efa5e387927c57c55f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="f6220-102">Kovariance a kontravariance (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6220-102">Covariance and Contravariance (Visual Basic)</span></span>
<span data-ttu-id="f6220-103">Kovariance a kontravariance povolit v jazyce Visual Basic implicitní převod odkazu pro typy polí, typy delegáta a argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="f6220-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="f6220-104">Kovariance zachovává kompatibility přiřazení a kontravariance obrátí ho.</span><span class="sxs-lookup"><span data-stu-id="f6220-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="f6220-105">Následující kód ukazuje rozdíl mezi kompatibility přiřazení, kovariance a kontravariance.</span><span class="sxs-lookup"><span data-stu-id="f6220-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="f6220-106">Kovariance pro pole umožňuje implicitní převod pole více odvozeného typu do pole méně odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="f6220-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="f6220-107">Ale tato operace není typově bezpečný, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f6220-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 <span data-ttu-id="f6220-108">Kovariance a kontravariance podpora pro metodu skupiny umožňuje odpovídající metoda podpisy s typy delegáta.</span><span class="sxs-lookup"><span data-stu-id="f6220-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="f6220-109">To umožňuje přiřadit delegáty nejen metody, které mají odpovídající podpisy, ale také metody, které vracejí, že informace odvozené typy (kovariance) nebo který přijímáte parametry, které mají méně odvozené typy (kontravariance) než je určeno typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="f6220-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="f6220-110">Další informace najdete v tématu [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [použití odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="f6220-110">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="f6220-111">Následující příklad kódu ukazuje, že kovariance a kontravariance podpora pro metodu skupiny.</span><span class="sxs-lookup"><span data-stu-id="f6220-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="f6220-112">V rozhraní .NET Framework 4 nebo novější Visual Basic podpora kovariance a kontravariance v obecných rozhraní a delegáti a povolit pro implicitní převod parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="f6220-112">In .NET Framework 4 or later Visual Basic support covariance and contravariance in generic interfaces and delegates and allow for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="f6220-113">Další informace najdete v tématu [odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) a [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="f6220-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="f6220-114">Následující příklad kódu ukazuje implicitní převod odkazu pro obecná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f6220-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="f6220-115">Obecná rozhraní nebo delegáta nazývá *variant* pokud jeho obecné parametry jsou deklarovány kovariantní nebo kontravariant.</span><span class="sxs-lookup"><span data-stu-id="f6220-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="f6220-116">Visual Basic umožňuje vytvářet vlastní variantních rozhraní a delegáti.</span><span class="sxs-lookup"><span data-stu-id="f6220-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="f6220-117">Další informace najdete v tématu [vytváření variantních obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) a [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="f6220-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="f6220-118">Související témata</span><span class="sxs-lookup"><span data-stu-id="f6220-118">Related Topics</span></span>  
  
|<span data-ttu-id="f6220-119">Název</span><span class="sxs-lookup"><span data-stu-id="f6220-119">Title</span></span>|<span data-ttu-id="f6220-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f6220-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f6220-121">Odchylky obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6220-121">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="f6220-122">Popisuje kovariance a kontravariance v obecných rozhraní a poskytuje seznam variantních obecných rozhraní v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6220-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="f6220-123">Vytváření variantních obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6220-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="f6220-124">Ukazuje, jak vytvořit vlastní variant rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f6220-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="f6220-125">Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6220-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="f6220-126">Ukazuje, jak podporují kovariance a kontravariance v <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> rozhraní umožňují opakované použití kódu.</span><span class="sxs-lookup"><span data-stu-id="f6220-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="f6220-127">Odchylky v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6220-127">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="f6220-128">Popisuje kovariance a kontravariance v obecných a neobecnou Delegáti a obsahuje seznam variant obecní delegáti v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6220-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="f6220-129">Použití odchylek v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6220-129">Using Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="f6220-130">Ukazuje, jak používat podporu kovariance a kontravariance v delegátech neobecnou tak, aby odpovídaly metoda podpisy s typy delegáta.</span><span class="sxs-lookup"><span data-stu-id="f6220-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="f6220-131">Použití odchylek pro Func a akce obecní delegáti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6220-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="f6220-132">Ukazuje, jak podporují kovariance a kontravariance v `Func` a `Action` Delegáti umožňují opakované použití kódu.</span><span class="sxs-lookup"><span data-stu-id="f6220-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
