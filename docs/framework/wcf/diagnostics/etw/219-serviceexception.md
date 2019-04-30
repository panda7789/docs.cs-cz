---
title: 219 – ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781729"
---
# <a name="219---serviceexception"></a>219 – ServiceException
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|219|  
|klíčová slova|EndToEndMonitoring HealthMonitoring, řešení potíží s ServiceModel|  
|úroveň|Chyba|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován, když dojde k neošetřené výjimce ve službě WCF. To zahrnuje neošetřené výjimky během aktivace, při zpracování zprávy a v uživatelském kódu.  
  
## <a name="message"></a>Zpráva  
 Při zpracování zprávy došlo k neošetřené výjimce typu '%2'. ToString úplných informacích o výjimce: %1.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|Výsledek volání `ToString`() na výjimky modulu CLR.|  
|ExceptionTypeName|`xs:string`|CLR úplný název typu výjimky.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
