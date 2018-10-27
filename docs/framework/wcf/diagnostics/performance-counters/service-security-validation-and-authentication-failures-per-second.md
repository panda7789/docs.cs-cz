---
title: 'Služba: Počet chyb ověřování zabezpečení za sekundu'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: 97752fbd4ff38c40917c132fddfe3798a7ee6766
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183630"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a>Služba: Počet chyb ověřování zabezpečení za sekundu
Název čítače: ověřování zabezpečení a ověřování chyb za sekundu.  
  
## <a name="description"></a>Popis  
 Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno". Tyto problémy patří:  
  
-   Token klienta nelze číst ze zprávy.  
  
-   Token klienta se nezdařilo ověřování (například špatné heslo).  
  
-   Ověření podpisu se nezdařilo (například, zpráva byla změněna).  
  
-   Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.  
  
-   Došlo k selhání dešifrování.  
  
-   Některé prvky (například chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.  
  
-   Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)
