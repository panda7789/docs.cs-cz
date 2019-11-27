---
title: 'Služba: Počet chyb ověření zabezpečení'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 399249926bcb1383fd33f60510c2c212c6f4261c
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204584"
---
# <a name="service-security-validation-and-authentication-failures"></a>Služba: Počet chyb ověření zabezpečení
Název čítače: ověření zabezpečení a selhání ověřování  
  
## <a name="description"></a>Popis  
 Tento čítač se zvyšuje vždy, když je zpráva odmítnuta z důvodu problému se zabezpečením, na který nepokrývá čítač "počet neautorizovaných volání zabezpečení". Mezi takové problémy patří:  
  
- Z zprávy nelze číst token klienta.  
  
- Token klienta se nezdařil při ověřování (například chybné heslo).  
  
- Ověření podpisu se nezdařilo (například zpráva byla zfalšována).  
  
- Zpráva je duplicitní z předchozí verze, ke které může dojít během útoku prostřednictvím opakovaného přehrání.  
  
- Došlo k chybě dešifrování.  
  
- Ve zprávě chybí některé povinné prvky (například chybějící časové razítko nebo šifrovaný blok dat).  
  
- Během TLSNEGO/SPNEGO handshake došlo k chybám.
