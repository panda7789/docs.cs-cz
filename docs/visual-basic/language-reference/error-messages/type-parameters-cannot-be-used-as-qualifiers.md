---
title: Parametry typů nelze použít jako kvalifikátory.
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 88b5f365c47b98964d9f5a0d22a941d85dcfb95f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592140"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="69d61-102">Parametry typů nelze použít jako kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="69d61-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="69d61-103">Programovací element je kvalifikován pomocí řetězce kvalifikace, který obsahuje parametr typu.</span><span class="sxs-lookup"><span data-stu-id="69d61-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="69d61-104">Parametr typu představuje požadavek pro typ, který se má zadat při sestavení obecného typu.</span><span class="sxs-lookup"><span data-stu-id="69d61-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="69d61-105">Nepředstavuje konkrétní definovaný typ.</span><span class="sxs-lookup"><span data-stu-id="69d61-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="69d61-106">Kvalifikační řetězec musí zahrnovat pouze prvky, které jsou definovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="69d61-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="69d61-107">Následující příkazy mohou vygenerovat tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="69d61-107">The following statements can generate this error.</span></span>  
  
```vb  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="69d61-108">**ID chyby:** BC32098</span><span class="sxs-lookup"><span data-stu-id="69d61-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="69d61-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="69d61-109">To correct this error</span></span>  
  
1. <span data-ttu-id="69d61-110">Odeberte parametr typu z řetězce kvalifikace nebo ho nahraďte definovaným typem.</span><span class="sxs-lookup"><span data-stu-id="69d61-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2. <span data-ttu-id="69d61-111">Pokud potřebujete použít konstruovaný typ k vyhledání programovacího prvku, který je kvalifikován, je nutné použít další logiku programu.</span><span class="sxs-lookup"><span data-stu-id="69d61-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69d61-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69d61-112">See also</span></span>

- [<span data-ttu-id="69d61-113">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="69d61-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="69d61-114">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69d61-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="69d61-115">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="69d61-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
