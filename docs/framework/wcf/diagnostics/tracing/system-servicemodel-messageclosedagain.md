---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: 3a73834888ae4a8945bd71492d787e23868fa5e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelmessageclosedagain"></a>System.ServiceModel.MessageClosedAgain
System.ServiceModel.MessageClosedAgain  
  
## <a name="description"></a>Popis  
 Zprávu se zavřel znovu.  
  
 Zprávu by měly být ukončeny pouze jednou. Pokud trasování je právě vygenerované v uživatelském kódu rozšíření, znamená to, že uživatelského kódu rozšíření ukončuje zprávu, která již byl uzavřen. Pokud toto trasování je právě vygenerované prostřednictvím kód produktu, znamená to, že uživatelského kódu rozšíření může potenciálně být zavření zprávy příliš brzké.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
