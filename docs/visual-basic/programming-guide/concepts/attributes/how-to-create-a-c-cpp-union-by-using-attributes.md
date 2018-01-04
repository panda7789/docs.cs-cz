---
title: "Postupy: vytváření sjednocení C-C++ pomocí atributů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51d04c573e91a351c48edefebdb3d32fce1d306f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="13449-102">Postupy: vytváření sjednocení C/C++ pomocí atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13449-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>
<span data-ttu-id="13449-103">Pomocí atributů můžete přizpůsobit, jak jsou rozloženy struktury v paměti.</span><span class="sxs-lookup"><span data-stu-id="13449-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="13449-104">Například můžete vytvořit, která se označuje jako sjednocení v jazyce C/C++ pomocí `StructLayout(LayoutKind.Explicit)` a `FieldOffset` atributy.</span><span class="sxs-lookup"><span data-stu-id="13449-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13449-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="13449-105">Example</span></span>  
 <span data-ttu-id="13449-106">V tomto segmentu kódu, všechna pole z `TestUnion` spustit ve stejném umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="13449-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="13449-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="13449-107">Example</span></span>  
 <span data-ttu-id="13449-108">Zde je další příklad kde počáteční pole v různých explicitně nastavit umístění.</span><span class="sxs-lookup"><span data-stu-id="13449-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
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
  
 <span data-ttu-id="13449-109">Pole dva celé číslo `i1` a `i2`, sdílet stejné umístění paměti jako `lg`.</span><span class="sxs-lookup"><span data-stu-id="13449-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="13449-110">Tento druh kontrolu nad struktura rozložení je užitečné při použití vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="13449-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13449-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="13449-111">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="13449-112">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13449-112">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="13449-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="13449-113">Attributes</span></span>](../../../../standard/attributes/index.md)  
 [<span data-ttu-id="13449-114">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13449-114">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="13449-115">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13449-115">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="13449-116">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13449-116">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="13449-117">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13449-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
