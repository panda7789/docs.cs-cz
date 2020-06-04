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
ms.openlocfilehash: 9b1bc40bb52244deefc0486d3a40c4b961ad1ee5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402678"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Určuje, že Visual Basic by měly zařazovat všechny řetězce do hodnot Unicode bez ohledu na název externí procedury, která je deklarována.  
  
 Při volání procedury definované mimo projekt, kompilátor Visual Basic nemá přístup k informacím, které musí mít, aby mohl správně zavolat proceduru. Tyto informace zahrnují, kde se nachází postup, jak se identifikuje, jeho volající sekvence a návratový typ a znaková sada, kterou používá. [Příkaz Declare](../statements/declare-statement.md) vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.  
  
 `charsetmodifier`Část v `Declare` příkazu poskytuje znakovou sadu informace pro zařazování řetězců během volání externí procedury. Ovlivňuje také způsob, jakým Visual Basic hledá Externí soubor pro název externí procedury. `Unicode`Modifikátor určuje, že Visual Basic by měl zařazovat všechny řetězce do hodnot Unicode a by měl vyhledat proceduru bez úpravy jejího názvu během hledání.  
  
 Pokud není zadán modifikátor znakové sady, `Ansi` je výchozí hodnota.  
  
## <a name="remarks"></a>Poznámky  
 `Unicode`V tomto kontextu lze použít modifikátor:  
  
 [Declare – příkaz](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Toto klíčové slovo není podporováno.  
  
## <a name="see-also"></a>Viz také

- [Ansi](ansi.md)
- [Automaticky](auto.md)
- [Klíčová slova](../keywords/index.md)
