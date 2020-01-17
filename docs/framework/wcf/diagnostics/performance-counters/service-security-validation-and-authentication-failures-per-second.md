---
title: 'Služba: Počet chyb ověřování zabezpečení za sekundu'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: f3f27100afb7390a68d99421cad6f43d9abaccd5
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163862"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a>Služba: Počet chyb ověřování zabezpečení za sekundu
Název čítače: ověření zabezpečení a počet selhání ověření za sekundu.  
  
## <a name="description"></a>Popis  
 Tento čítač se zvyšuje vždy, když je zpráva odmítnuta z důvodu problému se zabezpečením, na který nepokrývá čítač "počet neautorizovaných volání zabezpečení". Mezi takové problémy patří:  
  
- Z zprávy nelze číst token klienta.  
  
- Token klienta se nezdařil při ověřování (například chybné heslo).  
  
- Ověření podpisu se nezdařilo (například zpráva byla zfalšována).  
  
- Zpráva je duplicitní z předchozí verze, ke které může dojít během útoku prostřednictvím opakovaného přehrání.  
  
- Došlo k chybě dešifrování.  
  
- Ve zprávě chybí některé povinné prvky (například chybějící časové razítko nebo šifrovaný blok dat).  
  
- Během TLSNEGO/SPNEGO handshake došlo k chybám.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce:  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
