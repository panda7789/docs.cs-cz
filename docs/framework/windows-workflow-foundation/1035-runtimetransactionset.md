---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fcd6662c0f8899b6830dc8e06cee4f56b5ff906
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1035---runtimetransactionset"></a>1035 - RuntimeTransactionSet
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1035|  
|Klíčová slova|WFRuntime|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Značí, že aktivita má nastaven runtime transakce.  
  
## <a name="message"></a>Zpráva  
 Modul runtime transakce byla nastavena pomocí aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.  Provádění izolované k aktivitě %4, DisplayName: '%5', identifikátor InstanceId: '%6'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:String|Název typu aktivity.|  
|displayName|xs:String|Zobrazovaný název aktivity.|  
|identifikátor instanceId|xs:String|Id instance aktivity.|  
|IsolatedActivity|xs:String|Název typu aktivity, která je pro izolované transakce.|  
|IsolatedActivityDisplayName|xs:String|Zobrazovaný název aktivity, která je pro izolované transakce.|  
|IsolatedActivityInstanceId|xs:String|Id instance aktivity, která je pro izolované transakce.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
