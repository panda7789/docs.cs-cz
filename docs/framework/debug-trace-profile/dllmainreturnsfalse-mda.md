---
title: dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
description: Přečtěte si o Pomocníkovi spravovaném ladění dllMainReturnsFalse – v .NET. Tato knihovna MDA je aktivována, pokud selhala inicializace knihovny DLL.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 21d5e37d6823876e07cf5b2cbb881c1cf8b47b11
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416054"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
`dllMainReturnsFalse`Pomocník spravovaného ladění (MDA) je aktivován, pokud je spravovaná `DllMain` funkce uživatelského sestavení volána s důvodem DLL_PROCESS_ATTACH, vrátí hodnotu false.  
  
## <a name="symptoms"></a>Příznaky  
 `DllMain`Funkce vrátila hodnotu false, což značí, že nebyla správně provedena. To může způsobit neurčité problémy `DllMain` , protože funkce obvykle obsahují důležitý inicializační kód.  
  
## <a name="cause"></a>Příčina  
 `DllMain`Funkce je volána s důvodem DLL_PROCESS_ATTACH pro inicializaci knihovny DLL při načtení. Pokud vrátí hodnotu FALSE, znamená to, že inicializace knihovny DLL se nezdařila.  
  
## <a name="resolution"></a>Řešení  
 Analyzujte kód `DllMain` funkce neúspěšné knihovny DLL a Identifikujte příčinu selhání inicializace.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR. Pouze hlásí data o vrácené hodnotě `DllMain` .  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující, že `DllMain` funkce, která je volána z důvodu DLL_PROCESS_ATTACH, vrátila hodnotu false. Všimněte si, že tato aplikace MDA je aktivována pouze `DllMain` v případě, že je implementována ve spravovaném kódu.  
  
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
