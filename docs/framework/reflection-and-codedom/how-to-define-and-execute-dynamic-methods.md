---
title: "Postupy: Definování a provádění dynamických metod"
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
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b7384f625a6d1609294297645bebc335e72d1e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-and-execute-dynamic-methods"></a>Postupy: Definování a provádění dynamických metod
Následující postupy ukazují, jak definovat a provést jednoduchý dynamické metody a dynamické metoda vázaný na instanci třídy. Další informace o dynamických metod najdete v tématu <xref:System.Reflection.Emit.DynamicMethod> třídy a [reflexe Emitování dynamických metoda scénáře](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).  
  
### <a name="to-define-and-execute-a-dynamic-method"></a>K definování a provedení dynamické metody  
  
1.  Deklarace typu delegáta spuštění metody. Zvažte použití obecný delegát minimalizovat počet typů delegáta, které je třeba deklarovat. Následující kód deklaruje dva typy, které by mohly být použity delegovat `SquareIt` metoda a jeden z nich je obecná.  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  Vytvořte pole, které určuje typy parametrů pro metodu dynamické. V tomto příkladu je parametr pouze `int` (`Integer` v jazyce Visual Basic), takže pole má pouze jeden element.  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  Vytvoření <xref:System.Reflection.Emit.DynamicMethod>. V tomto příkladu je název metody `SquareIt`.  
  
    > [!NOTE]
    >  Není nutné poskytnout názvy dynamických metod a nemůže být volána podle názvu. Více dynamických metod může mít stejný název. Ale název se zobrazí v zásobníky volání a může být užitečná pro ladění.  
  
     Typ vrácené hodnoty je zadán jako `long`. Metoda souvisí s modul, který obsahuje `Example` třídy, která obsahuje ukázkový kód. Libovolný načíst modul může být určen. Dynamické metoda funguje jako úroveň modulu `static` – metoda (`Shared` v jazyce Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  Emitování metoda textu. V tomto příkladu <xref:System.Reflection.Emit.ILGenerator> objekt se používá k vydávání Microsoft (MSIL intermediate language). Alternativně <xref:System.Reflection.Emit.DynamicILInfo> objekt můžete použít ve spojení s nespravovaným kódem generátory pro vydávání metoda obsah <xref:System.Reflection.Emit.DynamicMethod>.  
  
     MSIL v tomto příkladu načte argument, který je `int`, do zásobníku, převede ji na `long`, duplicitní položky `long`a vynásobí dvou čísel. Kvadratických výsledek tak zůstane v zásobníku a všechny metody musí provést je návratový.  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  Vytvořte instanci delegáta (deklarované v kroku 1), která představuje dynamické metodu voláním <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metoda. Vytváření delegáta je metoda dokončena a všechny další pokusí změnit metodu – například přidání další MSIL – jsou ignorovány. Následující kód vytvoří delegáta a vyvolá, pomocí obecný delegát.  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a>K definování a provádění dynamických metodu, která je vázána na objekt  
  
1.  Deklarace typu delegáta spuštění metody. Zvažte použití obecný delegát minimalizovat počet typů delegáta, které je třeba deklarovat. Následující kód deklaruje typ obecný delegát, který můžete použít ke spuštění libovolné metody s jeden parametr a návratovou hodnotu, nebo metodu s dva parametry a návratové hodnoty, pokud delegát je vázána na objekt.  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  Vytvořte pole, které určuje typy parametrů pro metodu dynamické. Pokud delegát představující metoda má být vázána na objekt, první parametr musí odpovídat typu, který je vázána delegát. V tomto příkladu jsou dva parametry typu `Example` a typ `int` (`Integer` v jazyce Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  Vytvoření <xref:System.Reflection.Emit.DynamicMethod>. V tomto příkladu metoda nemá žádný název. Typ vrácené hodnoty je zadán jako `int` (`Integer` v jazyce Visual Basic). Metoda má přístup k privátním a chráněné členy `Example` třídy.  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  Emitování metoda textu. V tomto příkladu <xref:System.Reflection.Emit.ILGenerator> objekt se používá k vydávání Microsoft (MSIL intermediate language). Alternativně <xref:System.Reflection.Emit.DynamicILInfo> objekt můžete použít ve spojení s nespravovaným kódem generátory pro vydávání metoda obsah <xref:System.Reflection.Emit.DynamicMethod>.  
  
     MSIL v tomto příkladu načte první argument, což je instance služby `Example` třídy a používá ji načíst hodnotu pole privátní instance typu `int`. Druhý argument je načten a se násobí dvou čísel. Pokud je výsledkem je větší než `int`, se zkrátí hodnota a nejdůležitější bits se zahodí. Metoda vrátí s hodnotou vrácenou v zásobníku.  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  Vytvořte instanci delegáta (deklarované v kroku 1), která představuje dynamické metodu voláním <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> přetížení metody. Vytváření delegáta je metoda dokončena a všechny další pokusí změnit metodu – například přidání další MSIL – jsou ignorovány.  
  
    > [!NOTE]
    >  Můžete volat <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metoda několikrát k vytvoření delegáti vázána na ostatní instance typu cíle.  
  
     Následující kód vytvoří novou instanci třídy vazbu metodu `Example` třídu, jejíž privátní testovací je nastaveno na 42. To znamená, pokaždé, když je delegát vyvolat instanci `Example` předaný první parametr metody.  
  
     Delegát `OneParameter` je použít, protože první parametr metody vždy obdrží instanci `Example`. Po vyvolání delegáta je jenom druhý parametr je povinný.  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje jednoduchý dynamické metody a dynamické metoda vázaný na instanci třídy.  
  
 Jednoduché dynamické metoda přijímá jeden argument, 32bitové celé číslo a vrátí druhou 64-bit této celé číslo. – Obecný delegát se používá k vyvolání metody.  
  
 Druhý dynamické metoda má dva parametry typu `Example` a typ `int` (`Integer` v jazyce Visual Basic). Po vytvoření dynamické metody, je vázána na instanci `Example`, pomocí obecný delegát, který má jeden argument typu `int`. Delegát nemá argument typu `Example` protože první parametr metody vždy obdrží vázané instanci `Example`. Pokud delegát je vyvolána, pouze `int` zadán argument. Tato metoda dynamické přistupuje k privátní pole `Example` třídy a vrátí součin soukromé pole a `int` argument.  
  
 Příklad kódu definuje delegáti, které můžete použít ke spuštění metody.  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) potřebné pro kompilaci.  
  
-   Nejsou vyžadovány žádné odkazy na další sestavení.  
  
-   Kompilace kódu na příkazovém řádku pomocí csc.exe, vbc.exe nebo cl.exe. Kompilace kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [Emitování pomocí reflexe](http://msdn.microsoft.com/en-us/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [Emitování reflexe scénáře dynamické – metoda](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
