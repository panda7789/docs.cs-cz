---
title: 220 – MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 92ec664aead15470fbed576bf157d64d984ddebf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="220---messagesenttotransport"></a>220 – MessageSentToTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|220|  
|Klíčová slova|EndToEndMonitoring, řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované při modelu služby odešle zprávu do přenosu.  
  
> [!NOTE]
>  Tato událost nebude vygenerované pro jednosměrné přenosy.  
  
## <a name="message"></a>Zpráva  
 Dispečer poslali zprávu o přenos. ID korelace == '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|ID korelace|`xs:GUID`|Aktivita ID použít ke korelaci `MessageSentToTransport` událostí ze služby nebo klienta na jeho odpovídající `MessageReceivedFromTransport` na druhém konci.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
