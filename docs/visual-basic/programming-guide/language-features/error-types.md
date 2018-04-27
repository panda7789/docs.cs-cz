---
title: Typy chyb (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b3cf1307f54a5c902bf8e6379c8760c735a45e4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="error-types-visual-basic"></a>Typy chyb (Visual Basic)
V jazyce Visual Basic, chyby (také nazývané *výjimky*) spadají do tří kategorií: chyby syntaxe, chyby a logiku chyby.  
  
## <a name="syntax-errors"></a>Chyby syntaxe  
 *Chyby syntaxe* jsou ty, které se zobrazí při psaní kódu. Visual Basic zkontroluje váš kód při psaní do **Editor kódu** okno a upozorní vás, pokud došlo k chybě, třeba Chyba v pravopisu slovo nebo element jazyk nesprávně. Chyby syntaxe jsou nejběžnější typ chyby. Můžete je vyřešit je snadno v kódování prostředí Jakmile k nim dojde.  
  
> [!NOTE]
>  `Option Explicit` Příkaz je jeden z prostředků k zamezení chyby syntaxe. Vynutí předem, deklarovat všechny proměnné, který se má použít v aplikaci. Proto když tyto proměnné se používají v kódu, typografické chyby jsou zachyceny okamžitě a odstraněny.  
  
## <a name="run-time-errors"></a>Běhové chyby  
 *Běhové chyby* jsou ty, které zobrazují, jenom když zkompilování a spuštění kódu. To zahrnuje kód, který může zdají být správná, v tom má žádné chyby syntaxe, ale nelze jej provést. Například může správně zapsat řádek kódu a otevřete soubor. Pokud soubor je poškozený, aplikace nelze provést, ale `Open` funkce a zastaví se. Většina běhové chyby lze vyřešit přepsáním chybného kód a pak nutnosti rekompilace a znovu ji spustit.  
  
## <a name="logic-errors"></a>Logické chyby  
 *Logické chyby* jsou ty, které je zaprotokolována jednou aplikace je používána. Jsou většina nežádoucí nebo neočekávané výsledky v odpovědi na akce uživatele. Například chybným klíč nebo jiných vnějších vliv může způsobit, že aplikace přestane fungovat v rámci očekávané parametry, nebo úplně. Logické chyby jsou obvykle nejtěžší typ opravit, protože není vždy jasné, které pocházejí.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Základy ladicího programu](/visualstudio/debugger/debugger-basics)
