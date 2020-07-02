---
title: releaseHandleFailed – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění releaseHandleFailed (MDA), který může být aktivovaný z důvodu nevracení prostředků nebo paměti v rozhraní .NET.
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
ms.openlocfilehash: 167a304b4571aa35f758a2054caf6ae1c60a3c60
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803635"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed – pomocník spravovaného ladění (MDA)
`releaseHandleFailed`Je aktivován pomocník spravovaného ladění (MDA), který vývojářům oznamuje, když <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Metoda třídy odvozená <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> vrátí `false` .  
  
## <a name="symptoms"></a>Příznaky  
 Nevracení prostředků nebo paměti.  Pokud <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Metoda třídy odvozená z <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> dojde k chybě, pak prostředek zapouzdřený třídou nemusí být vydaný nebo vyčištěný.  
  
## <a name="cause"></a>Příčina  
 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>Pokud uživatelé vytvoří třídy, které jsou odvozeny z nebo;, musí poskytnout implementaci metody <xref:System.Runtime.InteropServices.SafeHandle> <xref:System.Runtime.InteropServices.CriticalHandle> . tyto podmínky jsou proto specifické pro jednotlivé prostředky. Požadavky jsou však následující:  
  
- <xref:System.Runtime.InteropServices.SafeHandle>a <xref:System.Runtime.InteropServices.CriticalHandle> typy reprezentují obálky pro důležité prostředky procesu. Nevracení paměti by vedlo k tomu, že proces nebude v průběhu času použitelný.  
  
- <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>Metoda nesmí selhat při provádění funkce. Jakmile proces získá takový prostředek, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> je jediným způsobem, jak ho uvolnit. Proto selhání implikuje nevracení prostředků.  
  
- Jakákoli chyba, ke které dojde během provádění <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> , je překážkou vydání prostředku, je chyba v implementaci <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> samotné metody. Je odpovědností programátora zajistit, aby smlouva byla splněna, a to i v případě, že tento kód volá kód vytvořený někým jiným, aby mohl provést jeho funkci.  
  
## <a name="resolution"></a>Řešení  
 Kód, který používá konkrétní <xref:System.Runtime.InteropServices.SafeHandle> typ (nebo <xref:System.Runtime.InteropServices.CriticalHandle> ), který vyvolal oznámení MDA, by měl být zkontrolován a hledat místa, kde je hodnota nezpracovaného popisovače extrahována z <xref:System.Runtime.InteropServices.SafeHandle> a zkopírována jinde. Toto je Obvyklá příčina selhání v rámci <xref:System.Runtime.InteropServices.SafeHandle> nebo <xref:System.Runtime.InteropServices.CriticalHandle> implementace, protože použití nezpracovaného popisovače je již nesledováno modulem runtime. Pokud je kopie nezpracovaného popisovače následně zavřena, může způsobit selhání pozdějšího <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> volání, protože došlo k pokusu o ukončení u stejného popisovače, který je nyní neplatný.  
  
 Existuje několik způsobů, jak se může vyskytnout nesprávné duplikace popisovače:  
  
- Vyhledejte volání <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> metody. Volání této metody by mělo být více než zřídka vzácné a všechny nalezené by měly být uzavřeny voláním <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> metody a. Tyto metody určují oblast kódu, ve které je možné bezpečně použít hodnotu nezpracovaného popisovače. Mimo tuto oblast, nebo pokud se počet odkazů nikdy nezvyšuje na prvním místě, může být hodnota popisovače na základě volání <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> nebo <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> do jiného vlákna zrušena kdykoli. Jakmile budou všechna použití <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> sledována, měli byste postupovat podle cesty, kterou nezpracovaný popisovač trvá, aby nedošlo k předání do některé součásti, která bude nakonec volat `CloseHandle` nebo jiné nativní metody nízké úrovně, která uvolní popisovač.  
  
- Zajistěte, aby popisovač používal kód, který se používá k inicializaci <xref:System.Runtime.InteropServices.SafeHandle> s platnou hodnotou nezpracovaného popisovače. Vytvoříte-li <xref:System.Runtime.InteropServices.SafeHandle> kolem popisovače, váš kód nevlastní bez nastavení `ownsHandle` parametru `false` v základním konstruktoru, pak se <xref:System.Runtime.InteropServices.SafeHandle> může pokusit o uzavření popisovače a vlastník reálného popisovače, což vede k chybě v <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> případě, že <xref:System.Runtime.InteropServices.SafeHandle> ztratí rasy.  
  
- Pokud <xref:System.Runtime.InteropServices.SafeHandle> je zařazování mezi doménami aplikace, potvrďte, že <xref:System.Runtime.InteropServices.SafeHandle> odvozená odvozená byla označena jako serializovatelný. Ve výjimečných případech, kdy byla Třída odvozena z <xref:System.Runtime.InteropServices.SafeHandle> byla provedena serializovatelný, by měla implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní nebo použít jednu z dalších technik pro řízení serializace a deserializace procesu ručně. To je nutné, protože výchozí akce serializace je vytvoření bitové kopie hodnoty uzavřeného nezpracovaného popisovače, což vede k tomu, že dvě <xref:System.Runtime.InteropServices.SafeHandle> instance mají za následek stejný popisovač. Oba se v <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> určitém bodě pokusí zavolat na stejný popisovač. Druhý <xref:System.Runtime.InteropServices.SafeHandle> postup se nezdaří. Správný postup při serializaci <xref:System.Runtime.InteropServices.SafeHandle> je zavolat `DuplicateHandle` funkci nebo podobnou funkci pro váš typ nativního popisovače, aby bylo možné vytvořit odlišnou kopii zákonného popisovače. Pokud typ popisovače tuto podporu nepodporuje, <xref:System.Runtime.InteropServices.SafeHandle> nelze zabalení typu provést serializovatelný.  
  
- Je možné sledovat, kde je popisovač uzavřený včas, což vede k selhání při <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> konečném volání metody, vložením zarážky ladicího programu na nativní rutinu, která se používá k uvolnění popisovače, například `CloseHandle` funkce. To nemusí být možné v případě zátěžových scénářů nebo dokonce středně velkých funkčních testů z důvodu těžkého provozu, na který tyto rutiny často řeší. Může vám pomáhat při instrumentaci kódu, který volá nativní metodu vydání, za účelem zachycení identity volajícího nebo pravděpodobně úplného trasování zásobníku a hodnoty vydávaného popisovače.  Hodnota popisovače může být porovnána s hodnotou hlášenou v rámci této aplikace MDA.  
  
- Všimněte si, že některé typy nativních popisovačů, jako jsou všechny popisovače Win32, které mohou být vydány prostřednictvím `CloseHandle` funkce, sdílejí stejný obor názvů obslužné rutiny. Chybné vydání jednoho typu popisovače může způsobit problémy s jiným. Například náhodné ukončení zpracování událostí Win32 dvakrát může vést k předčasnému zavření nesouvisejícího popisovače souboru. K tomu dojde, když je ovladač uvolněn a hodnota popisovače bude k dispozici pro sledování jiného prostředku, potenciálně jiného typu. Pokud k tomu dojde a následuje chybnou druhou verzí, může být neověřen popisovač nesouvisejícího vlákna.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující, že <xref:System.Runtime.InteropServices.SafeHandle> <xref:System.Runtime.InteropServices.CriticalHandle> popisovač nebo se nepodařilo správně uvolnit. Příklad:  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
