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
ms.openlocfilehash: 265344cb100a41cde5443cd0914dc66271aabf93
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216109"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed – pomocník spravovaného ladění (MDA)
Je aktivován Pomocník s `releaseHandleFailed` spravovaného ladění (MDA), který oznamuje vývojářům, když metoda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> třídy odvozené z <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> vrátí `false`.  
  
## <a name="symptoms"></a>Příznaky  
 Nevracení prostředků nebo paměti.  Pokud metoda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> třídy odvozené z <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> se nezdařila, pak prostředek zapouzdřený třídou pravděpodobně nebyl vydán nebo vyčištěn.  
  
## <a name="cause"></a>Příčina  
 Pokud uživatelé vytvoří třídy, které jsou odvozeny z <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle>, musí zadat implementaci metody <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>. Proto jsou okolnosti specifické pro jednotlivé prostředky. Požadavky jsou však následující:  
  
- typy <xref:System.Runtime.InteropServices.SafeHandle> a <xref:System.Runtime.InteropServices.CriticalHandle> reprezentují obálky pro důležité prostředky procesu. Nevracení paměti by vedlo k tomu, že proces nebude v průběhu času použitelný.  
  
- Metoda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nesmí selhat při provádění funkce. Jakmile proces získá takový prostředek, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> je jediným způsobem, jak ho uvolnit. Proto selhání implikuje nevracení prostředků.  
  
- Jakákoli chyba, ke které dojde během provádění <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, brání vydání prostředku, je chyba v implementaci samotné metody <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>. Je odpovědností programátora zajistit, aby smlouva byla splněna, a to i v případě, že tento kód volá kód vytvořený někým jiným, aby mohl provést jeho funkci.  
  
## <a name="resolution"></a>Řešení  
 Kód, který používá určitý typ <xref:System.Runtime.InteropServices.SafeHandle> (nebo <xref:System.Runtime.InteropServices.CriticalHandle>), který vyvolal oznámení MDA, by měl být zkontrolován a hledat místa, kde je hodnota nezpracovaného popisovače extrahována z <xref:System.Runtime.InteropServices.SafeHandle> a zkopírována jinde. Jedná se o obvyklou příčinu selhání v rámci implementace <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle>, protože použití nezpracované hodnoty popisovače již není sledováno modulem runtime. Pokud je kopie nezpracovaného popisovače následně zavřena, může dojít k selhání pozdějšího <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> volání, protože došlo k pokusu o zavření u stejného popisovače, který je nyní neplatný.  
  
 Existuje několik způsobů, jak se může vyskytnout nesprávné duplikace popisovače:  
  
- Vyhledejte volání metody <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A>. Volání této metody by mělo být více než zřídka vzácné a všechny nalezené by měly být obklopeny voláními <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> a <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>ch metod. Tyto metody určují oblast kódu, ve které je možné bezpečně použít hodnotu nezpracovaného popisovače. Mimo tuto oblast, nebo pokud počet odkazů nikdy není zvýšen na první místo, může být hodnota popisovače na základě volání <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> nebo <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> v jiném vlákně zrušena. Jakmile budou všechna použití <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> sledována, měli byste postupovat podle cesty, kterou nezpracovaný popisovač trvá, aby nedošlo k předání do některé součásti, která nakonec zavolá `CloseHandle` nebo jinou nativní metodu nižší úrovně, která uvolní popisovač.  
  
- Zajistěte, aby byl popisovač použit v kódu, který se používá k inicializaci <xref:System.Runtime.InteropServices.SafeHandle> s platnou hodnotou nezpracovaného popisovače. Pokud vytváříte <xref:System.Runtime.InteropServices.SafeHandle> kolem typu, který váš kód nevlastní bez nastavení parametru `ownsHandle` na `false` v základním konstruktoru, pak se může pokusit zavřít <xref:System.Runtime.InteropServices.SafeHandle> i vlastník reálného popisovače, což vede k chybě v <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, pokud <xref:System.Runtime.InteropServices.SafeHandle> ztratí rasy.  
  
- Pokud je <xref:System.Runtime.InteropServices.SafeHandle> zařazování mezi doménami aplikace, potvrďte, že používané odvození <xref:System.Runtime.InteropServices.SafeHandle> bylo označeno jako serializovatelný. Ve výjimečných případech, kdy byla Třída odvozena z <xref:System.Runtime.InteropServices.SafeHandle> provedena serializovatelný, by měla implementovat rozhraní <xref:System.Runtime.Serialization.ISerializable> nebo použít jednu z jiných metod pro řízení serializace a deserializace procesu ručně. To je nutné, protože výchozí akce serializace je vytvoření bitové kopie hodnoty uzavřeného nezpracovaného popisovače, což vede k tomu, že dvě instance <xref:System.Runtime.InteropServices.SafeHandle> mají na sebe stejný popisovač. Oba se pokusí volat <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> u stejného popisovače v určitém bodě. Druhý <xref:System.Runtime.InteropServices.SafeHandle> k tomuto účelu selže. Správná akce při serializaci <xref:System.Runtime.InteropServices.SafeHandle> je zavolat funkci `DuplicateHandle` nebo podobnou funkci pro váš typ nativního popisovače, aby bylo možné vytvořit odlišnou kopii zákonného popisovače. Pokud typ popisovače tuto podporu nepodporuje, <xref:System.Runtime.InteropServices.SafeHandle> typ obtékání nelze vytvořit serializovatelný.  
  
- Je možné sledovat, kde je popisovač uzavřený v rané fázi, což vede k selhání při konečném volání metody <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> tak, že umístíte zarážku ladicího programu na nativní rutinu, která se používá k uvolnění popisovače, například funkce `CloseHandle`. To nemusí být možné v případě zátěžových scénářů nebo dokonce středně velkých funkčních testů z důvodu těžkého provozu, na který tyto rutiny často řeší. Může vám pomáhat při instrumentaci kódu, který volá nativní metodu vydání, za účelem zachycení identity volajícího nebo pravděpodobně úplného trasování zásobníku a hodnoty vydávaného popisovače.  Hodnota popisovače může být porovnána s hodnotou hlášenou v rámci této aplikace MDA.  
  
- Všimněte si, že některé typy nativních popisovačů, jako jsou všechny popisovače Win32, které mohou být vydány prostřednictvím funkce `CloseHandle`, sdílejí stejný obor názvů popisovače. Chybné vydání jednoho typu popisovače může způsobit problémy s jiným. Například náhodné ukončení zpracování událostí Win32 dvakrát může vést k předčasnému zavření nesouvisejícího popisovače souboru. K tomu dojde, když je ovladač uvolněn a hodnota popisovače bude k dispozici pro sledování jiného prostředku, potenciálně jiného typu. Pokud k tomu dojde a následuje chybnou druhou verzí, může být neověřen popisovač nesouvisejícího vlákna.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující, že <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> se nepodařilo správně uvolnit popisovač. Například:  
  
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
 Následuje příklad kódu, který může aktivovat `releaseHandleFailed` MDA.  
  
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
