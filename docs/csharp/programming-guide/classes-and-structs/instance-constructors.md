---
title: Instance konstruktory - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 639a0db5bcc5c5b322618ed9119c582374447d34
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979962"
---
# <a name="instance-constructors-c-programming-guide"></a>Konstruktory instancí (Průvodce programováním v C#)
Konstruktory instancí se používají k vytváření a inicializace žádné proměnné členů instance při použití [nové](../../../csharp/language-reference/keywords/new.md) výraz, který se vytvoří objekt [třídy](../../../csharp/language-reference/keywords/class.md). Inicializace [statické](../../../csharp/language-reference/keywords/static.md) třídy nebo statické proměnné v nestatické třídy, je nutné definovat statický konstruktor. Další informace najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 Následující příklad ukazuje konstruktor instance:  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
>  Pro přehlednost Tato třída obsahuje veřejná pole. Použití veřejná pole není doporučený postup programování, protože umožňuje libovolné metody kdekoli v programu neomezený i neověřených přístup k objektu vnitřní fungování. Datové členy obecně by měly být privátní a by měl mít přístup jenom prostřednictvím metody třídy a vlastnosti.  
  
 Tento konstruktor instance je volána pokaždé, když se na základě objektu `Coords` je vytvořená třída. Jako tohoto objektu, která nepřijímá žádné argumenty, se nazývá konstruktor *výchozí konstruktor*. Často je však užitečný k zadání dalších konstruktory. Například můžeme přidat konstruktoru `Coords` třídu, která umožňuje zadat počáteční hodnoty pro datové členy:  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 Díky tomu `Coords` objekty vytvořené pomocí výchozí nebo konkrétní počáteční hodnoty tímto způsobem:  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 Pokud třída nemá konstruktor, výchozí konstruktor není automaticky vygenerován a výchozí hodnoty se používají k inicializaci pole objektů. Například [int](../../../csharp/language-reference/keywords/int.md) je inicializován na hodnotu 0. Další informace o výchozí hodnoty, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md). Proto protože `Coords` výchozí konstruktor třídy inicializuje všechny datové členy na hodnotu nula, je možné odebrat úplně beze změny, jak funguje třídy. V příkladu 1 dále v tomto tématu poskytuje kompletní příklad použití více konstruktorů a příklad o automaticky generovaný konstruktor je k dispozici v příkladu 2.  
  
 Konstruktory instancí lze také volat konstruktor instance základní třídy. Konstruktor třídy lze vyvolat konstruktor základní třídy pomocí inicializátoru, následujícím způsobem:  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 V tomto příkladu `Circle` třídy předá hodnoty představující radius a výšku konstruktoru poskytované `Shape` odkud `Circle` je odvozen. Úplný příklad použití `Shape` a `Circle` se zobrazí v tomto tématu jako příklad 3.  
  
## <a name="example-1"></a>Příklad 1  
 Následující příklad ukazuje třídu s dvěma třídami konstruktory, jeden bez argumentů a druhý se dvěma argumenty.  
  
 [!code-csharp[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a>Příklad 2  
 V tomto příkladu třída `Person` nemá žádné konstruktory, ve kterých případu, výchozí konstruktor je poskytována automaticky a pole jsou inicializovány na výchozích hodnotách.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 Všimněte si, že výchozí hodnota `age` je `0` a výchozí hodnota `name` je `null`. Další informace o výchozí hodnoty, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Příklad 3  
 Následující příklad ukazuje použití inicializátoru pro základní třídu. `Circle` Třídy je odvozen od obecné třídy `Shape`a `Cylinder` je třída odvozena z `Circle` třídy. Konstruktor pro jednotlivé odvozené třídy používá inicializátor její základní třídy.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 Další příklady vyvolání konstruktory základní třídy naleznete v tématu [virtuální](../../../csharp/language-reference/keywords/virtual.md), [přepsat](../../../csharp/language-reference/keywords/override.md), a [základní](../../../csharp/language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [static](../../../csharp/language-reference/keywords/static.md)
