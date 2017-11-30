---
title: "dllMainReturnsFalse – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91d2dfefc8de49770ec5c0b0083767bbb4b76c0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
`dllMainReturnsFalse` Pomocník spravovaného ladění (MDA) se aktivuje, pokud spravovaný `DllMain` funkce uživatelského sestavení, volána s důvod DLL_PROCESS_ATTACH, vrátí hodnotu FALSE.  
  
## <a name="symptoms"></a>Příznaky  
 `DllMain` Funkce vrátila hodnotu FALSE, která udává, že ho neproběhlo správně. Protože to může způsobit problémy s neurčená `DllMain` funkce obvykle obsahují důležité inicializace kódu.  
  
## <a name="cause"></a>příčina  
 `DllMain` Funkce je volána s důvod DLL_PROCESS_ATTACH inicializace knihovny DLL při zatížení. Pokud vrátí hodnotu FALSE, znamená to, že DLL inicializace se nezdařila.  
  
## <a name="resolution"></a>Rozlišení  
 Analýza kódu `DllMain` funkce selhání knihovny DLL a určete příčinu selhání inicializace.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR. Pouze sestavy data o návratovou hodnotu pro `DllMain`.  
  
## <a name="output"></a>Výstup  
 Zpráva, že `DllMain` volaná z důvodu DLL_PROCESS_ATTACH, funkce vrátí hodnotu FALSE. Všimněte si, že je tento MDA aktivovat pouze v případě, `DllMain` se implementují ve spravovaném kódu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
