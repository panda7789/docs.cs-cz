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
ms.openlocfilehash: 36526da1fc678e933a75e19bac9c8e1d0a40909c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743385"
---
# <a name="implementing-a-dispose-method"></a>Implementace metody Dispose

Můžete implementovat <xref:System.IDisposable.Dispose%2A> metodu pro uvolnění nespravovaných prostředků, které používá vaše aplikace. Uvolňování paměti .NET není přidělit nebo uvolnit nespravované paměti.  
  
Vzor pro zrušení objektu, uvedený jako [vzor dispose](../../../docs/standard/design-guidelines/dispose-pattern.md), ukládá pořadí u životnosti objektu. Vzor Dispose se používá pouze pro objekty, které mají přístup k nespravovaným prostředkům, jako jsou popisovače souboru a popisovače kanálu, popisovače registru, popisovače čekání nebo ukazatele na blok nespravované paměti. Důvodem je skutečnost, že systém uvolňování paměti je velmi efektivní při zpětném získávání nepoužitých spravovaných objektů, nedokáže však získat zpět nespravované objekty.  
  
Vzor Dispose má dvě varianty:  
  
* Obtékání jednotlivých nespravovaných prostředků, které typ používá v bezpečném popisovači (tedy ve třídě odvozené z <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>). V tomto případě implementujete <xref:System.IDisposable> rozhraní a další `Dispose(Boolean)` metody. Toto je doporučená varianta a nevyžaduje přepsání <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody.  
  
  > [!NOTE]
  > <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> Obor názvů obsahuje sadu tříd odvozených z <xref:System.Runtime.InteropServices.SafeHandle>, které jsou uvedeny v [používání bezpečných popisovačů](#SafeHandles) oddílu. Pokud nemůžete najít třídu, která je vhodná pro uvolnění nespravovaných prostředků, můžete implementovat vlastní podtřídu <xref:System.Runtime.InteropServices.SafeHandle>.  
  
* Implementujete <xref:System.IDisposable> rozhraní a další `Dispose(Boolean)` metoda a také přepsání <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. Je nutné přepsat <xref:System.Object.Finalize%2A> zajistit, že nespravovaných prostředků jsou odstraněny z, pokud vaše <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace není volána příjemcem typu. Pokud používáte doporučenou techniku popsanou v předchozím bodě <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> třídy to provede za vás.  
  
Abyste zajistili, že prostředky jsou vždy správně vyčištěné, <xref:System.IDisposable.Dispose%2A> metoda by měla být vícekrát bez vyvolání výjimky.  
  
Příklad kódu stanoveného pro <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> metoda ukazuje, jak agresivní systém uvolňování paměti může způsobit spuštění finalizační metody zatímco člen uvolňovaného objektu stále probíhá. Je vhodné volat <xref:System.GC.KeepAlive%2A> na konci dlouhé metody <xref:System.IDisposable.Dispose%2A> metoda.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Dispose() a Dispose(Boolean)  

<xref:System.IDisposable> Rozhraní vyžaduje implementaci jedné metody na konstruktor bez parametrů, <xref:System.IDisposable.Dispose%2A>. Vzor dispose však vyžaduje dva `Dispose` metody k implementaci:  
  
* Veřejnou nevirtuální (`NonInheritable` v jazyce Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace, která nemá žádné parametry.  
  
* Chráněná virtuální (`Overridable` v jazyce Visual Basic) `Dispose` metoda, jejíž podpis je:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Dispose() přetížení

Protože veřejnou, nevirtuální (`NonInheritable` v jazyce Visual Basic), konstruktor bez parametrů `Dispose` metoda je volána příjemcem typu, jejím účelem je pro uvolnění nespravovaných prostředků a k označení, že finalizační metodu, pokud je k dispozici, nemusí být spuštěna. Z tohoto důvodu má standardní implementaci:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
`Dispose` Metoda provádí vyčištění veškerých objektů, takže systému uvolňování paměti již nemusí volat objektů <xref:System.Object.Finalize%2A?displayProperty=nameWithType> přepsat. Proto volání <xref:System.GC.SuppressFinalize%2A> metody zabrání spuštění finalizační metody systému uvolňování paměti. Pokud typ neobsahuje žádnou finalizační metodu, volání <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> nemá žádný vliv. Všimněte si, že samotnou práci uvolnění nespravovaných prostředků provádí druhé přetížení `Dispose` metody.  
  
### <a name="the-disposeboolean-overload"></a>Přetížení Dispose(Boolean)

V druhé přetížení *disposing* parametr je <xref:System.Boolean> , která označuje, zda volání metody uskutečňuje z <xref:System.IDisposable.Dispose%2A> – metoda (její hodnota je `true`) nebo z finalizační metody (její hodnota je `false`).  
  
Tělo metody sestává ze dvou bloků kódu:  
  
* Blok, který uvolní nespravované prostředky. Tento blok se spustí bez ohledu na hodnotu `disposing` parametru.  
  
* Podmíněný blok, který uvolní spravované prostředky. Tento blok se spustí, pokud hodnota `disposing` je `true`. Mezi uvolněné spravované prostředky patří:  
  
  **Spravované objekty, které implementují <xref:System.IDisposable>.** Podmíněný blok je možné volat jejich <xref:System.IDisposable.Dispose%2A> implementace. Pokud jste k obtékání nespravovaného prostředku použili bezpečný popisovač, měli byste zavolat <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> implementaci.  
  
  **Spravované objekty, které využívají velké množství paměti nebo vzácné prostředky.** Explicitně v uvolněním těchto objektů `Dispose` metoda je uvolníte rychleji, než pokud byly získány zpět nedeterministicky systémem uvolňování.  
  
Pokud volání metody pochází z finalizační metody (tj. Pokud *disposing* je `false`), provádí pouze kód uvolňující nespravované prostředky. Vzhledem k tomu, že není definováno pořadí, ve které systému uvolňování paměti odstraňuje spravované objekty během finalizace, volající toto `Dispose` přetížení s hodnotou `false` brání nepokusí uvolnit spravované prostředky, které můžou mít finalizační metodu již bylo uvolněno.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementace vzoru Dispose pro základní třídu

Pokud implementujete vzor Dispose pro základní třídu, musíte poskytnout následující:  
  
> [!IMPORTANT]
> Měli byste implementovat tento vzor pro všechny základní třídy, které implementují <xref:System.IDisposable.Dispose> a nejsou `sealed` (`NotInheritable` v jazyce Visual Basic).  
  
* A <xref:System.IDisposable.Dispose%2A> implementace, která volá `Dispose(Boolean)` metody.  
  
* A `Dispose(Boolean)` metodu, která provádí vlastní uvolnění prostředků.  
  
* Třídu odvozenou z <xref:System.Runtime.InteropServices.SafeHandle> , která obtéká nespravovaný prostředek (doporučeno) nebo přepsání <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. <xref:System.Runtime.InteropServices.SafeHandle> Třída poskytuje finalizační metodu, díky které nemusíte vytvářet kód.  
  
Tady je obecný vzor implementace vzoru dispose pro základní třídu, která používá bezpečný popisovač.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> V předchozím příkladu se používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu pro ilustraci vzor; libovolný objekt odvozený od <xref:System.Runtime.InteropServices.SafeHandle> lze použít místo toho. Všimněte si, že v příkladu nevytvoří instanci správně jeho <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu.  
  
Tady je obecný vzor implementace vzoru dispose pro základní třídu, která přepíše <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> V jazyce C#, přepíšete <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definováním [destruktor](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementace vzoru Dispose pro odvozenou třídu

Třída odvozená z třídy, která implementuje <xref:System.IDisposable> by neměla implementovat rozhraní <xref:System.IDisposable>, protože implementace ze základní třídy <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> je zděděná z příslušných odvozených tříd. Pokud chcete namísto toho implementovat pro odvozenou třídu vzor Dispose, musíte poskytnout následující:  
  
* A `protected Dispose(Boolean)` metodu, která přepíše metodu základní třídy a provádí vlastní uvolnění prostředků odvozené třídy. Tato metoda by měla volat také `Dispose(Boolean)` metody základní třídy a předat stav disposing argumentu.  
  
* Třídu odvozenou z <xref:System.Runtime.InteropServices.SafeHandle> , která obtéká nespravovaný prostředek (doporučeno) nebo přepsání <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. <xref:System.Runtime.InteropServices.SafeHandle> Třída poskytuje finalizační metodu, díky které nemusíte vytvářet kód. Pokud poskytnete finalizační metodu, měla by volat `Dispose(Boolean)` přetížení s *disposing* argument `false`.  
  
Toto je obecný vzor implementace vzoru Dispose pro odvozenou třídu, která používá bezpečný popisovač:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> V předchozím příkladu se používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu pro ilustraci vzor; libovolný objekt odvozený od <xref:System.Runtime.InteropServices.SafeHandle> lze použít místo toho. Všimněte si, že v příkladu nevytvoří instanci správně jeho <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> objektu.  
  
Tady je obecný vzor implementace vzoru dispose pro odvozenou třídu, která přepíše <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> V jazyce C#, přepíšete <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definováním [destruktor](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Používání bezpečných popisovačů

Psaní kódu pro finalizační metodu objektu je složitý úkol, který může způsobit problémy, není-li prováděn správně. Proto doporučujeme, abyste zkonstruovali <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> objekty namísto implementace finalizační metody.  
  
Třídy odvozené z <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> třída zjednodušuje problémy životnosti objektu přiřazením a uvolněním popisovačů bez přerušení. Obsahují důležitou finalizační metodu, která se zaručeně spustí během uvolňování domény aplikace. Další informace o výhodách používání bezpečného popisovače naleznete v tématu <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. Následující odvozené třídy v <xref:Microsoft.Win32.SafeHandles> obor názvů poskytují bezpečné popisovače:  
  
* <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>, A <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> třídy, pro soubory, soubory mapované do paměti a kanály.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> Třída pro zobrazování paměti.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>, A <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> třídy pro konstrukce kryptografie.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> Třídy pro klíče registru.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> Třídy pro popisovače čekání.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Používání bezpečného popisovače pro implementaci vzoru Dispose pro základní třídu

Následující příklad znázorňuje vzor dispose pro základní třídu, `DisposableStreamResource`, že používá bezpečný popisovač pro zapouzdření nespravovaných prostředků. Definuje `DisposableResource` třídu, která používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> zabalit <xref:System.IO.Stream> objekt, který představuje otevřený soubor. `DisposableResource` Metoda zahrnuje také jedinou vlastnost `Size`, která vrátí celkový počet bajtů v datovém proudu.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Používání bezpečného popisovače pro implementaci vzoru Dispose pro odvozenou třídu

Následující příklad znázorňuje vzor dispose pro odvozenou třídu, `DisposableStreamResource2`, které dědí z `DisposableStreamResource` třídy uvedené v předchozím příkladu. Třída přidá další metodu `WriteFileInfo`a používá <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> pro obtékání popisovače zapisovatelného souboru.  
  
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
