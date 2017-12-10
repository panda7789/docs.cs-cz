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
ms.openlocfilehash: bcb5291737a9f4763f680daaf625c58d308423f8
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="8e811-102">Postupy: vytváření sjednocení C/C++ pomocí atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e811-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>
<span data-ttu-id="8e811-103">Pomocí atributů můžete přizpůsobit, jak jsou rozloženy struktury v paměti.</span><span class="sxs-lookup"><span data-stu-id="8e811-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="8e811-104">Například můžete vytvořit, která se označuje jako sjednocení v jazyce C/C++ pomocí `StructLayout(LayoutKind.Explicit)` a `FieldOffset` atributy.</span><span class="sxs-lookup"><span data-stu-id="8e811-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e811-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e811-105">Example</span></span>  
 <span data-ttu-id="8e811-106">V tomto segmentu kódu, všechna pole z `TestUnion` spustit ve stejném umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="8e811-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="8e811-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e811-107">Example</span></span>  
 <span data-ttu-id="8e811-108">Zde je další příklad kde počáteční pole v různých explicitně nastavit umístění.</span><span class="sxs-lookup"><span data-stu-id="8e811-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
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
  
 <span data-ttu-id="8e811-109">Pole dva celé číslo `i1` a `i2`, sdílet stejné umístění paměti jako `lg`.</span><span class="sxs-lookup"><span data-stu-id="8e811-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="8e811-110">Tento druh kontrolu nad struktura rozložení je užitečné při použití vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="8e811-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e811-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e811-111">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="8e811-112">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e811-112">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="8e811-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="8e811-113">Attributes</span></span>](../../../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="8e811-114">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e811-114">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="8e811-115">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e811-115">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="8e811-116">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e811-116">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="8e811-117">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e811-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
