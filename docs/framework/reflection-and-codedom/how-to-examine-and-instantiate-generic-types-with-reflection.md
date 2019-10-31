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
ms.openlocfilehash: 62e4e066740d0422f8f7045b043a5725278c209c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130139"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe
Informace o obecných typech jsou získány stejným způsobem jako informace o jiných typech: prozkoumáním <xref:System.Type> objektu, který představuje obecný typ. Hlavní rozdíl je v tom, že obecný typ obsahuje seznam <xref:System.Type> objektů představujících parametry obecného typu. První postup v této části prověřuje obecné typy.  
  
 Můžete vytvořit objekt <xref:System.Type>, který představuje konstruovaný typ pomocí argumentů typu vazby k parametrům typu definice obecného typu. Druhá procedura to demonstruje.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>Kontrola obecného typu a jeho parametrů typu  
  
1. Získat instanci <xref:System.Type>, která představuje obecný typ. V následujícím kódu je typ získán pomocí operátoru C# `typeof` (`GetType` v Visual Basic, `typeid` ve vizuálu C++). Další způsoby, jak získat objekt <xref:System.Type>, naleznete v tématu <xref:System.Type> třídy. Všimněte si, že ve zbývající části tohoto postupu je typ obsažen v parametru metody s názvem `t`.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. Pomocí vlastnosti <xref:System.Type.IsGenericType%2A> určete, zda je typ obecný, a pomocí vlastnosti <xref:System.Type.IsGenericTypeDefinition%2A> určete, zda je typ definice obecného typu.  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. Získejte pole, které obsahuje argumenty obecného typu, pomocí metody <xref:System.Type.GetGenericArguments%2A>.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. Pro každý argument typu určete, zda se jedná o parametr typu (například v definici obecného typu) nebo typ, který byl zadán pro parametr typu (například v konstruovaném typu) pomocí vlastnosti <xref:System.Type.IsGenericParameter%2A>.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. V systému typů je parametr obecného typu reprezentován instancí <xref:System.Type>, stejně jako běžné typy. Následující kód zobrazuje název a umístění parametru objektu <xref:System.Type>, který představuje parametr obecného typu. Pozice parametru je sem triviální informace; je mnohem zajímavější při zkoumání parametru typu, který byl použit jako argument typu jiného obecného typu.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. Určete omezení základního typu a omezení rozhraní parametru obecného typu pomocí metody <xref:System.Type.GetGenericParameterConstraints%2A> pro získání všech omezení v jednom poli. Omezení nejsou zaručena v žádném konkrétním pořadí.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. Použijte vlastnost <xref:System.Type.GenericParameterAttributes%2A> pro zjištění speciálních omezení parametru typu, například vyžadování, že se jedná o typ odkazu. Vlastnost také obsahuje hodnoty, které reprezentují odchylku, které lze odmaskovat, jak je znázorněno v následujícím kódu.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. Speciální atributy omezení jsou příznaky a stejný příznak (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>), který představuje žádná zvláštní omezení, také nepředstavuje žádnou koodchylku nebo kontravariance. Proto je nutné použít k otestování některé z těchto podmínek příslušnou masku. V takovém případě použijte <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> k izolaci speciálních příznaků omezení.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Konstrukce instance obecného typu  
 Obecný typ je jako šablona. Instance se nedají vytvořit, pokud neurčíte reálné typy pro své parametry obecného typu. K tomu v době běhu pomocí reflexe vyžaduje metodu <xref:System.Type.MakeGenericType%2A>.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>Vytvoření instance obecného typu  
  
1. Získat objekt <xref:System.Type>, který představuje obecný typ. Následující kód získá obecný typ <xref:System.Collections.Generic.Dictionary%602> dvěma různými způsoby: pomocí přetížení metody <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> s řetězcem, který popisuje typ a voláním metody <xref:System.Type.GetGenericTypeDefinition%2A> na vytvořeném typu `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic). Metoda <xref:System.Type.MakeGenericType%2A> vyžaduje definici obecného typu.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. Sestavte pole argumentů typu, které mají být nahrazeny parametry typu. Pole musí obsahovat správný počet <xref:System.Type> objektů ve stejném pořadí, v jakém jsou uvedeny v seznamu parametrů typu. V tomto případě je klíč (parametr prvního typu) typu <xref:System.String>a hodnoty ve slovníku jsou instancemi třídy s názvem `Example`.  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. Zavolejte metodu <xref:System.Type.MakeGenericType%2A> pro svázání argumentů typu s parametry typu a vytvořte typ.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. Použijte přetížení metody <xref:System.Activator.CreateInstance%28System.Type%29> k vytvoření objektu konstruovaného typu. Následující kód ukládá dvě instance `Example` třídy ve výsledném objektu `Dictionary<String, Example>`.  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje metodu `DisplayGenericType` pro prohlédnutí definice obecného typu a vytvořené typy používané v kódu a zobrazení jejich informací. Metoda `DisplayGenericType` ukazuje, jak používat vlastnosti <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>a <xref:System.Type.GenericParameterPosition%2A> a metodu <xref:System.Type.GetGenericArguments%2A>.  
  
 V příkladu je také definována metoda `DisplayGenericParameter` pro prověření parametru obecného typu a zobrazení jeho omezení.  
  
 Příklad kódu definuje sadu typů testů, včetně obecného typu, který ilustruje omezení parametrů typu a ukazuje, jak zobrazit informace o těchto typech.  
  
 Příklad vytvoří typ z třídy <xref:System.Collections.Generic.Dictionary%602> vytvořením pole argumentů typu a voláním metody <xref:System.Type.MakeGenericType%2A>. Program porovná objekt <xref:System.Type> vytvořený pomocí <xref:System.Type.MakeGenericType%2A> s objektem <xref:System.Type> získaným pomocí `typeof` (`GetType` v Visual Basic), který demonstruje, že jsou stejné. Podobně program používá metodu <xref:System.Type.GetGenericTypeDefinition%2A> k získání definice obecného typu konstruovaného typu a porovná je s objektem <xref:System.Type> reprezentujícím třídu <xref:System.Collections.Generic.Dictionary%602>.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [Reflexe a obecné typy](reflection-and-generic-types.md)
- [Zobrazení informací o typu](viewing-type-information.md)
- [Obecné typy](../../standard/generics/index.md)
