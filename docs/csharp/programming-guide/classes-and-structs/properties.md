---
title: Vlastnosti – C# Průvodce programováním
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 4f83d574357aa725b955870e3d93aa1f8222723a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714701"
---
# <a name="properties-c-programming-guide"></a>Vlastnosti (Průvodce programováním v C#)

Vlastnost je člen, který poskytuje flexibilní mechanismus pro čtení, zápis nebo výpočet hodnoty soukromého pole. Vlastnosti lze použít, jako by se jedná o veřejné datové členy, ale ve skutečnosti se jedná o speciální metody nazývané *přistupující objekty*. Díky tomu je možné snadno získávat data a pořád podporovat zabezpečení a flexibilitu metod.  

## <a name="properties-overview"></a>Přehled vlastností  
  
- Vlastnosti umožňují třídě zveřejnit veřejný způsob získávání a nastavování hodnot při skrývání implementačního nebo ověřovacího kódu.  
  
- Přístup k vlastnosti [Get](../../language-reference/keywords/get.md) se používá k vrácení hodnoty vlastnosti a k přiřazení nové hodnoty se používá přístupový objekt vlastnosti [sady](../../language-reference/keywords/set.md) . Tyto přístupové objekty mohou mít různé úrovně přístupu. Další informace najdete v tématu [Omezení přístupnosti přístupového objektu](./restricting-accessor-accessibility.md).  
  
- Klíčové slovo [Value](../../language-reference/keywords/value.md) slouží k definování hodnoty přidělené přístupovým objektem `set`.  
- Vlastnosti mohou být *pro čtení i zápis* (mají `get` a přistupující objekt `set`), *jen pro čtení* (mají přístup s `get`, ale žádné `set` přistupující objekty) nebo jen pro *zápis* (mají přístup k `set`, ale žádný `get` přistupující objekt). Vlastnosti jen pro zápis jsou vzácné a nejčastěji se používají k omezení přístupu k citlivým datům.

- Jednoduché vlastnosti, které nevyžadují žádný vlastní přistupující kód, se dají implementovat buď jako definice těla výrazu, nebo jako [automaticky implementované vlastnosti](./auto-implemented-properties.md).
 
## <a name="properties-with-backing-fields"></a>Vlastnosti s zálohovanými poli

Jeden základní vzor pro implementaci vlastnosti zahrnuje použití privátního zálohovacího pole pro nastavení a načtení hodnoty vlastnosti. Přistupující objekt `get` vrací hodnotu soukromého pole a přístupový objekt `set` může před přiřazením hodnoty k soukromému poli provádět nějaká ověření dat. Oba přistupující objekty mohou také provést nějaký převod nebo výpočet dat před uložením nebo vrácením.

Následující příklad znázorňuje tento model. V tomto příkladu třída `TimePeriod` představuje časový interval. Interně Třída ukládá časový interval v sekundách v soukromém poli s názvem `_seconds`. Vlastnost pro čtení i zápis s názvem `Hours` umožňuje zákazníkovi zadat časový interval v hodinách. `get` i přístupové objekty `set` provádějí potřebný převod mezi hodinami a sekundami. Kromě toho přistupující objekt `set` ověří data a vyvolá <xref:System.ArgumentOutOfRangeException>, pokud je počet hodin neplatný. 
   
 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Definice textu výrazu  

 Přistupující objekty vlastnosti se často skládají z jednoduchých příkazů, které pouze přiřadí nebo vracejí výsledek výrazu. Tyto vlastnosti můžete implementovat jako členy Expression-těle. Definice těla výrazu se skládají z `=>` symbol následovaný výrazem, který se má přiřadit nebo načíst z vlastnosti.

 Počínaje C# 6, vlastnosti jen pro čtení můžou implementovat přistupující objekt `get` jako člen těle výrazu. V takovém případě se nepoužije klíčové slovo přistupující objektu `get` ani klíčové slovo `return`. Následující příklad implementuje vlastnost `Name` jen pro čtení jako člen Expression-těle.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 Počínaje C# 7,0, `get` i přistupující objekt `set` lze implementovat jako členy Expression-těle. V takovém případě musí být k dispozici klíčová slova `get` a `set`. Následující příklad ilustruje použití definice textu výrazu pro přistupující objekty. Všimněte si, že klíčové slovo `return` se u přístupového objektu `get` nepoužívá.
 
  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Automaticky implementované vlastnosti

V některých případech vlastnosti `get` a přistupující objekty `set` přiřadí hodnotu k nebo načtou hodnotu z pole pro zálohování bez zahrnutí další logiky. Pomocí automaticky implementovaných vlastností můžete zjednodušit kód, zatímco C# kompilátor transparentně poskytuje pole pro zálohování. 

Pokud má vlastnost `get` i přistupující objekt `set`, musí být oba implementovány automaticky. Automaticky implementovanou vlastnost definujete pomocí klíčového slova `get` a `set`, aniž by byla zajištěna implementace. Následující příklad opakuje předchozí s tím rozdílem, že `Name` a `Price` jsou automaticky implementované vlastnosti. Všimněte si, že tento příklad také odebere parametrizovaný konstruktor, takže `SaleItem` objekty jsou nyní inicializovány s voláním konstruktoru bez parametrů a [inicializátoru objektu](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Související oddíly  
  
- [Použití vlastností](./using-properties.md)  
  
- [Vlastnosti rozhraní](./interface-properties.md)  
  
- [Porovnání mezi vlastnostmi a indexery](../indexers/comparison-between-properties-and-indexers.md)  
  
- [Omezení přístupnosti přístupového objektu](./restricting-accessor-accessibility.md)  
  
- [Automaticky implementované vlastnosti](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>C# – jazyková specifikace  

Další informace najdete v tématu [vlastnosti](~/_csharplang/spec/classes.md#properties) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Použití vlastností](./using-properties.md)
- [Indexery](../indexers/index.md)
- [získat klíčové slovo](../../language-reference/keywords/get.md)
- [Set – klíčové slovo](../../language-reference/keywords/set.md)
