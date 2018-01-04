---
title: "207 – FaultProviderInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9035739f8625a07e8bf2b9bce2fe109880676405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="207---faultproviderinvoked"></a>207 – FaultProviderInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|207|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované po `FaultProvider` metoda byla volána.  
  
## <a name="message"></a>Zpráva  
 Dispečer vyvolat FaultProvider typu "%1, s výjimkou typu '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Položka FullName CLR typu vyvolanou `FaultProvider`.|  
|ExceptionTypeName|`xs:string`|Položka FullName CLR výjimky, `FaultProvider` má zpracovat.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
