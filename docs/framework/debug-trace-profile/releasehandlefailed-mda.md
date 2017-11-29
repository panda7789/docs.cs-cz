---
title: "releaseHandleFailed – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), handles
- release handle failed
- CriticalHandle class, run-time errors
- releaseHandleFailed MDA
- ReleaseHandle method
- SafeHandle class, run-time errors
- MDAs (managed debugging assistants), handles
ms.assetid: 44cd98ba-95e5-40a1-874d-e8e163612c51
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbd6e2a52eb576f321dfa7dda5682d325f554158
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed – pomocník spravovaného ladění (MDA)
`releaseHandleFailed` Spravovaného ladění (MDA) pomocníka je aktivován je oznámit vývojáři při <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda třídy odvozené od <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> vrátí `false`.  
  
## <a name="symptoms"></a>Příznaky  
 Nevracení prostředků nebo paměti.  Pokud <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda odvozování z třídy <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> nezdaří, pak prostředků zapouzdřené v třídě nemusí mít vydání nebo vyčistit.  
  
## <a name="cause"></a>příčina  
 Uživatelé musí poskytovat implementace <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda pokud tvoří třídy, které jsou odvozeny od <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle>; proto v případech jsou specifické pro jednotlivé prostředků. Požadavky na však jsou následující:  
  
-   <xref:System.Runtime.InteropServices.SafeHandle>a <xref:System.Runtime.InteropServices.CriticalHandle> typy představují obálky kolem důležitých proces prostředky. Nevracení paměti by nepoužitelnost proces v čase.  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Metoda nesmí nepodaří fungoval. Jakmile proces získá prostředku, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> je jediný způsob, jak ji uvolnit. Proto selhání znamená nedostatku prostředků.  
  
-   Všechny chyby, ke kterým dochází při provádění <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>zpomalovat verze prostředku, je chyby při provádění <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda sama. Je zodpovědností programátorů zajistit, že smlouva splněna, i v případě, že kód volá kód vytvořené jiným uživatelem, aby fungoval.  
  
## <a name="resolution"></a>Rozlišení  
 Kód, který používá konkrétní <xref:System.Runtime.InteropServices.SafeHandle> (nebo <xref:System.Runtime.InteropServices.CriticalHandle>) typ, který vyvolá oznámení (mda) by měl být projdete, hledání míst, kde je hodnota nezpracovaná popisovač extrahují z <xref:System.Runtime.InteropServices.SafeHandle> a zkopírovat jinde. Toto je obvyklé příčiny selhání v rámci <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> implementace, protože využití popisovač nezpracované hodnoty je pak už sledovat modulem runtime. Pokud kopírování nezpracovaná popisovač je následně zavřená, může způsobit pozdější <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> volání se nezdařila, protože dojde k pokusu o ukončení na stejné popisovač, který je neplatný.  
  
 Existuje několik způsobů, ve kterém může dojít, duplikace nesprávná obslužná rutina:  
  
-   Podívejte se na volání <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> metoda. Volání této metody by měla být mimořádně výjimečná a všechny, které můžete najít musí být uzavřena do volání <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> a <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> metody. Tyto druhé metody zadejte oblast kódu, ve kterém může popisovač nezpracovanou hodnotu bezpečně používat. Mimo tuto oblast nebo pokud počet odkazů se nikdy zvýší na prvním místě, můžete hodnotu popisovač zruší kdykoli voláním <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> nebo <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> na jiné vlákno. Jednou všechna použití <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> sleduje dolů, postupujte podle cesty nezpracovaná popisovač trvá zajistit není předáno některé součásti, která bude volat nakonec `CloseHandle` nebo jiné nízké úrovně nativní metoda, která vydá popisovač.  
  
