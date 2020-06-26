---
title: failedQI – pomocník spravovaného ladění (MDA)
description: Přečtěte si téma Failedqi – Managed Debugging Assistant (MDA) v rozhraní .NET, které může být aktivováno, když se přetypování nebo volání modelu COM z obálky s voláním metody runtime (RCW) nezdařilo.
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
ms.openlocfilehash: 2d7f14c67d47e58bcb88eab4621df63d7c598a7a
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415937"
---
# <a name="failedqi-mda"></a>failedQI – pomocník spravovaného ladění (MDA)
`failedQI`Pomocník spravovaného ladění (MDA) je aktivován při volání za běhu `QueryInterface` v ukazateli rozhraní modelu COM za běhu s voláním obálky (RCW) za běhu a `QueryInterface` volání se nezdařilo.  
  
## <a name="symptoms"></a>Příznaky  
 Přetypování na RCW se nepovedlo nebo se neočekávaně vyvolá volání modelu COM z RCW.  
  
## <a name="cause"></a>Příčina  
  
- Volání bylo provedeno z chybného kontextu.  
  
- Registrovaný proxy server selhává při volání, `QueryInterface` protože došlo k pokusu o volání v nesprávném kontextu.  
  
- Proxy ve vlastnictví OLE vrátil chybu HRESULT.  
  
## <a name="resolution"></a>Řešení  
 Prohlédněte si dokumentaci MSDN o pravidlech modelu COM.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Pokud `QueryInterface` volání selže, kontext je přepnut a `QueryInterface` volání se znovu pokusí zjistit, zda došlo k chybě v nesprávném kontextu.  
  
## <a name="output"></a>Výstup  
 Spravovaný název rozhraní, identifikátor GUID rozhraní a hodnota HRESULT selhání.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
