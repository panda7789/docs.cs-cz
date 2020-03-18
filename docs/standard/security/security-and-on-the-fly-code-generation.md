---
title: Zabezpečení a průběžné vytváření kódu
description: Generování kódu jménem méně důvěryhodného kódu, který běží s vyšším vztahem důvěryhodnosti, je problém se zabezpečením, zejména pokud volající může ovlivnit generování kódu.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 34ebda27a81ca29ebb27a721b77b735a12be882e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186790"
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpečení a průběžné vytváření kódu
Některé knihovny pracují generováním kódu a jeho spuštěním k provedení některé operace pro volajícího. Základním problémem je generování kódu jménem méně důvěryhodného kódu a jeho spuštění s vyšším vztahem důvěryhodnosti. Problém se zhoršuje, když volající může ovlivnit generování kódu, takže je nutné zajistit, že je generován pouze kód, který považujete za bezpečný.  
  
 Musíte přesně vědět, jaký kód generujete za všech okolností. To znamená, že musíte mít přísné kontroly všech hodnot, které získáte od uživatele, ať už se jedná o řetězce uzavřené v uvozovkách (které by měly být uvozeny, aby nemohly obsahovat neočekávané prvky kódu), identifikátory (které by měly být zkontrolovány, aby se ověřilo, že jsou platné identifikátory) nebo cokoli jiného. Identifikátory mohou být nebezpečné, protože zkompilované sestavení lze upravit tak, aby jeho identifikátory obsahovaly podivné znaky, které je pravděpodobně přeruší (i když se zřídka jedná o chybu zabezpečení).  
  
 Doporučujese generovat kód s odrazem vyzařovat, což často pomáhá vyhnout se mnoho z těchto problémů.  
  
 Při kompilaci kódu zvažte, zda existuje nějaký způsob, jak škodlivý program může změnit. Existuje malé časové okno, během kterého škodlivý kód může změnit zdrojový kód na disku před překladač přečte nebo před kód načte soubor DLL? Pokud ano, je nutné chránit adresář obsahující tyto soubory pomocí seznamu řízení přístupu v systému souborů podle potřeby.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
