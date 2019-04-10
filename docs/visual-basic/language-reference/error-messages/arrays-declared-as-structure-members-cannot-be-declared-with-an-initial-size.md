---
title: U polí deklarovaných jako členové struktury nelze deklarovat počáteční velikost.
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 5d58b531b670715716e849cd37227bc899195df6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335300"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="8d4ee-102">U polí deklarovaných jako členové struktury nelze deklarovat počáteční velikost.</span><span class="sxs-lookup"><span data-stu-id="8d4ee-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="8d4ee-103">Pole ve struktuře je deklarována s počáteční velikostí.</span><span class="sxs-lookup"><span data-stu-id="8d4ee-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="8d4ee-104">Nelze inicializovat libovolný prvek struktury a deklarace velikost pole je jeden forma inicializace.</span><span class="sxs-lookup"><span data-stu-id="8d4ee-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="8d4ee-105">**ID chyby:** BC31043</span><span class="sxs-lookup"><span data-stu-id="8d4ee-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8d4ee-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8d4ee-106">To correct this error</span></span>  
  
1. <span data-ttu-id="8d4ee-107">Definování pole ve struktuře jako dynamický (žádná počáteční velikost).</span><span class="sxs-lookup"><span data-stu-id="8d4ee-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2. <span data-ttu-id="8d4ee-108">Pokud potřebujete velikost pole, můžete redimension dynamická pole [ReDim – příkaz](../../../visual-basic/language-reference/statements/redim-statement.md) při spouštění kódu.</span><span class="sxs-lookup"><span data-stu-id="8d4ee-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="8d4ee-109">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="8d4ee-109">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d4ee-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d4ee-110">See also</span></span>

- [<span data-ttu-id="8d4ee-111">Pole</span><span class="sxs-lookup"><span data-stu-id="8d4ee-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="8d4ee-112">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="8d4ee-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
