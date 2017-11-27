---
title: Auto (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e32c4c910567829a4f5c59b48020db4dfbbeb7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Určuje, že jazyka Visual Basic by měl zařazování řetězců podle rozhraní .NET Framework pravidla založená na externí název externí procedura se deklarovat.  
  
 Při volání procedury definované mimo projekt Visual Basic – kompilátor nemá přístup k informacím musí mít voláním procedury správně. Tyto informace zahrnují, kde se nachází postup, jak je identifikovat, jeho volací sekvence a návratový typ a řetězec znaková sada, se používá. [Deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.  
  
 `charsetmodifier` Část v `Declare` příkaz poskytuje informace o znakových sadách pro zařazování řetězců během volání externí procedura. Ovlivní také jak jazyka Visual Basic prohledává externí soubor pro externí procedura název. `Auto` Modifikátor Určuje, že by měl jazyka Visual Basic zařazování řetězců podle pravidel rozhraní .NET Framework a se musí určit základní znakovou sadu platformy spuštění a případně upravit název externí procedura pokud počáteční vyhledávání se nezdaří. Další informace najdete v tématu "Sady znaků" v [deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Pokud není zadaný žádný modifikátor sady znaků, `Ansi` je výchozí.  
  
## <a name="remarks"></a>Poznámky  
 `Auto` Modifikátor můžete v tomto kontextu použít:  
  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 This – klíčové slovo není podporováno.  
  
## <a name="see-also"></a>Viz také  
 [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Kódování Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
