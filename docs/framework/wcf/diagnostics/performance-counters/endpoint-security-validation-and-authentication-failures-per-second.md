---
title: 'Koncový bod: Ověřování zabezpečení a počet selhání ověření za sekundu'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bc68f49326818f0e6687c06a38e5e51fd6960c9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a>Koncový bod: Ověřování zabezpečení a počet selhání ověření za sekundu
Název čítače: ověřování zabezpečení a ověřování chyb za sekundu  
  
## <a name="description"></a>Popis  
 Tento čítač se navyšuje vždy, když zprávu byl odmítnut z důvodu problému zabezpečení nejsou pokryty čítač "Zabezpečení volání není oprávněn". Mezi tyto problémy patří:  
  
-   Token klienta nelze číst ze zprávy.  
  
-   Token klienta se nezdařilo ověření (třeba chybná hesla).  
  
-   Ověření podpisu se nezdařila (například zprávy s ní bylo neoprávněně).  
  
-   Zpráva je duplicitní z předchozí jeden, který může dojít při útoku formou opakovaného přehrávání.  
  
-   Došlo k selhání dešifrování.  
  
-   Některé elementy (například chybějící časové razítko nebo šifrovaná data blokovat) chybí požadované ze zprávy.  
  
-   Během TLSNEGO/SPNEGO metody handshake došlo k chybám.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce:  
  
 (N1-N0)/((D1-D0)/F)
