---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: b3c9452f8d144fb18ea3efcb35b85caed80e8692
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819343"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Určuje, že by měl Visual Basic zařazovat všechny řetězce k hodnotám Unicode bez ohledu na název externí procedury byl deklarován.  
  
 Při volání procedury definován vně vašeho projektu, kompilátor jazyka Visual Basic nemá přístup k informacím, musíte mít k voláním procedury správně. Tyto informace zahrnují, kde se nachází postup, jak je identifikovaný, jeho volací sekvence a návratový typ a řetězec znakové sady, ji používá. [Deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.  
  
 `charsetmodifier` Část v `Declare` příkaz poskytuje informace o sadě znak k zařazování řetězců v kódu při volání do externí procedury. Také ovlivní, jak Visual Basic vyhledá externí soubor pro název externí procedury. `Unicode` Modifikátor Určuje, že jazyka Visual Basic by měla zařazovat všechny řetězce k hodnotám Unicode a by měl vyhledávat proceduru bez úpravy jejího názvu během vyhledávání.  
  
 Pokud není zadána žádná modifikátor sady znaků, `Ansi` je výchozí nastavení.  
  
## <a name="remarks"></a>Poznámky  
 `Unicode` Modifikátor lze použít v tomto kontextu:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Toto klíčové slovo se nepodporuje.  
  
## <a name="see-also"></a>Viz také:

- [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
