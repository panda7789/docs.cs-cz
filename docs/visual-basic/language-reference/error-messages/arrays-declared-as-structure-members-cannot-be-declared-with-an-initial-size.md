---
title: U polí deklarovaných jako členové struktury nelze deklarovat počáteční velikost.
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: de9d77aa9ea853b6f044e91878044115588ca77c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701252"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="a5eaa-102">U polí deklarovaných jako členové struktury nelze deklarovat počáteční velikost.</span><span class="sxs-lookup"><span data-stu-id="a5eaa-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="a5eaa-103">Pole ve struktuře je deklarováno s počáteční velikostí.</span><span class="sxs-lookup"><span data-stu-id="a5eaa-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="a5eaa-104">Nemůžete inicializovat žádný element struktury a deklarovat velikost pole je jedna forma inicializace.</span><span class="sxs-lookup"><span data-stu-id="a5eaa-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="a5eaa-105">**ID chyby:** BC31043</span><span class="sxs-lookup"><span data-stu-id="a5eaa-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a5eaa-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a5eaa-106">To correct this error</span></span>  
  
1. <span data-ttu-id="a5eaa-107">Definujte pole ve vaší struktuře jako dynamické (bez počáteční velikosti).</span><span class="sxs-lookup"><span data-stu-id="a5eaa-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2. <span data-ttu-id="a5eaa-108">Pokud požadujete určitou velikost pole, můžete změnit rozměr dynamického pole pomocí [příkazu ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) , pokud je váš kód spuštěn.</span><span class="sxs-lookup"><span data-stu-id="a5eaa-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="a5eaa-109">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="a5eaa-109">The following example illustrates this.</span></span>  
  
    ```vb  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a5eaa-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5eaa-110">See also</span></span>

- [<span data-ttu-id="a5eaa-111">Pole</span><span class="sxs-lookup"><span data-stu-id="a5eaa-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="a5eaa-112">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="a5eaa-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
