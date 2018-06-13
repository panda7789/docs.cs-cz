---
title: Používání obslužných rutin uživatelsky filtrovaných výjimek
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e72f87bd4a33491df46576629971c60af4630ce3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571888"
---
# <a name="using-user-filtered-exception-handlers"></a>Používání obslužných rutin uživatelsky filtrovaných výjimek
Visual Basic v současné době podporuje uživatelem filtrované výjimky. Obslužných rutin uživatelsky filtrovaných výjimek catch a zpracování výjimek na základě požadavků, které definujete pro výjimku. Použijte tyto obslužné rutiny **Catch** příkaz s **při** – klíčové slovo.  
  
 Tato metoda je užitečná, když určitý objekt výjimky odpovídá více chybám. V takovém případě objekt obvykle má vlastnost, která obsahuje kód chyby související s chybou. Můžete vlastnost kódu chyby ve výrazu a vyberte pouze konkrétní chyby chcete zpracovávat v tom, že **Catch** klauzule.  
  
 Ukazuje následující příklad jazyka Visual Basic **Catch/When** příkaz.  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 Výraz klauzule uživatelem filtrované není omezena žádným způsobem. Pokud dojde k výjimce během zpracování výrazu uživatelem filtrované, je tato výjimka zahozena a výraz filtru je považován za vyhodnocení na hodnotu false. V tomto případě common language runtime pokračuje v hledání pro obslužnou rutinu pro aktuální výjimku.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Kombinování specifických výjimek a klauzulích uživatelem filtrované  
 Příkaz catch může obsahovat specifických výjimek a uživatelem filtrované klauzule. Modul runtime nejprve testuje specifickou výjimku. Pokud je specifická výjimka úspěšná, modul runtime provede filtru uživatelů. Obecný filtr může obsahovat odkaz na proměnnou uvedenou ve filtru třídy. Všimněte si, že pořadí dvou klauzulí filtru nelze vrátit zpět.  
  
 Následující příklad jazyka Visual Basic ukazuje specifickou výjimku `ClassLoadException` v **Catch** prohlášení, jakož i pomocí klauzule uživatelem filtrované **při** – klíčové slovo.  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a>Viz také
[Výjimky](index.md)
