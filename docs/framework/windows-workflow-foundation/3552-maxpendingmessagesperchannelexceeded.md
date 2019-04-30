---
title: 3552 – MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945935"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 – MaxPendingMessagesPerChannelExceeded
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3552|  
|klíčová slova|Quota, WFServices|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Určuje omezení bylo dosaženo omezení MaxPendingMessagesPerChannel.  
  
## <a name="message"></a>Zpráva  
 Bylo dosaženo omezení 'MaxPendingMessagesPerChannel' limit '%1'. Chcete-li tento limit zvýšit, upravte vlastnost MaxPendingMessagesPerChannel objektu bufferedreceiveservicebehavior.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Omezení|xs:string|Limit omezení MaxPendingMessagesPerChannel.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
