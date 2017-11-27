---
title: "Postupy: Vytvoření dokumentace XML v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 63b6485de5aba2ca49d54a057045bec2062d12dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Postupy: Vytvoření dokumentace XML v jazyce Visual Basic
Tento příklad ukazuje, jak přidat dokumentační komentáře XML do vašeho kódu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>K vytvoření dokumentace XML pro typ nebo člen  
  
1.  V **Editor kódu**, umístěte kurzor na řádku výše typ nebo člen, pro který chcete vytvořit dokumentaci.  
  
2.  Typ `'''` (tři jednoduchých uvozovek).  
  
     Kostru XML pro typ nebo člen je přidaný do **Editor kódu**.  
  
3.  Přidejte popisné informace mezi odpovídající značky.  
  
    > [!NOTE]
    >  Pokud chcete přidat další řádky uvnitř bloku dokumentace XML, musí každý řádek začínat `'''`.  
  
4.  Přidejte další kód, který používá typ nebo člen s nové dokumentační komentáře XML.  
  
     IntelliSense zobrazí text z \<souhrnné > značky pro typ nebo člen.  
  
5.  Zkompilujte kód generovat soubor XML obsahující dokumentační komentáře. Další informace najdete v tématu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [/ DOC](../../../visual-basic/reference/command-line-compiler/doc.md)
