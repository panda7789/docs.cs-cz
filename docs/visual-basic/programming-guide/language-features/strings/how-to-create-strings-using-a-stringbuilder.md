---
title: 'Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 5cd118ddd196bdf84045ae8b02fe590e5b087e4e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967955"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="877fd-102">Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="877fd-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="877fd-103">Tento příklad vytvoří dlouhý řetězec z mnoha menších řetězců pomocí <xref:System.Text.StringBuilder> třídy.</span><span class="sxs-lookup"><span data-stu-id="877fd-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="877fd-104"><xref:System.Text.StringBuilder> Třída je efektivnější než `&=` operátoru pro zřetězení řetězců mnoho.</span><span class="sxs-lookup"><span data-stu-id="877fd-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="877fd-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="877fd-105">Example</span></span>  
 <span data-ttu-id="877fd-106">Následující příklad vytvoří instance <xref:System.Text.StringBuilder> připojí 1 000 řetězce do této instance třídy a vrátí řetězcové vyjádření.</span><span class="sxs-lookup"><span data-stu-id="877fd-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]  
  
## <a name="see-also"></a><span data-ttu-id="877fd-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="877fd-107">See also</span></span>
- [<span data-ttu-id="877fd-108">Používání třídy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="877fd-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="877fd-109">&= – operátor</span><span class="sxs-lookup"><span data-stu-id="877fd-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="877fd-110">Řetězce</span><span class="sxs-lookup"><span data-stu-id="877fd-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="877fd-111">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="877fd-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="877fd-112">Práce s řetězci</span><span class="sxs-lookup"><span data-stu-id="877fd-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
