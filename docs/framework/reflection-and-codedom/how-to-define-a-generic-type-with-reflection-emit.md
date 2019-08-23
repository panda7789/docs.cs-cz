---
title: 'Postupy: Definování obecného typu pomocí generování reflexe'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 544d04236a8f1b824a15c6ee7912020346841076
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912534"
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a>Postupy: Definování obecného typu pomocí generování reflexe
Toto téma ukazuje, jak vytvořit jednoduchý obecný typ se dvěma parametry typu, jak použít omezení třídy, omezení rozhraní a speciální omezení pro parametry typu a jak vytvořit členy, které používají parametry typu třídy jako typy parametrů. a návratové typy.  
  
> [!IMPORTANT]
> Metoda není obecná jen proto, že patří obecnému typu a používá parametry typu daného typu. Metoda je obecná pouze v případě, že má svůj vlastní seznam parametrů typu. Většina metod u obecných typů není obecná, jako v tomto příkladu. Příklad generování obecné metody naleznete v tématu [How to: Definování obecné metody pomocí generování](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-method-with-reflection-emit.md)reflexe.  
  
### <a name="to-define-a-generic-type"></a>Definování obecného typu  
  
1. Definujte dynamické sestavení s názvem `GenericEmitExample1`. V tomto příkladu je sestavení spuštěno a uloženo na disk, takže <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> je určena.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2. Definujte dynamický modul. Sestavení je tvořeno spustitelnými moduly. Pro sestavení s jedním modulem je název modulu stejný jako název sestavení a název souboru je název modulu a přípona.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3. Definujte třídu. V tomto příkladu je třída pojmenována `Sample`.  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4. Definujte parametry obecného typu metody `Sample` předáním pole řetězců obsahujícího názvy parametrů metodě <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType>. Tím se třída stane obecným typem. Návratová hodnota je pole <xref:System.Reflection.Emit.GenericTypeParameterBuilder> objektů reprezentujících parametry typu, které lze použít v generovaném kódu.  
  
     V následujícím kódu `Sample` se vytvoří obecný typ s parametry `TFirst` typu a `TSecond`. Aby byl kód čitelnější, každá <xref:System.Reflection.Emit.GenericTypeParameterBuilder> je umístěna do proměnné se stejným názvem jako parametr typu.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5. Přidejte zvláštní omezení do parametrů typu. V tomto příkladu je parametr `TFirst` typu omezený na typy, které mají konstruktory bez parametrů a odkazují na typy.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6. Volitelně lze těmto parametrům typu přidat omezení rozhraní a třídy. V tomto příkladu je parametr `TFirst` typu omezený na typy, které jsou odvozeny ze základní třídy reprezentované <xref:System.Type> objektem obsaženým v proměnné `baseType`a které implementují rozhraní, jejichž typy jsou obsaženy v proměnných. `interfaceA` a .`interfaceB` Podívejte se na příklad kódu pro deklaraci a přiřazení těchto proměnných.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7. Definujte pole. V tomto příkladu je typ pole určen parametrem `TFirst`typu. <xref:System.Reflection.Emit.GenericTypeParameterBuilder>je odvozen z <xref:System.Type>, takže můžete použít parametry obecného typu kdekoli, kde lze použít typ.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8. Definujte metodu, která používá parametry typu obecného typu. Všimněte si, že tyto metody nejsou obecné, pokud nemají své vlastní seznamy parametrů typů. Následující kód `static` definuje metodu ( `TFirst` `Shared` v Visual Basic), která přebírá `List<TFirst>` pole a vrátí (`List(Of TFirst)` v Visual Basic) obsahující všechny prvky pole. Chcete-li definovat tuto metodu, je nutné vytvořit typ `List<TFirst>` voláním <xref:System.Type.MakeGenericType%2A> na definici `List<T>`obecného typu. (Při`GetType` použití operátoru (v Visual Basic) k získání definice obecného typu jehodnotavynechána.)`T` `typeof` Typ parametru je vytvořen pomocí <xref:System.Type.MakeArrayType%2A> metody.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Vygeneruje tělo metody. Tělo metody se skládá ze tří operačních kódů, které načítají vstupní pole do zásobníku, volají `List<TFirst>` konstruktor, který přebírá `IEnumerable<TFirst>` (který provádí veškerou práci vstupních prvků do seznamu) a vrátí (opustí nový <xref:System.Collections.Generic.List%601> objekt). v zásobníku). Obtížné součástí generování tohoto kódu je získání konstruktoru.  
  
     Metoda není podporována <xref:System.Reflection.Emit.GenericTypeParameterBuilder>na, takže není možné získat konstruktor `List<TFirst>` přímo. <xref:System.Type.GetConstructor%2A> Nejdřív je nutné získat konstruktor definice `List<T>` obecného typu a pak zavolat metodu, která ji převede na odpovídající `List<TFirst>`konstruktor.  
  
     Konstruktor použitý pro tento příklad kódu přijímá `IEnumerable<T>`. Všimněte si však <xref:System.Collections.Generic.IEnumerable%601> , že se nejedná o definici obecného typu obecného rozhraní; namísto toho musí `IEnumerable<T>`být parametr `T` typu z `List<T>` typu nahrazen pro parametr `T` typu. (To se zdá být matoucí, protože oba typy mají parametry typu `T`s názvem. Proto tento příklad kódu používá názvy `TFirst` a `TSecond`.) Chcete-li získat typ argumentu konstruktoru, začněte s definicí `IEnumerable<T>` obecného typu a zavolejte <xref:System.Type.MakeGenericType%2A> s `List<T>`prvním parametrem obecného typu. Seznam argumentů konstruktoru musí být předán jako pole s pouze jedním argumentem v tomto případě.  
  
    > [!NOTE]
    > Definice obecného typu je vyjádřena jako `IEnumerable<>` při `typeof` použití operátoru v C#, nebo `IEnumerable(Of )` při použití `GetType` operátoru v Visual Basic.  
  
     Nyní je možné získat konstruktor pro `List<T>` voláním <xref:System.Type.GetConstructor%2A> na definici obecného typu. Pro převod tohoto `List<TFirst>`konstruktoru na odpovídající konstruktor třídy, Pass `List<TFirst>` a konstruktoru z `List<T>` do statické <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> metody.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Vytvořte typ a uložte soubor.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Vyvolat metodu. `ExampleMethod`není obecný, ale typ, ke kterému patří, je obecný, takže aby bylo možné získat objekt <xref:System.Reflection.MethodInfo> , který lze vyvolat, je nutné vytvořit konstruovaný typ z definice typu pro. `Sample` Konstruovaný typ používá `Example` třídu, která splňuje `TFirst` omezení, protože se jedná o typ odkazu a má výchozí konstruktor bez parametrů a `ExampleDerived` třídu, která splňuje omezení `TSecond`. (Kód pro `ExampleDerived` lze nalézt v části příklad kódu.) Tyto dva typy jsou předány <xref:System.Type.MakeGenericType%2A> k vytvoření vytvořeného typu. Pak se získá <xref:System.Type.GetMethod%2A> pomocí metody. <xref:System.Reflection.MethodInfo>  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Následující kód vytvoří pole `Example` objektů, umístí pole do pole typu <xref:System.Object> reprezentující argumenty metody, která má být vyvolána, <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> a předá je metodě. První argument <xref:System.Reflection.MethodBase.Invoke%2A> metody je odkaz s hodnotou null, protože metoda je `static`.  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje třídu s názvem `Sample`, spolu se základní třídou a dvěma rozhraními. Program definuje dva parametry obecného typu pro `Sample`a jeho převod na obecný typ. Parametry typu jsou jediná ta, která vytváří obecný typ. Program zobrazí toto zobrazení zkušební zprávy před a po definici parametrů typu.  
  
 Parametr `TSecond` Type slouží k předvedení omezení třídy a rozhraní, použití základní třídy a rozhraní a parametr `TFirst` typu slouží k předvedení speciálních omezení.  
  
 Příklad kódu definuje pole a metodu pomocí parametrů typu třídy pro typ pole a pro parametr a návratový typ metody.  
  
 Po vytvoření `Sample` třídy je vyvolána metoda.  
  
 Program zahrnuje metodu, která obsahuje informace o obecném typu, a metodu, která obsahuje seznam speciálních omezení pro parametr typu. Tyto metody slouží k zobrazení informací o dokončené `Sample` třídě.  
  
 Program uloží dokončený modul na disk `GenericEmitExample1.dll`, takže ho můžete otevřít pomocí programu [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) a prostudovat jazyk MSIL pro `Sample` třídu.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.Emit.GenericTypeParameterBuilder>
- [Použití generování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Scénáře dynamického sestavení pro vygenerování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tt9483fk(v=vs.100))
