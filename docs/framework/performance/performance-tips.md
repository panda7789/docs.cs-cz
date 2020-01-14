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
ms.openlocfilehash: 12e8d9398a1cf76267f4e8441845007da17949cd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937903"
---
# <a name="net-performance-tips"></a>Tipy pro zvýšení výkonu rozhraní .NET
Pojem *výkon* obecně označuje rychlost spuštění programu. V některých základních pravidlech ve zdrojovém kódu můžete někdy zvýšit rychlost provádění. V některých programech je důležité prozkoumávat kód pečlivě a používat profilery k zajištění co nejrychlejšího provozu. V jiných programech není nutné provádět takovou optimalizaci, protože kód je spuštěný přijatelně rychle při zápisu. V tomto článku jsou uvedené některé běžné oblasti, ve kterých výkon může být zhoršený, a také tipy pro jejich vylepšení a odkazy na další témata týkající se výkonu. Další informace o plánování a měření výkonu najdete v tématu [výkon](index.md) .  
  
## <a name="boxing-and-unboxing"></a>Zabalení a rozbalení  
 Je nejvhodnější vyhnout se použití typů hodnot v situacích, kdy musí být zabaleny vysokým počtem, například v neobecných třídách kolekcí, například <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Zabalení typů hodnot se můžete vyhnout pomocí obecných kolekcí, jako je <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Zabalení a rozbalení jsou výpočty náročnými procesy. Pokud je hodnotový typ zabalený, musí být vytvořen zcela nový objekt. To může trvat až 20 krát déle než jednoduché přiřazení odkazu. Při rozbalení může proces přetypování trvat čtyřikrát, pokud je přiřazení. Další informace naleznete v tématu [zabalení a rozbalení](../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Řetězce  
 Když zřetězete velký počet proměnných řetězce, například v těsné smyčce, použijte <xref:System.Text.StringBuilder?displayProperty=nameWithType> namísto C# [operátoru +](../../csharp/language-reference/operators/addition-operator.md) nebo [operátorů zřetězení](../../visual-basic/language-reference/operators/concatenation-operators.md)Visual Basic. Další informace najdete v tématu [zřetězení více řetězců](../../csharp/how-to/concatenate-multiple-strings.md) a [operátorů zřetězení v Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Destruktory  
 Nemusíte používat prázdné destruktory. Pokud třída obsahuje destruktor, je ve frontě Finalize vytvořena položka. Při volání destruktoru je vyvolán systém uvolňování paměti pro zpracování fronty. Pokud je destruktor prázdný, znamená to, že dojde ke ztrátě výkonu. Další informace naleznete v tématu [destruktory](../../csharp/programming-guide/classes-and-structs/destructors.md) a [životnost objektu: jak jsou objekty vytvářeny a zničeny](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Další zdroje  
  
- [Psaní rychlejšího spravovaného kódu: informace o tom, co všechno stojí](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973852(v=msdn.10))  
  
- [Vytváření vysoce výkonných spravovaných aplikací: Úvod](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973858(v=msdn.10))  
  
- [Základní informace o systému uvolňování paměti a Nápověda k výkonu](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973837(v=msdn.10))  
  
- [Tipy a triky pro výkon v aplikacích .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v=msdn.10))  

- [Pikantní výkonu Mariani](https://docs.microsoft.com/archive/blogs/ricom/)  

- [Blog Vance Morrison](https://docs.microsoft.com/archive/blogs/vancem/)
  
## <a name="see-also"></a>Viz také:

- [Výkon](index.md)
- [Průvodce programováním Visual Basic](../../visual-basic/programming-guide/index.md)
- [Průvodce programováním v jazyce C#](../../csharp/programming-guide/index.md)
