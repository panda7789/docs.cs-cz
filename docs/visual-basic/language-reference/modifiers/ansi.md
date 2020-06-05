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
ms.openlocfilehash: 67792e52c21555bef46548e9ab0a6ebd32061071
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373197"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Určuje, že Visual Basic mají zařazovat všechny řetězce do organizace ANSI (American National Standards Institute) (ANSI) hodnoty bez ohledu na název deklarované externí procedury.  
  
 Při volání procedury definované mimo projekt, kompilátor Visual Basic nemá přístup k informacím, které potřebuje pro správné volání procedury. Tyto informace zahrnují, kde se nachází postup, jak se identifikuje, jeho volající sekvence a návratový typ a znaková sada, kterou používá. [Příkaz Declare](../statements/declare-statement.md) vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.  
  
 `charsetmodifier`Část v `Declare` příkazu poskytuje znakovou sadu informace pro zařazování řetězců během volání externí procedury. Ovlivňuje také způsob, jakým Visual Basic hledá Externí soubor pro název externí procedury. `Ansi`Modifikátor určuje, že Visual Basic by měl zařazovat všechny řetězce do hodnot ANSI a by měl vyhledat proceduru bez úpravy jejího názvu během hledání.  
  
 Pokud není zadán modifikátor znakové sady, `Ansi` je výchozí hodnota.  
  
## <a name="remarks"></a>Poznámky  
 `Ansi`V tomto kontextu lze použít modifikátor:  
  
 [Declare – příkaz](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Toto klíčové slovo není podporováno.  
  
## <a name="see-also"></a>Viz také

- [Automaticky](auto.md)
- [Kódování Unicode](unicode.md)
- [Klíčová slova](../keywords/index.md)
