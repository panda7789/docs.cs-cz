---
title: "Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe"
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
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc95b8474cdf9398d5b6705cce1b98772e5add98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe
Stejným způsobem jako informace o jiných typech se získat informace o obecných typů: prověřením <xref:System.Type> objekt, který reprezentuje obecného typu. Princip rozdíl je, že obecného typu má seznam <xref:System.Type> objekty, které představují jeho parametry obecného typu. První postup v této části prověří obecné typy.  
  
 Můžete vytvořit <xref:System.Type> objekt, který představuje vytvořený typ pomocí vazby argumenty typu do parametrů definice obecného typu. Druhý postup ukazuje to.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>K prozkoumání obecného typu a jeho parametry typu  
  
1.  Získat instanci <xref:System.Type> představující obecného typu. V následujícím kódu, se získávají pomocí jazyka C# typ `typeof` – operátor (`GetType` v jazyce Visual Basic `typeid` v jazyce Visual C++). Najdete v článku <xref:System.Type> téma třída pro jiné způsoby, jak získat <xref:System.Type> objektu. Všimněte si, že v zbytek tohoto postupu je typ obsažené v metoda parametr s názvem `t`.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2.  Použít <xref:System.Type.IsGenericType%2A> vlastnosti a určit, zda je obecný typ, použijte <xref:System.Type.IsGenericTypeDefinition%2A> vlastnosti k určení, zda je typ definice obecného typu.  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3.  Získat pole, které obsahuje argumenty obecného typu, pomocí <xref:System.Type.GetGenericArguments%2A> metoda.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4.  Pro každý typ argumentu, určují, zda je parametr typu (například v definici obecného typu) nebo typu, který byl zadaný pro parametr typu (například v vytvořený typ), pomocí <xref:System.Type.IsGenericParameter%2A> vlastnost.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5.  V systému typu parametr obecného typu je reprezentována instanci <xref:System.Type>, stejně jako obyčejnou typy. Následující kód zobrazí název a parametru umístění <xref:System.Type> objekt, který reprezentuje parametr obecného typu. Pozice parametr je trivial informace; je důležitější sledovat při kontrole parametr typu, která byla použita jako argument typu jiného obecného typu.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6.  Určit základní typ omezení a omezení rozhraní parametr obecného typu pomocí <xref:System.Type.GetGenericParameterConstraints%2A> metoda získat všechna omezení v jednom poli. Omezení nemusí být v libovolném pořadí.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7.  Použití <xref:System.Type.GenericParameterAttributes%2A> vlastnost ke zjištění zvláštní omezení pro parametr typu, jako je například požadavek, aby byl odkazového typu. Vlastnost také obsahuje hodnoty, které představují odchylku, která můžete vypnout maskování, jak je znázorněno v následujícím kódu.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8.  Atributy speciální omezení jsou příznaky a příznak stejné (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>), která představuje žádné zvláštní omezení také představuje žádné kovariance a kontravariance. Proto k testování pro některá z těchto podmínek je nutné použít příslušné masky. V takovém případě použijte <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> izolovat příznaky zvláštní omezení.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Vytváření instancí obecného typu  
 Obecný typ je jako šablonu. Nelze vytvořit instance ji, pokud nezadáte skutečné typy pro jeho parametry obecného typu. K tomu v době běhu pomocí reflexe, vyžaduje <xref:System.Type.MakeGenericType%2A> metoda.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>K vytvoření instance obecného typu  
  
1.  Získání <xref:System.Type> objekt, který reprezentuje obecného typu. Následující kód získá obecného typu <xref:System.Collections.Generic.Dictionary%602> dvěma různými způsoby: pomocí <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> přetížení metody s řetězec popisující typ a voláním <xref:System.Type.GetGenericTypeDefinition%2A> metoda sestavené typu `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` v Visual Basic). <xref:System.Type.MakeGenericType%2A> Metoda vyžaduje definice obecného typu.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2.  Vytvořte pole argumenty typu nelze nahradit pro parametry typu. Pole musí obsahovat správný počet <xref:System.Type> objekty ve stejném pořadí, jak se zobrazují v seznamu parametrů typu. V tomto případě klíč (první parametr typu) je typu <xref:System.String>, a hodnoty ve slovníku jsou instancemi třídy s názvem `Example`.  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3.  Volání <xref:System.Type.MakeGenericType%2A> metoda svázat argumenty typu do parametrů a vytvořit typ.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4.  Použití <xref:System.Activator.CreateInstance%28System.Type%29> přetížení metody pro vytvoření objektu sestavené typu. Následující kód ukládá dvě instance `Example` třídy v výsledná `Dictionary<String, Example>` objektu.  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje `DisplayGenericType` metoda sloužící ke zkoumání definice obecného typu a sestavené typy používá v kódu a zobrazení jejich informací. `DisplayGenericType` Metoda ukazuje způsob použití <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, a <xref:System.Type.GenericParameterPosition%2A> vlastnosti a <xref:System.Type.GetGenericArguments%2A> metoda.  
  
 Tento příklad také definuje `DisplayGenericParameter` metoda sloužící ke zkoumání parametr obecného typu a zobrazit její omezení.  
  
 Příklad kódu definuje sadu typů testu, včetně obecného typu, který ukazuje parametr omezení typu a ukazuje, jak zobrazit informace o těchto typech.  
  
 Tento příklad vytvoří určitého typu <xref:System.Collections.Generic.Dictionary%602> třída vytvořením pole typu argumentů a volání <xref:System.Type.MakeGenericType%2A> metoda. Program porovná <xref:System.Type> objekt vytvořený <xref:System.Type.MakeGenericType%2A> s <xref:System.Type> objektu získat pomocí `typeof` (`GetType` v jazyce Visual Basic), ukázka, aby byly stejné. Podobně, program používá <xref:System.Type.GetGenericTypeDefinition%2A> metoda získat definice obecného typu sestavené typu a porovná ho k <xref:System.Type> objekt reprezentující <xref:System.Collections.Generic.Dictionary%602> – třída.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) potřebné pro kompilaci.  
  
-   Nejsou vyžadovány žádné odkazy na další sestavení.  
  
-   Kompilace kódu na příkazovém řádku pomocí csc.exe, vbc.exe nebo cl.exe. Kompilace kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Type>  
 <xref:System.Reflection.MethodInfo>  
 [Reflexe a obecné typy](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [Obecné typy](../../../docs/standard/generics/index.md)
