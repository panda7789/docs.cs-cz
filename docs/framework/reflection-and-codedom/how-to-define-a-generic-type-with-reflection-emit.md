---
title: 'Postupy: Definování obecného typu pomocí generování reflexe'
description: Přečtěte si téma definování obecného typu pomocí generování reflexe. Vytvořte obecný typ se dvěma parametry typu, použijte omezení třídy, omezení rozhraní a další.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- generics [.NET Framework], dynamic types
- reflection emit, generic types
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
ms.openlocfilehash: fe8fb731fd160ab87e5c65debf367a96bc0dea2a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865122"
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a>Postupy: Definování obecného typu pomocí generování reflexe
Toto téma ukazuje, jak vytvořit jednoduchý obecný typ se dvěma parametry typu, jak použít omezení třídy, omezení rozhraní a speciální omezení pro parametry typu a jak vytvořit členy, které používají parametry typu třídy jako typy parametrů a návratové typy.  
  
> [!IMPORTANT]
> Metoda není obecná jen proto, že patří obecnému typu a používá parametry typu daného typu. Metoda je obecná pouze v případě, že má svůj vlastní seznam parametrů typu. Většina metod u obecných typů není obecná, jako v tomto příkladu. Příklad generování obecné metody naleznete v tématu [How to: define a Generic Method with reflexe Emit](how-to-define-a-generic-method-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-type"></a>Definování obecného typu  
  
1. Definujte dynamické sestavení s názvem `GenericEmitExample1` . V tomto příkladu je sestavení spuštěno a uloženo na disk, takže <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> je určena.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2. Definujte dynamický modul. Sestavení je tvořeno spustitelnými moduly. Pro sestavení s jedním modulem je název modulu stejný jako název sestavení a název souboru je název modulu a přípona.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3. Definujte třídu. V tomto příkladu je třída pojmenována `Sample` .  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4. Definujte parametry obecného typu metody `Sample` předáním pole řetězců obsahujícího názvy parametrů metodě <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType>. Tím se třída stane obecným typem. Návratová hodnota je pole <xref:System.Reflection.Emit.GenericTypeParameterBuilder> objektů reprezentujících parametry typu, které lze použít v generovaném kódu.  
  
     V následujícím kódu se `Sample` vytvoří obecný typ s parametry typu `TFirst` a `TSecond` . Aby byl kód čitelnější, každá <xref:System.Reflection.Emit.GenericTypeParameterBuilder> je umístěna do proměnné se stejným názvem jako parametr typu.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5. Přidejte zvláštní omezení do parametrů typu. V tomto příkladu je parametr typu `TFirst` omezený na typy, které mají konstruktory bez parametrů a odkazují na typy.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6. Volitelně lze těmto parametrům typu přidat omezení rozhraní a třídy. V tomto příkladu je parametr typu `TFirst` omezen na typy, které jsou odvozeny ze základní třídy reprezentované <xref:System.Type> objektem obsaženým v proměnné `baseType` a které implementují rozhraní, jejichž typy jsou obsaženy v proměnných `interfaceA` a `interfaceB` . Podívejte se na příklad kódu pro deklaraci a přiřazení těchto proměnných.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7. Definujte pole. V tomto příkladu je typ pole určen parametrem typu `TFirst` . <xref:System.Reflection.Emit.GenericTypeParameterBuilder>je odvozen z <xref:System.Type> , takže můžete použít parametry obecného typu kdekoli, kde lze použít typ.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8. Definujte metodu, která používá parametry typu obecného typu. Všimněte si, že tyto metody nejsou obecné, pokud nemají své vlastní seznamy parametrů typů. Následující kód definuje `static` metodu ( `Shared` v Visual Basic), která přebírá pole `TFirst` a vrátí `List<TFirst>` ( `List(Of TFirst)` v Visual Basic) obsahující všechny prvky pole. Chcete-li definovat tuto metodu, je nutné vytvořit typ `List<TFirst>` voláním <xref:System.Type.MakeGenericType%2A> na definici obecného typu `List<T>` . ( `T` Při použití `typeof` operátoru ( `GetType` v Visual Basic) k získání definice obecného typu je hodnota vynechána.) Typ parametru je vytvořen pomocí <xref:System.Type.MakeArrayType%2A> metody.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Vygeneruje tělo metody. Tělo metody se skládá ze tří operačních kódů, které načítají vstupní pole do zásobníku, volají `List<TFirst>` konstruktor, který přebírá `IEnumerable<TFirst>` (který provádí veškerou práci vstupních prvků do seznamu) a vrátí (opustí nový <xref:System.Collections.Generic.List%601> objekt v zásobníku). Obtížné součástí generování tohoto kódu je získání konstruktoru.  
  
     <xref:System.Type.GetConstructor%2A>Metoda není podporována na <xref:System.Reflection.Emit.GenericTypeParameterBuilder> , takže není možné získat konstruktor `List<TFirst>` přímo. Nejdřív je nutné získat konstruktor definice obecného typu `List<T>` a pak zavolat metodu, která ji převede na odpovídající konstruktor `List<TFirst>` .  
  
     Konstruktor použitý pro tento příklad kódu přijímá `IEnumerable<T>` . Všimněte si však, že se nejedná o definici obecného typu <xref:System.Collections.Generic.IEnumerable%601> obecného rozhraní; namísto toho `T` musí být parametr typu z typu `List<T>` nahrazen pro parametr typu `T` `IEnumerable<T>` . (To se zdá být matoucí, protože oba typy mají parametry typu s názvem `T` . Proto tento příklad kódu používá názvy `TFirst` a `TSecond` .) Chcete-li získat typ argumentu konstruktoru, začněte s definicí obecného typu `IEnumerable<T>` a zavolejte <xref:System.Type.MakeGenericType%2A> s prvním parametrem obecného typu `List<T>` . Seznam argumentů konstruktoru musí být předán jako pole s pouze jedním argumentem v tomto případě.  
  
    > [!NOTE]
    > Definice obecného typu je vyjádřena jako `IEnumerable<>` při použití `typeof` operátoru v jazyce C# nebo `IEnumerable(Of )` při použití `GetType` operátoru v Visual Basic.  
  
     Nyní je možné získat konstruktor pro `List<T>` voláním <xref:System.Type.GetConstructor%2A> na definici obecného typu. Pro převod tohoto konstruktoru na odpovídající konstruktor třídy `List<TFirst>` , Pass `List<TFirst>` a konstruktoru z `List<T>` do statické <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> metody.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Vytvořte typ a uložte soubor.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Vyvolat metodu. `ExampleMethod`není obecný, ale typ, ke kterému patří, je obecný, takže aby bylo možné získat objekt <xref:System.Reflection.MethodInfo> , který lze vyvolat, je nutné vytvořit konstruovaný typ z definice typu pro `Sample` . Konstruovaný typ používá `Example` třídu, která splňuje omezení, protože se jedná o `TFirst` typ odkazu a má výchozí konstruktor bez parametrů a `ExampleDerived` třídu, která splňuje omezení `TSecond` . (Kód pro `ExampleDerived` lze nalézt v části příklad kódu.) Tyto dva typy jsou předány k <xref:System.Type.MakeGenericType%2A> Vytvoření vytvořeného typu. <xref:System.Reflection.MethodInfo>Pak se získá pomocí <xref:System.Type.GetMethod%2A> metody.  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Následující kód vytvoří pole `Example` objektů, umístí pole do pole typu <xref:System.Object> reprezentující argumenty metody, která má být vyvolána, a předá je <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> metodě. První argument <xref:System.Reflection.MethodBase.Invoke%2A> metody je odkaz s hodnotou null, protože metoda je `static` .  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje třídu s názvem `Sample` , spolu se základní třídou a dvěma rozhraními. Program definuje dva parametry obecného typu pro `Sample` a jeho převod na obecný typ. Parametry typu jsou jediná ta, která vytváří obecný typ. Program zobrazí toto zobrazení zkušební zprávy před a po definici parametrů typu.  
  
 Parametr Type `TSecond` slouží k předvedení omezení třídy a rozhraní, použití základní třídy a rozhraní a parametr typu `TFirst` slouží k předvedení speciálních omezení.  
  
 Příklad kódu definuje pole a metodu pomocí parametrů typu třídy pro typ pole a pro parametr a návratový typ metody.  
  
 Po `Sample` Vytvoření třídy je vyvolána metoda.  
  
 Program zahrnuje metodu, která obsahuje informace o obecném typu, a metodu, která obsahuje seznam speciálních omezení pro parametr typu. Tyto metody slouží k zobrazení informací o dokončené `Sample` třídě.  
  
 Program uloží dokončený modul na disk `GenericEmitExample1.dll` , takže ho můžete otevřít pomocí [Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) a prostudovat jazyk MSIL pro `Sample` třídu.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection.Emit.GenericTypeParameterBuilder>
- [Použití generování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Scénáře dynamického sestavení pro vygenerování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tt9483fk(v=vs.100))
