---
title: Významná trasování
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: c230c65b4d3fd45c4905d4ae5f4cbbf90e10faad
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804710"
---
# <a name="significant-traces"></a>Významná trasování
V tomto tématu jsou uvedeny některé hlavní trasování vygenerované Windows Communication Foundation (WCF).  
  
## <a name="significant-traces"></a>Významná trasování  
  
|trasování|Popis|  
|-----------|-----------------|  
|Zprávy protokolu trasování|Trasování je vygenerované při zaznamenání zprávu WCF pomocí protokolování zpráv při funkce `System.ServiceModel.MessageLogging` zdroj trasování je povoleno. Kliknutím na toto trasování zobrazí zprávu. Existují čtyři body konfigurovat protokolování pro zprávu: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, také označené atributem zdroj zprávy v protokolu trasování zpráv.|  
|Přijatá zpráva trasování|Trasování je vygenerované při příjmu zprávy WCF, pokud `System.ServiceModel` zdroj trasování je povoleno na podrobné úrovni nebo informace. Trasování je nutné zobrazíte šipka korelace zprávy v zobrazení grafu aktivity.|  
|Zpráva byla odeslána trasování|Trasování jsou vydávány, když je odeslána zpráva WCF, pokud `System.ServiceModel` zdroj trasování je povoleno na podrobné úrovni nebo informace. Trasování je nutné zobrazíte šipka korelace zprávy v zobrazení grafu aktivity.|  
|Získat prvek ChannelEndpointElement|Trasování jsou vydávány v konstrukce kanálu, na úrovni informace. Nabízí že popis koncového bodu, klient je rozhovoru (vzdálené adresy, vazby, název kontraktu).|  
|Získat prvek ServiceElement|Trasování jsou vydávány v hostitele služby konstrukce, na úrovni informace. Poskytuje popis kontrakt služby a vazby.|  
|Vytvoření připojení SocketConnection|Trasování jsou vydávány v první akce proces prováděných klientem a přijímání bajtů aktivity ve službě. Poskytuje místní a vzdálené IP adresy. Na úrovni informace jsou vydávány ho.|
