---
title: 'Postupy: Definování a provádění dynamických metod'
description: Viz jak definovat a spouštět dynamické metody v rozhraní .NET. Zobrazení příkladů jednoduché dynamické metody a dynamické metody svázané s instancí třídy.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
ms.openlocfilehash: 7c68be91deb59ea9439e81561f50b7cc40766a45
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865109"
---
# <a name="how-to-define-and-execute-dynamic-methods"></a>Postupy: Definování a provádění dynamických metod
Následující postupy ukazují, jak definovat a spustit jednoduchou dynamickou metodu a dynamickou metodu svázanou s instancí třídy. Další informace o dynamických metodách naleznete v tématu <xref:System.Reflection.Emit.DynamicMethod> třídy a [reflexe emituje dynamické metody](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100)).  
  
### <a name="to-define-and-execute-a-dynamic-method"></a>Definování a spuštění dynamické metody  
  
1. Deklarujte typ delegáta pro provedení metody. Zvažte použití obecného delegáta pro minimalizaci počtu typů delegátů, které je třeba deklarovat. Následující kód deklaruje dva typy delegátů, které lze použít pro `SquareIt` metodu, a jedna z nich je obecná.  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2. Vytvořte pole, které určuje typy parametrů dynamické metody. V tomto příkladu je jediným parametrem `int` ( `Integer` v Visual Basic), takže pole má pouze jeden prvek.  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3. Vytvořte <xref:System.Reflection.Emit.DynamicMethod> . V tomto příkladu je metoda pojmenována `SquareIt` .  
  
    > [!NOTE]
    > Není nutné poskytovat názvy dynamických metod a nemohou být vyvolány podle názvu. Více dynamických metod může mít stejný název. Název se ale zobrazí v zásobníkech volání a může být užitečný pro ladění.  
  
     Typ návratové hodnoty je zadán jako `long` . Metoda je přidružena k modulu, který obsahuje `Example` třídu, která obsahuje vzorový kód. Je možné zadat libovolný načtený modul. Dynamická metoda funguje jako metoda na úrovni modulu `static` ( `Shared` v Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4. Vygeneruje tělo metody. V tomto příkladu <xref:System.Reflection.Emit.ILGenerator> je objekt použit k vygenerování jazyka MSIL (Microsoft Intermediate Language). Alternativně <xref:System.Reflection.Emit.DynamicILInfo> lze objekt použít ve spojení s nespravovanými generátory kódu k vygenerování těla metody pro <xref:System.Reflection.Emit.DynamicMethod> .  
  
     Jazyk MSIL v tomto příkladu načte argument, který je typu `int` , do zásobníku, převede ho na `long` , duplikuje `long` a vynásobí dvě čísla. Tím se v zásobníku ponechá čtvercový výsledek a všechny metody, které je potřeba provést, se vrátí.  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5. Vytvořte instanci delegáta (deklarovaná v kroku 1), která představuje dynamickou metodu voláním <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody. Vytvořením delegáta dokončí metodu a všechny další pokusy o změnu metody – například přidávání dalších MSIL – jsou ignorovány. Následující kód vytvoří delegáta a vyvolá jej pomocí obecného delegáta.  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a>Chcete-li definovat a spustit dynamickou metodu, která je svázána s objektem  
  
1. Deklarujte typ delegáta pro provedení metody. Zvažte použití obecného delegáta pro minimalizaci počtu typů delegátů, které je třeba deklarovat. Následující kód deklaruje typ obecného delegáta, který lze použít k provedení libovolné metody s jedním parametrem a návratovou hodnotou, nebo metody se dvěma parametry a návratovou hodnotou, pokud je delegát svázán s objektem.  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2. Vytvořte pole, které určuje typy parametrů dynamické metody. Pokud je delegát představující metodu svázán s objektem, první parametr musí odpovídat typu, ke kterému je delegát vázán. V tomto příkladu jsou dva parametry typu `Example` a typu `int` ( `Integer` v Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3. Vytvořte <xref:System.Reflection.Emit.DynamicMethod> . V tomto příkladu metoda nemá žádný název. Typ návratové hodnoty je zadán jako `int` ( `Integer` v Visual Basic). Metoda má přístup k soukromým a chráněným členům `Example` třídy.  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4. Vygeneruje tělo metody. V tomto příkladu <xref:System.Reflection.Emit.ILGenerator> je objekt použit k vygenerování jazyka MSIL (Microsoft Intermediate Language). Alternativně <xref:System.Reflection.Emit.DynamicILInfo> lze objekt použít ve spojení s nespravovanými generátory kódu k vygenerování těla metody pro <xref:System.Reflection.Emit.DynamicMethod> .  
  
     Jazyk MSIL v tomto příkladu načte první argument, který je instancí `Example` třídy, a použije jej k načtení hodnoty soukromého pole instance typu `int` . Načte se druhý argument a vynásobí se dvě čísla. Pokud je výsledek větší než `int` , hodnota se zkrátí a nejvýznamnější bity se zahodí. Metoda se vrátí s návratovou hodnotou v zásobníku.  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5. Vytvořte instanci delegáta (deklarovaná v kroku 1), která představuje dynamickou metodu voláním <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> přetížení metody. Vytvořením delegáta dokončí metodu a všechny další pokusy o změnu metody – například přidávání dalších MSIL – jsou ignorovány.  
  
    > [!NOTE]
    > Metodu můžete zavolat víckrát, aby bylo možné <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> vytvořit delegáty vázané na jiné instance cílového typu.  
  
     Následující kód sváže metodu s novou instancí `Example` třídy, jejíž pole privátního testu je nastaveno na 42. To znamená, že pokaždé, když je delegát vyvolán, instance `Example` je předána prvnímu parametru metody.  
  
     Delegát `OneParameter` je použit, protože první parametr metody vždy obdrží instanci `Example` . Když je vyvolán delegát, je vyžadován pouze druhý parametr.  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje jednoduchou dynamickou metodu a dynamickou metodu svázanou s instancí třídy.  
  
 Jednoduchá dynamická metoda přijímá jeden argument, 32 celé číslo a vrací 64-bit čtverce z daného celého čísla. K vyvolání metody je použit obecný delegát.  
  
 Druhá dynamická metoda má dva parametry typu `Example` a typu `int` ( `Integer` v Visual Basic). Pokud byla dynamická metoda vytvořena, je svázána s instancí s `Example` použitím obecného delegáta, který má jeden argument typu `int` . Delegát nemá argument typu, `Example` protože první parametr metody vždy obdrží vázanou instanci `Example` . Když je vyvolán delegát, `int` je zadán pouze argument. Tato dynamická metoda přistupuje k soukromému poli `Example` třídy a vrátí součin privátního pole a `int` argumentu.  
  
 Příklad kódu definuje delegáty, které lze použít ke spuštění metod.  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection.Emit.DynamicMethod>
- [Použití generování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Scénáře dynamické metody generování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))
