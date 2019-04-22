---
title: 'Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 00fefcc138164288d872cd339f165dc6ffc0131a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834189"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="7a635-102">Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a635-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="7a635-103">Tento příklad vytvoří dlouhý řetězec z mnoha menších řetězců pomocí <xref:System.Text.StringBuilder> třídy.</span><span class="sxs-lookup"><span data-stu-id="7a635-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="7a635-104"><xref:System.Text.StringBuilder> Třída je efektivnější než `&=` operátoru pro zřetězení řetězců mnoho.</span><span class="sxs-lookup"><span data-stu-id="7a635-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a635-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a635-105">Example</span></span>  
 <span data-ttu-id="7a635-106">Následující příklad vytvoří instance <xref:System.Text.StringBuilder> připojí 1 000 řetězce do této instance třídy a vrátí řetězcové vyjádření.</span><span class="sxs-lookup"><span data-stu-id="7a635-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]  
  
## <a name="see-also"></a><span data-ttu-id="7a635-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a635-107">See also</span></span>

- [<span data-ttu-id="7a635-108">Používání třídy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="7a635-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="7a635-109">&= – operátor</span><span class="sxs-lookup"><span data-stu-id="7a635-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="7a635-110">Řetězce</span><span class="sxs-lookup"><span data-stu-id="7a635-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="7a635-111">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="7a635-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="7a635-112">Práce s řetězci</span><span class="sxs-lookup"><span data-stu-id="7a635-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
