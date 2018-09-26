---
title: 'Koncový bod: Ověřování zabezpečení a počet selhání ověření za sekundu'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
author: BrucePerlerMS
ms.openlocfilehash: 43f5f7ef37be22124288529160cf18ce02396aa4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200513"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a>Koncový bod: Ověřování zabezpečení a počet selhání ověření za sekundu
Název čítače: ověřování zabezpečení a ověřování chyb za sekundu  
  
## <a name="description"></a>Popis  
 Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno". Tyto problémy patří:  
  
-   Token klienta nelze číst ze zprávy.  
  
-   Token klienta se nezdařilo ověřování (například špatné heslo).  
  
-   Ověření podpisu se nezdařilo (například, zpráva byla změněna).  
  
-   Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.  
  
-   Došlo k selhání dešifrování.  
  
-   Některé prvky (například chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.  
  
-   Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce:  
  
 (N1-N0)/((D1-D0)/F)
