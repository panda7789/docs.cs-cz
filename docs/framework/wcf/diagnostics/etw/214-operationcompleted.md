---
title: "214 – OperationCompleted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09a8dc1994da30c0f0c180640e3f66c8806e4528
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="214---operationcompleted"></a>214 – OperationCompleted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|214|  
|Klíčová slova|HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované při výchozí Model služby `OperationInvoker` volání metody byla dokončena bez dané metody došlo k výjimce.  
  
## <a name="message"></a>Zpráva  
 OperationInvoker dokončit volání metody '%1'. Doba trvání volání metoda byla ms '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název metody|`xs:string`|CLR název metody, který byl vyvolán `OperationInvoker`.|  
|Doba trvání|`xs:long`|Čas v milisekundách, po které trvalo `OperationInvoker` k vyvolání metody.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
