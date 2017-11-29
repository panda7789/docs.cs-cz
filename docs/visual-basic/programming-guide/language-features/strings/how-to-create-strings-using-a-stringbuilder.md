---
title: "Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c799794b319843b0239ce9589e0c556c603c8617
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="aadeb-102">Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aadeb-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="aadeb-103">Tento příklad vytvoří dlouhý řetězec z mnoha menší řetězců pomocí <xref:System.Text.StringBuilder> třídy.</span><span class="sxs-lookup"><span data-stu-id="aadeb-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="aadeb-104"><xref:System.Text.StringBuilder> Třída je efektivnější než `&=` operátor pro zřetězení mnoha řetězců.</span><span class="sxs-lookup"><span data-stu-id="aadeb-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aadeb-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="aadeb-105">Example</span></span>  
 <span data-ttu-id="aadeb-106">Následující příklad vytvoří instanci <xref:System.Text.StringBuilder> třída, připojí 1000 řetězce do této instance a vrátí její řetězcová reprezentace.</span><span class="sxs-lookup"><span data-stu-id="aadeb-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="aadeb-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="aadeb-107">See Also</span></span>  
 [<span data-ttu-id="aadeb-108">Používání třídy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="aadeb-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)  
 [<span data-ttu-id="aadeb-109">& = – operátor</span><span class="sxs-lookup"><span data-stu-id="aadeb-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="aadeb-110">Řetězce</span><span class="sxs-lookup"><span data-stu-id="aadeb-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="aadeb-111">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="aadeb-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="aadeb-112">Manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="aadeb-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)  
 [<span data-ttu-id="aadeb-113">Ukázka řetězce</span><span class="sxs-lookup"><span data-stu-id="aadeb-113">Strings Sample</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)
