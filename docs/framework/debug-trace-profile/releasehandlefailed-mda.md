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
ms.openlocfilehash: 268acb01a6777315829378e6fd8c06c46d3136d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181752"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed – pomocník spravovaného ladění (MDA)
`releaseHandleFailed` Spravovaný ladicí asistent (MDA) je aktivován <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> je upozornit vývojáře, když metoda třídy odvozené z <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> vrátí `false`.  
  
## <a name="symptoms"></a>Příznaky  
 Nevracení prostředků nebo paměti.  Pokud <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda třídy pocházející z <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> se nezdaří, pak prostředek zapouzdřený třídou pravděpodobně nebyly uvolněny nebo vyčištěny.  
  
## <a name="cause"></a>Příčina  
 Uživatelé musí poskytnout <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementaci metody, pokud vytvářejí <xref:System.Runtime.InteropServices.SafeHandle> <xref:System.Runtime.InteropServices.CriticalHandle>třídy, které jsou odvozeny od nebo ; okolnosti jsou tedy specifické pro jednotlivé zdroje. Požadavky jsou však následující:  
  
- <xref:System.Runtime.InteropServices.SafeHandle>a <xref:System.Runtime.InteropServices.CriticalHandle> typy představují obálky kolem životně důležitých procesních zdrojů. Nevracení paměti by proces nepoužitelný v průběhu času.  
  
- Metoda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nesmí selhat při plnění své funkce. Jakmile proces získá takový prostředek, je jediný způsob, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> jak jej uvolnit. Proto selhání znamená nevracení prostředků.  
  
- Jakékoli selhání, ke kterému <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>dojde během provádění , brání uvolnění prostředku, je chyba <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> v implementaci samotné metody. Je odpovědností programátora zajistit, aby smlouva byla splněna, a to i v případě, že kód volá kód, který vytvořil někdo jiný k plnění své funkce.  
  
## <a name="resolution"></a>Řešení  
 Kód, který používá <xref:System.Runtime.InteropServices.SafeHandle> konkrétní <xref:System.Runtime.InteropServices.CriticalHandle>(nebo ) typ, který vyvolal oznámení MDA by měly být přezkoumány, hledání míst, kde je extrahována hodnota nezpracovaného popisovače z <xref:System.Runtime.InteropServices.SafeHandle> a zkopírovány jinde. Toto je obvyklá příčina selhání v rámci <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> implementace, protože použití hodnoty nezpracovaného popisovače je pak již sledována za běhu. Pokud je kopie nezpracovaného popisovače následně <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> uzavřena, může způsobit selhání pozdějšího volání, protože se pokusí o zavření na stejném popisovači, který je nyní neplatný.  
  
 Existuje několik způsobů, jak může dojít k nesprávné mušle duplikace:  
  
- Vyhledejte volání <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> metody. Volání této metody by měla být mimořádně vzácné a všechny, které <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> najdete by měl být obklopen volání a <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> metody. Tyto druhé metody určují oblast kódu, ve kterém lze bezpečně použít hodnotu nezpracovaného popisovače. Mimo tuto oblast nebo pokud počet odkazů není nikdy zvýšil na prvním místě, hodnota popisovače může být <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> kdykoli zneplatněna volánínebo na jiné vlákno. Po všechna <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> použití byly sledovány, měli byste sledovat cestu nezpracovaná popisovač trvá zajistit, že `CloseHandle` není předán a některé součásti, která bude nakonec volat nebo jiné nižší úrovně nativní metoda, která uvolní popisovač.  
  
- Ujistěte se, že kód, který <xref:System.Runtime.InteropServices.SafeHandle> se používá k inicializaci s platnou hodnotu nezpracovaného popisovače vlastní popisovač. Pokud vytvoříte <xref:System.Runtime.InteropServices.SafeHandle> kolem popisovač váš kód nevlastní `ownsHandle` bez `false` nastavení parametru v základní <xref:System.Runtime.InteropServices.SafeHandle> konstruktoru, pak i skutečný vlastník popisovače <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> můžete <xref:System.Runtime.InteropServices.SafeHandle> pokusit zavřít popisovač, což vede k chybě v případě, že ztratí závod.  
  
- Pokud <xref:System.Runtime.InteropServices.SafeHandle> je a zařazen mezi aplikační <xref:System.Runtime.InteropServices.SafeHandle> domény, potvrďte, že použitá odvozenina byla označena jako serializovatelná. Ve výjimečných případech, kdy <xref:System.Runtime.InteropServices.SafeHandle> byla třída odvozená z byla provedena <xref:System.Runtime.Serialization.ISerializable> serializovatelné, by měla implementovat rozhraní nebo použít jeden z dalších technik pro řízení serializace a deserializace procesu ručně. To je nutné, protože výchozí serializace akce je vytvořit bitový klon uzavřené hodnoty <xref:System.Runtime.InteropServices.SafeHandle> popisovače raw, výsledkem je dvě instance, které si myslí, že vlastní stejný popisovač. Oba se pokusí <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> volat na stejný popisovač v určitém okamžiku. Druhý <xref:System.Runtime.InteropServices.SafeHandle> k tomu se nezdaří. Správný postup při serializaci <xref:System.Runtime.InteropServices.SafeHandle> a je `DuplicateHandle` volání funkce nebo podobné funkce pro nativní typ popisovače, aby se vytvořila samostatná kopie právního popisovače. Pokud typ popisovače nepodporuje <xref:System.Runtime.InteropServices.SafeHandle> toto pak typ obtékání nelze serializovat.  
  
- Může být možné sledovat, kde je popisovač právě uzavřen <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> brzy, což vede k selhání při volání metody, umístěním ladicího programu `CloseHandle` zarážky na nativní rutiny slouží k uvolnění popisovače, například funkce. To nemusí být možné pro stresové scénáře nebo dokonce středně velké funkční testy kvůli hustému provozu, se kterým se tyto rutiny často zabývají. Může pomoci instrumentovat kód, který volá metodu nativní verze, aby bylo možné zachytit identitu volajícího nebo případně trasování celého zásobníku a hodnotu uvolněného popisovače.  Hodnotu popisovače lze porovnat s hodnotou hlášenou tímto MDA.  
  
- Všimněte si, že některé nativní typy popisovačů, jako `CloseHandle` jsou všechny popisovače Win32, které lze uvolnit prostřednictvím funkce, sdílejí stejný obor názvů popisovače. Chybné uvolnění jednoho typu popisovače může způsobit problémy s jiným. Například náhodné zavření popisovače události Win32 dvakrát může vést k zdánlivě nesouvisející popisovač souboru předčasně uzavřen. K tomu dochází, když je uvolněna popisovač a hodnota popisovače bude k dispozici pro použití ke sledování jiného prostředku, potenciálně jiného typu. Pokud k tomu dojde a následuje chybné druhé vydání, popisovač nesouvisející vlákno může být zrušena.  
  
## <a name="effect-on-the-runtime"></a>Vliv na běhový čas  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující, že popisovač <xref:System.Runtime.InteropServices.SafeHandle> nebo nepodařilo <xref:System.Runtime.InteropServices.CriticalHandle> se správně uvolnit. Například:  
  
```output
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
 Následuje příklad kódu, který může `releaseHandleFailed` aktivovat MDA.  
  
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

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
