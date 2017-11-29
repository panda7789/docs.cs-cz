---
title: "Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f4a682c7ae32ace0b1f859d52963342546a83f29
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="d78e0-102">Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d78e0-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="d78e0-103">Deklarace proměnné [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md) zadáním `As Object` v [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d78e0-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="d78e0-104">Přiřazení objektu k tuto proměnnou tím, že objekt za znaménkem rovnítka (`=`) v klauzuli příkaz nebo inicializace přiřazení.</span><span class="sxs-lookup"><span data-stu-id="d78e0-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d78e0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d78e0-105">Example</span></span>  
 <span data-ttu-id="d78e0-106">Následující příklad deklaruje `Object` proměnnou a přiřadí aktuální instance k němu.</span><span class="sxs-lookup"><span data-stu-id="d78e0-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="d78e0-107">Deklarace a přiřazení můžete kombinovat podle inicializace proměnné jako součást jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="d78e0-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="d78e0-108">Následující příklad je ekvivalentní v předcházejícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d78e0-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d78e0-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d78e0-109">Compiling the Code</span></span>  
 <span data-ttu-id="d78e0-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="d78e0-110">This example requires:</span></span>  
  
-   <span data-ttu-id="d78e0-111">Odkaz na <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d78e0-111">A reference to the <xref:System> namespace.</span></span>  
  
-   <span data-ttu-id="d78e0-112">Třída, struktura nebo modul, ve kterém se umístí `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d78e0-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
-   <span data-ttu-id="d78e0-113">Postup, do kterého chcete vložit příkaz přiřazení.</span><span class="sxs-lookup"><span data-stu-id="d78e0-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d78e0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d78e0-114">See Also</span></span>  
 [<span data-ttu-id="d78e0-115">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="d78e0-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="d78e0-116">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="d78e0-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="d78e0-117">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="d78e0-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="d78e0-118">Object – datový typ</span><span class="sxs-lookup"><span data-stu-id="d78e0-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="d78e0-119">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="d78e0-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="d78e0-120">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="d78e0-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="d78e0-121">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="d78e0-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
