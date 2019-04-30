---
title: 'Koncový bod: Počet chyb ověření zabezpečení'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: e69549a276e2f9cece966dd44f6a1b3a3d3cb59f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916327"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a>Koncový bod: Počet chyb ověření zabezpečení
Název čítače: Počet chyb ověření zabezpečení  
  
## <a name="description"></a>Popis  
 Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno". Tyto problémy patří:  
  
- Token klienta nelze číst ze zprávy.  
  
- Token klienta se nezdařilo ověřování (špatné heslo).  
  
- Ověření podpisu se nezdařilo (zprávě někdo nemanipuloval).  
  
- Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.  
  
- Došlo k selhání dešifrování.  
  
- Zpráva chybí některé požadované prvky (chybějící časového razítka nebo šifrovaného datového bloku).  
  
- Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.
