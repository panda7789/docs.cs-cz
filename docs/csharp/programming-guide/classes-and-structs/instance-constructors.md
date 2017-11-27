---
title: "Konstruktory instancí (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: efb82128ffc27a7c065d2ba12bfc08396d3b5cf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="instance-constructors-c-programming-guide"></a>Konstruktory instancí (Průvodce programováním v C#)
Konstruktory instancí se používají k vytvoření a inicializace žádné proměnné členů instance při použití [nové](../../../csharp/language-reference/keywords/new.md) výraz, který se vytvořit objekt [třída](../../../csharp/language-reference/keywords/class.md). K chybě při inicializaci [statické](../../../csharp/language-reference/keywords/static.md) třídu nebo statické proměnné v třídě nestatické, je nutné definovat statického konstruktoru. Další informace najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 Následující příklad ukazuje konstruktoru instance:  
  
 [!code-csharp[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  Pro přehlednost Tato třída obsahuje veřejná pole. Použití veřejná pole není doporučený postup programování, protože umožňuje libovolné metody kdekoli v programu neomezený a neověřených přístup k objektu vnitřního chodu. Datové členy obecně by měly být privátní a by měly být dostupné pouze prostřednictvím metody třídy a vlastnosti.  
  
 Tento konstruktor instance je volána, když na základě objektu `CoOrds` vytvořit třídu. Konstruktor jako tento jeden, které nepřijímá žádné argumenty, se nazývá *výchozí konstruktor*. Často je však vhodné, když poskytují další konstruktory. Například nyní můžete přidat konstruktor k `CoOrds` třídu, která umožňuje zadat počáteční hodnoty pro datové členy:  
  
 [!code-csharp[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 To umožňuje `CoOrd` objekty, které chcete vytvořit výchozí nebo konkrétní počáteční hodnoty, jako jsou to:  
  
 [!code-csharp[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 Pokud třídu nemá konstruktor, výchozí konstruktor je automaticky vygenerováno a použijí se výchozí hodnoty k chybě při inicializaci pole objektů. Například [int](../../../csharp/language-reference/keywords/int.md) je inicializován na 0. Další informace o výchozí hodnoty, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md). Proto protože `CoOrds` třída výchozí konstruktor inicializuje všechny datové členy na nulu, můžete ji úplně odebrat beze změny, jak funguje třídy. Kompletní příklad použití více konstruktorů je uveden v příkladu 1 později v tomto tématu a příklad automaticky generované konstruktor je uvedený v příkladu 2.  
  
 Konstruktory instancí lze také volání konstruktory instancí základní třídy. Konstruktoru třídy můžete vyvolat konstruktor základní třídy pomocí inicializátoru, následujícím způsobem:  
  
 [!code-csharp[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 V tomto příkladu `Circle` třída předá hodnoty představující radius a výšky konstruktoru poskytované `Shape` ze kterého `Circle` je odvozený. Úplný příklad pomocí `Shape` a `Circle` se zobrazí v tomto tématu jako příklad 3.  
  
## <a name="example-1"></a>Příklad 1  
 Následující příklad ukazuje třídu s třída dva konstruktory, jeden bez argumentů a s dva argumenty.  
  
 [!code-csharp[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a>Příklad 2  
 V tomto příkladu třída `Person` nemá žádné konstruktory, ve kterých případě výchozí konstruktor je automaticky poskytnuty a pole jsou inicializovány na výchozí hodnoty.  
  
 [!code-csharp[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 Všimněte si, že na výchozí hodnotu `age` je `0` a výchozí hodnota `name` je `null`. Další informace o výchozí hodnoty, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Příklad 3  
 Následující příklad ukazuje použití inicializátoru základní třídy. `Circle` Třída je odvozena od třídy Obecné `Shape`a `Cylinder` je třída odvozená z `Circle` třídy. Konstruktor na každý odvozená třída používá jeho základní třída inicializátoru.  
  
 [!code-csharp[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 Další příklady vyvolání konstruktory základní třídy, v tématu [virtuální](../../../csharp/language-reference/keywords/virtual.md), [přepsat](../../../csharp/language-reference/keywords/override.md), a [základní](../../../csharp/language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [statické](../../../csharp/language-reference/keywords/static.md)
