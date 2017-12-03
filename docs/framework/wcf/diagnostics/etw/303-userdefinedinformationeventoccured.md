---
title: "303 – UserDefinedInformationEventOccured"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bc04837834277dccc9d21d27e89c84f09f36167
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="303---userdefinedinformationeventoccured"></a>303 – UserDefinedInformationEventOccured
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|303|  
|Klíčová slova|Řešení potíží, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované z uživatelského kódu. Vývojáři mohou emitování Tato událost při výskytu vlastní informační události ve své služby. To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API. Kromě toho je WCF vzorku, který zabalí toto rozhraní API a ukazuje, jak správně emitování této události.  
  
## <a name="message"></a>Zpráva  
 Název: %1, Reference: %2, datové části: % 3  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název|`xs:string`|Uživatelem definovaný název události|  
|HostReference|`xs:string`|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.|  
|datová část|`xs:string`|Uživatelem definované datové části události.|
