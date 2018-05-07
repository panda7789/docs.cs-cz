---
title: Významná trasování
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: 2dc5010874285ba14dae625fcbf92740eb1707b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="significant-traces"></a>Významná trasování
V tomto tématu jsou uvedeny některé hlavní trasování vygenerované Windows Communication Foundation (WCF).  
  
## <a name="significant-traces"></a>Významná trasování  
  
|trasování|Popis|  
|-----------|-----------------|  
|Zprávy protokolu trasování|Trasování je vygenerované při [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zaznamenána podle protokolování zpráv funkci, kdy `System.ServiceModel.MessageLogging` zdroj trasování je povoleno. Kliknutím na toto trasování zobrazí zprávu. Existují čtyři body konfigurovat protokolování pro zprávu: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, také označené atributem zdroj zprávy v protokolu trasování zpráv.|  
|Přijatá zpráva trasování|Trasování je vygenerované při [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] je přijatá zpráva, pokud `System.ServiceModel` zdroj trasování je povoleno na podrobné úrovni nebo informace. Trasování je nutné zobrazíte šipka korelace zprávy v zobrazení grafu aktivity.|  
|Zpráva byla odeslána trasování|Trasování je vygenerované při [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] je odeslána zpráva, pokud `System.ServiceModel` zdroj trasování je povoleno na podrobné úrovni nebo informace. Trasování je nutné zobrazíte šipka korelace zprávy v zobrazení grafu aktivity.|  
|Získat prvek ChannelEndpointElement|Trasování jsou vydávány v konstrukce kanálu, na úrovni informace. Nabízí že popis koncového bodu, klient je rozhovoru (vzdálené adresy, vazby, název kontraktu).|  
|Získat prvek ServiceElement|Trasování jsou vydávány v hostitele služby konstrukce, na úrovni informace. Poskytuje popis kontrakt služby a vazby.|  
|Vytvoření připojení SocketConnection|Trasování jsou vydávány v první akce proces prováděných klientem a přijímání bajtů aktivity ve službě. Poskytuje místní a vzdálené IP adresy. Na úrovni informace jsou vydávány ho.|
