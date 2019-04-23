---
title: Chybové zprávy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 822c0f266e7dd68f063043d98a9f4af308ae93fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770097"
---
# <a name="error-messages-visual-basic"></a>Chybové zprávy (Visual Basic)
Při zápisu, kompilaci či spuštění aplikace v jazyce Visual Basic, může dojít k následující typy chyb:  
  
1. Chyby v době návrhu, ke kterým dochází při psaní aplikace v sadě Visual Studio.  
  
2. Chyby při kompilaci, ke kterým dochází při kompilaci aplikace v sadě Visual Studio nebo příkazového řádku.  
  
3. Běhové chyby, ke kterým dochází při spuštění aplikace v sadě Visual Studio nebo jako samostatný spustitelný soubor.  
  
 Informace o tom, jak řešit konkrétní chyby naleznete v tématu [další zdroje informací pro programátory v jazyce Visual Basic](../../../visual-basic/getting-started/additional-resources.md).  
  
## <a name="run-time-errors"></a>Chyby při spuštění  
 Pokud aplikace v jazyce Visual Basic se pokusí provést akci, která systém nemůže spustit, dojde k chybě za běhu, a vyvolá výjimku jazyka Visual Basic `Exception` objektu. Visual Basic můžete vygenerovat vlastní chyby jakýchkoli dat zadejte, včetně `Exception` objektů pomocí `Throw` příkaz. Aplikace můžete identifikovat chyby tím, že zobrazuje počet chyb a zprávy zachycené výjimky. Pokud chyba není zachycena, aplikace se ukončí.  
  
 Kód můžete zachytit a zkontrolovat chyby za běhu. Pokud je kód, který generuje chybu v uzavřít `Try` bloku, můžete zachytit všechny vyvolané chyby v rámci odpovídající `Catch` bloku. Informace o tom, jak zachytávat chyby za běhu a reagovat na ně ve vašem kódu, naleznete v tématu [zkuste... Catch... Příkaz finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="compile-time-errors"></a>Chyby při kompilaci  
 Pokud kompilátor jazyka Visual Basic narazí na problém v kódu, dojde k chybě v době kompilace. V editoru kódu můžete snadno identifikovat který řádek kódu způsobil chybu, protože vlnovku se zobrazí pod tento řádek kódu. Pokud můžete buď odkazovat na podtržení vlnovkou nebo otevřené, zobrazí se chybová zpráva **seznam chyb**, které zároveň ukazuje další zprávy.  
  
 Pokud má identifikátor podtržení vlnovkou a krátký podtržení se zobrazí v části znaku zcela vpravo, můžete vygenerovat zástupnou proceduru pro třída, konstruktor, metody, vlastnosti, pole nebo výčtu. Další informace najdete v tématu [Generovat z využití](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).
  
 Pomocí řešení upozornění z kompilátoru jazyka Visual Basic, je možné napsat kód, který běží rychleji a má méně chyb. Tato upozornění identifikovat kód, který může způsobit chyby při spuštění aplikace. Například kompilátor vás upozorní vás při pokusu o vyvolání členské proměnné nepřiřazený objekt vrácení z funkce, aniž byste museli nastavovat návratová hodnota nebo spusťte `Try` blok s chyby v logice jak zachytávat výjimky. Další informace o upozornění, jak je zapnout a vypnout, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).
