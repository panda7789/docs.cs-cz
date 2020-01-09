---
title: Zabezpečení a průběžné vytváření kódu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 64ddcc6a379e5719eb734eede13e576a707696fe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705883"
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpečení a průběžné vytváření kódu
Některé knihovny fungují tak, že generují kód a spouštějí ho k provedení určité operace pro volajícího. Základní problém je generování kódu jménem méně důvěryhodného kódu a jeho spuštění s vyšší důvěryhodností. Problém se zhorší, když volající může ovlivnit generování kódu, takže je nutné zajistit, aby byl vygenerován pouze kód, který považujete za bezpečný.  
  
 Je potřeba přesně zjistit, co kód vygenerujete za všech okolností. To znamená, že musíte mít přísné ovládací prvky pro všechny hodnoty, které obdržíte od uživatele, jako řetězce v uvozovkách (které by měly být uvozeny řídicími znaky), identifikátory (které by měly být zkontrolovány, abyste ověřili, že jsou platné. identifikátory) nebo cokoli jiného. Identifikátory mohou být nebezpečné, protože zkompilované sestavení lze upravit tak, aby jeho identifikátory obsahovaly nezvyklé znaky, což bude pravděpodobně přerušeno (i když se jedná o vzácnou chybu zabezpečení).  
  
 Doporučujeme, abyste vygenerovali kód s vygenerováním reflexe, což často pomáhá vyhnout se mnohé z těchto problémů.  
  
 Při kompilování kódu zvažte, zda existuje nějaký způsob, jak škodlivý program upravit. Existuje malé okno času, během kterého škodlivý kód může změnit zdrojový kód na disku před tím, než ho kompilátor přečte nebo před tím, než kód načte soubor. dll? V takovém případě je nutné chránit adresář obsahující tyto soubory pomocí seznamu Access Control v systému souborů podle potřeby.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
