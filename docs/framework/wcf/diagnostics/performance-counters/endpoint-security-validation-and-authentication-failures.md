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
ms.openlocfilehash: 7d1f05ddc4b0fcf93c87e69932f860f3c7e2ff85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
