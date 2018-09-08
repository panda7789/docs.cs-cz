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
ms.openlocfilehash: d1e771a95542153dfad0981d3198e6b4c31cdeb9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44182093"
---
# <a name="using-user-filtered-exception-handlers"></a>Používání obslužných rutin uživatelsky filtrovaných výjimek
Visual Basic v současné době podporuje uživatelsky filtrovaných výjimek. Obslužných rutin uživatelsky filtrovaných výjimek zachytit a zpracovat výjimky založené na požadavcích, které definujete pro výjimku. Použijte tyto obslužné rutiny **Catch** příkaz **při** – klíčové slovo.  
  
 Tato technika je užitečná, když určitý objekt výjimky odpovídá více chyb. V takovém případě objekt obvykle má vlastnost, která obsahuje chybový kód, který je přidružený k chybě. Chcete-li vybrat pouze konkrétní chyba zpracování v, který můžete použít vlastnost chybového kódu ve výrazu **Catch** klauzuli.  
  
 Ukazuje následující příklad jazyka Visual Basic **Catch/když** příkazu.  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 Výraz v klauzuli filtrované uživatele není omezeno žádným způsobem. Pokud dojde k výjimce během zpracování výrazu uživatelsky filtrovaných, tato výjimka se zahodí a považován za výraz filtru má být vyhodnocen na hodnotu false. V tomto případě common language runtime pokračuje v hledání pro obslužnou rutinu pro aktuální výjimku.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Kombinování specifické výjimky a uživatelsky filtrovaných klauzule  
 Příkaz catch může obsahovat určité výjimky a uživatelsky filtrovaných klauzule. Modul runtime nejprve ověřuje určité výjimky. Pokud bude úspěšné konkrétní výjimky, modul runtime spustí filtr uživatelů. Obecný filtr může obsahovat odkaz na proměnné deklarované ve třídě filtru. Všimněte si, že pořadí dvou klauzulí filtru je nevratná.  
  
 Ukazuje následující příklad jazyka Visual Basic specifickou výjimku `ClassLoadException` v **Catch** příkaz jako použití klauzule filtrované uživatelem **při** – klíčové slovo.  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
