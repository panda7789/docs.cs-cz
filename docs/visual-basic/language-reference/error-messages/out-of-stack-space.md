---
title: Nedostatek místa v zásobníku
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349186"
---
# <a name="out-of-stack-space-visual-basic"></a>Nedostatek místa v zásobníku (Visual Basic)
Zásobník je pracovní oblast paměti, která dynamicky zvětšuje a zmenšuje s požadavky spuštěného programu. Překročila se jejich omezení.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ověřte, že procedury nejsou vnořené příliš hluboko.  
  
2. Zajistěte, aby rekurzivní procedury byly ukončeny správně.  
  
3. Pokud místní proměnné vyžadují více místních proměnných místo, než je k dispozici, zkuste deklarovat některé proměnné na úrovni modulu. Můžete také deklarovat všechny proměnné v proceduře static pomocí předchozího klíčového slova `Property`, `Sub`nebo `Function` s `Static`. Případně můžete použít příkaz `Static` k deklarování jednotlivých statických proměnných v rámci procedur.  
  
4. Předefinujte některé řetězce s pevnou délkou jako řetězce s proměnlivou délkou, protože řetězce s pevnou délkou používají více místa v zásobníku než řetězce s proměnlivou délkou. Můžete také definovat řetězec na úrovni modulu, kde nevyžaduje žádné místo v zásobníku.  
  
5. Zkontrolujte počet volání vnořených `DoEvents` funkcí pomocí dialogového okna `Calls` k zobrazení, které postupy jsou v zásobníku aktivní.  
  
6. Ujistěte se, že jste nezpůsobili "událost Cascade" aktivací události, která volá proceduru události, která je již v zásobníku. Kaskádová událost je podobná neukončenému volání rekurzivní procedury, ale je méně zřejmé, protože volání je provedeno Visual Basic spíše než explicitní volání v kódu. Pomocí dialogového okna `Calls` můžete zobrazit, které postupy jsou v zásobníku aktivní.  
  
## <a name="see-also"></a>Viz také:

- [Okna paměti](/visualstudio/debugger/memory-windows)
