---
title: Kódování Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: c4286ed9e9d5fd768ae29b7050b3d1505ccca9dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344225"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Určuje, že Visual Basic by měly zařazovat všechny řetězce do hodnot Unicode bez ohledu na název externí procedury, která je deklarována.  
  
 Při volání procedury definované mimo projekt, kompilátor Visual Basic nemá přístup k informacím, které musí mít, aby mohl správně zavolat proceduru. Tyto informace zahrnují, kde se nachází postup, jak se identifikuje, jeho volající sekvence a návratový typ a znaková sada, kterou používá. [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.  
  
 Část `charsetmodifier` v příkazu `Declare` poskytuje znakovou sadu informace pro zařazování řetězců během volání do externí procedury. Ovlivňuje také způsob, jakým Visual Basic hledá Externí soubor pro název externí procedury. Modifikátor `Unicode` určuje, že Visual Basic by měly zařazovat všechny řetězce do hodnot Unicode a měly by Hledat postup beze změny jeho názvu během hledání.  
  
 Pokud není zadán žádný modifikátor znakové sady, je `Ansi` výchozí hodnota.  
  
## <a name="remarks"></a>Poznámky  
 V tomto kontextu lze použít modifikátor `Unicode`:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Toto klíčové slovo není podporováno.  
  
## <a name="see-also"></a>Viz také:

- [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
