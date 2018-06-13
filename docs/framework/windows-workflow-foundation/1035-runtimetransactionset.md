---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510031"
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
