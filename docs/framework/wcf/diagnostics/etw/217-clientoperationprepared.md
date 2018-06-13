---
title: 217 – ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: 5979cd8ffe0e05b61af01d2aa98c4a2c63fd432c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461062"
---
# <a name="217---clientoperationprepared"></a>217 – ClientOperationPrepared
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|217|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované klienty těsně před operace je odešle do služby.  
  
## <a name="message"></a>Zpráva  
 Klient je provádění akce '%1' přidružené ke smlouvě '%2'. Zpráva bude odeslána na "%3".  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Akce|`xs:string`|Hlavička protokolu SOAP akce odchozí zprávy.|  
|Název smlouvy|`xs:string`|Název smlouvy. Příklad: ICalculator.|  
|Cílový|`xs:string`|Adresa koncového bodu služby, který je zpráva odeslána.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
