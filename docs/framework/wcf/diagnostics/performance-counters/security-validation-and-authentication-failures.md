---
title: Počet chyb ověřování zabezpečení
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5d7964c59f28f33d6ec7bc3ba605b84e6a201b14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="security-validation-and-authentication-failures"></a>Počet chyb ověřování zabezpečení
Název čítače: počet chyb ověření zabezpečení  
  
## <a name="description"></a>Popis  
 Tento čítač se navyšuje vždy, když zprávu byl odmítnut z důvodu problému zabezpečení nejsou pokryty čítač "Zabezpečení volání není oprávněn". Mezi tyto problémy patří:  
  
-   Token klienta nelze číst ze zprávy.  
  
-   Token klienta se nezdařilo ověření (třeba chybná hesla).  
  
-   Ověření podpisu se nezdařila (například zprávy s ní bylo neoprávněně).  
  
-   Zpráva je duplicitní z předchozí jeden, který může dojít při útoku formou opakovaného přehrávání.  
  
-   Došlo k selhání dešifrování.  
  
-   Některé elementy (například chybějící časové razítko nebo šifrovaná data blokovat) chybí požadované ze zprávy.  
  
-   Během TLSNEGO/SPNEGO metody handshake došlo k chybám.
