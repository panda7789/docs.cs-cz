---
title: Byl očekáván konec příkazu.
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 169f01b02df377ba6cc21ffad53c36f5d4537140
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409644"
---
# <a name="end-of-statement-expected"></a>Byl očekáván konec příkazu.
Příkaz je syntakticky dokončen, ale další programovací prvek následuje za prvkem, který dokončí příkaz. Na konci každého příkazu je vyžadován ukončovací znak řádku.
  
 Zakončení řádku rozděluje znaky zdrojového souboru Visual Basic do řádků. Příklady zakončení řádků jsou návratový znak Unicode (&HD), znak odřádkování Unicode (&HA) a znak návratu na začátek řádku Unicode následovaný znakem odřádkování Unicode. Další informace o ukončovacích koncích řádků najdete v tématu [specifikace jazyka Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).
  
 **ID chyby:** BC30205
  
## <a name="to-correct-this-error"></a>Oprava této chyby
  
1. Zkontrolujte, zda byly na stejný řádek neúmyslně vloženy dva různé příkazy.
  
2. Vložte ukončovací znak řádku za prvek, který dokončí příkaz.
  
## <a name="see-also"></a>Viz také

- [Postupy: Přerušení a kombinování příkazů v kódu](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
