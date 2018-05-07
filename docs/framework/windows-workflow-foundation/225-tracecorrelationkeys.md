---
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 0bb54387dbd738a01225008edfc45ecb7297cd00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="225---tracecorrelationkeys"></a>225 - TraceCorrelationKeys
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|225|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
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
|HostReference|`xs:string`|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
