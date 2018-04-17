---
title: 'Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0e15c7df07822ee104a88525c209768c05470e3
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="db2f0-102">Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="db2f0-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="db2f0-103">Tento příklad vytvoří dlouhý řetězec z mnoha menší řetězců pomocí <xref:System.Text.StringBuilder> třídy.</span><span class="sxs-lookup"><span data-stu-id="db2f0-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="db2f0-104"><xref:System.Text.StringBuilder> Třída je efektivnější než `&=` operátor pro zřetězení mnoha řetězců.</span><span class="sxs-lookup"><span data-stu-id="db2f0-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db2f0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="db2f0-105">Example</span></span>  
 <span data-ttu-id="db2f0-106">Následující příklad vytvoří instanci <xref:System.Text.StringBuilder> třída, připojí 1000 řetězce do této instance a vrátí její řetězcová reprezentace.</span><span class="sxs-lookup"><span data-stu-id="db2f0-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="db2f0-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="db2f0-107">See Also</span></span>  
 [<span data-ttu-id="db2f0-108">Používání třídy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="db2f0-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)  
 [<span data-ttu-id="db2f0-109">&= – operátor</span><span class="sxs-lookup"><span data-stu-id="db2f0-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="db2f0-110">Řetězce</span><span class="sxs-lookup"><span data-stu-id="db2f0-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="db2f0-111">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="db2f0-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="db2f0-112">Práce s řetězci</span><span class="sxs-lookup"><span data-stu-id="db2f0-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)  
 <span data-ttu-id="db2f0-113">[Ukázka řetězce](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="db2f0-113">[Strings Sample](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span></span>
