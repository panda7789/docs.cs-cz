---
title: "Parametry typů nelze použít jako kvalifikátory."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 58be51e0c05750ee044f0287cde8db037718b4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="55505-102">Parametry typů nelze použít jako kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="55505-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="55505-103">Programovací element je kvalifikovaný s kvalifikací řetězec, který obsahuje parametr typu.</span><span class="sxs-lookup"><span data-stu-id="55505-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="55505-104">Parametr typu představuje požadavek pro typ, který je nutné zadat, když se obecného typu.</span><span class="sxs-lookup"><span data-stu-id="55505-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="55505-105">Nereprezentuje konkrétního typu definované.</span><span class="sxs-lookup"><span data-stu-id="55505-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="55505-106">Kvalifikace řetězec musí obsahovat pouze elementy, které jsou definovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="55505-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="55505-107">Tato chyba může generovat následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="55505-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="55505-108">**ID chyby:** BC32098</span><span class="sxs-lookup"><span data-stu-id="55505-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="55505-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="55505-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="55505-110">Odeberte parametr typu z řetězce kvalifikaci, nebo nahraďte určitého typu.</span><span class="sxs-lookup"><span data-stu-id="55505-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2.  <span data-ttu-id="55505-111">Pokud potřebujete použít vytvořený typ najít programovací element jako kvalifikované, je nutné použít další logiku programu.</span><span class="sxs-lookup"><span data-stu-id="55505-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55505-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="55505-112">See Also</span></span>  
 [<span data-ttu-id="55505-113">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="55505-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="55505-114">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55505-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="55505-115">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="55505-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
