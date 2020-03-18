---
title: Používání obslužných rutin uživatelsky filtrovaných výjimek
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 5537404178b746310f720c5b0c075c77287dda4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708450"
---
# <a name="using-user-filtered-exception-handlers"></a>Používání obslužných rutin uživatelsky filtrovaných výjimek

V současné době jazyk Visual Basic podporuje výjimky filtrované uživatelem. Uživatelem filtrované obslužné rutiny výjimek zachycují a zpracovávají výjimky na základě požadavků, které definujete pro výjimku. Tyto obslužné rutiny používají **Catch** prohlášení s **When** klíčové slovo.  
  
 Tato technika je užitečná, když konkrétní objekt výjimky odpovídá více chybám. V tomto případě objekt má obvykle vlastnost, která obsahuje konkrétní kód chyby spojené s chybou. Vlastnost kódu chyby ve výrazu můžete použít k výběru pouze konkrétní chyby, kterou chcete zpracovat v této klauzuli **Catch.**  
  
 Následující příklad jazyka znázorňuje **catch/When** prohlášení.  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 Výraz uživatelem filtrované klauzule není žádným způsobem omezen. Pokud dojde k výjimce během provádění výrazu filtrovaného uživatelem, je tato výjimka zahozena a výraz filtru je považován za vyhodnocený jako nepravdivý. V tomto případě za běhu společného jazyka pokračuje hledání obslužné rutiny pro aktuální výjimku.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Kombinace konkrétní výjimky a klauzulí filtrovaných uživatelem  
 Příkaz catch může obsahovat konkrétní výjimku a klauzule filtrované uživatelem. Za běhu nejprve testuje konkrétní výjimku. Pokud je konkrétní výjimka úspěšná, runtime spustí filtr uživatele. Obecný filtr může obsahovat odkaz na proměnnou deklarovanou ve filtru třídy. Všimněte si, že pořadí dvou klauzulí filtru nelze stornovat.  
  
 Následující příklad jazyka znázorňuje `ClassLoadException` konkrétní výjimku v **Catch** prohlášení, stejně jako uživatelem filtrované klauzule pomocí **When** klíčové slovo.  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
