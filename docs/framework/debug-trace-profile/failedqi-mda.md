---
title: failedQI – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fec1bfb402f3b394ceb36590c3a880f82c5cb101
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052785"
---
# <a name="failedqi-mda"></a>failedQI – pomocník spravovaného ladění (MDA)
Pomocník spravovaného ladění (MDA) je aktivován při volání `QueryInterface` za běhu v ukazateli rozhraní modelu COM za běhu s voláním obálky (RCW) za běhu a `QueryInterface` volání se nezdařilo. `failedQI`  
  
## <a name="symptoms"></a>Příznaky  
 Přetypování na RCW se nepovedlo nebo se neočekávaně vyvolá volání modelu COM z RCW.  
  
## <a name="cause"></a>příčina  
  
- Volání bylo provedeno z chybného kontextu.  
  
- Registrovaný proxy server selhává `QueryInterface` při volání, protože došlo k pokusu o volání v nesprávném kontextu.  
  
- Proxy ve vlastnictví OLE vrátil chybu HRESULT.  
  
## <a name="resolution"></a>Řešení  
 Prohlédněte si dokumentaci MSDN o pravidlech modelu COM.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Pokud volání selže, kontext je přepnut `QueryInterface` a volání se znovu pokusí zjistit, zda došlo k chybě v nesprávném kontextu. `QueryInterface`  
  
## <a name="output"></a>Výstup  
 Spravovaný název rozhraní, identifikátor GUID rozhraní a hodnota HRESULT selhání.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
