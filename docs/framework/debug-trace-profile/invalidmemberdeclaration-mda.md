---
title: "invalidMemberDeclaration – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4f625cbc7d7c46eee5b2eb8d7e47d4a5754fc26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration – pomocník spravovaného ladění (MDA)
`invalidMemberDeclaration` Pomocník spravovaného ladění (MDA) je aktivováno zobrazovat chyby, ke kterému dochází při zjišťování, jak přeuspořádat parametry členem, abyste mohli volat z modelu COM.  
  
## <a name="symptoms"></a>Příznaky  
 Selhání HRESULT je vrácen do modelu COM bez spravovaného byla volání metody.  
  
## <a name="cause"></a>příčina  
 Příčinou je pravděpodobně z důvodu nekompatibilní <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut na jeden z parametrů.  
  
## <a name="resolution"></a>Rozlišení  
 Zadejte platný <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributů na parametry.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 Informační zpráva obsahujícího název člena, název typu a chybová zpráva.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
