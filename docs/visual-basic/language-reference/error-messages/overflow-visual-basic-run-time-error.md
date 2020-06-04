---
title: Přetečení (chyba za běhu jazyka Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 5606ae8188c12142800adef46819791b732ff73c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387267"
---
# <a name="overflow-visual-basic-run-time-error"></a>Přetečení (chyba za běhu jazyka Visual Basic)
Při pokusu o přiřazení, které překračuje limity cíle přiřazení, dojde k přetečení.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že výsledky přiřazení, výpočtů a převodů datových typů nejsou příliš velké, aby je bylo možné znázornit v rámci rozsahu proměnných povolených pro daný typ hodnoty, a hodnotu přiřaďte proměnné typu, který může v případě potřeby obsahovat větší rozsah hodnot.  
  
2. Zajistěte, aby přiřazení vlastností odpovídaly rozsahu vlastnosti, na kterou jsou vytvořeny.  
  
3. Ujistěte se, že čísla použitá ve výpočtech, která jsou převedena do celých čísel, nemají výsledky větší než celá čísla.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [Datové typy](../data-types/index.md)
- [Typy chyb](../../programming-guide/language-features/error-types.md)
