---
title: 215 – MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: a8ba90b88ef8dbe3c8651bc565da61aae16a0a4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="215---messagereceivedbytransport"></a>215 – MessageReceivedByTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|215|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 K této události dojde, když přenos protokolu TCP přijme zprávu o. Všimněte si, že se na úrovni přenosu, více zpráv nelze vyměňovat mezi klienty a služby pro jednu operaci. To může být z důvodu chování infrastruktury, je dobrým příkladem zabezpečení. Proto počet `MessageReceivedByTransport` události, které jsou vygenerované lišit v závislosti na vaší služby vazby a jeho konfigurace.  
  
> [!NOTE]
>  Tato událost není vygenerované pro jednosměrné přenosy.  
  
## <a name="message"></a>Zpráva  
 Přenos přijala zprávu z '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Adresu naslouchání|`xs:string`|Adresa, která se zobrazila zpráva.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
