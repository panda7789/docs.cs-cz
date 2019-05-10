---
title: 'Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 949760026bc965fbb9a94d1f40eb0996a1ce7e92
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592386"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe
Získat informace o obecných typů stejným způsobem jako informace o ostatních typech: prozkoumáním <xref:System.Type> objekt, který reprezentuje obecného typu. Hlavní rozdíl je, že obecný typ obsahuje seznam <xref:System.Type> reprezentují jeho parametry obecného typu. První postup v této části prozkoumá obecných typů.  
  
 Můžete vytvořit <xref:System.Type> objekt, který reprezentuje konstruovaný typ argumenty typu vazby parametrů typu v definici obecného typu. Druhý postup ukazuje to.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>Prozkoumat obecného typu a jeho parametry typu  
  
1. Získat instanci <xref:System.Type> , která představuje obecného typu. V následujícím kódu je získat pomocí typu C# `typeof` – operátor (`GetType` v jazyce Visual Basic `typeid` v jazyce Visual C++). Najdete v článku <xref:System.Type> tématu třídy pro další způsoby, jak získat <xref:System.Type> objektu. Všimněte si, že ve zbývající části tohoto postupu, je typ obsažen v parametru metody s názvem `t`.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. Použít <xref:System.Type.IsGenericType%2A> vlastnosti k určení, zda je typ obecný a použít <xref:System.Type.IsGenericTypeDefinition%2A> a určí, zda je typ definice obecného typu.  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. Získat pole obsahující argumenty obecného typu, pomocí <xref:System.Type.GetGenericArguments%2A> metody.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. Pro každý typ argumentu, určete, zda je parametr typu (například v definici obecného typu) nebo typ, který se zadal pro parametr typu (například v konstruovaný typ), pomocí <xref:System.Type.IsGenericParameter%2A> vlastnost.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. V systému typů, parametr obecného typu je reprezentována instance <xref:System.Type>, stejně jako běžné typy. Následující kód zobrazí název a parametru umístění <xref:System.Type> objekt, který reprezentuje parametr obecného typu. Pozice parametru je triviální informace. je důležitější, když zkoumáte parametr typu, který se použil jako argument typu jiným obecným typem.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. Určit základní typ omezení a interface omezení parametru obecného typu pomocí <xref:System.Type.GetGenericParameterConstraints%2A> metodu k získání všech omezení jedno pole. Omezení nemusí být v libovolném pořadí.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. Použití <xref:System.Type.GenericParameterAttributes%2A> vlastnost ke zjištění zvláštní omezení pro parametr typu, třeba vyžadovat, aby být odkazovým typem. Vlastnost také obsahuje hodnoty, které představují odchylku, což může zastínit vypnout, jak je znázorněno v následujícím kódu.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. Atributy zvláštní omezení jsou příznaky a stejný příznak (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>), která představuje žádné zvláštní omezení taky představuje žádné kovariance a kontravariance. Díky tomu se k otestování pro některý z těchto podmínek je nutné použít odpovídající masku. V takovém případě použijte <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> izolovat příznaky zvláštní omezení.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Vytváření Instance obecného typu  
 Obecný typ je jako šablonu. Nelze vytvořit instance ji, pokud neurčíte skutečné typy pro parametry obecného typu. Chcete-li to provést v době běhu pomocí reflexe, vyžaduje <xref:System.Type.MakeGenericType%2A> metody.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>K vytvoření instance obecného typu  
  
1. Získání <xref:System.Type> objekt, který reprezentuje obecného typu. Následující kód načte obecného typu <xref:System.Collections.Generic.Dictionary%602> dvěma různými způsoby: pomocí <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> přetížení metody řetězec, který popisuje typ a ve volání <xref:System.Type.GetGenericTypeDefinition%2A> metodu na konstruovaný typ `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` v Visual Basic). <xref:System.Type.MakeGenericType%2A> Metoda vyžaduje definici obecného typu.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. Vytvoření pole argumentů typu pro nahrazení pro parametry typu. Pole musí obsahovat správný počet <xref:System.Type> objekty ve stejném pořadí, jak se objeví v seznamu parametrů typu. V takovém případě klíč (první parametr typu) je typu <xref:System.String>, a hodnoty ve slovníku jsou instance třídy s názvem `Example`.  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. Volání <xref:System.Type.MakeGenericType%2A> způsob svázání parametrů typu argumentů typu a vytvořit tento typ.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. Použití <xref:System.Activator.CreateInstance%28System.Type%29> přetížení metody pro vytvoření objektu konstruovaný typ. Následující kód obsahuje dvě instance `Example` třídy ve výsledné `Dictionary<String, Example>` objektu.  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje `DisplayGenericType` metoda k prozkoumání definice obecného typu a typy konstrukcí používá v kódu a zobrazit jejich informace. `DisplayGenericType` Metoda ukazuje způsob použití <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, a <xref:System.Type.GenericParameterPosition%2A> vlastnosti a <xref:System.Type.GetGenericArguments%2A> metoda.  
  
 Příklad také definuje `DisplayGenericParameter` metoda sloužící ke zkoumání parametr obecného typu a zobrazit jeho omezení.  
  
 Příklad kódu definuje sadu typů testů, včetně obecného typu, který znázorňuje omezeními parametrů typů a ukazuje, jak zobrazit informace o těchto typech.  
  
 Tento příklad vytvoří typ z <xref:System.Collections.Generic.Dictionary%602> třídy vytvořením pole argumentů typu a volání <xref:System.Type.MakeGenericType%2A> metody. Porovná program <xref:System.Type> přiřazený objekt vytvořený pomocí <xref:System.Type.MakeGenericType%2A> s <xref:System.Type> objektu pomocí `typeof` (`GetType` v jazyce Visual Basic), představením toho, že jsou stejné. Podobně program používá <xref:System.Type.GetGenericTypeDefinition%2A> metoda získat definici obecných typů konstruovaný typ a porovná ji <xref:System.Type> objekt představující <xref:System.Collections.Generic.Dictionary%602> třídy.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) nezbytné pro kompilaci.  
  
- Nejsou vyžadovány žádné odkazy na další sestavení.  
  
- Kompilace kódu do příkazového řádku pomocí csc.exe a vbc.exe, cl.exe. Ke kompilaci kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [Reflexe a obecné typy](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
- [Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Obecné typy](../../../docs/standard/generics/index.md)
