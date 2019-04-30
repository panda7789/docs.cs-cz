---
title: 218 – ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 83f39be84a8d62962b85652b0e39b537c92e612c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781759"
---
# <a name="218---clientoperationcompleted"></a>218 – ClientOperationCompleted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|218|  
|klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován klienti hned po dokončení operace. Jednosměrná operace jde hned po úspěšném odeslání zprávy je. Pro operace požadavek odpověď jde po přijetí odpovědi.  
  
## <a name="message"></a>Zpráva  
 Klient dokončil provádění akce '%1' přidružené ke smlouvě '%2'. Zpráva byla odeslána na "%3".  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Akce|xs:string|Záhlaví SOAP akce odchozí zprávy.|  
|Název smlouvy|`xs:string`|Název smlouvy. Příklad: ICalculator.|  
|Cíl|`xs:string`|Adresa se zpráva odeslala do koncového bodu služby.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
