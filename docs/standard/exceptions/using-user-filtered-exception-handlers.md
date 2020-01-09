---
title: Používání obslužných rutin uživatelsky filtrovaných výjimek
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 5537404178b746310f720c5b0c075c77287dda4c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708450"
---
# <a name="using-user-filtered-exception-handlers"></a>Používání obslužných rutin uživatelsky filtrovaných výjimek

V současné době Visual Basic podporuje výjimky filtrované uživatelem. Uživatelsky filtrované obslužné rutiny výjimek zachytí a zpracovávají výjimky na základě požadavků, které definujete pro výjimku. Tyto obslužné rutiny používají příkaz **catch** s klíčovým slovem **when** .  
  
 Tato technika je užitečná, když konkrétní objekt výjimky odpovídá více chybám. V takovém případě má objekt obvykle vlastnost, která obsahuje konkrétní kód chyby spojený s chybou. Vlastnost kód chyby ve výrazu můžete použít k výběru pouze konkrétní chyby, kterou chcete v této klauzuli **catch** zpracovat.  
  
 Následující příklad Visual Basic ukazuje příkaz **catch/when** .  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 Výraz klauzule filtrované uživatelem není nijak omezen. Pokud při provádění výrazu filtrovaného uživatelem dojde k výjimce, je tato výjimka zahozena a výraz filtru je považován za vyhodnocený jako NEPRAVDA. V takovém případě modul CLR (Common Language Runtime) pokračuje v hledání obslužné rutiny pro aktuální výjimku.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Kombinování konkrétní výjimky a uživatelem filtrovaných klauzulí  
 Příkaz catch může obsahovat konkrétní výjimku i klauzule filtrované uživatelem. Modul runtime nejprve testuje specifickou výjimku. Pokud je specifická výjimka úspěšná, modul runtime spustí filtr uživatele. Obecný filtr může obsahovat odkaz na proměnnou deklarovanou ve filtru třídy. Všimněte si, že pořadí dvou klauzulí filtru nelze vrátit zpět.  
  
 Následující příklad Visual Basic ukazuje konkrétní výjimku `ClassLoadException` v příkazu **catch** a také klauzuli filtrovanou uživatelem pomocí klíčového slova **when** .  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
