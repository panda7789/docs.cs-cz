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
ms.openlocfilehash: 7ca7d98dba7f66aee96d0f2059086c442df17f5b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660457"
---
# <a name="failedqi-mda"></a>failedQI – pomocník spravovaného ladění (MDA)
`failedQI` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul runtime volá `QueryInterface` na ukazatele rozhraní modelu COM jménem obálka volatelná aplikacemi běhu (RCW) a `QueryInterface` volání selže.  
  
## <a name="symptoms"></a>Příznaky  
 Přetypování na obálky RCW selže nebo volání COM z obálky RCW dojde k neočekávanému selhání.  
  
## <a name="cause"></a>Příčina  
  
- Při volání z nesprávného kontextu.  
  
- Registrovaný server proxy se nedaří `QueryInterface` volat, protože došlo k pokusu o volání v chybném kontextu.  
  
- Proxy služby vlastnictví OLE vrátí selhání hodnoty HRESULT.  
  
## <a name="resolution"></a>Řešení  
 Pravidla modelu COM naleznete v dokumentaci MSDN.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Pokud `QueryInterface` volání selže, kontext se přepnul a `QueryInterface` volání se opakovat pokus o zobrazíte, pokud byl nesprávný kontextu 2!s!(0x%3!s!).  
  
## <a name="output"></a>Výstup  
 Název spravovaného rozhraní, GUID rozhraní a hodnota HRESULT chyby.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
