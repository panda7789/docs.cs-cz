---
title: Postup přidání vlastních metod pro dotazy LINQ (C#)
description: Naučte se rozšířit syntaxi dotazů LINQ přidáním rozšiřujících metod do <T> rozhraní IEnumerable v jazyce C#.
ms.date: 08/26/2020
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 768882fce40a2fc6e018f24c8928341e7c65bc4b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122422"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Postup přidání vlastních metod pro dotazy LINQ (C#)

Můžete rozšířit sadu metod, které používáte pro dotazy LINQ přidáním rozšiřujících metod do <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Například kromě standardních průměrných nebo maximálních operací můžete vytvořit vlastní agregační metodu pro výpočet jedné hodnoty z sekvence hodnot. Také vytvoříte metodu, která funguje jako vlastní filtr nebo konkrétní transformace dat pro posloupnost hodnot a vrátí novou sekvenci. Příklady takových metod jsou <xref:System.Linq.Enumerable.Distinct%2A> , <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Reverse%2A> .

Když rozšíříte <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete použít vlastní metody na jakoukoli vyčíslitelné kolekci. Další informace naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md).

## <a name="adding-an-aggregate-method"></a>Přidání agregační metody

Agregační metoda vypočítá jednu hodnotu ze sady hodnot. LINQ poskytuje několik agregačních metod, včetně <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Min%2A> a <xref:System.Linq.Enumerable.Max%2A> . Můžete vytvořit vlastní agregační metodu přidáním metody rozšíření do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.

Následující příklad kódu ukazuje, jak vytvořit rozšiřující metodu volanou pro `Median` Výpočet mediánu pro sekvenci čísel typu `double` .

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="LinqExtensionClass":::

Tuto metodu rozšíření pro každou vyčíslitelné kolekci můžete zavolat stejným způsobem jako jiné agregační metody z <xref:System.Collections.Generic.IEnumerable%601> rozhraní.

Následující příklad kódu ukazuje, jak použít `Median` metodu pro pole typu `double` .

:::code language="csharp" source="./snippets/Program.cs" ID="MedianUsage":::

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Přetížení agregované metody pro příjem různých typů

Můžete přetížit agregační metodu tak, aby mohla přijímat sekvence různých typů. Standardní přístup je vytvořit přetížení pro každý typ. Další možností je vytvořit přetížení, které bude přebírat obecný typ a převést jej na konkrétní typ pomocí delegáta. Oba přístupy můžete také kombinovat.

#### <a name="to-create-an-overload-for-each-type"></a>Pro vytvoření přetížení pro každý typ

Můžete vytvořit konkrétní přetížení pro každý typ, který chcete podporovat. Následující příklad kódu ukazuje přetížení `Median` metody pro daný `int` typ.

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="IntOverload":::

Nyní můžete volat `Median` přetížení pro oba `integer` `double` typy a, jak je znázorněno v následujícím kódu:

:::code language="csharp" source="./snippets/Program.cs" ID="OverloadUsage":::

#### <a name="to-create-a-generic-overload"></a>Vytvoření obecného přetížení

Můžete také vytvořit přetížení, které přijímá sekvenci generických objektů. Toto přetížení přebírá jako parametr delegáta a používá ho k převodu sekvence objektů obecného typu na konkrétní typ.

Následující kód ukazuje přetížení `Median` metody, která přebírá <xref:System.Func%602> delegáta jako parametr. Tento delegát přebírá objekt typu Generic Type T a vrátí objekt typu `double` .

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="GenericOverload":::

Nyní můžete zavolat `Median` metodu pro sekvenci objektů libovolného typu. Pokud typ nemá vlastní metodu přetížení, je nutné předat parametr delegáta. V jazyce C# můžete pro tento účel použít výraz lambda. Také v Visual Basic pouze v případě, že použijete `Aggregate` `Group By` klauzuli OR namísto volání metody, můžete předat libovolnou hodnotu nebo výraz, který je v rozsahu této klauzule.

Následující příklad kódu ukazuje, jak zavolat `Median` metodu pro pole celých čísel a pole řetězců. Pro řetězce se počítá medián pro délky řetězců v poli. Příklad ukazuje, jak předat <xref:System.Func%602> parametr delegáta `Median` metodě pro každý případ.

:::code language="csharp" source="./snippets/Program.cs" ID="GenericUsage":::

## <a name="adding-a-method-that-returns-a-sequence"></a>Přidání metody, která vrací sekvenci

Rozhraní můžete roztáhnout <xref:System.Collections.Generic.IEnumerable%601> vlastní metodou dotazu, která vrací sekvenci hodnot. V tomto případě musí metoda vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601> . Tyto metody lze použít k aplikování filtrů nebo transformací dat na sekvenci hodnot.

Následující příklad ukazuje, jak vytvořit rozšiřující metodu s názvem `AlternateElements` , která vrátí všechny ostatní prvky v kolekci počínaje prvním prvkem.

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="SequenceElement":::

Tuto metodu rozšíření můžete zavolat pro všechny vyčíslitelné kolekce stejně, jako byste volali jiné metody z <xref:System.Collections.Generic.IEnumerable%601> rozhraní, jak je znázorněno v následujícím kódu:

:::code language="csharp" source="./snippets/Program.cs" ID="SequenceUsage":::

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic.IEnumerable%601>
- [Metody rozšíření](../../classes-and-structs/extension-methods.md)
