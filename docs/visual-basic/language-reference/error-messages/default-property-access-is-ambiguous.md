---
title: Zděděné členy '<defaultpropertyname>' rozhraní '<interfacename1>' a členy '<defaultpropertyname>' rozhraní '<interfacename2>' mají nejednoznačný přístup k výchozím vlastnostem.
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: a36cfe8e5496bbfd1941afa8a46086491ae96a2a
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512753"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="ecfc9-102">Zděděné členy\<defaultpropertyname >\<rozhraní\<interfacename1 > a defaultpropertyname > of interface\< mají nejednoznačný přístup k výchozím vlastnostem. interfacename2 > '</span><span class="sxs-lookup"><span data-stu-id="ecfc9-102">Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>

<span data-ttu-id="ecfc9-103">Rozhraní dědí ze dvou rozhraní, z nichž každý deklaruje výchozí vlastnost se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="ecfc9-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="ecfc9-104">Kompilátor nemůže přeložit přístup k této výchozí vlastnosti bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="ecfc9-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="ecfc9-105">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ecfc9-105">The following example illustrates this.</span></span>

```vb
Public Interface Iface1
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface2
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface3
    Inherits Iface1, Iface2
End Interface
Public Class testClass
    Public Sub accessDefaultProperty()
        Dim testObj As Iface3
        Dim testInt As Integer = testObj(1)
    End Sub
End Class
```

<span data-ttu-id="ecfc9-106">Když zadáte `testObj(1)`, kompilátor se pokusí ho přeložit na výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ecfc9-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="ecfc9-107">Existují však dvě možné výchozí vlastnosti z důvodu zděděných rozhraní, takže kompilátor tuto chybu signalizuje.</span><span class="sxs-lookup"><span data-stu-id="ecfc9-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>

<span data-ttu-id="ecfc9-108">**ID chyby:** BC30686</span><span class="sxs-lookup"><span data-stu-id="ecfc9-108">**Error ID:** BC30686</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ecfc9-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ecfc9-109">To correct this error</span></span>

- <span data-ttu-id="ecfc9-110">Vyhněte se dědění všech členů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="ecfc9-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="ecfc9-111">V předchozím příkladu, pokud `testObj` nepotřebuje žádné z členů, řekněme, `Iface2`a pak ho deklarovat takto:</span><span class="sxs-lookup"><span data-stu-id="ecfc9-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>

  ```vb
  Dim testObj As Iface1
  ```

  <span data-ttu-id="ecfc9-112">\-ani</span><span class="sxs-lookup"><span data-stu-id="ecfc9-112">\-or-</span></span>

- <span data-ttu-id="ecfc9-113">Implementujte rozhraní dědění ve třídě.</span><span class="sxs-lookup"><span data-stu-id="ecfc9-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="ecfc9-114">Pak můžete implementovat všechny děděné vlastnosti s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="ecfc9-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="ecfc9-115">Nicméně pouze jeden z nich může být výchozí vlastností implementující třídy.</span><span class="sxs-lookup"><span data-stu-id="ecfc9-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="ecfc9-116">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ecfc9-116">The following example illustrates this.</span></span>

  ```vb
  Public Class useIface3
      Implements Iface3
      Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop
          ' Insert code to define Get and Set procedures for prop1.
      End Property
      Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop
          ' Insert code to define Get and Set procedures for prop2.
      End Property
  End Class
  ```

## <a name="see-also"></a><span data-ttu-id="ecfc9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecfc9-117">See also</span></span>

- [<span data-ttu-id="ecfc9-118">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecfc9-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
