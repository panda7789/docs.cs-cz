---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 16b0261a53df29b1fc2049c25375c651735a524c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
Služba protokolu WS-AT se nepodařilo zaregistrovat účastníka pro protokol ovládacího prvku.  
  
## <a name="description"></a>Popis  
 Trasovat, pokud služba MSDTC zjistí Neplatná žádost o registraci. Příčinou může být více dokončení žádosti o registraci a interní chyby.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Nepokoušejte se registrace pro dokončení více než jednou.  Také zkontrolujte stav řetězce v rámci zpráva trasování, která k určení, zda existuje libovolnou položku níž lze provést akci.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
