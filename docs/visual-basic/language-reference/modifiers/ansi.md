---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 0c38c2b81af7b4cb8fd1723853a09c5413f805af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344743"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Určuje, že Visual Basic mají zařazovat všechny řetězce do organizace ANSI (American National Standards Institute) (ANSI) hodnoty bez ohledu na název deklarované externí procedury.  
  
 Při volání procedury definované mimo projekt, kompilátor Visual Basic nemá přístup k informacím, které potřebuje pro správné volání procedury. Tyto informace zahrnují, kde se nachází postup, jak se identifikuje, jeho volající sekvence a návratový typ a znaková sada, kterou používá. [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.  
  
 Část `charsetmodifier` v příkazu `Declare` poskytuje znakovou sadu informace pro zařazování řetězců během volání do externí procedury. Ovlivňuje také způsob, jakým Visual Basic hledá Externí soubor pro název externí procedury. Modifikátor `Ansi` určuje, že Visual Basic by měly zařazovat všechny řetězce do hodnot ANSI a by měly vyhledat proceduru bez úpravy jejího názvu během hledání.  
  
 Pokud není zadán žádný modifikátor znakové sady, je `Ansi` výchozí hodnota.  
  
## <a name="remarks"></a>Poznámky  
 V tomto kontextu lze použít modifikátor `Ansi`:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Toto klíčové slovo není podporováno.  
  
## <a name="see-also"></a>Viz také:

- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
