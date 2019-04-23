---
title: Parametry typů nelze použít jako kvalifikátory.
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: ba7348ae50965ffcf2719b20934451916c8fa95a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296352"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="03e7e-102">Parametry typů nelze použít jako kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="03e7e-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="03e7e-103">Programovací element je kvalifikován s kvalifikací řetězec, který obsahuje parametr typu.</span><span class="sxs-lookup"><span data-stu-id="03e7e-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="03e7e-104">Parametr typu představuje požadavek pro typ, který se nemusí zadávat, když je vytvořen obecného typu.</span><span class="sxs-lookup"><span data-stu-id="03e7e-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="03e7e-105">To nepředstavuje konkrétní typ definovaný.</span><span class="sxs-lookup"><span data-stu-id="03e7e-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="03e7e-106">Kvalifikace řetězec musí obsahovat pouze prvky, které jsou definovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="03e7e-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="03e7e-107">Tato chyba může generovat následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="03e7e-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="03e7e-108">**ID chyby:** BC32098</span><span class="sxs-lookup"><span data-stu-id="03e7e-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="03e7e-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="03e7e-109">To correct this error</span></span>  
  
1. <span data-ttu-id="03e7e-110">Odeberte parametr typu z řetězce kvalifikaci, nebo nahraďte určitého typu.</span><span class="sxs-lookup"><span data-stu-id="03e7e-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2. <span data-ttu-id="03e7e-111">Pokud budete muset použít konstruovaný typ najít programovací element je kvalifikován, musíte použít další logiku programu.</span><span class="sxs-lookup"><span data-stu-id="03e7e-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e7e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03e7e-112">See also</span></span>

- [<span data-ttu-id="03e7e-113">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="03e7e-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="03e7e-114">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03e7e-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="03e7e-115">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="03e7e-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
