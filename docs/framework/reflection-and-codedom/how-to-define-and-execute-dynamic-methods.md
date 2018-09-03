---
title: 'Postupy: Definování a provádění dynamických metod'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 865d9aa6806e00bb9cf7b3991b4f323d361cbb63
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43487455"
---
# <a name="how-to-define-and-execute-dynamic-methods"></a>Postupy: Definování a provádění dynamických metod
Následující postupy ukazují, jak definovat a spustí jednoduchou dynamickou metodu a dynamická metoda svázána s instancí třídy. Další informace o dynamické metody, naleznete v tématu <xref:System.Reflection.Emit.DynamicMethod> třídy a [emitování dynamické metody scénáře reflexe](https://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).  
  
### <a name="to-define-and-execute-a-dynamic-method"></a>Definování a spouštění dynamické – metoda  
  
1.  Deklarujte typ delegáta se vykonat metodu. Zvažte, chcete-li minimalizovat počet typy delegátů, které je potřeba deklarovat pomocí obecného delegáta. Následující kód deklaruje delegáta dva typy, které by mohly být použity `SquareIt` metoda a jeden z nich je obecný.  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  Vytvořte pole, která určuje typy parametrů pro dynamickou metodu. V tomto příkladu je jediným parametrem `int` (`Integer` v jazyce Visual Basic), takže pole obsahuje pouze jeden element.  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  Vytvoření <xref:System.Reflection.Emit.DynamicMethod>. V tomto příkladu je pojmenována metodu `SquareIt`.  
  
    > [!NOTE]
    >  Není nutné pojmenovat dynamických metod a není možné vyvolat podle názvu. Více dynamické metody mohou mít stejný název. Ale název se zobrazí v zásobnících volání a může být užitečné pro ladění.  
  
     Typ vrácené hodnoty je určen jako `long`. Metoda je spojen s modulem, který obsahuje `Example` třídu, která obsahuje příklad kódu. Jakýkoli načíst modul by mohl být specifikován. Dynamická metoda funguje jako úroveň modulu `static` – metoda (`Shared` v jazyce Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  Vygenerování těla metody. V tomto příkladu <xref:System.Reflection.Emit.ILGenerator> objekt se používá ke generování Microsoft intermediate language (MSIL). Můžete také <xref:System.Reflection.Emit.DynamicILInfo> objektu můžete použít ve spojení s nespravovaným kódem generátorů ke generování tělo metody <xref:System.Reflection.Emit.DynamicMethod>.  
  
     Jazyk MSIL v tomto příkladě načte argument, který je `int`, do zásobníku, převede jej na `long`, duplicitní položky `long`a součin dvou čísel. Tak zůstanou ve čtverci výsledek v zásobníku a vše, co tato metoda má udělat je vrácená.  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  Vytvoření instance delegáta (deklaruje se v kroku 1), který představuje dynamickou metodu. voláním <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody. Vytvoření delegáta je metoda dokončena a žádné další pokusy o změnit metodu – například přidat další jazyk MSIL, jsou ignorovány. Následující kód vytvoří delegát a vyvolá, pomocí obecného delegáta.  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a>Definování a spouštění dynamickou metodu, která je vázána na objekt  
  
1.  Deklarujte typ delegáta se vykonat metodu. Zvažte, chcete-li minimalizovat počet typy delegátů, které je potřeba deklarovat pomocí obecného delegáta. Následující kód deklaruje typ obecného delegátu, který je možné spustit libovolnou metodu s jedním parametrem a návratovou hodnotu, nebo metodu se dvěma parametry a návratové hodnoty, když je delegát je vázán na objekt.  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  Vytvořte pole, která určuje typy parametrů pro dynamickou metodu. Pokud delegát představující metodu je vázán na objekt, první parametr musí odpovídat typu, který je vázán na delegáta. V tomto příkladu jsou dva parametry typu `Example` a typ `int` (`Integer` v jazyce Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  Vytvoření <xref:System.Reflection.Emit.DynamicMethod>. V tomto příkladu metoda nemá žádný název. Typ vrácené hodnoty je určen jako `int` (`Integer` v jazyce Visual Basic). Tato metoda má přístup k soukromým a chráněným členům `Example` třídy.  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  Vygenerování těla metody. V tomto příkladu <xref:System.Reflection.Emit.ILGenerator> objekt se používá ke generování Microsoft intermediate language (MSIL). Můžete také <xref:System.Reflection.Emit.DynamicILInfo> objektu můžete použít ve spojení s nespravovaným kódem generátorů ke generování tělo metody <xref:System.Reflection.Emit.DynamicMethod>.  
  
     Jazyk MSIL v tomto příkladě načte první argument, který je instancí nástroje `Example` třídy a použije ho k načtení hodnoty pole soukromé instanci typu `int`. Druhý argument je načten a jsou vynásobí dvě čísla. Pokud je větší než výsledek `int`, je oříznutá hodnota a nejvýznamnější bity se zahodí. Metoda vrátí s návratovou hodnotou v zásobníku.  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  Vytvoření instance delegáta (deklaruje se v kroku 1), který představuje dynamickou metodu. voláním <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> přetížení metody. Vytvoření delegáta je metoda dokončena a žádné další pokusy o změnit metodu – například přidat další jazyk MSIL, jsou ignorovány.  
  
    > [!NOTE]
    >  Můžete volat <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metoda víc než jednou k vytváření delegátů vázán na ostatní instance cílového typu.  
  
     Následující kód vytvoří vazbu metodu na novou instanci třídy `Example` třídy, jehož privátní testovací je nastaveno na 42. To znamená, že pokaždé, když je delegát vyvolán instanci `Example` je předán pro první parametr metody.  
  
     Delegát `OneParameter` se používá, protože první parametr metody vždy přijímá instanci `Example`. Když je vyvolán delegát, pouze druhý parametr je povinný.  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje jednoduchou dynamickou metodu a dynamická metoda svázána s instancí třídy.  
  
 Jednoduchou dynamickou metodu přijímá jeden argument, 32bitové celé číslo a vrátí hodnotu 64-bit druhou mocninu tohoto čísla. Obecný delegát se používá k volání metody.  
  
 Druhý dynamická metoda má dva parametry typu `Example` a typ `int` (`Integer` v jazyce Visual Basic). Po vytvoření dynamické metody je vázán k instanci `Example`, pomocí obecného delegáta, který má jeden argument typu `int`. Delegát nemá argument typu `Example` vzhledem k tomu, že první parametr metody vždy obdrží vázané instanci `Example`. Když je vyvolán delegát, pouze `int` není zadaný argument. Tato dynamická metoda přistupuje k soukromé pole `Example` třídy a vrátí součin soukromé pole a `int` argument.  
  
 Příklad kódu definuje delegáty, které lze použít k provedení metody.  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) nezbytné pro kompilaci.  
  
-   Nejsou vyžadovány žádné odkazy na další sestavení.  
  
-   Kompilace kódu do příkazového řádku pomocí csc.exe a vbc.exe, cl.exe. Ke kompilaci kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [Použití generování reflexe](https://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [Scénáře dynamických metod generování reflexe](https://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
