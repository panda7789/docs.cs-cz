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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 964c788c5fc1ac791ed3ddd20c9c5c972d07b2c1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106879"
---
# <a name="implementing-a-dispose-method"></a>Implementace metody Dispose

Implementujete <xref:System.IDisposable.Dispose%2A> metodu pro uvolnění nespravovaných prostředků používaných vaší aplikací. Systém uvolňování paměti .NET nepřiřazuje ani neuvolní nespravovanou paměť.  
  
Vzor pro likvidaci objektu, na který se říká [vzor Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md), ukládá pořadí životnosti objektu. Vzor Dispose se používá pouze pro objekty, které mají přístup k nespravovaným prostředkům, jako jsou popisovače souboru a popisovače kanálu, popisovače registru, popisovače čekání nebo ukazatele na blok nespravované paměti. Důvodem je skutečnost, že systém uvolňování paměti je velmi efektivní při zpětném získávání nepoužitých spravovaných objektů, nedokáže však získat zpět nespravované objekty.  
  
Vzor Dispose má dvě varianty:  
  
- Zabalíte každý nespravovaný prostředek, který typ používá v bezpečném popisovači (to znamená ve třídě odvozené <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>z). V tomto případě implementujete <xref:System.IDisposable> rozhraní a další `Dispose(Boolean)` metodu. Toto je doporučená varianta a nevyžaduje přepsání <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody.  
  
  > [!NOTE]
  > Obor názvů poskytuje sadu tříd odvozených z <xref:System.Runtime.InteropServices.SafeHandle>, které jsou uvedeny v části [použití bezpečných popisovačů](#SafeHandles) . <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> Pokud nemůžete najít třídu, která je vhodná pro uvolnění nespravovaného prostředku, můžete implementovat vlastní podtřídu <xref:System.Runtime.InteropServices.SafeHandle>třídy.  
  
- Implementujete <xref:System.IDisposable> rozhraní a další `Dispose(Boolean)` metodu <xref:System.Object.Finalize%2A?displayProperty=nameWithType> a také přepíšete metodu. Je nutné přepsat <xref:System.Object.Finalize%2A> , aby bylo zajištěno, že nespravované prostředky budou <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> odstraněny, pokud vaše implementace není volána příjemcem vašeho typu. Použijete-li doporučený postup popsaný v předchozí odrážce <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> , třída to provede vaším jménem.  
  
Aby bylo možné zajistit, aby se prostředky vždy vyčistily <xref:System.IDisposable.Dispose%2A> , je třeba volat metodu vícekrát, aniž by došlo k vyvolání výjimky.  
  
Příklad kódu, který je k <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> dispozici pro metodu, ukazuje, jak agresivní uvolňování paměti může způsobit spuštění finalizační metody v době, kdy je stále prováděn člen uvolněného objektu. Je vhodné zavolat <xref:System.GC.KeepAlive%2A> metodu na konci <xref:System.IDisposable.Dispose%2A> zdlouhavé metody.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Dispose() a Dispose(Boolean)  

Rozhraní vyžaduje implementaci jediné metody bez parametrů, <xref:System.IDisposable.Dispose%2A>. <xref:System.IDisposable> Nicméně vzor Dispose vyžaduje, aby `Dispose` byly implementovány dvě metody:  
  
- Veřejná nevirtuální (`NonInheritable` v Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace, která nemá žádné parametry.  
  
- Chráněná virtuální (`Overridable` v Visual Basic) `Dispose` metoda, jejíž signatura je:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Přetížení metody Dispose ()

Vzhledem k tomu, že veřejná, nevirtuální (`NonInheritable` v Visual Basic), `Dispose` Metoda bez parametrů je volána příjemcem typu, jeho účelem je uvolnit nespravované prostředky a označit, že finalizační metoda, je-li k dispozici, nemusí být spuštěna. Z tohoto důvodu má standardní implementaci:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
Metoda provádí vyčištění všech objektů, takže systém uvolňování paměti již nemusí volat <xref:System.Object.Finalize%2A?displayProperty=nameWithType> přepis objektů. `Dispose` Proto volání <xref:System.GC.SuppressFinalize%2A> metody zabrání systému uvolňování paměti ve spuštění finalizační metody. Pokud typ nemá finalizační metodu, volání <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> nemá žádný vliv. Všimněte si, že skutečná práce uvolnění nespravovaných prostředků je prováděna druhým přetížením `Dispose` metody.  
  
### <a name="the-disposeboolean-overload"></a>Přetížení Dispose (Boolean)

Ve druhém přetížení je <xref:System.Boolean> parametr *disposing* , který označuje, zda <xref:System.IDisposable.Dispose%2A> volání metody pochází z metody (její hodnota je `true`) nebo z finalizační metody (její hodnota je `false`).  
  
Tělo metody sestává ze dvou bloků kódu:  
  
- Blok, který uvolní nespravované prostředky. Tento blok se provede bez ohledu na hodnotu `disposing` parametru.  
  
- Podmíněný blok, který uvolní spravované prostředky. Tento blok `disposing` se spustí, pokud je `true`hodnota. Mezi uvolněné spravované prostředky patří:  
  
  **Spravované objekty, které <xref:System.IDisposable>implementují.** Podmíněný blok lze použít k volání jejich <xref:System.IDisposable.Dispose%2A> implementace. Pokud jste použili bezpečný popisovač k zabalení nespravovaného prostředku, měli byste zavolat <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> implementaci zde.  
  
  **Spravované objekty, které využívají velké množství paměti nebo využívají omezených prostředky.** Uvolnění těchto objektů explicitně v `Dispose` metodě je uvolňuje rychleji, než kdyby byly uvolněny nedeterministické systémem uvolňování paměti.  
  
Pokud volání metody pochází z finalizační metody (tj. Pokud je určena `false`pro řazení), je spuštěn pouze kód, který uvolní nespravované prostředky. Protože pořadí, ve kterém uvolňování paměti zničí spravované objekty během finalizace není definováno, volání tohoto `Dispose` přetížení s `false` hodnotou brání finalizační metodě v pokusu o vydání spravovaných prostředků, které mohou mít již bylo uvolněno.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementace vzoru Dispose pro základní třídu

Pokud implementujete vzor Dispose pro základní třídu, musíte poskytnout následující:  
  
> [!IMPORTANT]
> Tento model byste měli implementovat pro všechny základní třídy, které <xref:System.IDisposable.Dispose> implementují a `sealed` nejsou`NotInheritable` (v Visual Basic).  
  
- Implementace, která `Dispose(Boolean)` volá metodu. <xref:System.IDisposable.Dispose%2A>  
  
- `Dispose(Boolean)` Metoda, která provádí skutečnou práci uvolnění prostředků.  
  
- Buď třída odvozená z <xref:System.Runtime.InteropServices.SafeHandle> , která zabalí váš nespravovaný prostředek (doporučeno), nebo přepíše <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metodu. <xref:System.Runtime.InteropServices.SafeHandle> Třída poskytuje finalizační metodu, která vám uvolní, abyste ji nemuseli nakódovat.  
  
Zde je obecný vzor pro implementaci vzoru dispose pro základní třídu, která používá bezpečný popisovač.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> Předchozí příklad používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objekt k ilustraci vzoru; namísto toho lze použít libovolný objekt odvozený od <xref:System.Runtime.InteropServices.SafeHandle> . Všimněte si, že v příkladu není správně vytvořena instance <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu.  
  
Zde je obecný vzor pro implementaci vzoru dispose pro základní třídu, která přepisuje <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> V C#můžete přepsat <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definováním destruktoru [](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementace vzoru Dispose pro odvozenou třídu

Třída odvozená od třídy, která implementuje <xref:System.IDisposable> rozhraní, by neměla implementovat <xref:System.IDisposable>, protože implementace <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> základní třídy je zděděna svými odvozenými třídami. Pokud chcete namísto toho implementovat pro odvozenou třídu vzor Dispose, musíte poskytnout následující:  
  
- `protected Dispose(Boolean)` Metoda, která přepíše metodu základní třídy a provede skutečnou práci uvolnění prostředků odvozené třídy. Tato metoda by měla také volat `Dispose(Boolean)` metodu základní třídy a předat její stav disposing argumentu.  
  
- Buď třída odvozená z <xref:System.Runtime.InteropServices.SafeHandle> , která zabalí váš nespravovaný prostředek (doporučeno), nebo přepíše <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metodu. <xref:System.Runtime.InteropServices.SafeHandle> Třída poskytuje finalizační metodu, která vám uvolní, abyste ji nemuseli nakódovat. Pokud zadáte finalizační metodu, měla by volat `Dispose(Boolean)` přetížení s argumentem `false`disposing.  
  
Toto je obecný vzor implementace vzoru Dispose pro odvozenou třídu, která používá bezpečný popisovač:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> Předchozí příklad používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objekt k ilustraci vzoru; namísto toho lze použít libovolný objekt odvozený od <xref:System.Runtime.InteropServices.SafeHandle> . Všimněte si, že v příkladu není správně vytvořena instance <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu.  
  
Zde je obecný vzor pro implementaci vzoru dispose pro odvozenou třídu, která přepisuje <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> V C#můžete přepsat <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definováním destruktoru [](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Používání bezpečných popisovačů

Psaní kódu pro finalizační metodu objektu je složitý úkol, který může způsobit problémy, není-li prováděn správně. Proto doporučujeme místo implementace finalizační metody vytvořit <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> objekty.  
  
Třídy odvozené od <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> třídy zjednodušují problémy životního cyklu objektů přiřazením a uvolněním popisovačů bez přerušení. Obsahují důležitou finalizační metodu, která se zaručeně spustí během uvolňování domény aplikace. Další informace o výhodách používání bezpečného popisovače najdete v tématu <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. Následující odvozené třídy v <xref:Microsoft.Win32.SafeHandles> oboru názvů poskytují bezpečné popisovače:  
  
- Třídy, a<xref:Microsoft.Win32.SafeHandles.SafePipeHandle> pro soubory, soubory mapované paměti a kanály. <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>  
  
- <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> Třída pro zobrazení paměti.  
  
- Třídy, a<xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle>prokonstrukcekryptografie. <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle> <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>  
  
- <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> Třída pro klíče registru.  
  
- <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> Třída pro obslužné rutiny čekání.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Používání bezpečného popisovače pro implementaci vzoru Dispose pro základní třídu

Následující příklad znázorňuje vzor Dispose pro základní třídu `DisposableStreamResource`,, který používá bezpečný popisovač k zapouzdření nespravovaných prostředků. Definuje `DisposableResource` třídu, která <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> používá k zabalení <xref:System.IO.Stream> objektu, který představuje otevřený soubor. Metoda také obsahuje jedinou `Size`vlastnost, která vrátí celkový počet bajtů v datovém proudu souboru. `DisposableResource`  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Používání bezpečného popisovače pro implementaci vzoru Dispose pro odvozenou třídu

Následující příklad znázorňuje vzor Dispose pro odvozenou třídu `DisposableStreamResource2`,, která dědí `DisposableStreamResource` z třídy uvedené v předchozím příkladu. Třída přidá další metodu, `WriteFileInfo`a <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> pomocí objektu zabalí popisovač zapisovatelného souboru.  
  
[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.GC.SuppressFinalize%2A>
- <xref:System.IDisposable>
- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>
- <xref:Microsoft.Win32.SafeHandles>
- <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>
- [Postupy: Definice a používání tříd a struktur (C++/CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)
- [Vzor pro metodu Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md)
