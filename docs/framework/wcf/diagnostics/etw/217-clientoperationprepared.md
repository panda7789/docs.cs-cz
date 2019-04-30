---
title: 217 – ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: 5979cd8ffe0e05b61af01d2aa98c4a2c63fd432c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781758"
---
# <a name="217---clientoperationprepared"></a>217 – ClientOperationPrepared
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|217|  
|klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován klienty těsně před plánovaným operace je odeslána do služby.  
  
## <a name="message"></a>Zpráva  
 Klient provádí akci '%1' přidružené ke smlouvě '%2'. "% 3" pošle zpráva.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Akce|`xs:string`|Záhlaví SOAP akce odchozí zprávy.|  
|Název smlouvy|`xs:string`|Název smlouvy. Příklad: ICalculator.|  
|Cíl|`xs:string`|Adresa koncového bodu služby, které je zpráva odeslána.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
