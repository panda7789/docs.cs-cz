---
title: "Zabezpečení a průběžné vytváření kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c6bb895979fb44616349505a07591f9ced9fedac
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpečení a průběžné vytváření kódu
Některé knihovny fungují pomocí generování kódu a spustit a provést nějaké operace pro volajícího. Základní problém generování kódu jménem kódu nižší úrovně důvěryhodnosti a spuštěná na vyšší vztah důvěryhodnosti. Problém se zhoršuje, když volající může ovlivnit generování kódu, proto musíte zajistit, že je vygenerováno, pouze kód, které považujete za bezpečná.  
  
 Je třeba vědět, přesně jaký kód generují za všech okolností. To znamená, že je nutné mít přísné ovládacích prvků na všechny hodnoty, které jste získali od uživatele, mohou to být řetězce uzavřené v uvozovkách, (které by měly být ukončeny, takže nemůžou zahrnovat neočekávané prvky kódu), identifikátory (které by měly být zkontrolovány ověřte, zda jsou platná identifikátorů), nebo cokoliv jiného. Identifikátory může být nebezpečné, protože kompilované sestavení můžete upravit tak, aby jeho identifikátory obsahovat neobvyklé znaky, které bude pravděpodobně ho rozdělit (i když je zřídka chybu zabezpečení).  
  
 Doporučujeme, abyste generovali kód pomocí reflexe emitování, což často umožňuje vyhnout se mnoho z těchto problémů.  
  
 Při kompilaci kódu zvažte, zda je nějakým způsobem škodlivý program se může změnit. Je k dispozici krátké době, během které škodlivý kód změnit zdrojový kód na disku, než ho kompilátor přečte nebo před kódu souboru .dll? Pokud ano, je nutné chránit adresář obsahující tyto soubory použít seznam řízení přístupu v systému souborů, podle potřeby.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
