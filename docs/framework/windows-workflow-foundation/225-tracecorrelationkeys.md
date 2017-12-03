---
title: 225 - TraceCorrelationKeys
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f4b6eb5df59977de91f1651a47a96cdf44bcf29
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="225---tracecorrelationkeys"></a>225 - TraceCorrelationKeys
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|225|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované při korelace na základě obsahu se používá pro služby pracovních postupů. Obsahuje korelace klíčů, které se použijí ke korelaci zprávu, která instance.  
  
## <a name="message"></a>Zpráva  
 Vypočítat korelace klíč '%1' v nadřazeném oboru: %3' pomocí hodnoty '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Klíč instance|`xs:GUID`|Klíč, který byl vygenerován z hodnot korelace.|  
|Hodnoty|`xs:string`|Hodnoty, které byly použity k výpočtu klíčem instance korelace.|  
|Nadřazeného oboru|`xs:string`||  
|HostReference|`xs:string`|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
