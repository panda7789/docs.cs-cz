---
title: 499 - TransferEmitted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a0bbe31095a59be4b091de6974ae0173753e240
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="499---transferemitted"></a>499 - TransferEmitted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|499|  
|Klíčová slova|Řešení potíží, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|úroveň|LogAlways|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované při výskytu události přenosu.  
  
## <a name="message"></a>Zpráva  
 Vygenerované událost přenosu.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu & #124; Virtuální cesta služby & #124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication & #124;/CalculatorService.svc & #124; CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
