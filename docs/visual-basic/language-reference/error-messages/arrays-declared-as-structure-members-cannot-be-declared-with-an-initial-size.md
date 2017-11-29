---
title: "U polí deklarovaných jako členové struktury nelze deklarovat počáteční velikost."
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords: BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 983154a144a79991c86db5056ad0e0e563a3ba73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="ba704-102">U polí deklarovaných jako členové struktury nelze deklarovat počáteční velikost.</span><span class="sxs-lookup"><span data-stu-id="ba704-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="ba704-103">Pole ve struktuře je deklarována s počáteční velikostí.</span><span class="sxs-lookup"><span data-stu-id="ba704-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="ba704-104">Nelze inicializovat libovolný element, struktura a deklarace velikost pole je jednu formu inicializace.</span><span class="sxs-lookup"><span data-stu-id="ba704-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="ba704-105">**ID chyby:** BC31043</span><span class="sxs-lookup"><span data-stu-id="ba704-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ba704-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ba704-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="ba704-107">Definujte pole v strukturu jako dynamický (žádné počáteční velikost).</span><span class="sxs-lookup"><span data-stu-id="ba704-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2.  <span data-ttu-id="ba704-108">Pokud budete potřebovat určité velikosti pole, můžete redimension dynamické pole s [ReDim – příkaz](../../../visual-basic/language-reference/statements/redim-statement.md) při spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="ba704-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="ba704-109">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ba704-109">The following example illustrates this.</span></span>  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ba704-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba704-110">See Also</span></span>  
 [<span data-ttu-id="ba704-111">Pole</span><span class="sxs-lookup"><span data-stu-id="ba704-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="ba704-112">Postupy: definice struktury</span><span class="sxs-lookup"><span data-stu-id="ba704-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
