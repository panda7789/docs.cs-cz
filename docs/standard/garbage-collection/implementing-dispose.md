---
title: Implementace metody Dispose
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
ms.openlocfilehash: f3d3269ccf56954f963762503d2bc1c53b9e6b83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78238985"
---
# <a name="implementing-a-dispose-method"></a>Implementace metody Dispose

Implementovat <xref:System.IDisposable.Dispose%2A> metodu k uvolnění nespravovaných prostředků používaných vaší aplikací. Systém uvolňování paměti .NET nepřiděluje nebo neuvolňuje nespravovanou paměť.  
  
Vzorek pro likvidaci objektu, označovaný jako [dispose vzor](implementing-dispose.md), ukládá pořadí na životnost objektu. Vzor Dispose se používá pouze pro objekty, které mají přístup k nespravovaným prostředkům, jako jsou popisovače souboru a popisovače kanálu, popisovače registru, popisovače čekání nebo ukazatele na blok nespravované paměti. Důvodem je skutečnost, že systém uvolňování paměti je velmi efektivní při zpětném získávání nepoužitých spravovaných objektů, nedokáže však získat zpět nespravované objekty.  
  
Vzor Dispose má dvě varianty:  
  
- Zalomit každý nespravovaný prostředek, který typ používá v bezpečném popisovači (to znamená ve třídě odvozené z <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>). V tomto případě implementovat <xref:System.IDisposable> rozhraní `Dispose(Boolean)` a další metodu. Toto je doporučená varianta a <xref:System.Object.Finalize%2A?displayProperty=nameWithType> nevyžaduje přepsání metody.  
  
  > [!NOTE]
  > Obor <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> názvů poskytuje sadu tříd odvozených z <xref:System.Runtime.InteropServices.SafeHandle>, které jsou uvedeny v části Using safe [handles](#SafeHandles) . Pokud nemůžete najít třídu, která je vhodná pro uvolnění nespravovaného prostředku, můžete implementovat vlastní podtřídu aplikace <xref:System.Runtime.InteropServices.SafeHandle>.  
  
- Implementovat <xref:System.IDisposable> rozhraní a `Dispose(Boolean)` další metodu a také <xref:System.Object.Finalize%2A?displayProperty=nameWithType> přepsat metodu. Je nutné <xref:System.Object.Finalize%2A> přepsat zajistit, že nespravované prostředky <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> jsou uvolněny, pokud vaše implementace není volána příjemce vašeho typu. Pokud použijete doporučenou techniku popsané <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> v předchozí odrážce, třída to provádí vaším jménem.  
  
Chcete-li zajistit, že prostředky jsou <xref:System.IDisposable.Dispose%2A> vždy vyčistit odpovídajícím způsobem, metoda by měla být volatelné vícekrát bez vyvolání výjimky.  
  
Příklad kódu k dispozici <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> pro metodu ukazuje, jak uvolňování paměti může způsobit finalizační metodu ke spuštění, zatímco nespravovaný odkaz na objekt nebo jeho členy je stále používán. Může mít smysl <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> využít k tomu, aby objekt nebyl způsobilý pro uvolňování paměti od začátku aktuální rutiny do bodu, kde je tato metoda volána.
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Dispose() a Dispose(Boolean)  

Rozhraní <xref:System.IDisposable> vyžaduje implementaci jediné metody bez <xref:System.IDisposable.Dispose%2A>parametrů . Však dispose vzor `Dispose` vyžaduje dvě metody, které mají být implementovány:  
  
- Veřejná nevirtuální`NonInheritable` (v jazyce Visual Basic), <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> která nemá žádné parametry.  
  
- Chráněná virtuální`Overridable` metoda ( `Dispose` v jazyce Visual Basic), jejíž podpis je:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Dispose() přetížení

Vzhledem k tomu,`NonInheritable` že veřejné, non-virtual ( v jazyce Visual Basic), metoda bez `Dispose` parametrů je volána spotřebitele typu, jeho účelem je uvolnit nespravované prostředky a označit, že finalizační metoda, pokud je k dispozici, nemusí spustit. Z tohoto důvodu má standardní implementaci:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
Metoda `Dispose` provádí všechny vyčištění objektu, takže systém uvolňování paměti <xref:System.Object.Finalize%2A?displayProperty=nameWithType> již není třeba volat přepsání objektů. Proto volání <xref:System.GC.SuppressFinalize%2A> metody zabrání uvolňování systému spuštění finalizační metody. Pokud typ nemá žádnou finalizační <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> metodu, volání nemá žádný vliv. Všimněte si, že skutečná práce uvolnění nespravovaných prostředků se provádí druhé přetížení `Dispose` metody.  
  
### <a name="the-disposeboolean-overload"></a>Dispose(boolean) přetížení

V druhém přetížení je parametr *likvidace,* <xref:System.Boolean> který označuje, zda <xref:System.IDisposable.Dispose%2A> volání metody pochází `true`z metody (jeho hodnota `false`je ) nebo z finalizační metody (jeho hodnota je ).  
  
Tělo metody sestává ze dvou bloků kódu:  
  
- Blok, který uvolní nespravované prostředky. Tento blok se spustí bez ohledu `disposing` na hodnotu parametru.  
  
- Podmíněný blok, který uvolní spravované prostředky. Tento blok se spustí, `disposing` `true`pokud je hodnota . Mezi uvolněné spravované prostředky patří:  
  
  **Spravované objekty, které implementují <xref:System.IDisposable>.** Podmíněný blok lze volat jejich <xref:System.IDisposable.Dispose%2A> implementaci. Pokud jste použili bezpečný popisovač zabalit nespravované <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> ho prostředků, měli byste volat implementace zde.  
  
  **Spravované objekty, které spotřebovávají velké množství paměti nebo spotřebovávají omezené prostředky.** Uvolnění těchto objektů explicitně v metodě `Dispose` uvolní je rychleji, než kdyby byly uvolněny nedeterministicky systémem uvolňování paměti.  
  
Pokud volání metody pochází z finalizační metody (to `false`znamená, pokud *je likvidace* ), spustí se pouze kód, který uvolní nespravované prostředky. Vzhledem k tomu, že pořadí, ve kterém systém uvolňování `Dispose` paměti zničí spravované `false` objekty během dokončení, není definováno, volání tohoto přetížení s hodnotou zabrání finalizační metodě ve snaze uvolnit spravované prostředky, které již byly uvolněny.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementace vzoru Dispose pro základní třídu

Pokud implementujete vzor Dispose pro základní třídu, musíte poskytnout následující:  
  
> [!IMPORTANT]
> Tento vzor byste měli implementovat <xref:System.IDisposable.Dispose> pro všechny `sealed` `NotInheritable` základní třídy, které implementují a nejsou (v jazyce Visual Basic).  
  
- Implementace, <xref:System.IDisposable.Dispose%2A> která `Dispose(Boolean)` volá metodu.  
  
- Metoda, `Dispose(Boolean)` která provádí skutečnou práci uvolnění prostředků.  
  
- Buď třída odvozená <xref:System.Runtime.InteropServices.SafeHandle> z toho obtéká nespravovaný prostředek <xref:System.Object.Finalize%2A?displayProperty=nameWithType> (doporučeno) nebo přepsání metody. Třída <xref:System.Runtime.InteropServices.SafeHandle> poskytuje finalizační metodu, která vás osvobozuje od nutnosti kódovat jeden.  
  
Zde je obecný vzor pro implementaci dispose vzor pro základní třídy, která používá bezpečné popisovač.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> Předchozí příklad používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objekt pro ilustraci vzorku; místo toho lze <xref:System.Runtime.InteropServices.SafeHandle> použít libovolný objekt odvozený z. Všimněte si, že v příkladu <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> není správně vytvořit konkretizovat jeho objekt.  
  
Zde je obecný vzor pro implementaci dispose vzor pro základní <xref:System.Object.Finalize%2A?displayProperty=nameWithType>třídy, která přepíše .  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> V c#, přepsat <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definováním [destruktoru](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementace vzoru Dispose pro odvozenou třídu

Třída odvozená z třídy, <xref:System.IDisposable> která implementuje <xref:System.IDisposable>rozhraní by neměla <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementovat , protože implementace základní třídy je zděděna jeho odvozené třídy. Místo toho uvolnit prostředky odvozené třídy, zadejte následující:  
  
- Metoda, `protected Dispose(Boolean)` která přepíše metodu základní třídy a provede skutečnou práci uvolnění prostředků odvozené třídy. Tato metoda by `Dispose(Boolean)` měla také volat metodu základní třídy a předat jeho stav likvidace pro argument.  
  
- Buď třída odvozená <xref:System.Runtime.InteropServices.SafeHandle> z toho obtéká nespravovaný prostředek <xref:System.Object.Finalize%2A?displayProperty=nameWithType> (doporučeno) nebo přepsání metody. Třída <xref:System.Runtime.InteropServices.SafeHandle> poskytuje finalizační metodu, která vás osvobozuje od nutnosti kódovat jeden. Pokud zadáte finalizační metodu, by `Dispose(Boolean)` měl volat přetížení s `false` *disposing* argument .  
  
Toto je obecný vzor implementace vzoru Dispose pro odvozenou třídu, která používá bezpečný popisovač:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> Předchozí příklad používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objekt pro ilustraci vzorku; místo toho lze <xref:System.Runtime.InteropServices.SafeHandle> použít libovolný objekt odvozený z. Všimněte si, že v příkladu <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> není správně vytvořit konkretizovat jeho objekt.  
  
Zde je obecný vzor pro implementaci dispose vzor pro odvozené <xref:System.Object.Finalize%2A?displayProperty=nameWithType>třídy, která přepíše :  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> V c#, přepsat <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definováním [destruktoru](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>
## <a name="using-safe-handles"></a>Používání bezpečných popisovačů

Psaní kódu pro finalizační metodu objektu je složitý úkol, který může způsobit problémy, není-li prováděn správně. Proto doporučujeme vytvořit <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> objekty namísto implementace finalizační metody.  
  
Třídy odvozené <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> z třídy zjednodušují problémy s životností objektu přiřazením a uvolněním popisovačů bez přerušení. Obsahují důležitou finalizační metodu, která se zaručeně spustí během uvolňování domény aplikace. Další informace o výhodách použití bezpečného <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>popisovače naleznete v tématu . Následující odvozené třídy <xref:Microsoft.Win32.SafeHandles> v oboru názvů poskytují bezpečné popisovače:  
  
- Třída <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> a třída pro soubory, soubory mapované v paměti a kanály.  
  
- Třída, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> pro zobrazení paměti.  
  
- V <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle> <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> a třídy, pro kryptografické konstrukce.  
  
- Třída <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> pro klíče registru.  
  
- Třída, <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> pro čekat úchyty.  
  
<a name="base"></a>
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Používání bezpečného popisovače pro implementaci vzoru Dispose pro základní třídu

Následující příklad ilustruje disponuje vzor `DisposableStreamResource`pro základní třídy , který používá bezpečný popisovač zapouzdřit nespravované prostředky. Definuje třídu, `DisposableResource` která <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> používá k <xref:System.IO.Stream> zalomení objektu, který představuje otevřený soubor. Metoda `DisposableResource` také obsahuje jednu `Size`vlastnost , která vrací celkový počet bajtů v datovém proudu souborů.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Používání bezpečného popisovače pro implementaci vzoru Dispose pro odvozenou třídu

Následující příklad ilustruje vzorek dispose pro odvozenou `DisposableStreamResource2`třídu , `DisposableStreamResource` která dědí z třídy uvedené v předchozím příkladu. Třída přidá další metodu `WriteFileInfo`a <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> použije objekt k zabalení popisovače zapisovatelného souboru.  
  
[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.GC.SuppressFinalize%2A>
- <xref:System.IDisposable>
- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>
- <xref:Microsoft.Win32.SafeHandles>
- <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>
- [Postupy: Definice a používání tříd a struktur (C++/CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)
- [Vzor pro metodu Dispose](implementing-dispose.md)
