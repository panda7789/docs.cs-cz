---
title: "failedQI – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87fe67e1e64d69912095e1d9587d277805a3eb80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="failedqi-mda"></a>failedQI – pomocník spravovaného ladění (MDA)
`failedQI` Pomocník spravovaného ladění (MDA) se aktivuje při volání modulu runtime `QueryInterface` na ukazatel rozhraní COM jménem obálka volatelná aplikacemi runtime (RCW) a `QueryInterface` volání selže.  
  
## <a name="symptoms"></a>Příznaky  
 Přetypování na RCW selže nebo volání COM z RCW neočekávaně selže.  
  
## <a name="cause"></a>příčina  
  
-   Přišla z nesprávného kontextu.  
  
-   Registrovaný proxy selhává `QueryInterface` volat, protože došlo k pokusu o volání v chybě kontextu.  
  
-   Proxy služby vlastněných OLE vrátila chybu HRESULT.  
  
## <a name="resolution"></a>Rozlišení  
 V MSDN dokumentaci na COM pravidla.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Pokud `QueryInterface` volání selže, kontext se přepnul a `QueryInterface` volání je opakovat pokus o chcete zobrazit, pokud byl nesprávný kontextu při selhání.  
  
## <a name="output"></a>Výstup  
 Název spravovaného rozhraní, identifikátor GUID rozhraní a HRESULT selhání.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
