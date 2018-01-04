---
title: "Postupy: Definování obecného typu pomocí generování reflexe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- generics [.NET Framework], dynamic types
- reflection emit, generic types
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e10f0f4ad1552c7b8ba7e6bc5175ffe7576ec986
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a>Postupy: Definování obecného typu pomocí generování reflexe
Toto téma ukazuje, jak vytvořit jednoduché obecného typu se dva parametry typu, jak se má použít třída omezení, omezení rozhraní a zvláštní omezení pro parametry typu a postup vytvoření členy, které používají parametry typu třídy jako typy parametrů a návratové typy.  
  
> [!IMPORTANT]
>  Metoda není obecná jen proto, že patří obecnému typu a používá parametry typu daného typu. Metoda je obecná pouze v případě, že má svůj vlastní seznam parametrů typu. Většinu metod v obecných typech nejsou obecné, jako v následujícím příkladu. Příklad výstupu obecná metoda, naleznete v části [postupy: definování obecné metody pomocí generování reflexe](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-method-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-type"></a>K definování obecného typu  
  
1.  Definování dynamické sestavení s názvem `GenericEmitExample1`. V tomto příkladu je sestavení provést a uložit na disk, takže <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> je zadán.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2.  Definování dynamické modulu. Sestavení se skládá z spustitelné moduly. Pro jeden modul sestavení název modulu je stejný jako název sestavení a název souboru je název modulu a rozšíření.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3.  Definice třídy. V tomto příkladu je třída s názvem `Sample`.  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4.  Definujte parametry obecného typu metody `Sample` předáním pole řetězců obsahujícího názvy parametrů metodě <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType>. Díky tomu třída obecného typu. Vrácená hodnota je pole <xref:System.Reflection.Emit.GenericTypeParameterBuilder> objekty, které představují typ parametry, které se dají použít v emitovaného kódu.  
  
     V následujícím kódu `Sample` stane obecného typu pomocí parametrů typu `TFirst` a `TSecond`. Chcete-li kód snadněji číst, každý <xref:System.Reflection.Emit.GenericTypeParameterBuilder> je umístěn v proměnné se stejným názvem jako parametr typu.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5.  Přidáte zvláštní omezení pro parametry typu. V tomto příkladu zadejte parametr `TFirst` je omezené na typy, které mají bezparametrové konstruktory a odkazové typy.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6.  Volitelně lze těmto parametrům typu přidat omezení rozhraní a třídy. V tomto příkladu zadejte parametr `TFirst` je omezené na typy, které jsou odvozeny od základní třídy reprezentována <xref:System.Type> objektů obsažených v proměnné `baseType`, a které implementují rozhraní, jejichž typy jsou obsaženy v proměnné `interfaceA` a `interfaceB`. Podívejte se na příklad kódu pro deklarace a přiřazení těchto proměnných.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7.  Zadejte pole. V tomto příkladu je typ pole určený parametrem typu `TFirst`. <xref:System.Reflection.Emit.GenericTypeParameterBuilder>odvozená z <xref:System.Type>, abyste mohli používat parametry obecného typu odkudkoli typ lze použít.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8.  Zadejte metodu, která používá typ parametry obecného typu. Všimněte si, že tyto metody nejsou obecné, pokud mají své vlastní seznamy parametrů typu. Následující kód definuje `static` – metoda (`Shared` v jazyce Visual Basic), která má pole `TFirst` a vrátí `List<TFirst>` (`List(Of TFirst)` v jazyce Visual Basic) obsahující všechny elementy pole. Chcete-li definovat tuto metodu, je nutné k vytvoření typu `List<TFirst>` voláním <xref:System.Type.MakeGenericType%2A> v definici obecného typu `List<T>`. ( `T` Je vynechán, při použití `typeof` – operátor (`GetType` v jazyce Visual Basic) získat definice obecného typu.) Typ parametru je vytvořená pomocí <xref:System.Type.MakeArrayType%2A> metoda.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Emitování metoda textu. Metoda textu se skládá ze tří operační kódy, které načítají vstupního pole do zásobníku, volejte `List<TFirst>` konstruktor, který přebírá `IEnumerable<TFirst>` (na které se všechnu práci týkající se uvedení elementy vstupu do seznamu) a vrátí (ponechat nové <xref:System.Collections.Generic.List%601> objektu v zásobníku). Obtížné součástí generování tento kód je získávání konstruktoru.  
  
     <xref:System.Type.GetConstructor%2A> Metoda není podporována u <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, takže není možné získat konstruktoru `List<TFirst>` přímo. Nejprve je nutné získat konstruktor definice obecného typu `List<T>` a pak volat metodu, která se převede na odpovídající konstruktoru `List<TFirst>`.  
  
     Konstruktor pro tento příklad kódu používá trvá `IEnumerable<T>`. Upozorňujeme však, že se nejedná definice obecného typu <xref:System.Collections.Generic.IEnumerable%601> obecné rozhraní; místo toho parametr typu `T` z `List<T>` musí být nahrazena pro parametr typu `T` z `IEnumerable<T>`. (To zdá se, že matoucí, protože oba typy mít parametry typu s názvem `T`. That is, proč tento příklad kódu používá názvy `TFirst` a `TSecond`.) Chcete-li získat typ argument konstruktoru, můžete začít s definice obecného typu `IEnumerable<T>` a volání <xref:System.Type.MakeGenericType%2A> s první parametr obecného typu `List<T>`. Seznam argumentů konstruktor v takovém případě musí být předán jako pole, s právě jeden argument.  
  
    > [!NOTE]
    >  Definice obecného typu je vyjádřen jako `IEnumerable<>` při použití `typeof` operátor v jazyce C# nebo `IEnumerable(Of )` při použití `GetType` operátor v jazyce Visual Basic.  
  
     Nyní je možné získat konstruktoru `List<T>` voláním <xref:System.Type.GetConstructor%2A> v definici obecného typu. Tento konstruktor převést na odpovídající konstruktoru `List<TFirst>`, předat `List<TFirst>` a konstruktoru z `List<T>` ke statickému <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> metoda.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Vytvoření typu a soubor uložte.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Vyvolání metody. `ExampleMethod`není obecná, ale patří do typ je obecný tak, aby bylo možné získat <xref:System.Reflection.MethodInfo> vyvolat, je nutné vytvořit typu vytvořený z definice typu `Sample`. Vytvořený typ používá `Example` třídy, která splňuje požadavky na `TFirst` protože je typu odkazu a má výchozí konstruktor bez parametrů a `ExampleDerived` třídy, který splňuje požadavky omezení na `TSecond`. (Kód pro `ExampleDerived` lze nalézt v ukázkovém kódu.) Tyto dva typy jsou předávány <xref:System.Type.MakeGenericType%2A> vytvoření sestavené typu. <xref:System.Reflection.MethodInfo> Je pak získat pomocí <xref:System.Type.GetMethod%2A> metoda.  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Následující kód vytvoří pole `Example` objektů, umístí tohoto pole v poli typu <xref:System.Object> představující argumenty metoda má být volána a předá je <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> metoda. První argument funkce <xref:System.Reflection.MethodBase.Invoke%2A> metoda je odkaz s hodnotou null, protože je metoda `static`.  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje třídu s názvem `Sample`, spolu s základní třídy a dvě rozhraní. Program definuje dva parametry obecného typu pro `Sample`, zakažte ho do obecného typu. Parametry typu jsou jediné, co provede obecného typu. Program zobrazí to zobrazením testovací zprávu před a po definici parametrů typu.  
  
 Parametr typu `TSecond` slouží k předvedení omezení třídy a rozhraní, pomocí základní třídy a rozhraní a parametr typu `TFirst` slouží k předvedení zvláštní omezení.  
  
 Příklad kódu definuje pole a pomocí parametrů typu třídy pro typ pole a pro parametr metody a návratový typ metody.  
  
 Po `Sample` vytvořil třídy, se vyvolá metoda.  
  
 Program zahrnuje metodu, která jsou uvedeny informace o typu Obecné a metodu, která jsou uvedena zvláštní omezení pro parametr typu. Tyto metody slouží k zobrazení informací o dokončené `Sample` třídy.  
  
 Program uloží modul dokončení na disk jako `GenericEmitExample1.dll`, takže je můžete otevřít [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) a prozkoumat MSIL pro `Sample` třída.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) potřebné pro kompilaci.  
  
-   Nejsou vyžadovány žádné odkazy na další sestavení.  
  
-   Kompilace kódu na příkazovém řádku pomocí csc.exe, vbc.exe nebo cl.exe. Kompilace kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.Emit.GenericTypeParameterBuilder>  
 [Emitování pomocí reflexe](http://msdn.microsoft.com/en-us/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [Emitování dynamických sestavení scénáře reflexe](http://msdn.microsoft.com/en-us/e1cc6750-e20f-473b-bb4e-f43bc66aecce)
