---
title: 'Postupy: Vytváření sjednocení C / C++ pomocí atributů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: 0c3ebf248f5d2f20e2fff25fb8326a294b51d153
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829301"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="82b37-102">Postupy: Vytváření sjednocení C/C++ pomocí atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82b37-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>
<span data-ttu-id="82b37-103">Pomocí atributů můžete přizpůsobit, jak jsou rozloženy struktury v paměti.</span><span class="sxs-lookup"><span data-stu-id="82b37-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="82b37-104">Například můžete vytvořit, která se označuje jako sjednocení v jazyce C/C++ pomocí `StructLayout(LayoutKind.Explicit)` a `FieldOffset` atributy.</span><span class="sxs-lookup"><span data-stu-id="82b37-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82b37-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="82b37-105">Example</span></span>  
 <span data-ttu-id="82b37-106">V tomto segmentu kódu, všechna pole z `TestUnion` začínají na stejné místo v paměti.</span><span class="sxs-lookup"><span data-stu-id="82b37-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
<System.Runtime.InteropServices.StructLayout(   
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestUnion  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public i As Integer  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public d As Double  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public c As Char  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public b As Byte  
End Structure  
```  
  
## <a name="example"></a><span data-ttu-id="82b37-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="82b37-107">Example</span></span>  
 <span data-ttu-id="82b37-108">Tady je další příklad – kde pole začínají na různých explicitně nastavit umístění.</span><span class="sxs-lookup"><span data-stu-id="82b37-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
 <System.Runtime.InteropServices.StructLayout(  
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestExplicit  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public lg As Long  
  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public i1 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(4)>   
     Public i2 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(8)>   
     Public d As Double  
  
     <System.Runtime.InteropServices.FieldOffset(12)>   
     Public c As Char  
  
     <System.Runtime.InteropServices.FieldOffset(14)>   
     Public b As Byte  
 End Structure  
```  
  
 <span data-ttu-id="82b37-109">Dvě celočíselné pole, `i1` a `i2`, sdílet stejné umístění paměti jako `lg`.</span><span class="sxs-lookup"><span data-stu-id="82b37-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="82b37-110">Tento typ kontroly nad rozložení struktury je užitečné při použití vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="82b37-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82b37-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82b37-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="82b37-112">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82b37-112">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="82b37-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="82b37-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="82b37-114">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82b37-114">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="82b37-115">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82b37-115">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="82b37-116">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82b37-116">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="82b37-117">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82b37-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
