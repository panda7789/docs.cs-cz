---
title: Chybové zprávy
ms.date: 07/20/2015
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 15d12802c92e7b9ed99c83885bd38e381c8b687d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353704"
---
# <a name="error-messages-visual-basic"></a>Chybové zprávy (Visual Basic)
Když píšete, zkompilujete nebo spustíte Visual Basic aplikaci, může dojít k následujícím typům chyb:  
  
1. Chyby v době návrhu, ke kterým dochází při psaní aplikace v aplikaci Visual Studio.  
  
2. Chyby při kompilaci, ke kterým dochází při kompilaci aplikace v aplikaci Visual Studio nebo na příkazovém řádku.  
  
3. Běhové chyby, ke kterým dochází při spuštění aplikace v aplikaci Visual Studio nebo jako samostatného spustitelného souboru.  
  
 Informace o tom, jak řešit určitou chybu, najdete v tématu [Další zdroje informací pro Visual Basic programátory](../../../visual-basic/getting-started/additional-resources.md).  
  
## <a name="run-time-errors"></a>Chyby běhu  
 Pokud se aplikace Visual Basic pokusí provést akci, kterou systém nemůže spustit, dojde k chybě za běhu a Visual Basic vyvolá objekt `Exception`. Visual Basic může generovat vlastní chyby libovolného datového typu, včetně objektů `Exception`, pomocí příkazu `Throw`. Aplikace může identifikovat chybu zobrazením čísla chyby a zprávy zachycené výjimky. Pokud chyba není zachycena, aplikace skončí.  
  
 Kód může zachytit a ověřit běhové chyby. Pokud uzavřete kód, který vytváří chybu v bloku `Try`, můžete zachytit vyvolanou chybu v rámci odpovídajícího bloku `Catch`. Informace o tom, jak zachytit chyby v době běhu a reagovat na ně v kódu, naleznete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="compile-time-errors"></a>Chyby při kompilaci  
 Pokud Visual Basic kompilátor narazí na problém v kódu, dojde k chybě při kompilaci. V editoru kódu můžete snadno určit, který řádek kódu způsobil chybu, protože pod tímto řádkem kódu se zobrazí Vlnová čára. Chybová zpráva se zobrazí, pokud buď ukážete na vlnové podtržení, nebo otevřete **Seznam chyb**, ve kterém se zobrazí také další zprávy.  
  
 Pokud je identifikátor podtržen vlnovkou a v rámci pravého znaku se zobrazí krátké podtržení, můžete vygenerovat zástupnou proceduru pro třídu, konstruktor, metodu, vlastnost, pole nebo výčet. Další informace najdete v tématu [generování z využití](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).
  
 Řešením upozornění z Visual Basic kompilátoru může být možné napsat kód, který běží rychleji a obsahuje méně chyb. Tato upozornění identifikují kód, který může způsobit chyby při spuštění aplikace. Například kompilátor vás upozorní, pokud se pokusíte vyvolat člena nepřiřazené proměnné objektu, vracet z funkce bez nastavení návratové hodnoty, nebo spustit `Try` blok s chybami v logice k zachycení výjimek. Další informace o upozorněních, včetně toho, jak je zapnout nebo vypnout, najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).
