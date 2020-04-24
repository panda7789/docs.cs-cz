---
title: 'Postup: vytvoření řetězců pomocí StringBuilder'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645326"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="a2ae8-102">Postup: vytvoření řetězců pomocí StringBuilder v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2ae8-102">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="a2ae8-103">Tento příklad vytvoří dlouhý řetězec z mnoha <xref:System.Text.StringBuilder> menších řetězců pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="a2ae8-104">Třída <xref:System.Text.StringBuilder> je efektivnější než `&=` operátor pro zřetězení mnoho řetězců.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="a2ae8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a2ae8-105">Example</span></span>

<span data-ttu-id="a2ae8-106">Následující příklad vytvoří instanci <xref:System.Text.StringBuilder> třídy, připojí k této instanci 1 000 řetězců a pak vrátí její řetězcovou reprezentaci:</span><span class="sxs-lookup"><span data-stu-id="a2ae8-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="a2ae8-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2ae8-107">See also</span></span>

- [<span data-ttu-id="a2ae8-108">Používání třídy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="a2ae8-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="a2ae8-109">&= Operátor</span><span class="sxs-lookup"><span data-stu-id="a2ae8-109">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="a2ae8-110">Řetězce</span><span class="sxs-lookup"><span data-stu-id="a2ae8-110">Strings</span></span>](index.md)
- [<span data-ttu-id="a2ae8-111">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="a2ae8-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="a2ae8-112">Práce s řetězci</span><span class="sxs-lookup"><span data-stu-id="a2ae8-112">Manipulating Strings</span></span>](../../../../standard/base-types/best-practices-strings.md)
