---
title: "215 – MessageReceivedByTransport"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: acc39fea579a66479de6686cba928915a437f864
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="215---messagereceivedbytransport"></a>215 – MessageReceivedByTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|215|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
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
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
