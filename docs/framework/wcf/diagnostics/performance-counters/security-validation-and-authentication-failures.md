---
title: "Počet chyb ověřování zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c1d448d709c7ad20e9d08a291f5a38546cd93ce4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
