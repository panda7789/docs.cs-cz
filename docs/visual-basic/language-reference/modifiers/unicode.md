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
ms.openlocfilehash: 491bbb24be8e6a3044b0a433c5ad262596ae00d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655280"
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
