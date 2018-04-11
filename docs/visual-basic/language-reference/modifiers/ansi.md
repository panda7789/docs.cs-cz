---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa5724eb9123b2776c3a579e4244c55b3129816b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Určuje, že jazyka Visual Basic má zařazování všechny řetězce hodnoty American National Standards Institute (ANSI) bez ohledu na název externí procedura je deklarován.  
  
 Při volání procedury definované mimo projekt Visual Basic – kompilátor nemá přístup k informacím, které potřebuje voláním procedury správně. Tyto informace zahrnují, kde se nachází postup, jak je identifikovat, jeho volací sekvence a návratový typ a řetězec znaková sada, se používá. [Deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.  
  
 `charsetmodifier` Část v `Declare` příkaz poskytuje informace o znakových sadách pro zařazování řetězců během volání externí procedura. Ovlivní také jak jazyka Visual Basic prohledává externí soubor pro externí procedura název. `Ansi` Modifikátor Určuje, že jazyka Visual Basic má zařazování všechny řetězce ANSI hodnoty a musí vyhledat postup beze změny jeho názvu během hledání.  
  
 Pokud není zadaný žádný modifikátor sady znaků, `Ansi` je výchozí.  
  
## <a name="remarks"></a>Poznámky  
 `Ansi` Modifikátor můžete v tomto kontextu použít:  
  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 This – klíčové slovo není podporováno.  
  
## <a name="see-also"></a>Viz také  
 [Automaticky](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Kódování Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
