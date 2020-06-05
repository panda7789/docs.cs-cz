---
title: Implementace metody Dispose
description: V tomto článku se naučíte implementovat metodu Dispose, která uvolňuje nespravované prostředky používané vaším kódem v .NET.
ms.date: 05/27/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
ms.openlocfilehash: c8b4b9a79577776bc049ef77e222d63374178708
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447170"
---
# <a name="implement-a-dispose-method"></a>Implementace metody Dispose

Implementace <xref:System.IDisposable.Dispose%2A> metody je primárně určena pro uvolňování nespravovaných prostředků používaných vaším kódem. Při práci se členy instance, které jsou <xref:System.IDisposable> implementace, je běžné volání kaskády <xref:System.IDisposable.Dispose%2A> . K dispozici jsou další důvody pro implementaci <xref:System.IDisposable.Dispose%2A> , jako je například vrácení dříve provedených změn. Například uvolnění paměti, která byla přidělena, odebrání položky z kolekce, která byla přidána, signalizace vydání zámku, který byl získán a tak dále.

[Systém uvolňování paměti .NET](index.md) nepřiřazuje ani neuvolní nespravovanou paměť. Vzor pro likvidaci objektu, který je označován jako vzor Dispose, ukládá pořadí pro životnost objektu. Vzor Dispose se používá pro objekty, které implementují <xref:System.IDisposable> rozhraní a je běžné při interakci s popisovači souborů a kanálů, obslužnými rutinami registru, obslužnými rutinami čekání nebo ukazateli na bloky nespravované paměti. Důvodem je to, že systém uvolňování paměti nemůže uvolnit nespravované objekty.

Aby bylo možné zajistit, aby se prostředky vždy vyčistily správně, <xref:System.IDisposable.Dispose%2A> měla by být metoda idempotentní, aby byla vícenásobně volat bez vyvolání výjimky. Kromě toho by následné vyvolání <xref:System.IDisposable.Dispose%2A> nemělo dělat nic.

Příklad kódu, který je k dispozici pro <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> metodu, ukazuje, jak uvolňování paměti může způsobit spuštění finalizační metody, zatímco nespravovaný odkaz na objekt nebo jeho členy se stále používá. Může být vhodné využít <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> k tomu, aby objekt nezpůsobil pro uvolňování paměti od začátku aktuální rutiny do bodu, ve kterém je tato metoda volána.

## <a name="safe-handles"></a>Bezpečné popisovače

Psaní kódu pro finalizační metodu objektu je složitý úkol, který může způsobit problémy, není-li prováděn správně. Proto doporučujeme <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> místo implementace finalizační metody vytvořit objekty.

<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>Je abstraktní spravovaný typ, který zabalí <xref:System.IntPtr?displayProperty=nameWithType> , který identifikuje nespravovaný prostředek. V systému Windows může identifikovat popisovač v systému UNIX, popisovač souboru. Poskytuje veškerou logiku nutnou k zajištění toho, že se tento prostředek vydává jednou a jenom jednou, když `SafeHandle` je vyřazený z nebo když jsou všechny odkazy na `SafeHandle` vyřazené a `SafeHandle` instance se dokončuje.

<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>Je abstraktní základní třída. Odvozené třídy poskytují konkrétní instance pro různé druhy popisovačů. Tyto odvozené třídy ověřují, které hodnoty pro <xref:System.IntPtr?displayProperty=nameWithType> jsou považovány za neplatné a jak je ve skutečnosti zadarmo zadarmo. Například <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> je odvozen od `SafeHandle` pro zabalení `IntPtrs` , které identifikuje otevřené popisovače souborů/popisovače, a Přepisuje její <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle?displayProperty=nameWithType> metodu pro její zavření (prostřednictvím `close` funkce v systému UNIX nebo `CloseHandle` ve Windows). Většina rozhraní API v knihovnách .NET, které vytváří nespravovaný prostředek, zabalí ho do `SafeHandle` a a vrátí, `SafeHandle` co je potřeba, místo ručního vrácení nezpracovaného ukazatele zpět. V situacích, kdy pracujete s nespravovanou komponentou a získáte `IntPtr` pro nespravovaný prostředek, můžete vytvořit vlastní `SafeHandle` typ, který ho zabalí. V důsledku toho některé `SafeHandle` netypy nemusejí implementovat finalizační metody; většina implementací vzorku na jedno použití pouze ukončí zalamování jiných spravovaných prostředků, z nichž některé mohou být `SafeHandle` s.

Následující odvozené třídy v <xref:Microsoft.Win32.SafeHandles> oboru názvů poskytují bezpečné popisovače:

- <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>Třídy, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle> a <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> pro soubory, soubory mapované paměti a kanály.
- <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle>Třída pro zobrazení paměti.
- <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>Třídy, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle> a <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> pro konstrukce kryptografie.
- <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle>Třída pro klíče registru.
- <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle>Třída pro obslužné rutiny čekání.

