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
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Postupy: Vytváření řetězců pomocí StringBuilder v jazyce Visual Basic
Tento příklad vytvoří dlouhý řetězec z mnoha menší řetězců pomocí <xref:System.Text.StringBuilder> třídy. <xref:System.Text.StringBuilder> Třída je efektivnější než `&=` operátor pro zřetězení mnoha řetězců.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří instanci <xref:System.Text.StringBuilder> třída, připojí 1000 řetězce do této instance a vrátí její řetězcová reprezentace.  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Používání třídy StringBuilder](../../../../standard/base-types/stringbuilder.md)  
 [& = – operátor](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Vytváření nových řetězců](../../../../standard/base-types/creating-new.md)  
 [Manipulace s řetězci](../../../../standard/base-types/manipulating-strings.md)  
 [Ukázka řetězce](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)
