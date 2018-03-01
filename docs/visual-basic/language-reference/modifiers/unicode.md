---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 042908b8427de2de0de96bbb32df7be018bb915c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Určuje, že jazyka Visual Basic má zařazování všechny řetězce Unicode hodnoty bez ohledu na název externí procedura se deklarovat.  
  
 Při volání procedury definované mimo projekt Visual Basic – kompilátor nemá přístup k informacím, že se musí mít, aby správně voláním procedury. Tyto informace zahrnují, kde se nachází postup, jak je identifikovat, jeho volací sekvence a návratový typ a řetězec znaková sada, se používá. [Deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.  
  
 `charsetmodifier` Část v `Declare` příkaz poskytuje informace sady znaků, které zařazování řetězců během volání externí procedura. Ovlivní také jak jazyka Visual Basic prohledává externí soubor pro externí procedura název. `Unicode` Modifikátor Určuje, že jazyka Visual Basic má zařazování všechny řetězce Unicode hodnoty a musí vyhledat postup beze změny jeho názvu během hledání.  
  
 Pokud není zadaný žádný modifikátor sady znaků, `Ansi` je výchozí.  
  
## <a name="remarks"></a>Poznámky  
 `Unicode` Modifikátor můžete v tomto kontextu použít:  
  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 This – klíčové slovo není podporováno.  
  
## <a name="see-also"></a>Viz také  
 [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Automaticky](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
