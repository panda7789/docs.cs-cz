---
title: Statické a pozdní vazby
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: bd70d8642c18e9bc2baba8128ec908c88e0477ce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345188"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="a4289-102">Statické a pozdní vazby (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4289-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="a4289-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span><span class="sxs-lookup"><span data-stu-id="a4289-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="a4289-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span><span class="sxs-lookup"><span data-stu-id="a4289-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="a4289-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span><span class="sxs-lookup"><span data-stu-id="a4289-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="a4289-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="a4289-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="a4289-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span><span class="sxs-lookup"><span data-stu-id="a4289-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="a4289-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span><span class="sxs-lookup"><span data-stu-id="a4289-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="a4289-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span><span class="sxs-lookup"><span data-stu-id="a4289-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="a4289-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span><span class="sxs-lookup"><span data-stu-id="a4289-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="a4289-111">Advantages of Early Binding</span><span class="sxs-lookup"><span data-stu-id="a4289-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="a4289-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span><span class="sxs-lookup"><span data-stu-id="a4289-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="a4289-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span><span class="sxs-lookup"><span data-stu-id="a4289-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="a4289-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span><span class="sxs-lookup"><span data-stu-id="a4289-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="a4289-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span><span class="sxs-lookup"><span data-stu-id="a4289-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4289-116">Late binding can only be used to access type members that are declared as `Public`.</span><span class="sxs-lookup"><span data-stu-id="a4289-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="a4289-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span><span class="sxs-lookup"><span data-stu-id="a4289-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4289-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4289-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="a4289-119">Doba života objektu: Vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="a4289-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="a4289-120">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="a4289-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
