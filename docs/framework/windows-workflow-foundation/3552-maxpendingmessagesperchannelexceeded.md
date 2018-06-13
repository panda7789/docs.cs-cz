---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511228"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 - MaxPendingMessagesPerChannelExceeded
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3552|  
|Klíčová slova|Kvóta, WFServices|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Určuje omezení MaxPendingMessagesPerChannel bylo dosaženo limitu.  
  
## <a name="message"></a>Zpráva  
 Omezení limit 'MaxPendingMessagesPerChannel' % 1, který byl vybrán. Chcete-li tento limit zvýšit, upravte vlastnost MaxPendingMessagesPerChannel na BufferedReceiveServiceBehavior.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Limit|xs:String|Limit omezovače MaxPendingMessagesPerChannel.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
