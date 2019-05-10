---
title: 'Koncový bod: Počet chyb ověření zabezpečení'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: 9e0192ea600bb52abd555f2f83cfe8e96d3fe203
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619343"
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
