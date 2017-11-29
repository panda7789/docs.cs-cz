---
title: "Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54d604fc08dd97e0e31f9bcec148431374e8ef8f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic
Tento příklad ukazuje, jak používat <xref:System.String.Chars%2A> vlastnost, která má přístup ke znakům v zadaném umístění v řetězci.  
  
## <a name="example"></a>Příklad  
 Někdy je užitečné používat data o znaky v řetězec vašeho a pozice z těchto znaků v rámci vaší řetězec. Řetězce si můžete představit jako pole znaků (`Char` instance); určitý znak můžete načíst odkazem index tento znak prostřednictvím <xref:System.String.Chars%2A> vlastnost.  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 `index` Parametr <xref:System.String.Chars%2A> vlastnost je počítáno od nuly.  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.String.Chars%2A> Vlastnost vrátí znak na zadané pozici. Některé znaky kódování Unicode však může být reprezentovaný více než jeden znak. Další informace o tom, jak pracovat s znaky znakové sady Unicode, najdete v části [postupy: převedení řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A> Vlastnost vyvolává <xref:System.IndexOutOfRangeException> výjimka pokud `index` parametr je větší než nebo rovna hodnotě délky řetězce, nebo pokud ji je menší než nula  
  
## <a name="see-also"></a>Viz také  
 <xref:System.String.Chars%2A>  
 [Postupy: převedení řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [Převod mezi řetězci a ostatními typy dat v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)
