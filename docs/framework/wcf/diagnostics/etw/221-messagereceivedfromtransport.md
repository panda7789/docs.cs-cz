---
title: 221 – MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 98dbf2728242fa73b3e54b7cf32f9e227e5251b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="221---messagereceivedfromtransport"></a>221 – MessageReceivedFromTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|221|  
|Klíčová slova|EndToEndMonitoring, řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované, když Model služby přijme zprávu o z přenosu.  
  
## <a name="message"></a>Zpráva  
 Dispečer přijala zprávu z přenosu. ID korelace == '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|ID korelace|`xs:GUID`|Aktivita ID použít ke korelaci `MessageSentToTransport` událostí ze služby nebo klienta na jeho odpovídající `MessageReceivedFromTransport` na druhém konci.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
