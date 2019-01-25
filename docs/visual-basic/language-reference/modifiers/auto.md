---
title: Auto (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: c128ab9982ae7ccd5fff34020f2750f703da16a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664600"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Určuje, že by měl Visual Basic zařazovat řetězce podle pravidel rozhraní .NET Framework, které jsou založené na externí název externí procedury byl deklarován.  
  
 Při volání procedury definován vně vašeho projektu, kompilátor jazyka Visual Basic nemá přístup k informacím musí mít k voláním procedury správně. Tyto informace zahrnují, kde se nachází postup, jak je identifikovaný, jeho volací sekvence a návratový typ a řetězec znakové sady, ji používá. [Deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.  
  
 `charsetmodifier` Část v `Declare` příkaz poskytuje informace o znakových sadách pro zařazování řetězce při volání do externí procedury. Také ovlivní, jak Visual Basic vyhledá externí soubor pro název externí procedury. `Auto` Modifikátor Určuje, že by měl Visual Basic zařazovat řetězce podle pravidel rozhraní .NET Framework a, že ho měli určit základní znakové sady běhovou platformu a případně upravit název externí procedury úvodním vyhledávání se nezdaří. Další informace najdete v tématu "Znakových sadách" [deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Pokud není zadána žádná modifikátor sady znaků, `Ansi` je výchozí nastavení.  
  
## <a name="remarks"></a>Poznámky  
 `Auto` Modifikátor lze použít v tomto kontextu:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Toto klíčové slovo se nepodporuje.  
  
## <a name="see-also"></a>Viz také:
- [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
