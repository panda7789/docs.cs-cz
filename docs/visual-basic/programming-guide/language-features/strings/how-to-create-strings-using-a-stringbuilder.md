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
 [Ukázka řetězce](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))
