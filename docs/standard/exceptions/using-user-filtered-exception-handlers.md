---
title: "Používání obslužných rutin uživatelsky filtrovaných výjimek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a71a722063448fb0d568f4bfb4f71d4e01c57454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
