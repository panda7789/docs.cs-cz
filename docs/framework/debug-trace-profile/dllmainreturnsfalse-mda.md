---
title: dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
author: mairaw
ms.author: mairaw
ms.openlocfilehash: adc05ae9bd357c142ff09de069aff446b5ea60e8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052860"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
Pokud spravovaná`DllMain` funkce uživatelského sestavení, která je volána s důvodem DLL_PROCESS_ATTACH, vrátí hodnotu false, je aktivován pomocník spravovanéholadění(MDA).`dllMainReturnsFalse`  
  
## <a name="symptoms"></a>Příznaky  
 `DllMain` Funkce vrátila hodnotu false, což značí, že nebyla správně provedena. To může způsobit neurčité problémy, `DllMain` protože funkce obvykle obsahují důležitý inicializační kód.  
  
## <a name="cause"></a>příčina  
 `DllMain` Funkce je volána s důvodem DLL_PROCESS_ATTACH pro inicializaci knihovny DLL při načtení. Pokud vrátí hodnotu FALSE, znamená to, že inicializace knihovny DLL se nezdařila.  
  
## <a name="resolution"></a>Řešení  
 Analyzujte kód `DllMain` funkce neúspěšné knihovny DLL a Identifikujte příčinu selhání inicializace.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR. Pouze hlásí data o vrácené hodnotě `DllMain`.  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující, že `DllMain` funkce volaná z důvodu DLL_PROCESS_ATTACH vrátila hodnotu false. Všimněte si, že tato aplikace MDA je `DllMain` aktivována pouze v případě, že je implementována ve spravovaném kódu.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
