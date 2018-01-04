---
title: Implementace metody Dispose
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
caps.latest.revision: "44"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 90edda252c33b6f07c795b8db1a0edaf1a688445
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-a-dispose-method"></a>Implementace metody Dispose

Můžete implementovat <xref:System.IDisposable.Dispose%2A> metodu pro uvolnění nespravované prostředky využívané vaší aplikace. Uvolňování paměti rozhraní .NET nemá přidělit nebo verzi nespravované paměti.  
  
Vzor pro uvolnění objektu, označuje jako [dispose vzor](../../../docs/standard/design-guidelines/dispose-pattern.md), ukládá pořadí na životnosti objektu. Vzor Dispose se používá pouze pro objekty, které mají přístup k nespravovaným prostředkům, jako jsou popisovače souboru a popisovače kanálu, popisovače registru, popisovače čekání nebo ukazatele na blok nespravované paměti. Důvodem je skutečnost, že systém uvolňování paměti je velmi efektivní při zpětném získávání nepoužitých spravovaných objektů, nedokáže však získat zpět nespravované objekty.  
  
Vzor Dispose má dvě varianty:  
  
* Zabalení všechny nespravované prostředky, které používají typ v bezpečném popisovač (tedy třídy odvozené od <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>). V takovém případě implementace <xref:System.IDisposable> rozhraní a další `Dispose(Boolean)` metoda. Toto je doporučená variace a nevyžaduje přepsání <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metoda.  
  
  > [!NOTE]
  > <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> Obor názvů obsahuje sadu třídy odvozené od třídy <xref:System.Runtime.InteropServices.SafeHandle>, které jsou uvedeny v [pomocí bezpečné obslužné rutiny](#SafeHandles) části. Pokud nemůžete najít třídu, která je vhodná pro uvolnění nespravovaných zdrojů, můžete implementovat vlastní podtřídou třídy <xref:System.Runtime.InteropServices.SafeHandle>.  
  
* Můžete implementovat <xref:System.IDisposable> rozhraní a další `Dispose(Boolean)` metoda a můžete také přepsat <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metoda. Je nutné přepsat <xref:System.Object.Finalize%2A> zajistit, že pokud jsou zapomenuty nespravované prostředky vaší <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace nevolá příjemce vašeho typu. Pokud použijete doporučené technik popsaných v předchozím seznamu, <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> třída tomu vaším jménem.  
  
Abyste zajistili, že prostředky jsou vždy vyčistit správně, <xref:System.IDisposable.Dispose%2A> metoda by měla být možné volat vícekrát bez způsobení výjimky.  
  
Ukázkový kód pro <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> metoda ukazuje, jak agresivní paměti kolekce může způsobit finalizační metodu členem regenerovaný objektu se stále provádí-li spustit. Je vhodné k volání <xref:System.GC.KeepAlive%2A> metoda na konci zdlouhavé <xref:System.IDisposable.Dispose%2A> metoda.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Dispose() a Dispose(Boolean)  

<xref:System.IDisposable> Rozhraní vyžaduje provádění jedné bez parametrů metody, <xref:System.IDisposable.Dispose%2A>. Vzor uvolnění však vyžaduje dva `Dispose` metody k implementaci:  
  
* Veřejné nevirtuálních (`NonInheritable` v jazyce Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace, která nemá žádné parametry.  
  
* A chráněná virtuální (`Overridable` v jazyce Visual Basic) `Dispose` metoda, jejíž podpis je:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Přetížení Dispose()

Protože public, nevirtuálních (`NonInheritable` v jazyce Visual Basic) bez parametrů `Dispose` metoda je volána metodou příjemce typu, jejím účelem je kvůli uvolnění nespravovaných prostředků a k označení, že finalizační metodu, pokud je k dispozici, není nutné spustit. Z tohoto důvodu má standardní implementaci:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
`Dispose` Metoda provádí všechny objekt čištění, bude systém uvolňování už potřebuje volat objektu <xref:System.Object.Finalize%2A?displayProperty=nameWithType> přepsat. Proto volání <xref:System.GC.SuppressFinalize%2A> metoda zabrání spuštění finalizační metodu uvolňování paměti. Pokud má tento typ žádné finalizační metodu volání <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> nemá žádný vliv. Všimněte si, že samotnou práci vydání nespravovaných prostředků provádí druhý přetížení `Dispose` metoda.  
  
### <a name="the-disposeboolean-overload"></a>Přetížení Dispose(Boolean)

V druhé přetížení *uvolnění* parametr <xref:System.Boolean> určující, zda volání metody, které pochází z <xref:System.IDisposable.Dispose%2A> – metoda (jeho hodnota může být `true`) nebo z finalizační metody (jeho hodnota může být `false`).  
  
Tělo metody sestává ze dvou bloků kódu:  
  
* Blok, který uvolní nespravované prostředky. Tento blok spustí bez ohledu na hodnotu `disposing` parametr.  
  
* Podmíněný blok, který uvolní spravované prostředky. Tento blok spustí, pokud hodnota `disposing` je `true`. Mezi uvolněné spravované prostředky patří:  
  
  **Spravované objekty, které implementují <xref:System.IDisposable>.** Podmíněné bloku lze použít k volání jejich <xref:System.IDisposable.Dispose%2A> implementace. Pokud jste použili bezpečné popisovač zabalit nespravovaný prostředek, měli byste zavolat <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> implementace sem.  
  
  **Spravované objekty, které využívají velké objemy paměti nebo využívat omezených prostředků.** Uvolnění tyto objekty explicitně v `Dispose` metoda uvolní je rychleji, než pokud nedeterministicky byly převzaty systémem uvolňování paměti.  
  
Pokud volání metody, které pochází z finalizační metody (tj. Pokud *uvolnění* je `false`), provede pouze kód, který uvolní nespravované prostředky. Protože není definováno pořadí, ve kterém bude systém uvolňování zničí spravované objekty během dokončení, volání to `Dispose` přetížení s hodnotou `false` finalizační metodu brání v pokusu o vydání spravované prostředky, které mohou mít již bylo uvolněno.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementace vzoru Dispose pro základní třídu

Pokud implementujete vzor Dispose pro základní třídu, musíte poskytnout následující:  
  
> [!IMPORTANT]
> Měli byste implementovat tento vzor pro všechny základní třídy, které implementují <xref:System.IDisposable.Dispose> a nejsou `sealed` (`NotInheritable` v jazyce Visual Basic).  
  
* A <xref:System.IDisposable.Dispose%2A> implementace, která volá `Dispose(Boolean)` metoda.  
  
* A `Dispose(Boolean)` metoda, která provádí samotnou práci uvolnění prostředků.  
  
* Buď třída odvozená z <xref:System.Runtime.InteropServices.SafeHandle> který zabalí nespravovaný prostředek (doporučeno) nebo přepsání pro <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metoda. <xref:System.Runtime.InteropServices.SafeHandle> Třída poskytuje finalizační metodu, která s kódu, jeden není.  
  
Tady je obecný vzor pro implementaci vzoru dispose pro základní třídu, která používá bezpečné popisovač.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> Předchozí příklad používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu pro ilustraci vzoru; libovolného objektu odvozené z <xref:System.Runtime.InteropServices.SafeHandle> může místo toho použít. Všimněte si, že v příkladu nevytvoří instanci správně jeho <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu.  
  
Tady je obecný vzor pro implementaci vzoru dispose pro základní třídu, která přepisuje <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> V jazyce C#, přepíšete <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definováním [destruktor](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementace vzoru Dispose pro odvozenou třídu

Třída odvozená z třídy, která implementuje <xref:System.IDisposable> by neměly implementovat rozhraní <xref:System.IDisposable>, protože základní třídy implementace <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> zdědí jejich odvozené třídy. Pokud chcete namísto toho implementovat pro odvozenou třídu vzor Dispose, musíte poskytnout následující:  
  
* A `protected``Dispose(Boolean)` metodu, která přepíše metodu základní třídy a provádí samotnou práci uvolnění prostředků odvozené třídy. Tato metoda by měla také zavolat `Dispose(Boolean)` metoda základní třídy a předejte ji hodnotu `true` pro *uvolnění* argument.  
  
* Buď třída odvozená z <xref:System.Runtime.InteropServices.SafeHandle> který zabalí nespravovaný prostředek (doporučeno) nebo přepsání pro <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metoda. <xref:System.Runtime.InteropServices.SafeHandle> Třída poskytuje finalizační metodu, která s kódu, jeden není. Pokud zadáte finalizační metody by měly volat `Dispose(Boolean)` přetížení s *uvolnění* argument `false`.  
  
Toto je obecný vzor implementace vzoru Dispose pro odvozenou třídu, která používá bezpečný popisovač:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> Předchozí příklad používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu pro ilustraci vzoru; libovolného objektu odvozené z <xref:System.Runtime.InteropServices.SafeHandle> může místo toho použít. Všimněte si, že v příkladu nevytvoří instanci správně jeho <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu.  
  
Tady je obecný vzor pro implementace metody dispose vzor odvozené třídy, který přepíše <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> V jazyce C#, přepíšete <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definováním [destruktor](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Používání bezpečných popisovačů

Psaní kódu pro finalizační metodu objektu je složitý úkol, který může způsobit problémy, není-li prováděn správně. Proto doporučujeme, aby vytvoříte <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> objekty místo implementace finalizační metody.  
  
Třídy odvozené od <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> třída zjednodušit problematika životnosti objektů přiřazení a uvolněním obslužných rutin bez přerušení. Obsahují důležitou finalizační metodu, která se zaručeně spustí během uvolňování domény aplikace. Další informace o výhodách používání bezpečné popisovač najdete v tématu <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. Následující odvozených tříd v <xref:Microsoft.Win32.SafeHandles> oboru názvů zadejte bezpečné obslužné rutiny:  
  
* <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>, A <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> třída, pro soubory, soubory mapované paměti a kanály.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> Třídu pro zobrazení paměti.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>, A <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> třídy pro šifrování konstrukce.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> Třídy pro klíče registru.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> Třídu pro obslužné rutiny čekání.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Používání bezpečného popisovače pro implementaci vzoru Dispose pro základní třídu

Následující příklad ilustruje vzoru dispose pro základní třídu `DisposableStreamResource`, že používá sejfu zpracování pro zapouzdření nespravovaných prostředků. Definuje `DisposableResource` třídu, která využívá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> zabalit <xref:System.IO.Stream> objekt, který reprezentuje soubor otevřený. `DisposableResource` Metoda také zahrnuje jednu vlastnost `Size`, který vrátí celkový počet bajtů v datový proud souboru.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Používání bezpečného popisovače pro implementaci vzoru Dispose pro odvozenou třídu

Následující příklad ilustruje vzoru dispose pro třídu odvozenou `DisposableStreamResource2`, který dědí z `DisposableStreamResource` třídy uvedené v předchozím příkladu. Třída přidává další způsob, `WriteFileInfo`a používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objekt zabalit popisovač souboru s možností zápisu.  
  
[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a>Viz také

<xref:System.GC.SuppressFinalize%2A>   
<xref:System.IDisposable>   
<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>   
<xref:Microsoft.Win32.SafeHandles>   
<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>   
<xref:System.Object.Finalize%2A?displayProperty=nameWithType>   
[Postupy: definování a používání tříd a struktur (C + +/ CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)   
[Vzor pro metodu Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md)
