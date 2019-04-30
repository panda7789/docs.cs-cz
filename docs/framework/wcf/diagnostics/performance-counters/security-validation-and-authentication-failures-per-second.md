---
title: Ověřování zabezpečení a počet selhání ověření za sekundu
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: e3db8cb20399bdff9b73a428ea2a53909da4eee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915769"
---
# <a name="security-validation-and-authentication-failures-per-second"></a>Ověřování zabezpečení a počet selhání ověření za sekundu
Název čítače: Ověřování zabezpečení a počet selhání ověření za sekundu.  
  
## <a name="description"></a>Popis  
 Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno". Tyto problémy patří:  
  
- Token klienta nelze číst ze zprávy.  
  
- Token klienta se nezdařilo ověřování (například špatné heslo).  
  
- Ověření podpisu se nezdařilo (například, zpráva byla změněna).  
  
- Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.  
  
- Došlo k selhání dešifrování.  
  
- Některé prvky (například chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.  
  
- Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce:  
  
 (N1-N0)/((D1-D0)/F)
