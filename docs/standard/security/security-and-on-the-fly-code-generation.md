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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2cfc93e1c8d3d9e878d96de164b0d646e62c0998
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583965"
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpečení a průběžné vytváření kódu
Některé knihovny fungují pomocí generování kódu a spustit a provést nějaké operace pro volajícího. Základní problém generování kódu jménem kódu nižší úrovně důvěryhodnosti a spuštěná na vyšší vztah důvěryhodnosti. Problém se zhoršuje, když volající může ovlivnit generování kódu, proto musíte zajistit, že je vygenerováno, pouze kód, které považujete za bezpečná.  
  
 Je třeba vědět, přesně jaký kód generují za všech okolností. To znamená, že je nutné mít přísné ovládacích prvků na všechny hodnoty, které jste získali od uživatele, mohou to být řetězce uzavřené v uvozovkách, (které by měly být ukončeny, takže nemůžou zahrnovat neočekávané prvky kódu), identifikátory (které by měly být zkontrolovány ověřte, zda jsou platná identifikátorů), nebo cokoliv jiného. Identifikátory může být nebezpečné, protože kompilované sestavení můžete upravit tak, aby jeho identifikátory obsahovat neobvyklé znaky, které bude pravděpodobně ho rozdělit (i když je zřídka chybu zabezpečení).  
  
 Doporučujeme, abyste generovali kód pomocí reflexe emitování, což často umožňuje vyhnout se mnoho z těchto problémů.  
  
 Při kompilaci kódu zvažte, zda je nějakým způsobem škodlivý program se může změnit. Je k dispozici krátké době, během které škodlivý kód změnit zdrojový kód na disku, než ho kompilátor přečte nebo před kódu souboru .dll? Pokud ano, je nutné chránit adresář obsahující tyto soubory použít seznam řízení přístupu v systému souborů, podle potřeby.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