-   Ujistěte se, že kód, který se používá k chybě při inicializaci <xref:System.Runtime.InteropServices.SafeHandle> s platný popisovač nezpracovanou hodnotu vlastní popisovač. Pokud jste formuláři <xref:System.Runtime.InteropServices.SafeHandle> kolem popisovač kódu není vlastníkem bez nastavení `ownsHandle` parametru `false` v základní konstruktoru, pak oba <xref:System.Runtime.InteropServices.SafeHandle> a vlastník skutečné popisovač můžete zkusit zavřít popisovač, což v chybu<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Pokud <xref:System.Runtime.InteropServices.SafeHandle> ztratí soupeření.  
  
-   Když <xref:System.Runtime.InteropServices.SafeHandle> je zařazené mezi doménami aplikací, zkontrolujte <xref:System.Runtime.InteropServices.SafeHandle> odvození používá byl označen jako serializovatelný. Ve výjimečných případech, kde třída odvozená z <xref:System.Runtime.InteropServices.SafeHandle> byl provedené serializable, musí implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní nebo použijte jednu z jiné postupy pro řízení serializace a deserializace proces ručně. To je nutná, protože výchozí akci serializace je vytvořit bitové závorkách popisovač nezpracované hodnoty, což vede ke dvěma <xref:System.Runtime.InteropServices.SafeHandle> instance myslím vlastní stejné popisovač. Jak se pokusí zavolat <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> na stejné popisovač v určitém okamžiku. Druhý <xref:System.Runtime.InteropServices.SafeHandle> k tomu se nezdaří. Správné během akce při serializaci <xref:System.Runtime.InteropServices.SafeHandle> je volání `DuplicateHandle` funkce nebo podobné funkce pro nativního zpracovat typ k vytvoření kopie odlišné právní popisovač. Pokud váš typ popisovače nepodporuje potom <xref:System.Runtime.InteropServices.SafeHandle> typ zabalení ji nelze provést serializable.  
  
-   Je možné sledovat, kde je již v rané fázi, zavřít popisovač vedoucí k selhání při <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nakonec zavolání metody umístěním zarážku ladicí program na nativní rutiny použijí k uvolnění popisovač, například `CloseHandle` funkce. Toto nemusí být možné scénáře přízvuk nebo i střední funkčních testů z důvodu silný provoz tyto rutiny často řešit. Může být užitečné instrumentace kód, který volá metodu nativní verzi, aby bylo možné zaznamenat identitu volajícího, nebo může být trasování úplné zásobníku a hodnota popisovač vydán.  Hodnota popisovač lze porovnat s hodnotou hlášené této (mda).  
  
-   Všimněte si, že některé typy nativní popisovač, například všechny Win32 zpracovává, se uvolní prostřednictvím `CloseHandle` fungovat, sdílejí stejný obor názvů popisovač. Chybné verzi jeden typ může způsobit problémy s jinou. Například omylem dvakrát zavřít popisovač události Win32 může vést k popisovač zjevně nesouvisejícími souboru předčasně ukončil. To se stane, když popisovač vydání a popisovač hodnota je k dispozici pro použití ke sledování jiný prostředek, potenciálně jiného typu. Pokud to se stane a je následován chybné druhá verze, může být zrušena popisovač nesouvisejícími vlákno.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva, že <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> Nepodařilo se správně uvolnit popisovač. Příklad:  
  
```  
"A SafeHandle or CriticalHandle of type 'MyBrokenSafeHandle'   
failed to properly release the handle with value 0x0000BEEF. This   
usually indicates that the handle was released incorrectly via   
another means (such as extracting the handle using DangerousGetHandle   
and closing it directly or building another SafeHandle around it."  
```  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <releaseHandleFailed/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Tady je příklad kódu, který může aktivovat `releaseHandleFailed` (mda).  
  
```  
bool ReleaseHandle()  
{  
    // Calling the Win32 CloseHandle function to release the   
    // native handle wrapped by this SafeHandle. This method returns   
    // false on failure, but should only fail if the input is invalid   
    // (which should not happen here). The method specifically must not   
    // fail simply because of lack of resources or other transient   
    // failures beyond the user’s control. That would make it unacceptable   
    // to call CloseHandle as part of the implementation of this method.  
    return CloseHandle(handle);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
