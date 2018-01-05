---
title: 4203 - RenewLockSystemError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fabe6f2c023bf9b997d2a4e19b4a3755c93f408
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="4203---renewlocksystemerror"></a>4203 - RenewLockSystemError
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4203|  
|Klíčová slova|WFInstanceStore|  
|úroveň|Chyba|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Určuje zprostředkovatele SQL se nepodařilo prodloužit platnost zámku z důvodu vypršení buď zámku již uplynul nebo vlastníka zámku byla odstraněna. SqlWorkflowInstanceStore bude ukončeno.  
  
## <a name="message"></a>Zpráva  
 Prodloužit platnost uzamčení se nezdařilo, vypršení platnosti zámku již předán nebo vlastníka zámku byla odstraněna. Probíhá rušení SqlWorkflowInstanceStore.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
