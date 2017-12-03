---
title: "301 – UserDefinedErrorOccurred"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56cfe60c221062e3ad7ae1b8cbdc9b135e6fa2e8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="301---userdefinederroroccurred"></a>301 – UserDefinedErrorOccurred
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|301|  
|Klíčová slova|Řešení potíží, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|úroveň|Chyba|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované z uživatelského kódu. Vývojáři mohou emitování tuto událost, pokud dojde k chybě s vlastní ve své služby. To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API. Kromě toho je WCF vzorku, který zabalí toto rozhraní API a ukazuje, jak správně emitování této události.  
  
## <a name="message"></a>Zpráva  
 Název: %1, Reference: %2, datové části: % 3  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název|`xs:string`|Název uživatelem definované události.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.|  
|datová část|`xs:string`|Uživatelem definované datové části události.|