## <a name="dispose-and-disposebool"></a>Dispose () a Dispose (bool)

<xref:System.IDisposable>Rozhraní vyžaduje implementaci jediné metody bez parametrů, <xref:System.IDisposable.Dispose%2A> . Kromě toho by měla být jakákoli nezapečetěná Třída mít `Dispose(bool)` k implementaci další metodu přetížení:

- `public`Nevirtuální ( `NonInheritable` v Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace bez parametrů.

- `protected virtual`Metoda ( `Overridable` in Visual Basic), `Dispose` jejíž signatura je:

  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]

  > [!IMPORTANT]
  > `disposing`Parametr by měl být `false` při volání z finalizační `true` metody a při volání z <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metody. Jinými slovy, je `true` při deterministickém volání a `false` při nedeterministickém volání.

### <a name="the-dispose-method"></a>Metoda Dispose ()

Vzhledem k tomu, že `public` nevirtuální ( `NonInheritable` v Visual Basic), metoda bez parametrů `Dispose` je volána příjemcem typu, jeho účelem je uvolnit nespravované prostředky, provést obecné vyčištění a označit, že finalizační metoda, pokud je k dispozici, nemusí být spuštěna. Uvolnění aktuální paměti přidružené ke spravovanému objektu je vždy doména [uvolňování paměti](index.md). Z tohoto důvodu má standardní implementaci:

[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]

`Dispose`Metoda provádí vyčištění všech objektů, takže systém uvolňování paměti již nemusí volat <xref:System.Object.Finalize%2A?displayProperty=nameWithType> přepis objektů. Proto volání <xref:System.GC.SuppressFinalize%2A> metody zabrání systému uvolňování paměti ve spuštění finalizační metody. Pokud typ nemá finalizační metodu, volání <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> nemá žádný vliv. Všimněte si, že vlastní vyčištění je provedeno `Dispose(bool)` přetížením metody.

### <a name="the-disposebool-method-overload"></a>Přetížení metody Dispose (bool)

V přetížení `disposing` je parametr <xref:System.Boolean> , který označuje, zda volání metody pochází z <xref:System.IDisposable.Dispose%2A> metody (její hodnota je `true` ) nebo z finalizační metody (její hodnota je `false` ).

Tělo metody sestává ze dvou bloků kódu:

- Blok, který uvolní nespravované prostředky. Tento blok se provede bez ohledu na hodnotu `disposing` parametru.
- Podmíněný blok, který uvolní spravované prostředky. Tento blok `disposing` se spustí, pokud je hodnota `true` . Mezi uvolněné spravované prostředky patří:

  - **Spravované objekty, které implementují <xref:System.IDisposable> .** Podmíněný blok lze použít k volání jejich <xref:System.IDisposable.Dispose%2A> implementace (Dispose kaskády). Pokud jste použili odvozenou třídu <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> pro zabalení nespravovaného prostředku, měli byste zavolat <xref:System.Runtime.InteropServices.SafeHandle.Dispose?displayProperty=nameWithType> implementaci zde.

  - **Spravované objekty, které využívají velké množství paměti nebo využívají omezených prostředky.** Přiřazení rozsáhlých odkazů na spravované objekty, aby `null` bylo pravděpodobnější, že budou pravděpodobně nedostupné. Tato verze je rychlejší, než kdyby byla uvolněna bez jejich nedeterministického.

Pokud volání metody pochází z finalizační metody, měla by být spuštěna pouze kód, který uvolní nespravované prostředky. Implementátor zodpovídá za to, že nepravdivá cesta nekomunikuje se spravovanými objekty, které mohou být uvolněny. To je důležité kvůli tomu, že systém uvolňování paměti během finalizace nedeterministické spravované objekty.

## <a name="cascade-dispose-calls"></a>Volání Dispose pro kaskády

Pokud vaše třída vlastní pole nebo vlastnost a její typ implementuje <xref:System.IDisposable> , měla by být také implementována obsažená třída <xref:System.IDisposable> . Třída, která vytváří instanci <xref:System.IDisposable> implementace a ukládá ji jako člen instance, je také zodpovědná za její vyčištění. To vám umožní zajistit, aby se odkazované typy na jedno použití dostaly do čistého výkonu prostřednictvím <xref:System.IDisposable.Dispose%2A> metody. V tomto příkladu je třída `sealed` (nebo `NotInheritable` v Visual Basic).

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/disposable1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/disposable1.vb#1)]

## <a name="implement-the-dispose-pattern"></a>Implementace vzoru Dispose

Všechny nezapečetěné třídy nebo (Visual Basic třídy neupravené jako `NotInheritable` ) by měly být považovány za potenciální základní třídu, protože by mohly být děděny. Pokud implementujete vzor Dispose pro jakoukoli potenciální základní třídu, je nutné zadat následující:

