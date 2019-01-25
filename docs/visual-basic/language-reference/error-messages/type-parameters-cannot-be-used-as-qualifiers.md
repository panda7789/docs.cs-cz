---
title: Parametry typů nelze použít jako kvalifikátory.
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 8ee0fd5822c22da090aa0abee679e2f68e0fc1d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659699"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="b3d1b-102">Parametry typů nelze použít jako kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="b3d1b-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="b3d1b-103">Programovací element je kvalifikován s kvalifikací řetězec, který obsahuje parametr typu.</span><span class="sxs-lookup"><span data-stu-id="b3d1b-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="b3d1b-104">Parametr typu představuje požadavek pro typ, který se nemusí zadávat, když je vytvořen obecného typu.</span><span class="sxs-lookup"><span data-stu-id="b3d1b-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="b3d1b-105">To nepředstavuje konkrétní typ definovaný.</span><span class="sxs-lookup"><span data-stu-id="b3d1b-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="b3d1b-106">Kvalifikace řetězec musí obsahovat pouze prvky, které jsou definovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="b3d1b-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="b3d1b-107">Tato chyba může generovat následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="b3d1b-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="b3d1b-108">**ID chyby:** BC32098</span><span class="sxs-lookup"><span data-stu-id="b3d1b-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3d1b-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b3d1b-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="b3d1b-110">Odeberte parametr typu z řetězce kvalifikaci, nebo nahraďte určitého typu.</span><span class="sxs-lookup"><span data-stu-id="b3d1b-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2.  <span data-ttu-id="b3d1b-111">Pokud budete muset použít konstruovaný typ najít programovací element je kvalifikován, musíte použít další logiku programu.</span><span class="sxs-lookup"><span data-stu-id="b3d1b-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d1b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3d1b-112">See also</span></span>
- [<span data-ttu-id="b3d1b-113">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="b3d1b-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="b3d1b-114">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3d1b-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="b3d1b-115">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="b3d1b-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
