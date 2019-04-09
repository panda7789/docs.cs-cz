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
ms.openlocfilehash: 54eb0bf5c364faa4f6c0f2a8d14490137e4ea442
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101192"
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a>Postupy: Definování obecného typu pomocí generování reflexe
Toto téma ukazuje, jak vytvořit jednoduchý obecný typ s dvěma parametry typu, jak použít omezení třídy, omezení rozhraní a zvláštní omezení pro parametry typu a jak vytvořit členy, které používají parametry typu třídy jako typy parametrů a návratové typy.  
  
> [!IMPORTANT]
>  Metoda není obecná jen proto, že patří obecnému typu a používá parametry typu daného typu. Metoda je obecná pouze v případě, že má svůj vlastní seznam parametrů typu. Většina metod v obecných typech nejsou obecné, jako v následujícím příkladu. Příklad výstupu obecné metody, naleznete v tématu [jak: Definování obecné metody pomocí reflexe generování](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-method-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-type"></a>K definování obecného typu  
  
1.  Definujte dynamické sestavení s názvem `GenericEmitExample1`. V tomto příkladu je sestavení spustí a uložit na disk, tak <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> je zadán.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2.  Definování dynamického modulu. Sestavení se skládá z spustitelných modulů. Pro jeden modul sestavení název modulu je stejný jako název sestavení a název souboru je název modulu s příponou.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3.  Definice třídy. V tomto příkladu je název třídy `Sample`.  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4.  Definujte parametry obecného typu metody `Sample` předáním pole řetězců obsahujícího názvy parametrů metodě <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType>. Díky tomu třídy obecného typu. Vrácená hodnota je pole <xref:System.Reflection.Emit.GenericTypeParameterBuilder> objekty, které představují parametry typu, které je možné použít v emitovaný kód.  
  
     V následujícím kódu `Sample` stane obecný typ s parametry typu `TFirst` a `TSecond`. Chcete-li kód lépe čitelný, každý <xref:System.Reflection.Emit.GenericTypeParameterBuilder> je umístěn v proměnné se stejným názvem jako parametr typu.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5.  Těmto parametrům typu přidáte zvláštní omezení. V tomto příkladu zadejte parametr `TFirst` je omezen na typy, které mít konstruktor bez parametrů a typy odkazů.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6.  Volitelně lze těmto parametrům typu přidat omezení rozhraní a třídy. V tomto příkladu zadejte parametr `TFirst` je omezen na typy, které jsou odvozeny od základní třídy, která je reprezentována <xref:System.Type> objektů obsažených v proměnné `baseType`, a které implementují rozhraní, jejichž typy jsou obsaženy v proměnné `interfaceA` a `interfaceB`. Podívejte se na příklad kódu pro deklaraci a přiřazení těchto proměnných.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7.  Definování pole. V tomto příkladu je typ pole určená parametr typu `TFirst`. <xref:System.Reflection.Emit.GenericTypeParameterBuilder> je odvozen od <xref:System.Type>, abyste mohli používat parametry obecného typu, kdekoli typ lze použít.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8.  Definujte metodu, která používá typ parametry obecného typu. Všimněte si, že tyto metody nejsou obecné, pokud nemají své vlastní seznamy parametru typu. Následující kód definuje `static` – metoda (`Shared` v jazyce Visual Basic), který přijímá pole `TFirst` a vrátí `List<TFirst>` (`List(Of TFirst)` v jazyce Visual Basic) obsahující všechny prvky pole. Pokud chcete definovat tuto metodu, je potřeba vytvořit typ `List<TFirst>` voláním <xref:System.Type.MakeGenericType%2A> v definici obecného typu `List<T>`. ( `T` Vynecháte při použití `typeof` – operátor (`GetType` v jazyce Visual Basic) Chcete-li získat definici obecného typu.) Typ parametru je vytvořená pomocí <xref:System.Type.MakeArrayType%2A> metody.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Vygenerování těla metody. Tělo metody se skládá ze tří operační kódy, které načítají vstupní pole do zásobníku, zavolejte `List<TFirst>` konstruktor, který přijímá `IEnumerable<TFirst>` (který vykonává všechnu práci uvedení vstupních prvků do seznamu) a vrátí (byste museli opustit nové <xref:System.Collections.Generic.List%601> objektu v zásobníku). Složitou částí vysílat tento kód je stále konstruktoru.  
  
     <xref:System.Type.GetConstructor%2A> Metoda není podporována u <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, takže ho není možné získat konstruktoru `List<TFirst>` přímo. Nejprve je potřeba získat konstruktor třídy definice obecného typu `List<T>` a pak volat metodu, která se převede na odpovídající konstruktor třídy `List<TFirst>`.  
  
     Konstruktor používá pro tento příklad kódu používá `IEnumerable<T>`. Upozorňujeme, že to není definici obecných typů <xref:System.Collections.Generic.IEnumerable%601> obecné rozhraní; místo toho parametr typu `T` z `List<T>` musí nahrazené za parametr typu `T` z `IEnumerable<T>`. (Zdá se, že dojde k záměně pouze, protože oba typy má parametry typu s názvem `T`. That is, proč tento příklad kódu používá názvy `TFirst` a `TSecond`.) Chcete-li získat typ argumentu konstruktoru, začněte s definice obecného typu `IEnumerable<T>` a volat <xref:System.Type.MakeGenericType%2A> s první parametr obecného typu `List<T>`. Seznam argumentů konstruktoru v tomto případě musí být předán jako pole s jedním argumentem.  
  
    > [!NOTE]
    >  Definice obecného typu je vyjádřena jako `IEnumerable<>` při použití `typeof` operátor v jazyce C#, nebo `IEnumerable(Of )` při použití `GetType` operátor v jazyce Visual Basic.  
  
     Nyní je možné získat konstruktoru `List<T>` voláním <xref:System.Type.GetConstructor%2A> v definici obecného typu. Tento konstruktor převést na odpovídající konstruktor třídy `List<TFirst>`, předejte `List<TFirst>` a konstruktoru z `List<T>` statické <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> metody.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Vytvoření typu a soubor uložte.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Vyvolání metody. `ExampleMethod` není obecný, ale patří do typ není obecný, takže pokud chcete získat <xref:System.Reflection.MethodInfo> , který může být vyvolána je potřeba vytvořit konstruovaný typ z definice typu pro `Sample`. Konstruovaný typ používá `Example` třídu, která splňuje omezení na `TFirst` vzhledem k tomu, že je typem odkazu a má výchozí konstruktor bez parametrů a `ExampleDerived` třída, která splňuje omezení na `TSecond`. (Kód `ExampleDerived` najdete v části příklad kódu.) Tyto dva typy jsou předány <xref:System.Type.MakeGenericType%2A> konstruovaný typ vytvoření. <xref:System.Reflection.MethodInfo> Se potom získá pomocí <xref:System.Type.GetMethod%2A> metody.  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Následující kód vytvoří pole `Example` objektů, umístí takové pole do pole typu <xref:System.Object> představující argumenty metody mají být vyvolány a předává je do <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> metody. Prvním argumentem funkce <xref:System.Reflection.MethodBase.Invoke%2A> metoda je odkaz s hodnotou null, protože metoda je `static`.  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje třídu s názvem `Sample`, spolu s základní třídu a dvě rozhraní. Program definuje dva parametry obecného typu pro `Sample`, zapnutí do obecného typu. Parametry typu jsou pouze jednu, která provádí obecného typu. Tento program zobrazí zobrazením zkušební zprávu, před a po definování parametrů typu.  
  
 Parametr typu `TSecond` slouží k předvedení omezení rozhraní a třídy pomocí základní třídy a rozhraní a typ parametru `TFirst` slouží k předvedení zvláštní omezení.  
  
 Příklad kódu definuje pole a metodu pomocí třídy parametry typu pro typ pole a pro parametr a návratový typ metody.  
  
 Po `Sample` třídy se vytvořil, je vyvolána metoda.  
  
 Program zahrnuje metodu, která obsahuje informace o obecný typ a metodu, která jsou uvedena zvláštní omezení pro parametr typu. Tyto metody slouží k zobrazení informací o dokončené `Sample` třídy.  
  
 Program uloží na disk jako dokončené modulu `GenericEmitExample1.dll`, takže ho můžete otevřít [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) a zkontrolovat jazyk MSIL pro `Sample` třídy.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) nezbytné pro kompilaci.  
  
-   Nejsou vyžadovány žádné odkazy na další sestavení.  
  
-   Kompilace kódu do příkazového řádku pomocí csc.exe a vbc.exe, cl.exe. Ke kompilaci kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.Emit.GenericTypeParameterBuilder>
- [Použití generování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Scénáře dynamických sestavení generování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tt9483fk(v=vs.100))
