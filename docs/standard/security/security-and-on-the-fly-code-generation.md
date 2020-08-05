---
title: Zabezpečení a průběžné vytváření kódu
description: Generování kódu jménem méně důvěryhodného kódu, který běží ve vyšším vztahu důvěryhodnosti, je bezpečnostním problémem, zejména v případě, že volající může ovlivnit generování kódu.
ms.date: 07/15/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: a3fc51c346feffa85537d95ccdbd23d943827edf
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555692"
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpečení a průběžné vytváření kódu

Některé knihovny fungují tak, že generují kód a spouštějí ho k provedení určité operace pro volajícího. Základní problém je generování kódu jménem méně důvěryhodného kódu a jeho spuštění s vyšší důvěryhodností. Problém se zhorší, když volající může ovlivnit generování kódu, takže je nutné zajistit, aby byl vygenerován pouze kód, který považujete za bezpečný.  
  
Je potřeba přesně zjistit, co kód vygenerujete za všech okolností. To znamená, že musíte mít přísné ovládací prvky pro všechny hodnoty, které obdržíte od uživatele, jako řetězce v uvozovkách (které by měly být uvozeny řídicími znaky), identifikátory (které by měly být zkontrolovány, zda jsou platné identifikátory) nebo cokoli jiného. Identifikátory mohou být nebezpečné, protože zkompilované sestavení lze upravit tak, aby jeho identifikátory obsahovaly nezvyklé znaky, což bude pravděpodobně přerušeno (i když se jedná o vzácnou chybu zabezpečení).  
  
Doporučujeme, abyste vygenerovali kód s vygenerováním reflexe, což často pomáhá vyhnout se mnohé z těchto problémů.  
  
Při kompilování kódu zvažte, zda existuje nějaký způsob, jak škodlivý program upravit. Existuje malé okno času, během kterého škodlivý kód může změnit zdrojový kód na disku před tím, než ho kompilátor přečte nebo před tím, než kód načte soubor. dll? V takovém případě je nutné chránit adresář obsahující tyto soubory pomocí seznamu Access Control v systému souborů podle potřeby.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](secure-coding-guidelines.md)
- [ASP.NET Core zabezpečení](/aspnet/core/security/)
