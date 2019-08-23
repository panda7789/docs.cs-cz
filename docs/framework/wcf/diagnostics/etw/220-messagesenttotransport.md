---
title: 220 – MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 9f95edf42e0b1ec19d2019773def282fc279871b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948287"
---
# <a name="220---messagesenttotransport"></a>220 – MessageSentToTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|Id|220|  
|klíčová slova|EndToEndMonitoring, řešení potíží, ServiceModel|  
|Level|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je generována, když model služby pošle zprávu na přenos.  
  
> [!NOTE]
> Tato událost nebude vygenerována pro jednosměrná přenos.  
  
## <a name="message"></a>Message  
 Dispečer odeslal zprávu přenosu. ID korelace =% 1.  
  
## <a name="details"></a>Podrobnosti  
  
|Název datové položky|Typ datové položky|Popis|  
|--------------------|--------------------|-----------------|  
|ID korelace|`xs:GUID`|ID aktivity, které se používá ke korelaci `MessageSentToTransport` události ze služby nebo klienta s odpovídajícím `MessageReceivedFromTransport` na druhém konci.|  
|HostReference|`xs:string`|V případě služeb hostovaných na webu toto pole jedinečně identifikuje službu ve webové hierarchii. Jeho formát je definován jako název webové stránky služba virtuální cesta&#124;&#124;ServiceName. Příklad: ' Výchozí web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '.|  
|AppDomain|`xs:string`|Řetězec vrácený třídou AppDomain. CurrentDomain. FriendlyName|
