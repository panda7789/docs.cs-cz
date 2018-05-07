---
title: Ordinální číslo není platné.
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 12d73b33e3c025b40c98d84e3507af7be1e1e91a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ordinal-is-not-valid"></a>Ordinální číslo není platné.
Volání do dynamická knihovna (DLL) uvedené pro použití číslo místo názvu postup pomocí `#num` syntaxe. Tato chyba má následující možné příčiny:  
  
-   Pokus o převést `#num` výraz, který má pořadí se nezdařilo.  
  
-   `#num` Zadaný v knihovně DLL neurčuje žádné funkce.  
  
-   Knihovny typů obsahuje neplatný deklaraci výsledkem interní použití neplatné číslo pořadí.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, zda že výraz představuje platné číslo nebo voláním procedury podle názvu.  
  
2.  Zajistěte, aby `#num` identifikuje platnou funkcí v knihovně DLL.  
  
3.  Izolujte volání procedury příčinou problému pomocí komentářů si kód. Zápis `Declare` příkaz pro postup a sestava tyto potíže k dodavatele knihovny typu.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