- <xref:System.IDisposable.Dispose%2A>Implementace, která volá `Dispose(bool)` metodu.
- `Dispose(bool)`Metoda, která provede skutečné vyčištění.
- Buď třída odvozená z <xref:System.Runtime.InteropServices.SafeHandle> , která zabalí váš nespravovaný prostředek (doporučeno), nebo přepíše <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metodu. <xref:System.Runtime.InteropServices.SafeHandle>Třída poskytuje finalizační metodu, takže nemusíte psát sami sebe.

> [!IMPORTANT]
> Základní třída může odkazovat pouze na spravované objekty a implementovat vzor Dispose. V těchto případech není finalizační metoda nutná. Finalizační metoda je nutná pouze v případě, že přímo odkazujete na nespravované prostředky.

Zde je obecný vzor pro implementaci vzoru dispose pro základní třídu, která používá bezpečný popisovač.

[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]

> [!NOTE]
> Předchozí příklad používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objekt k ilustraci vzoru; <xref:System.Runtime.InteropServices.SafeHandle> namísto toho lze použít libovolný objekt odvozený od. Všimněte si, že v příkladu není správně vytvořena instance <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu.

Zde je obecný vzor pro implementaci vzoru dispose pro základní třídu, která přepisuje <xref:System.Object.Finalize%2A?displayProperty=nameWithType> .

[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]

> [!TIP]
> V jazyce C# vytvoříte [finalizační metodu](../../csharp/programming-guide/classes-and-structs/destructors.md) přepsáním <xref:System.Object.Finalize%2A?displayProperty=nameWithType> . V Visual Basic se to dělá s `Protected Overrides Sub Finalize()` .

## <a name="implement-the-dispose-pattern-for-a-derived-class"></a>Implementace vzoru dispose pro odvozenou třídu

Třída odvozená od třídy, která implementuje <xref:System.IDisposable> rozhraní, by neměla implementovat <xref:System.IDisposable> , protože implementace základní třídy <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> je zděděna svými odvozenými třídami. Místo toho pro vyčištění odvozené třídy zadejte následující:

- `protected override void Dispose(bool)`Metoda, která přepisuje metodu základní třídy a provede skutečné vyčištění odvozené třídy. Tato metoda musí také volat `base.Dispose(bool)` metodu ( `MyBase.Dispose(bool)` v Visual Basic) základní třídy a předat její stav disposing argumentu.
- Buď třída odvozená z <xref:System.Runtime.InteropServices.SafeHandle> , která zabalí váš nespravovaný prostředek (doporučeno), nebo přepíše <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metodu. <xref:System.Runtime.InteropServices.SafeHandle>Třída poskytuje finalizační metodu, která vám uvolní, abyste ji nemuseli nakódovat. Pokud zadáte finalizační metodu, musí volat `Dispose(bool)` přetížení s `disposing` argumentem `false` .

Toto je obecný vzor implementace vzoru Dispose pro odvozenou třídu, která používá bezpečný popisovač:

[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]

> [!NOTE]
> Předchozí příklad používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objekt k ilustraci vzoru; <xref:System.Runtime.InteropServices.SafeHandle> namísto toho lze použít libovolný objekt odvozený od. Všimněte si, že v příkladu není správně vytvořena instance <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu.

Zde je obecný vzor pro implementaci vzoru dispose pro odvozenou třídu, která přepisuje <xref:System.Object.Finalize%2A?displayProperty=nameWithType> :

[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]

## <a name="implement-the-dispose-pattern-with-safe-handles"></a>Implementace vzoru dispose pomocí bezpečných popisovačů

Následující příklad znázorňuje vzor Dispose pro základní třídu, `DisposableStreamResource` , který používá bezpečný popisovač k zapouzdření nespravovaných prostředků. Definuje `DisposableStreamResource` třídu, která používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> k zabalení <xref:System.IO.Stream> objektu, který představuje otevřený soubor. Třída také obsahuje jedinou vlastnost, `Size` která vrací celkový počet bajtů v datovém proudu souboru.

[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]

## <a name="implement-the-dispose-pattern-for-a-derived-class-with-safe-handles"></a>Implementace vzoru dispose pro odvozenou třídu s bezpečnými popisovači

Následující příklad znázorňuje vzor Dispose pro odvozenou třídu, `DisposableStreamResource2` , která dědí z třídy uvedené `DisposableStreamResource` v předchozím příkladu. Třída přidá další metodu, `WriteFileInfo` a pomocí <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu zabalí popisovač zapisovatelného souboru.

[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]

## <a name="see-also"></a>Viz také

- <xref:System.GC.SuppressFinalize%2A>
- <xref:System.IDisposable>
- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>
- <xref:Microsoft.Win32.SafeHandles>
- <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>
- [Definování a využívání tříd a struktur (C++/CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)
