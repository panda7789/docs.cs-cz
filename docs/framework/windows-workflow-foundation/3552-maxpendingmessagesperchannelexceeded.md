---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5455472a5b9ebdba7aea7d0384ce9cd4a9a2849d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 - MaxPendingMessagesPerChannelExceeded
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3552|  
|Klíčová slova|Kvóta, WFServices|  
|úroveň|Upozornění|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Určuje omezení MaxPendingMessagesPerChannel bylo dosaženo limitu.  
  
## <a name="message"></a>Zpráva  
 Omezení limit 'MaxPendingMessagesPerChannel' % 1, který byl vybrán. Chcete-li tento limit zvýšit, upravte vlastnost MaxPendingMessagesPerChannel na BufferedReceiveServiceBehavior.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Limit|xs:String|Limit omezovače MaxPendingMessagesPerChannel.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
