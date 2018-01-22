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
ms.openlocfilehash: 9def5da754d9075a8b498ac80e624caae5c97b96
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic
Tento příklad vytvoří dlouhý řetězec z mnoha menší řetězců pomocí <xref:System.Text.StringBuilder> třídy. <xref:System.Text.StringBuilder> Třída je efektivnější než `&=` operátor pro zřetězení mnoha řetězců.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří instanci <xref:System.Text.StringBuilder> třída, připojí 1000 řetězce do této instance a vrátí její řetězcová reprezentace.  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Používání třídy StringBuilder](../../../../standard/base-types/stringbuilder.md)  
 [&= – operátor](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Vytváření nových řetězců](../../../../standard/base-types/creating-new.md)  
 [Práce s řetězci](../../../../standard/base-types/manipulating-strings.md)  
 [Ukázka řetězce](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)
