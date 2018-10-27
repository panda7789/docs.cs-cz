---
title: 'Služba: Počet chyb ověřování zabezpečení'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: ba8da3ae6be6bd089690359f19e153da1e0b54fc
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50039988"
---
# <a name="service-security-validation-and-authentication-failures"></a>Služba: Počet chyb ověřování zabezpečení
Název čítače: počet chyb ověření zabezpečení  
  
## <a name="description"></a>Popis  
 Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno". Tyto problémy patří:  
  
-   Token klienta nelze číst ze zprávy.  
  
-   Token klienta se nezdařilo ověřování (například,, chybných zadání hesla).  
  
-   Ověření podpisu se nezdařilo (například, zpráva byla změněna).  
  
-   Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.  
  
-   Došlo k selhání dešifrování.  
  
-   Některé prvky (například,, chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.  
  
-   Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.
