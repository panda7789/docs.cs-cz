---
title: dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 0b413521e0a2dc06c2ff0be642f080eaf541202f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216446"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
Pokud se funkce spravovaného `DllMain` uživatelského sestavení, která se volá s důvodem DLL_PROCESS_ATTACH, vrátí hodnotu FALSE, aktivuje se pomocníka spravovaného ladění `dllMainReturnsFalse` (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Funkce `DllMain` vrátila hodnotu FALSE, která značí, že nebyla správně provedena. To může způsobit neurčité problémy, protože `DllMain` funkce obvykle obsahují důležitý inicializační kód.  
  
## <a name="cause"></a>Příčina  
 Funkce `DllMain` je volána s důvodem DLL_PROCESS_ATTACH pro inicializaci knihovny DLL při načtení. Pokud vrátí hodnotu FALSE, znamená to, že inicializace knihovny DLL se nezdařila.  
  
## <a name="resolution"></a>Řešení  
 Analyzujte kód `DllMain` funkce knihovny DLL, která selhala, a Identifikujte příčinu selhání inicializace.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR. Pouze hlásí data o vrácené hodnotě pro `DllMain`.  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující, že funkce `DllMain` volaná pro DLL_PROCESS_ATTACH důvodu vrátila hodnotu FALSE. Všimněte si, že tento MDA je aktivován pouze v případě, že je implementováno `DllMain` ve spravovaném kódu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
