---
title: 'Postupy: vytvoření sjednocení jazyka C-C pomocí atributů'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: ebab0ad947f776932f9379af3969e369eeec1941
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400678"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="eb475-102">Postupy: vytváření sjednocení C/C++ pomocí atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb475-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>

<span data-ttu-id="eb475-103">Pomocí atributů můžete přizpůsobit způsob, jakým jsou struktury rozloženy v paměti.</span><span class="sxs-lookup"><span data-stu-id="eb475-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="eb475-104">Můžete například vytvořit, co je v C/C++ známé jako sjednocení pomocí `StructLayout(LayoutKind.Explicit)` `FieldOffset` atributů a.</span><span class="sxs-lookup"><span data-stu-id="eb475-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="eb475-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb475-105">Example</span></span>

<span data-ttu-id="eb475-106">V tomto segmentu kódu všechna pole `TestUnion` začínají ve stejném umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="eb475-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

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

## <a name="example"></a><span data-ttu-id="eb475-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb475-107">Example</span></span>

<span data-ttu-id="eb475-108">Následuje další příklad, kdy se pole spouštějí v různých explicitních nastaveních umístění.</span><span class="sxs-lookup"><span data-stu-id="eb475-108">The following is another example where fields start at different explicitly set locations.</span></span>

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

<span data-ttu-id="eb475-109">Dvě celočíselná pole `i1` a `i2` sdílejí stejná umístění v paměti jako `lg` .</span><span class="sxs-lookup"><span data-stu-id="eb475-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="eb475-110">Tento druh řízení nad rozložením struktury je užitečný při volání platformy.</span><span class="sxs-lookup"><span data-stu-id="eb475-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb475-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb475-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="eb475-112">Příručka k programování v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb475-112">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="eb475-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="eb475-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="eb475-114">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb475-114">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="eb475-115">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb475-115">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="eb475-116">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb475-116">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="eb475-117">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb475-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
