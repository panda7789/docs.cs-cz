---
title: Přístup k výchozí vlastnosti je nejednoznačný mezi členy zděděné rozhraní &#39; &lt;defaultpropertyname&gt; &#39; rozhraní &#39; &lt;interfacename1&gt; &#39; a &#39; &lt;defaultpropertyname&gt; &#39; rozhraní &#39; &lt;interfacename2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 65a10067284cad3bf56ecdc441ebefa0a740ef53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590852"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a><span data-ttu-id="40a8b-102">Přístup k výchozí vlastnosti je nejednoznačný mezi členy zděděné rozhraní &#39; &lt;defaultpropertyname&gt; &#39; rozhraní &#39; &lt;interfacename1&gt; &#39; a &#39; &lt;defaultpropertyname&gt; &#39; rozhraní &#39; &lt;interfacename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="40a8b-102">Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39;</span></span>
<span data-ttu-id="40a8b-103">Rozhraní dědí od dvě rozhraní, z nichž každý deklaruje výchozí vlastnost se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="40a8b-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="40a8b-104">Kompilátor nelze vyřešit přístup k této vlastnosti výchozí bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="40a8b-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="40a8b-105">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="40a8b-105">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="40a8b-106">Pokud zadáte `testObj(1)`, kompilátor pokusí přeložit na výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="40a8b-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="40a8b-107">Nicméně existují dvě možné výchozí vlastnosti kvůli zděděné rozhraní, tak tato chyba signalizuje kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="40a8b-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="40a8b-108">**ID chyby:** BC30686</span><span class="sxs-lookup"><span data-stu-id="40a8b-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40a8b-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="40a8b-109">To correct this error</span></span>  
  
-   <span data-ttu-id="40a8b-110">Vyhněte se dědí všechny členy se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="40a8b-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="40a8b-111">V předchozím příkladu Pokud `testObj` není třeba žádné členy, Řekněme, `Iface2`, deklarovat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="40a8b-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="40a8b-112">-nebo-</span><span class="sxs-lookup"><span data-stu-id="40a8b-112">-or-</span></span>  
  
-   <span data-ttu-id="40a8b-113">Implementujte rozhraní dědičných v třídě.</span><span class="sxs-lookup"><span data-stu-id="40a8b-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="40a8b-114">Poté můžete implementovat každé vlastnosti zděděné s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="40a8b-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="40a8b-115">Však jen jeden z nich může být výchozí vlastnost implementující třídu.</span><span class="sxs-lookup"><span data-stu-id="40a8b-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="40a8b-116">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="40a8b-116">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="40a8b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="40a8b-117">See Also</span></span>  
 [<span data-ttu-id="40a8b-118">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="40a8b-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
