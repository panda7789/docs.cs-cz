---
title: 'Postupy: vytvořeníC++ sjednocení jazyka C pomocí atributů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: 6595d6477d9d0838745e19eb2a44d26f6e534c70
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524270"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="e7c0b-102">Postupy: vytvoření C/C++ sjednocení pomocí atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7c0b-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>

<span data-ttu-id="e7c0b-103">Pomocí atributů můžete přizpůsobit způsob, jakým jsou struktury rozloženy v paměti.</span><span class="sxs-lookup"><span data-stu-id="e7c0b-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="e7c0b-104">Můžete například vytvořit, co se říká sjednocení v C/C++ pomocí atributů `StructLayout(LayoutKind.Explicit)` a `FieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="e7c0b-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="e7c0b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7c0b-105">Example</span></span>

<span data-ttu-id="e7c0b-106">V tomto segmentu kódu se všechna pole `TestUnion` začínají na stejném místě v paměti.</span><span class="sxs-lookup"><span data-stu-id="e7c0b-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

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

## <a name="example"></a><span data-ttu-id="e7c0b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7c0b-107">Example</span></span>

<span data-ttu-id="e7c0b-108">Následuje další příklad, kdy se pole spouštějí v různých explicitních nastaveních umístění.</span><span class="sxs-lookup"><span data-stu-id="e7c0b-108">The following is another example where fields start at different explicitly set locations.</span></span>

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

<span data-ttu-id="e7c0b-109">Dvě celočíselná pole, `i1` a `i2`, sdílejí stejná umístění v paměti jako `lg`.</span><span class="sxs-lookup"><span data-stu-id="e7c0b-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="e7c0b-110">Tento druh řízení nad rozložením struktury je užitečný při volání platformy.</span><span class="sxs-lookup"><span data-stu-id="e7c0b-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7c0b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7c0b-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="e7c0b-112">Průvodce programováním Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7c0b-112">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="e7c0b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="e7c0b-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="e7c0b-114">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7c0b-114">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="e7c0b-115">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7c0b-115">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="e7c0b-116">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7c0b-116">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="e7c0b-117">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7c0b-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
