---
title: 'Služba: Počet chyb ověření zabezpečení'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: ba8da3ae6be6bd089690359f19e153da1e0b54fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998306"
---
# <a name="service-security-validation-and-authentication-failures"></a>Služba: Počet chyb ověření zabezpečení
Název čítače: Počet chyb ověření zabezpečení  
  
## <a name="description"></a>Popis  
 Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno". Tyto problémy patří:  
  
- Token klienta nelze číst ze zprávy.  
  
- Token klienta se nezdařilo ověřování (například,, chybných zadání hesla).  
  
- Ověření podpisu se nezdařilo (například, zpráva byla změněna).  
  
- Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.  
  
- Došlo k selhání dešifrování.  
  
- Některé prvky (například,, chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.  
  
- Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.
