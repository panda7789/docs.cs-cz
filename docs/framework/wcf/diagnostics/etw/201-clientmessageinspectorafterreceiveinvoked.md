---
title: "201 – ClientMessageInspectorAfterReceiveInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cb6d243177700daa1e653c394e027a6f5428371
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a>201 – ClientMessageInspectorAfterReceiveInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|201|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované po Model služby má vyvolat `AfterReceiveReply` metodu na zpráva inspector klienta.  
  
## <a name="message"></a>Zpráva  
 Dispečer vyvolat 'AfterReceiveReply' na ClientMessageInspector typu '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Položka FullName CLR vyvolaná inspector typu.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
