---
title: Statické a pozdní vazby (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa63a250ce6bdf4a8a34d9f1c0284a9d04e75f38
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="3746d-102">Statické a pozdní vazby (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3746d-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="3746d-103">Visual Basic – kompilátor provede proces nazvaný `binding` když je objekt přiřazení proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="3746d-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="3746d-104">Je-li objekt *časné* když je přiřazený k proměnné deklarované jako konkrétní typy objektů.</span><span class="sxs-lookup"><span data-stu-id="3746d-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="3746d-105">Časná vázaným objektům povolení kompilátoru přidělit paměť a provádět další optimalizace před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="3746d-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="3746d-106">Například následující fragment kódu deklaruje proměnnou být typu <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="3746d-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 <span data-ttu-id="3746d-107">Protože <xref:System.IO.FileStream> je konkrétní typy objektů, instance přiřazené `FS` je již v rané fázi vázána.</span><span class="sxs-lookup"><span data-stu-id="3746d-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="3746d-108">Naopak je objekt *pozdní vazba* když je přiřazený k proměnné deklarované jako typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="3746d-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="3746d-109">Objekty tohoto typu udržení odkazů na libovolného objektu, ale nemají mnoho výhod časné vazby objektů.</span><span class="sxs-lookup"><span data-stu-id="3746d-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="3746d-110">Například následující fragment kódu deklaruje proměnné objektu pro objekt vrácený `CreateObject` funkce:</span><span class="sxs-lookup"><span data-stu-id="3746d-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="3746d-111">Výhody časná vazba</span><span class="sxs-lookup"><span data-stu-id="3746d-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="3746d-112">Měli byste použít objekty časné vazby, pokud je to možné, protože kompilátor, aby byl důležité optimalizace, které vrací efektivnější aplikace.</span><span class="sxs-lookup"><span data-stu-id="3746d-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="3746d-113">Objekty časné vazby je výrazně rychlejší než pozdní vazbou a snadněji číst a údržbě, protože s informacemi o tom přesně jaký typ objektů, které používají váš kód.</span><span class="sxs-lookup"><span data-stu-id="3746d-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="3746d-114">Časná vazba jiné výhodou je, že umožňuje užitečných funkcí, jako je doplňování kódu pro automatické a dynamické nápovědy, protože integrované vývojové prostředí (IDE) sady Visual Studio můžete určit přesně jaký typ objektu práci se při úpravě kód.</span><span class="sxs-lookup"><span data-stu-id="3746d-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="3746d-115">Časná vazba snižuje počet a závažnost běhové chyby, protože umožňuje kompilátoru zprávy o chybách, když je program kompilován.</span><span class="sxs-lookup"><span data-stu-id="3746d-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3746d-116">Pozdní vazba pouze umožňuje přístup ke členům typu, které jsou deklarované jako `Public`.</span><span class="sxs-lookup"><span data-stu-id="3746d-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="3746d-117">Přístup ke členům deklarován jako `Friend` nebo `Protected Friend` výsledkem chyba spuštění.</span><span class="sxs-lookup"><span data-stu-id="3746d-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3746d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3746d-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>  
 [<span data-ttu-id="3746d-119">Doba života objektu: Vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="3746d-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [<span data-ttu-id="3746d-120">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="3746d-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
