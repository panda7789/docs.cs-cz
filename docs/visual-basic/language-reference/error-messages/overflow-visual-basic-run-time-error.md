---
title: Přetečení (chyba za běhu jazyka Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 7546676b85465577b357b7ad0757b4db8d40dbe3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934436"
---
# <a name="overflow-visual-basic-run-time-error"></a>Přetečení (chyba za běhu jazyka Visual Basic)
Přetečení výsledky při pokusu o přiřazení, která překračuje omezení cíle tohoto přiřazení.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že výsledky typu přiřazení, výpočty a data převody nejsou příliš velké a nelze je reprezentovat v rozsahu povolená pro daný typ hodnoty proměnných a přiřaďte hodnotu k proměnné typu, který může obsahovat větší rozsah hodnot , pokud je to nutné.  
  
2.  Zajistěte, aby přiřazení k vlastnosti podle rozsahu vlastnost, ke které se provedou.  
  
3.  Ujistěte se, že používá ve výpočtech, které jsou přiřazeny do celých čísel čísla nemají výsledky větší než celých čísel.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/index.md)  
 [Typy chyb](../../../visual-basic/programming-guide/language-features/error-types.md)
