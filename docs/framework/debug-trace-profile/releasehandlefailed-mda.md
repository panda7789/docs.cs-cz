---
title: releaseHandleFailed – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), handles
- release handle failed
- CriticalHandle class, run-time errors
- releaseHandleFailed MDA
- ReleaseHandle method
- SafeHandle class, run-time errors
- MDAs (managed debugging assistants), handles
ms.assetid: 44cd98ba-95e5-40a1-874d-e8e163612c51
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 155cf7138d4074467195bdc1302e28c0789f93cf
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151002"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed – pomocník spravovaného ladění (MDA)
`releaseHandleFailed` Spravovaného ladění (MDA) pomocníka s nastavením je aktivován je upozornit vývojáře při <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metodě třídy odvozené z <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> vrátí `false`.  
  
## <a name="symptoms"></a>Příznaky  
 Nevracení prostředku nebo paměti.  Pokud <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda třídy odvozené od <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> nezdaří, pak prostředků zapouzdřena objektem třídy nemusí mít vydání nebo vyčistit.  
  
## <a name="cause"></a>příčina  
 Uživatelé musí zadat provádění <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metodu, pokud uživatel vytvořit třídy, které jsou odvozeny z <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle>; proto okolnosti, které jsou specifické pro jednotlivé prostředky. Požadavky jsou však následujícím způsobem:  
  
-   <xref:System.Runtime.InteropServices.SafeHandle> a <xref:System.Runtime.InteropServices.CriticalHandle> typy představují obálky prostředky důležité procesu. Nevracení paměti by mohlo způsobit nepoužitelnost procesu mraku v čase.  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Metoda nesmí selhat a provést jeho funkci. Po procesu získá prostředek, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> je jediný způsob, jak ji. Proto znamená selhání nedostatku prostředků.  
  
-   Jakékoli neúspěchy, ke kterým došlo během provádění <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>Včerejší verze prostředku, je chyba v implementaci <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda sama. Je odpovědností programátorovi, aby zajistěte, aby byl kontrakt, i v případě, že kód volá kód vytvořené někým jiným, aby fungoval.  
  
## <a name="resolution"></a>Rozlišení  
 Kód, který používá konkrétní <xref:System.Runtime.InteropServices.SafeHandle> (nebo <xref:System.Runtime.InteropServices.CriticalHandle>) typ, který vyvolá oznámení MDA byste měli zkontrolovat, hledá místa, kde je hodnota nezpracovanou popisovače extrahují z <xref:System.Runtime.InteropServices.SafeHandle> a zkopírovat jinde. Toto je obvyklou příčinou selhání v rámci <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> implementace, protože využití hodnota nezpracovanou popisovače je potom už sledován pomocí funkce modulu runtime. Kopírování nezpracovaná popisovač je následně zavřená, může způsobit pozdější <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> volání se nezdařila, protože dojde k pokusu o uzavření na stejné popisovač, který je nyní neplatný.  
  
 Existuje mnoho způsobů, ve kterém může dojít, duplikace nesprávné popisovač:  
  
-   Podívejte se na volání <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> metody. Volání této metody by měla být mimořádně vzácné a všechny, které můžete najít by měl být uzavřen v volání <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> a <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> metody. Tyto metody druhá možnost zadat tuto oblast kódu, ve kterém může hodnota nezpracovanou popisovače bezpečně používat. Mimo oblast nebo pokud na prvním místě je nikdy zvýšen počet odkazů, hodnota popisovače lze zrušit platnost v okamžiku volání <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> nebo <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> v jiném vlákně. Jakmile všechna použití <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> sleduje snižování kapacity, měli byste postupovat podle cesty nezpracovaná popisovač potřebný k zajištění není předávána některé komponenty, který bude nakonec zavolat `CloseHandle` nebo jiné nízké úrovně nativní metodu, která bude uvolnit popisovač.  
  
-   Ujistěte se, že kód, který slouží k inicializaci <xref:System.Runtime.InteropServices.SafeHandle> s platný popisovač nezpracovanou hodnotu vlastní popisovač. Pokud při vytváření <xref:System.Runtime.InteropServices.SafeHandle> kolem popisovač kódu není vlastníkem bez nastavení `ownsHandle` parametr `false` v konstruktor základní třídy a pak i <xref:System.Runtime.InteropServices.SafeHandle> a vlastník skutečné popisovač Zkuste zavřít popisovač, což vede k chybě v <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Pokud <xref:System.Runtime.InteropServices.SafeHandle> ztratí závodu.  
  
-   Když <xref:System.Runtime.InteropServices.SafeHandle> je zařadit mezi doménami aplikace, zkontrolujte <xref:System.Runtime.InteropServices.SafeHandle> odvození používá byl označen jako serializovatelný. Ve výjimečných případech, kde třída odvozená z <xref:System.Runtime.InteropServices.SafeHandle> byl proveden serializovatelný, by měly implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní nebo použijte některý z jiné techniky pro řízení serializace a deserializace procesu ručně. To je nutná, protože výchozí akci serializace je schopna vytvářet klony bitové hodnoty uzavřené nezpracovaná popisovač, výsledkem jsou dvě <xref:System.Runtime.InteropServices.SafeHandle> uvažujete vlastní stejné popisovač instance. Obojí se pokusí zavolat <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> na stejné popisovač v určitém okamžiku. Druhá <xref:System.Runtime.InteropServices.SafeHandle> k tomu se nezdaří. Správný kurz akce serializace <xref:System.Runtime.InteropServices.SafeHandle> je zavolat `DuplicateHandle` funkce nebo podobnou funkci pro vaše nativní zpracovat typ vytvořit kopii odlišné platný popisovač. Pokud to vaše – typ obslužné rutiny nepodporuje pak bude <xref:System.Runtime.InteropServices.SafeHandle> typ závěrečné nelze nastavit jako serializovatelný.  
  
-   Je možné sledovat, kde popisovač se zavírá již v rané fázi, což vede k selhání při <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda nakonec je volána, umístěním zarážky ladicího programu na nativní rutiny použijí k uvolnění popisovače, například `CloseHandle` funkce. To nemusí být možné v situacích zátěže nebo dokonce střední funkční testy kvůli velkému provozu těchto rutin často řešit. To může pomoct s instrumentací kódu, který volá metodu nativní verzi, aby bylo možné zaznamenat identitu volajícího a případně úplné trasování zásobníku a hodnota popisovač se vydávají.  Hodnota popisovače můžete porovnat s hodnotou hlášených toto MDA.  
  
-   Všimněte si, že některé typy nativní popisovač, jako je například rozhraní Win32 zpracovává, které mohou být vydány prostřednictvím `CloseHandle` funkce, které sdílejí stejný obor názvů popisovač. Chybná verze jednoho popisovače typu může způsobit problémy s jiným. Například neúmyslně zavření popisovač události Win32 dvakrát může vést k popisovač souboru zdánlivě nezávislých předčasně zavřená. To se stane, když se uvolní popisovač a hodnota popisovače je k dispozici pro použití ke sledování jiný prostředek, potenciálně jiného typu. Pokud to se stane a je následována chybné druhé vydání, popisovač nesouvisejících vlákno může zneplatněny.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva, že <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> nezdařilo správně uvolnit popisovač. Příklad:  
  
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
 Tady je příklad kódu, který můžete aktivovat `releaseHandleFailed` MDA.  
  
```csharp
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
