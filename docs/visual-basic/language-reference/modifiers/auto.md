---
title: Auto
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: b9bdeed55788252c71b8fb1c995c140cbfdf60eb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373125"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Určuje, že by Visual Basic měla zařazovat řetězce podle .NET Framework pravidla na základě vnějšího názvu deklarované externí procedury.  
  
 Při volání procedury definované mimo projekt, kompilátor Visual Basic nemá přístup k informacím, které musí splňovat správné volání procedury. Tyto informace zahrnují, kde se nachází postup, jak se identifikuje, jeho volající sekvence a návratový typ a znaková sada, kterou používá. [Příkaz Declare](../statements/declare-statement.md) vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.  
  
 `charsetmodifier`Část v `Declare` příkazu poskytuje znakovou sadu informace pro zařazování řetězců během volání externí procedury. Ovlivňuje také způsob, jakým Visual Basic hledá Externí soubor pro název externí procedury. `Auto`Modifikátor určuje, že Visual Basic by měl zařazovat řetězce v souladu s pravidly .NET Framework a že by měl určit základní znakovou sadu běhové platformy a případně upravit název externí procedury, pokud se nepovede počáteční vyhledávání. Další informace naleznete v tématu "znakové sady" v [příkazu Declare](../statements/declare-statement.md).  
  
 Pokud není zadán modifikátor znakové sady, `Ansi` je výchozí hodnota.  
  
## <a name="remarks"></a>Poznámky  
 `Auto`V tomto kontextu lze použít modifikátor:  
  
 [Declare – příkaz](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Toto klíčové slovo není podporováno.  
  
## <a name="see-also"></a>Viz také

- [Ansi](ansi.md)
- [Kódování Unicode](unicode.md)
- [Klíčová slova](../keywords/index.md)
