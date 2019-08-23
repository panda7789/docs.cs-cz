---
title: 215 – MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: aa1ad30526aa65501e5d9875d3877631ca00879b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964190"
---
# <a name="215---messagereceivedbytransport"></a>215 – MessageReceivedByTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|id|215|  
|klíčová slova|Řešení potíží, ServiceModel|  
|Level|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 K této události dojde, když přenos založený na protokolu TCP obdrží zprávu. Všimněte si, že na úrovni přenosu je možné vyměňovat více zpráv mezi klienty a službami pro jednu operaci. To může být způsobeno chováním infrastruktury, takže zabezpečení je dobrým příkladem. Počet `MessageReceivedByTransport` událostí, které jsou vygenerovány, se tedy liší v závislosti na vazbě služby a její konfiguraci.  
  
> [!NOTE]
> Tato událost se nevysílá pro jednosměrná přenos.  
  
## <a name="message"></a>Message  
 Přenos přijal zprávu od '% 1 '.  
  
## <a name="details"></a>Podrobnosti  
  
|Název datové položky|Typ datové položky|Popis|  
|--------------------|--------------------|-----------------|  
|Adresa naslouchání|`xs:string`|Adresa, která přijala zprávu.|  
|HostReference|`xs:string`|V případě služeb hostovaných na webu toto pole jedinečně identifikuje službu ve webové hierarchii. Jeho formát je definován jako název webové stránky služba virtuální cesta&#124;&#124;ServiceName. Příklad: ' Výchozí web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '.|  
|AppDomain|`xs:string`|Řetězec vrácený třídou AppDomain. CurrentDomain. FriendlyName|
