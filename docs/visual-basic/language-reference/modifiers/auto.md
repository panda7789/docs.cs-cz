---
title: Autom.
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 7ea46e5f8b882bb986f23e792b240bad0c5be7a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351620"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Určuje, že by Visual Basic měla zařazovat řetězce podle .NET Framework pravidla na základě vnějšího názvu deklarované externí procedury.  
  
 Při volání procedury definované mimo projekt, kompilátor Visual Basic nemá přístup k informacím, které musí splňovat správné volání procedury. Tyto informace zahrnují, kde se nachází postup, jak se identifikuje, jeho volající sekvence a návratový typ a znaková sada, kterou používá. [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.  
  
 Část `charsetmodifier` v příkazu `Declare` poskytuje znakovou sadu informace pro zařazování řetězců během volání do externí procedury. Ovlivňuje také způsob, jakým Visual Basic hledá Externí soubor pro název externí procedury. Modifikátor `Auto` určuje, že Visual Basic by měl zařazovat řetězce podle pravidel .NET Framework a že by měl určit základní znakovou sadu běhové platformy a případně upravit název externí procedury, pokud se nepovede počáteční vyhledávání. Další informace naleznete v tématu "znakové sady" v [příkazu Declare](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Pokud není zadán žádný modifikátor znakové sady, je `Ansi` výchozí hodnota.  
  
## <a name="remarks"></a>Poznámky  
 V tomto kontextu lze použít modifikátor `Auto`:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Toto klíčové slovo není podporováno.  
  
## <a name="see-also"></a>Viz také:

- [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
