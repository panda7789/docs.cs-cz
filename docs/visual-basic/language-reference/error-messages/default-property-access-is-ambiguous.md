---
title: Zděděné členy '<defaultpropertyname>' rozhraní '<interfacename1>' a členy '<defaultpropertyname>' rozhraní '<interfacename2>' mají nejednoznačný přístup k výchozím vlastnostem.
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 5f058c8e7d480b9145452ae85f186a6ac2ed0d56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803727"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="8a50a-102">Přístup k výchozím vlastnostem je nejednoznačné mezi členy zděděné rozhraní\<defaultpropertyname >' rozhraní '\<interfacename1 >' a '\<defaultpropertyname > "rozhraní"\< interfacename2 > "</span><span class="sxs-lookup"><span data-stu-id="8a50a-102">Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>
<span data-ttu-id="8a50a-103">Rozhraní se dědí z dvě rozhraní, z nichž každý deklaruje výchozí vlastnost se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="8a50a-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="8a50a-104">Kompilátor nelze vyřešit přístup k této vlastnosti výchozí bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="8a50a-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="8a50a-105">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="8a50a-105">The following example illustrates this.</span></span>  
  
```  
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
  
 <span data-ttu-id="8a50a-106">Pokud zadáte `testObj(1)`, kompilátor se pokusí přeložit na výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8a50a-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="8a50a-107">Nicméně existují dva možné výchozí vlastnosti z důvodu zděděných rozhraních, tak tato chyba signalizuje kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8a50a-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="8a50a-108">**ID chyby:** BC30686</span><span class="sxs-lookup"><span data-stu-id="8a50a-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8a50a-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8a50a-109">To correct this error</span></span>  
  
- <span data-ttu-id="8a50a-110">Vyhněte se dědí všechny členy se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="8a50a-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="8a50a-111">V předchozím příkladu Pokud `testObj` nemusí některé členy, například `Iface2`, deklarujte následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8a50a-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="8a50a-112">-nebo-</span><span class="sxs-lookup"><span data-stu-id="8a50a-112">-or-</span></span>  
  
- <span data-ttu-id="8a50a-113">Implementujte rozhraní dědičné ve třídě.</span><span class="sxs-lookup"><span data-stu-id="8a50a-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="8a50a-114">Potom můžete implementovat všechny zděděné vlastnosti s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="8a50a-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="8a50a-115">Pouze jeden z nich však může být výchozí vlastnost implementující třídu.</span><span class="sxs-lookup"><span data-stu-id="8a50a-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="8a50a-116">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="8a50a-116">The following example illustrates this.</span></span>  
  
    ```  
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
  
## <a name="see-also"></a><span data-ttu-id="8a50a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a50a-117">See also</span></span>

- [<span data-ttu-id="8a50a-118">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="8a50a-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
