---
title: U polí deklarovaných jako členy struktury nejde deklarovat počáteční velikost.
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 83342b780c0fa7c3a2e0a6797b80ef788117ae92
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250157"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="3a51d-102">U polí deklarovaných jako členy struktury nejde deklarovat počáteční velikost.</span><span class="sxs-lookup"><span data-stu-id="3a51d-102">Arrays declared as structure members cannot be declared with an initial size</span></span>

<span data-ttu-id="3a51d-103">Pole ve struktuře je deklarováno s počáteční velikostí.</span><span class="sxs-lookup"><span data-stu-id="3a51d-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="3a51d-104">Nemůžete inicializovat žádný element struktury a deklarovat velikost pole je jedna forma inicializace.</span><span class="sxs-lookup"><span data-stu-id="3a51d-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>

<span data-ttu-id="3a51d-105">**ID chyby:** BC31043</span><span class="sxs-lookup"><span data-stu-id="3a51d-105">**Error ID:** BC31043</span></span>

## <a name="example"></a><span data-ttu-id="3a51d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a51d-106">Example</span></span>

<span data-ttu-id="3a51d-107">Následující příklad generuje BC31043:</span><span class="sxs-lookup"><span data-stu-id="3a51d-107">The following example generates BC31043:</span></span>

```vb
Structure DemoStruct
    Public demoArray(9) As Integer
End Structure
```

## <a name="to-correct-this-error"></a><span data-ttu-id="3a51d-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3a51d-108">To correct this error</span></span>

1. <span data-ttu-id="3a51d-109">Definujte pole ve vaší struktuře jako dynamické (bez počáteční velikosti).</span><span class="sxs-lookup"><span data-stu-id="3a51d-109">Define the array in your structure as dynamic (no initial size).</span></span>

2. <span data-ttu-id="3a51d-110">Pokud požadujete určitou velikost pole, můžete změnit rozměr dynamického pole pomocí [příkazu ReDim](../statements/redim-statement.md) , pokud je váš kód spuštěn.</span><span class="sxs-lookup"><span data-stu-id="3a51d-110">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="3a51d-111">Následující příklad znázorňuje toto:</span><span class="sxs-lookup"><span data-stu-id="3a51d-111">The following example illustrates this:</span></span>
  
    ```vb
    Structure DemoStruct
        Public demoArray() As Integer
    End Structure
    Sub UseStruct()
        Dim struct As DemoStruct  
        ReDim struct.demoArray(9)
        Struct.demoArray(2) = 777
    End Sub  
    ```
  
## <a name="see-also"></a><span data-ttu-id="3a51d-112">Související témata</span><span class="sxs-lookup"><span data-stu-id="3a51d-112">See also</span></span>

- [<span data-ttu-id="3a51d-113">Řadách</span><span class="sxs-lookup"><span data-stu-id="3a51d-113">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="3a51d-114">Postupy: deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="3a51d-114">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
