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
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238985"
---
# <a name="implementing-a-dispose-method"></a>Implementace metody Dispose

Implementujete metodu <xref:System.IDisposable.Dispose%2A> pro uvolnění nespravovaných prostředků používaných vaší aplikací. Systém uvolňování paměti .NET nepřiřazuje ani neuvolní nespravovanou paměť.  
  
Vzor pro likvidaci objektu, na který se říká [vzor Dispose](implementing-dispose.md), ukládá pořadí životnosti objektu. Vzor Dispose se používá pouze pro objekty, které mají přístup k nespravovaným prostředkům, jako jsou popisovače souboru a popisovače kanálu, popisovače registru, popisovače čekání nebo ukazatele na blok nespravované paměti. Důvodem je skutečnost, že systém uvolňování paměti je velmi efektivní při zpětném získávání nepoužitých spravovaných objektů, nedokáže však získat zpět nespravované objekty.  
  
Vzor Dispose má dvě varianty:  
  
- Zabalíte každý nespravovaný prostředek, který typ používá v bezpečném popisovači (to znamená ve třídě odvozené od <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>). V tomto případě implementujete rozhraní <xref:System.IDisposable> a další `Dispose(Boolean)` metodu. Toto je doporučená varianta a nevyžaduje přepsání metody <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
  > [!NOTE]
  > Obor názvů <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> poskytuje sadu tříd odvozených z <xref:System.Runtime.InteropServices.SafeHandle>, které jsou uvedeny v části [použití bezpečných popisovačů](#SafeHandles) . Pokud nemůžete najít třídu, která je vhodná pro uvolnění nespravovaného prostředku, můžete implementovat svou vlastní podtřídu <xref:System.Runtime.InteropServices.SafeHandle>.  
  
- Implementujete rozhraní <xref:System.IDisposable> a další `Dispose(Boolean)` metodu a přepíšete také metodu <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. Musíte přepsat <xref:System.Object.Finalize%2A>, abyste zajistili, že nespravované prostředky budou odstraněny, pokud vaše <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace není volána příjemcem vašeho typu. Použijete-li doporučený postup popsaný v předchozí odrážce, třída <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> provede vaše jménem.  
  
Aby bylo možné zajistit, aby se prostředky vždy vyčistily, měla by být metoda <xref:System.IDisposable.Dispose%2A> volat několikrát, aniž by došlo k vyvolání výjimky.  
  
Příklad kódu, který je k dispozici pro metodu <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> ukazuje, jak uvolňování paměti může způsobit spuštění finalizační metody, zatímco nespravovaný odkaz na objekt nebo jeho členy se stále používá. Může být vhodné využít <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> k tomu, aby objekt nezpůsobil pro uvolňování paměti od začátku aktuální rutiny do bodu, ve kterém je tato metoda volána.
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Dispose() a Dispose(Boolean)  

Rozhraní <xref:System.IDisposable> vyžaduje implementaci jediné metody bez parametrů, <xref:System.IDisposable.Dispose%2A>. Nicméně vzor Dispose vyžaduje, aby byly implementovány dvě `Dispose` metody:  
  
- Veřejná nevirtuální (`NonInheritable` v Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci, která nemá žádné parametry.  
  
- Chráněná virtuální (`Overridable` v Visual Basic) `Dispose` metoda, jejíž signatura je:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Přetížení metody Dispose ()

Protože veřejné, nevirtuální (`NonInheritable` v Visual Basic), metoda bez `Dispose` parametrů je volána příjemcem typu, jeho účelem je uvolnit nespravované prostředky a označit, že finalizační metoda, pokud je k dispozici, nemusí být spuštěna. Z tohoto důvodu má standardní implementaci:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
Metoda `Dispose` provádí vyčištění všech objektů, takže systém uvolňování paměti již nepotřebuje volat objekty "<xref:System.Object.Finalize%2A?displayProperty=nameWithType> přepsat". Proto volání metody <xref:System.GC.SuppressFinalize%2A> zabraňuje systému uvolňování paměti ve spuštění finalizační metody. Pokud typ nemá žádný finalizační metodu, volání <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> nemá žádný vliv. Všimněte si, že skutečná práce uvolnění nespravovaných prostředků je prováděna druhým přetížením metody `Dispose`.  
  
### <a name="the-disposeboolean-overload"></a>Přetížení Dispose (Boolean)

Ve druhém přetížení je parametr *disposing* <xref:System.Boolean>, který označuje, zda volání metody pochází z metody <xref:System.IDisposable.Dispose%2A> (její hodnota je `true`) nebo z finalizační metody (její hodnota je `false`).  
  
Tělo metody sestává ze dvou bloků kódu:  
  
- Blok, který uvolní nespravované prostředky. Tento blok se provede bez ohledu na hodnotu parametru `disposing`.  
  
- Podmíněný blok, který uvolní spravované prostředky. Tento blok se spustí, pokud je hodnota `disposing` `true`. Mezi uvolněné spravované prostředky patří:  
  
  **Spravované objekty, které implementují <xref:System.IDisposable>.** Podmíněný blok lze použít k volání implementace <xref:System.IDisposable.Dispose%2A>. Pokud jste použili bezpečný popisovač k zabalení nespravovaného prostředku, měli byste zavolat implementaci <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> zde.  
  
  **Spravované objekty, které využívají velké množství paměti nebo využívají omezených prostředky.** Uvolnění těchto objektů explicitně v metodě `Dispose` uvolní je rychleji, než kdyby byly uvolněny nedeterministické systémem uvolňování paměti.  
  
Pokud volání metody pochází z finalizační metody ( *to znamená, pokud je* zrušení `false`), spustí se pouze kód, který uvolní nespravované prostředky. Protože pořadí, ve kterém uvolňování paměti ničí spravované objekty během finalizace není definováno, voláním tohoto `Dispose` přetížení s hodnotou `false` zabrání finalizačnímu programu v pokusu o vydání spravovaných prostředků, které mohou být již uvolněny.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementace vzoru Dispose pro základní třídu

Pokud implementujete vzor Dispose pro základní třídu, musíte poskytnout následující:  
  
> [!IMPORTANT]
> Tento model byste měli implementovat pro všechny základní třídy, které implementují <xref:System.IDisposable.Dispose> a nejsou `sealed` (`NotInheritable` v Visual Basic).  
  
- <xref:System.IDisposable.Dispose%2A> implementace, která volá metodu `Dispose(Boolean)`.  
  
- `Dispose(Boolean)` metoda, která provádí skutečnou práci uvolnění prostředků.  
  
- Buď třída odvozená od <xref:System.Runtime.InteropServices.SafeHandle>, která zabalí váš nespravovaný prostředek (doporučeno), nebo přepíše metodu <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. Třída <xref:System.Runtime.InteropServices.SafeHandle> poskytuje finalizační metodu, která vám uvolní, abyste ji museli nakódovat.  
  
Zde je obecný vzor pro implementaci vzoru dispose pro základní třídu, která používá bezpečný popisovač.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> Předchozí příklad používá objekt <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> k ilustraci vzoru; místo toho lze použít jakýkoli objekt odvozený od <xref:System.Runtime.InteropServices.SafeHandle>. Všimněte si, že v příkladu není správně vytvořena instance objektu <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>.  
  
Zde je obecný vzor pro implementaci vzoru dispose pro základní třídu, která přepisuje <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> V C#můžete přepsat <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definováním [destruktoru](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementace vzoru Dispose pro odvozenou třídu

Třída odvozená od třídy, která implementuje rozhraní <xref:System.IDisposable>, by neměla implementovat <xref:System.IDisposable>, protože implementace základní třídy <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> je zděděna svými odvozenými třídami. Namísto toho, abyste uvolnili prostředky odvozené třídy, je třeba zadat následující:  
  
- `protected Dispose(Boolean)` metoda, která přepíše metodu základní třídy a provede skutečnou práci uvolnění prostředků odvozené třídy. Tato metoda by měla také volat metodu `Dispose(Boolean)` základní třídy a předávat svůj stav disposing argumentu.  
  
- Buď třída odvozená od <xref:System.Runtime.InteropServices.SafeHandle>, která zabalí váš nespravovaný prostředek (doporučeno), nebo přepíše metodu <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. Třída <xref:System.Runtime.InteropServices.SafeHandle> poskytuje finalizační metodu, která vám uvolní, abyste ji museli nakódovat. Pokud zadáte finalizační metodu, měla by volat `Dispose(Boolean)` přetížení s argumentem *disposing* `false`.  
  
Toto je obecný vzor implementace vzoru Dispose pro odvozenou třídu, která používá bezpečný popisovač:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> Předchozí příklad používá objekt <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> k ilustraci vzoru; místo toho lze použít jakýkoli objekt odvozený od <xref:System.Runtime.InteropServices.SafeHandle>. Všimněte si, že v příkladu není správně vytvořena instance objektu <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>.  
  
Zde je obecný vzor pro implementaci vzoru dispose pro odvozenou třídu, která přepisuje <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> V C#můžete přepsat <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definováním [destruktoru](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>
## <a name="using-safe-handles"></a>Používání bezpečných popisovačů

Psaní kódu pro finalizační metodu objektu je složitý úkol, který může způsobit problémy, není-li prováděn správně. Proto doporučujeme sestavit <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> objektů namísto implementace finalizační metody.  
  
Třídy odvozené od třídy <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> zjednodušují problémy životního cyklu objektů přiřazením a uvolněním popisovačů bez přerušení. Obsahují důležitou finalizační metodu, která se zaručeně spustí během uvolňování domény aplikace. Další informace o výhodách používání bezpečného popisovače najdete v tématu <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. Následující odvozené třídy v oboru názvů <xref:Microsoft.Win32.SafeHandles> poskytují bezpečné popisovače:  
  
- Třída <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>a <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> pro soubory, soubory mapované paměti a kanály.  
  
- Třída <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> pro zobrazení paměti.  
  
- Třídy <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>a <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> pro konstruktory kryptografie.  
  
- Třída <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> pro klíče registru.  
  
- Třída <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> pro obslužné rutiny čekání.  
  
<a name="base"></a>
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Používání bezpečného popisovače pro implementaci vzoru Dispose pro základní třídu

Následující příklad znázorňuje vzor Dispose pro základní třídu, `DisposableStreamResource`, která používá bezpečný popisovač k zapouzdření nespravovaných prostředků. Definuje třídu `DisposableResource`, která používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> k zabalení <xref:System.IO.Stream>ho objektu, který představuje otevřený soubor. Metoda `DisposableResource` také obsahuje jedinou vlastnost `Size`, která vrátí celkový počet bajtů v datovém proudu souboru.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Používání bezpečného popisovače pro implementaci vzoru Dispose pro odvozenou třídu

Následující příklad znázorňuje vzor Dispose pro odvozenou třídu, `DisposableStreamResource2`, která dědí z třídy `DisposableStreamResource` prezentované v předchozím příkladu. Třída přidá další metodu, `WriteFileInfo`a pomocí objektu <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> zabalí popisovač zapisovatelného souboru.  
  
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
