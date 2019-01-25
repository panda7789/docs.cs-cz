---
title: 'Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 84f0f41cf8ee23466d47dae3b1068c3bc5334072
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528443"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="697e7-102">Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="697e7-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="697e7-103">Tento příklad vytvoří dlouhý řetězec z mnoha menších řetězců pomocí <xref:System.Text.StringBuilder> třídy.</span><span class="sxs-lookup"><span data-stu-id="697e7-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="697e7-104"><xref:System.Text.StringBuilder> Třída je efektivnější než `&=` operátoru pro zřetězení řetězců mnoho.</span><span class="sxs-lookup"><span data-stu-id="697e7-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="697e7-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="697e7-105">Example</span></span>  
 <span data-ttu-id="697e7-106">Následující příklad vytvoří instance <xref:System.Text.StringBuilder> připojí 1 000 řetězce do této instance třídy a vrátí řetězcové vyjádření.</span><span class="sxs-lookup"><span data-stu-id="697e7-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="697e7-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="697e7-107">See also</span></span>
- [<span data-ttu-id="697e7-108">Používání třídy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="697e7-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="697e7-109">&= – operátor</span><span class="sxs-lookup"><span data-stu-id="697e7-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="697e7-110">Řetězce</span><span class="sxs-lookup"><span data-stu-id="697e7-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="697e7-111">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="697e7-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="697e7-112">Práce s řetězci</span><span class="sxs-lookup"><span data-stu-id="697e7-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
- <span data-ttu-id="697e7-113">[Řetězce – ukázka](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="697e7-113">[Strings Sample](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span></span>
