---
title: 'Služba: Počet chyb ověřování zabezpečení'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
author: BrucePerlerMS
ms.openlocfilehash: 4c74cb1962bbc0f03ac33d8fcc7b10052bec8273
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47197072"
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
