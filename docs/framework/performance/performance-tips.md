---
title: Tipy pro zvýšení výkonu rozhraní .NET
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0c4177faca86fab9934f1cae57f02f8e42a2ae0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943369"
---
# <a name="net-performance-tips"></a>Tipy pro zvýšení výkonu rozhraní .NET
Pojem *výkon* obecně označuje rychlost spuštění programu. V některých základních pravidlech ve zdrojovém kódu můžete někdy zvýšit rychlost provádění. V některých programech je důležité prozkoumávat kód pečlivě a používat profilery k zajištění co nejrychlejšího provozu. V jiných programech není nutné provádět takovou optimalizaci, protože kód je spuštěný přijatelně rychle při zápisu. V tomto článku jsou uvedené některé běžné oblasti, ve kterých výkon může být zhoršený, a také tipy pro jejich vylepšení a odkazy na další témata týkající se výkonu. Další informace o plánování a měření výkonu najdete v tématu [výkon](../../../docs/framework/performance/index.md) .  
  
## <a name="boxing-and-unboxing"></a>Zabalení a rozbalení  
 Je nejlepší se vyhnout použití typů hodnot v situacích, kdy musí být v krabici vysoký počet, například v neobecných třídách kolekcí, jako je <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Zabalení typů hodnot lze zabránit pomocí obecných kolekcí, jako je například <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Zabalení a rozbalení jsou výpočty náročnými procesy. Pokud je hodnotový typ zabalený, musí být vytvořen zcela nový objekt. To může trvat až 20 krát déle než jednoduché přiřazení odkazu. Při rozbalení může proces přetypování trvat čtyřikrát, pokud je přiřazení. Další informace naleznete v tématu [zabalení a rozbalení](../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Řetězce  
 Když zřetězete velký počet proměnných řetězce, například v těsné smyčce, použijte <xref:System.Text.StringBuilder?displayProperty=nameWithType> místo [](../../csharp/language-reference/operators/addition-operator.md) C# operátoru + nebo operátorů [zřetězení](../../visual-basic/language-reference/operators/concatenation-operators.md)Visual Basic. Další informace najdete v tématu [jak: Zřetězení více řetězců](../../csharp/how-to/concatenate-multiple-strings.md) a [operátorů zřetězení v Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Destruktory  
 Nemusíte používat prázdné destruktory. Pokud třída obsahuje destruktor, je ve frontě Finalize vytvořena položka. Při volání destruktoru je vyvolán systém uvolňování paměti pro zpracování fronty. Pokud je destruktor prázdný, znamená to, že dojde ke ztrátě výkonu. Další informace naleznete v tématu [destruktory](../../csharp/programming-guide/classes-and-structs/destructors.md) a [životnost objektu: Způsob vytváření a zničení](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)objektů.  
  
## <a name="other-resources"></a>Další zdroje  
  
- [Psaní rychlejšího spravovaného kódu: Informace o tom, co všechno stojí](https://go.microsoft.com/fwlink/?LinkId=99294)  
  
- [Vytváření vysoce výkonných spravovaných aplikací: A Primer](https://go.microsoft.com/fwlink/?LinkId=99295)  
  
- [Základní informace o systému uvolňování paměti a Nápověda k výkonu](https://go.microsoft.com/fwlink/?LinkId=99296)  
  
- [Tipy a triky pro výkon v aplikacích .NET](https://go.microsoft.com/fwlink/?LinkId=99297)  

- [Pikantní výkonu Mariani](https://go.microsoft.com/fwlink/?LinkId=115679)  

- [Blog Vance Morrison](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a>Viz také:

- [Výkon](../../../docs/framework/performance/index.md)
- [Průvodce programováním Visual Basic](../../visual-basic/programming-guide/index.md)
- [Průvodce programováním v jazyce C#](../../csharp/programming-guide/index.md)
