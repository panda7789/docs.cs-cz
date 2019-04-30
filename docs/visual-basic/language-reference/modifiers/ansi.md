---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 98dafab3e524ea371bba228eb231e28d46cc3b4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802554"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Určuje, že by měl Visual Basic zařazovat všechny řetězce na hodnoty American National Standards Institute (ANSI) bez ohledu na název externí procedury byl deklarován.  
  
 Při volání procedury definován vně vašeho projektu, kompilátor jazyka Visual Basic nemá přístup k informacím, které potřebuje k voláním procedury správně. Tyto informace zahrnují, kde se nachází postup, jak je identifikovaný, jeho volací sekvence a návratový typ a řetězec znakové sady, ji používá. [Deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.  
  
 `charsetmodifier` Část v `Declare` příkaz poskytuje informace o znakových sadách pro zařazování řetězce při volání do externí procedury. Také ovlivní, jak Visual Basic vyhledá externí soubor pro název externí procedury. `Ansi` Modifikátor Určuje, že jazyka Visual Basic by měla zařazovat všechny řetězce na hodnoty ANSI a by měl vyhledávat proceduru bez úpravy jejího názvu během vyhledávání.  
  
 Pokud není zadána žádná modifikátor sady znaků, `Ansi` je výchozí nastavení.  
  
## <a name="remarks"></a>Poznámky  
 `Ansi` Modifikátor lze použít v tomto kontextu:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Toto klíčové slovo se nepodporuje.  
  
## <a name="see-also"></a>Viz také:

- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
