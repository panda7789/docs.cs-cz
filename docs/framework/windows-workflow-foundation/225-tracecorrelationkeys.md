---
title: 225 – TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 0bb54387dbd738a01225008edfc45ecb7297cd00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755659"
---
# <a name="225---tracecorrelationkeys"></a>225 – TraceCorrelationKeys
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|225|  
|klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován při korelace na základě obsahu se používá pro služby pracovního postupu. Obsahuje klíče korelace, které se použijí pro korelaci zprávy do instance.  
  
## <a name="message"></a>Zpráva  
 Vypočítá klíč korelace '%1' pomocí hodnoty '%2' v nadřazeném oboru '%3'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Klíč instance|`xs:GUID`|Klíč, který byl vytvořen hodnoty korelace.|  
|Hodnoty|`xs:string`|Hodnoty, které byly použity k výpočtu korelace klíč instance.|  
|Nadřazený obor|`xs:string`||  
|HostReference|`xs:string`|Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
