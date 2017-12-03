---
title: 223 - OperationFaulted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0428d90135823761e7b8a12f560786e34e12734
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="223---operationfaulted"></a>223 - OperationFaulted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|223|  
|Klíčová slova|EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel|  
|úroveň|Upozornění|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované při výchozí Model služby `OperationInvoker` došlo k výjimce odvozování z `FaultException` při vyvolání příslušnou metodu.  
  
## <a name="message"></a>Zpráva  
 Metoda "%1" způsobila FaultException při vyvolané OperationInvoker. Doba trvání volání metoda byla ms '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|MethodName|`xs:string`|CLR název metody, který byl vyvolán `OperationInvoker`.|  
|Doba trvání|`xs:long`|Čas v milisekundách, po které trvalo `OperationInvoker` k vyvolání metody.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
