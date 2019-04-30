---
title: Významná trasování
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: c230c65b4d3fd45c4905d4ae5f4cbbf90e10faad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784945"
---
# <a name="significant-traces"></a>Významná trasování
V tomto tématu jsou uvedeny některé hlavní trasování generované technologií Windows Communication Foundation (WCF).  
  
## <a name="significant-traces"></a>Významná trasování  
  
|Trasování|Popis|  
|-----------|-----------------|  
|Zprávy protokolu trasování|Trasování je vygenerován, když se zaznamená zprávu WCF pomocí protokolování zpráv při funkcí `System.ServiceModel.MessageLogging` zdroj trasování je povolené. Kliknutím na toto trasování zobrazí zprávu. Existují čtyři body konfigurovat protokolování zprávy: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, také označený atributem zdroj zprávy protokolu trasování zprávy.|  
|Byla přijata zpráva trasování|Trasování je vygenerován při doručení zprávy do WCF, pokud `System.ServiceModel` je povolený zdroj trasování na podrobné úrovni nebo informace. Trasování je nutné zobrazit šipka korelace zprávy v zobrazení grafu aktivit.|  
|Byla odeslána zpráva trasování|Trasování je vygenerován při odesílání zprávy WCF, pokud `System.ServiceModel` je povolený zdroj trasování na podrobné úrovni nebo informace. Trasování je nutné zobrazit šipka korelace zprávy v zobrazení grafu aktivit.|  
|Získat element ChannelEndpointElement|Trasování je vygenerován v konstrukci objekt pro vytváření kanálů, na úrovni informace. To poskytuje že popis koncového bodu, klient se mluví (Vzdálená adresa, vazba, název smlouvy).|  
|Získat element ServiceElement|Trasování je vygenerován v konstrukci hostitele služby, na úrovni informace. Poskytuje popis kontraktu služby a vazby.|  
|Vytvoření připojení SocketConnection|Trasování je vygenerován v první proces akcí prováděných klientem a v aktivitě Receive bajtů na službu. Poskytuje místní a vzdálené IP adresy. Je vygenerován na úrovni informace.|
