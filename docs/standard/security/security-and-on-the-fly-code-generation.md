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
ms.openlocfilehash: ffb1081c80c31353ad38080ae16ef9f8a74b5481
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45512839"
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpečení a průběžné vytváření kódu
Některé knihovny fungují tak, že generování kódu a spouštěním provádět některé operace pro volajícího. Základní problém je generování kódu jménem nižší úrovně důvěryhodnosti kódu a běží na vyšší vztah důvěryhodnosti. Problém se zhoršuje, když volající může ovlivnit generování kódu, proto musíte zajistit, že je vygenerována pouze kód, které považujete za bezpečný.  
  
 Je potřeba vědět, přesně jaký kód generují po celou dobu. To znamená, že musí mít přísné ovládacích prvků na všechny hodnoty, které jste získali od uživatele, mohou to být uzavřené v uvozovkách řetězce, (které by měl být uvozen řídicími znaky, takže nemůžou obsahovat prvky neočekávaný kód), identifikátory (které by měly být porovnány k ověření, že jsou platné identifikátory), nebo cokoli jiného. Identifikátory mohou být nebezpečné, protože zkompilovaného sestavení lze upravit tak, aby jeho identifikátory obsahují zvláštní znaky, které budou pravděpodobně ho rozdělit (i když je zřídka ohrožení zabezpečení).  
  
 Doporučuje se, že generování kódu pomocí reflexe generování, které často umožňuje vyhnout se mnohé z těchto problémů.  
  
 Při kompilaci kódu, zvažte, zda je nějakým způsobem ho změnit škodlivý program. Existuje krátké období, během které škodlivý kód může změnit zdrojový kód na disku před kompilátor přečte nebo před kódu načte soubor .dll? Pokud ano, je nutné chránit adresáře, který obsahuje tyto soubory použít seznam řízení přístupu v systému souborů, podle potřeby.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
