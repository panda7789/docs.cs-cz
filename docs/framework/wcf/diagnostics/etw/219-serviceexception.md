---
title: 219 – ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="219---serviceexception"></a>219 – ServiceException
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|219|  
|Klíčová slova|EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel|  
|úroveň|Chyba|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované, když dojde k neošetřené výjimce služby WCF. To zahrnuje neošetřené výjimky během aktivace, při zpracování zprávy a v uživatelském kódu.  
  
## <a name="message"></a>Zpráva  
 Při zpracování zprávy došlo k neošetřené výjimce typu '%2'. ToString – Úplná výjimka: %1.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|Výsledek volání `ToString`() na výjimky CLR.|  
|ExceptionTypeName|`xs:string`|Položka FullName CLR v výjimky typu.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
