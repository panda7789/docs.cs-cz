---
title: "using – příkaz (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fdf37e1bfc57bf850b332f167e57d3e05d23e78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-c-reference"></a>using – příkaz (Referenční dokumentace jazyka C#)
Poskytuje pohodlné syntaxe, které zajišťuje správné použití <xref:System.IDisposable> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití pomocí příkazu.  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.IO.File>a <xref:System.Drawing.Font> jsou příklady spravovaných typů, která přistupují k nespravované prostředky (v této obslužné rutiny souborů případu a kontexty zařízení). Existuje mnoho dalších druhů nespravované prostředky a typů knihovny tříd, které zapouzdřují je. Všechny tyto typy musí implementovat <xref:System.IDisposable> rozhraní.  
  
Po dobu životnosti `IDisposable` objektu je omezený na jednu metodu, musí deklarovat a vytvoří instanci v `using` příkaz. `using` Příkaz volání <xref:System.IDisposable.Dispose%2A> metoda v objektu správným způsobem a (pokud ji používáte jako je uvedené výše) také způsobuje, že samotného se dostala mimo rozsah objektu co nejrychleji <xref:System.IDisposable.Dispose%2A> je volána. V rámci `using` blok, objekt je jen pro čtení a nelze změnit ani znovu přiřazen.  
  
 `using` Příkaz zajistí, že <xref:System.IDisposable.Dispose%2A> je volána, i když dojde k výjimce při volání metody pro objekt. Můžete dosáhnout stejný výsledek vložení objektu do bloku try a pak voláním <xref:System.IDisposable.Dispose%2A> v a nakonec blokovat; ve skutečnosti, jedná se jak `using` příkaz je přeložen kompilátoru. Příklad kódu se dříve zasahuje do následující kód v době kompilace (Všimněte si velmi složené závorky k vytvoření omezeným oborem pro objekt):  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 V může být deklarován více instancí typu `using` příkaz, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 Můžete vytvořit instanci objektu prostředků a pak předejte proměnnou `using` prohlášení, ale to není osvědčený postup. V takovém případě zůstane objekt v oboru řízení odešel `using` blokovat, i když je pravděpodobně nebude mít přístup k jeho nespravovaných prostředků. Jinými slovy ji budou už inicializována plně. Pokud se pokusíte použít objekt mimo `using` blok riziko způsobuje vyvolání výjimky. Z tohoto důvodu je obecně lepší vytvořit instanci objektu v `using` příkaz a omezit její obor `using` bloku.  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
Další informace o uvolnění `IDisposable` objekty, najdete v části [použití objektů implementujících rozhraní IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Using – direktiva](../../../csharp/language-reference/keywords/using-directive.md)  
 [Uvolňování paměti](../../../standard/garbage-collection/index.md)  
 [Použití objektů implementujících rozhraní IDisposable](../../../standard/garbage-collection/using-objects.md)  
 [Rozhraní IDisposable](xref:System.IDisposable)
