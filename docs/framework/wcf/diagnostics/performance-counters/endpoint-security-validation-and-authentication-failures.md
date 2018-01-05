---
title: "Koncový bod: Počet chyb ověřování zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5bd38ae0e3506397378b7c59976c6c692045054d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-security-validation-and-authentication-failures"></a>Koncový bod: Počet chyb ověřování zabezpečení
Název čítače: počet chyb ověření zabezpečení  
  
## <a name="description"></a>Popis  
 Tento čítač se navyšuje vždy, když zprávu byl odmítnut z důvodu problému zabezpečení nejsou pokryty čítač "Zabezpečení volání není oprávněn". Mezi tyto problémy patří:  
  
-   Token klienta nelze číst ze zprávy.  
  
-   Token klienta se nezdařilo ověření (špatné heslo).  
  
-   Ověření podpisu se nezdařilo. (zpráva s ní bylo neoprávněně).  
  
-   Zpráva je duplicitní z předchozí jeden, který může dojít při útoku formou opakovaného přehrávání.  
  
-   Došlo k selhání dešifrování.  
  
-   Zpráva chybí některé požadované prvky (chybějící časové razítko nebo blok šifrovaných dat).  
  
-   Během TLSNEGO/SPNEGO metody handshake došlo k chybám.
