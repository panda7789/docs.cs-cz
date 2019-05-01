---
title: Typy chyb (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: 07db963ac3cf9d1c0d17c420480189d362cdaf2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973170"
---
# <a name="error-types-visual-basic"></a>Typy chyb (Visual Basic)
V jazyce Visual Basic, chyby (také nazývané *výjimky*) spadají do jedné ze tří kategorií: chyby syntaxe, chyby za běhu a chyby logiky.  
  
## <a name="syntax-errors"></a>Chyby syntaxe  
 *Chyby syntaxe* jsou ty, které se zobrazí při psaní kódu. Visual Basic zkontroluje váš kód během psaní v **Editor kódu** okno a upozorní vás, pokud uděláte chybu, jako je například Chyba v pravopisu slova nebo nesprávně pomocí prvku jazyka. Chyby syntaxe jsou nejběžnějším typem chyby. Je lze opravit snadno v kódování prostředí Jakmile k nim dojde.  
  
> [!NOTE]
>  `Option Explicit` Příkaz je jeden způsob jak se vyhnout chyby syntaxe. Vynutí předem deklarovat všechny proměnné, který se má použít v aplikaci. Proto při těchto proměnných se používá v kódu, jsou zachyceny okamžitě typografické chyby a lze napravit.  
  
## <a name="run-time-errors"></a>Chyby za běhu  
 *Chyby za běhu* jsou ty, které se zobrazí pouze po kompilaci a spuštění kódu. To zahrnuje kód, který se zdá být správná, nemá žádné chyby syntaxe, ale nelze jej provést. Například můžete například napsat správně psát kód pro otevření souboru. Pokud soubor je poškozený, aplikace nelze provést, ale `Open` funkce a zastaví se. Většina chyb za běhu můžete vyřešit přepsání chybného kódu zkompilováním a spuštěním.  
  
## <a name="logic-errors"></a>Logické chyby  
 *Logické chyby* jsou ty, které se zobrazí, až se aplikace nepoužívá. Jsou to většina často nežádoucí nebo neočekávané výsledky v reakci na akce uživatele. Chybným zadáním klíče nebo jiných mimo vliv například může způsobit, že aplikace přestane fungovat během očekávané parametry, nebo úplně se vynechá. Logické chyby jsou obvykle nejtěžší typ k vyřešení, protože není vždy jasné kde pocházejí.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Základy ladicího programu](/visualstudio/debugger/debugger-basics)
