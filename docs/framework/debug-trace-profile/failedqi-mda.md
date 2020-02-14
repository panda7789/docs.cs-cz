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
ms.openlocfilehash: 4c36ec514645a38ef1228e76bdf6dbd06e886bae
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217509"
---
# <a name="failedqi-mda"></a>failedQI – pomocník spravovaného ladění (MDA)
Pokud běhové prostředí za běhu `QueryInterface` na ukazatel rozhraní modelu COM za běhu RCW (), a volání `QueryInterface` se nezdařilo, aktivuje se Pomocník pro správu spravovaného ladění (MDA). `failedQI`  
  
## <a name="symptoms"></a>Příznaky  
 Přetypování na RCW se nepovedlo nebo se neočekávaně vyvolá volání modelu COM z RCW.  
  
## <a name="cause"></a>Příčina  
  
- Volání bylo provedeno z chybného kontextu.  
  
- Registrovaný proxy server selhává `QueryInterface` volání, protože došlo k pokusu o volání v nesprávném kontextu.  
  
- Proxy ve vlastnictví OLE vrátil chybu HRESULT.  
  
## <a name="resolution"></a>Řešení  
 Prohlédněte si dokumentaci MSDN o pravidlech modelu COM.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Selže-li `QueryInterface` volání, je kontext přepnut a je znovu proveden pokus o `QueryInterface` volání, aby bylo možné zjistit, zda došlo k chybě v nesprávném kontextu.  
  
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
