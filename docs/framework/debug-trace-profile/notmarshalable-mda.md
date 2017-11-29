---
title: "notMarshalable – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5de75130acab30c4f73522728c00b69c1c3e8d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="notmarshalable-mda"></a>notMarshalable – pomocník spravovaného ladění (MDA)
`notMarshalable` Pomocník spravovaného ladění (MDA) se aktivuje, když se modul CLR (CLR) setká ukazatele rozhraní modelu COM bez platné registrované proxy nebo zástupnou proceduru nebo nesprávné `IMarshal` implementace při pokusu o rozhraní zařazování rozhraní mezi kontexty.  
  
## <a name="symptoms"></a>Příznaky  
 Nejsou servis volání nebo volání, ke kterým došlo v nesprávný kontext ukazatele rozhraní COM.  
  
## <a name="cause"></a>příčina  
 Žádný platný registrované proxy/stub nebo nesprávné `IMarshal` při pokusu o zařazování rozhraní mezi kontexty.  
  
## <a name="resolution"></a>Rozlišení  
 Zajistěte, aby byla proxy se zakázaným inzerováním zaregistrován a zda `IMarshal` implementace je platný.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu runtime.  
  
## <a name="output"></a>Výstup  
 Zpráva s popisem problému.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
