---
title: Vlastnosti – C# Průvodce programováním
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: dec4d4239fd1a953da6e64a1e1aff9593e2863e2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596150"
---
# <a name="properties-c-programming-guide"></a>Vlastnosti (Průvodce programováním v C#)

Vlastnost je člen, který poskytuje flexibilní mechanismus pro čtení, zápis nebo výpočet hodnoty soukromého pole. Vlastnosti lze použít, jako by se jedná o veřejné datové členy, ale ve skutečnosti se jedná o speciální metody nazývané *přistupující objekty*. Díky tomu je možné snadno získávat data a pořád podporovat zabezpečení a flexibilitu metod.  

## <a name="properties-overview"></a>Přehled vlastností  
  
- Vlastnosti umožňují třídě zveřejnit veřejný způsob získávání a nastavování hodnot při skrývání implementačního nebo ověřovacího kódu.  
  
- Přístup k vlastnosti [Get](../../language-reference/keywords/get.md) se používá k vrácení hodnoty vlastnosti a k přiřazení nové hodnoty se používá přístupový objekt vlastnosti [sady](../../language-reference/keywords/set.md) . Tyto přístupové objekty mohou mít různé úrovně přístupu. Další informace najdete v tématu [Omezení přístupnosti přístupového objektu](./restricting-accessor-accessibility.md).  
  
- Klíčové slovo [Value](../../language-reference/keywords/value.md) slouží k definování hodnoty přidělené `set` přístupovým objektem.  
- Vlastnosti mohou být *určeny pro čtení i zápis* (mají přístup `get` k objektům a i `set` přístup), *jen pro čtení* ( `get` mají přistupující objekt `set` , ale `set` bez přístupového objektu), nebo *jen pro zápis* (mají přistupující objekt, ale `get` bez přístupového objektu). Vlastnosti jen pro zápis jsou vzácné a nejčastěji se používají k omezení přístupu k citlivým datům.

- Jednoduché vlastnosti, které nevyžadují žádný vlastní přistupující kód, se dají implementovat buď jako definice těla výrazu, nebo jako [automaticky implementované vlastnosti](./auto-implemented-properties.md).
 
## <a name="properties-with-backing-fields"></a>Vlastnosti s zálohovanými poli

Jeden základní vzor pro implementaci vlastnosti zahrnuje použití privátního zálohovacího pole pro nastavení a načtení hodnoty vlastnosti. Přistupující objekt vrátí hodnotu soukromého pole `set` a přistupující objekt může provést některá ověření dat před přiřazením hodnoty k soukromému poli. `get` Oba přistupující objekty mohou také provést nějaký převod nebo výpočet dat před uložením nebo vrácením.

Následující příklad znázorňuje tento model. V tomto příkladu `TimePeriod` třída představuje časový interval. Interně Třída ukládá časový interval v sekundách v rámci soukromého pole s názvem `_seconds`. Vlastnost pro čtení i zápis s `Hours` názvem umožňuje zákazníkovi zadat časový interval v hodinách. `get` Ipřistupujícíobjektyprovádějínezbytnýpřevodmezihodinami`set` a sekundami. Kromě toho `set` přistupující objekt ověřuje data a <xref:System.ArgumentOutOfRangeException> vyvolá v případě, že počet hodin je neplatný. 
   
 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Definice textu výrazu  

 Přistupující objekty vlastnosti se často skládají z jednoduchých příkazů, které pouze přiřadí nebo vracejí výsledek výrazu. Tyto vlastnosti můžete implementovat jako členy Expression-těle. Definice textu výrazu se skládají z `=>` symbolu následovaného výrazem, který se má přiřadit nebo načíst z vlastnosti.

 Počínaje C# 6 můžou vlastnosti jen pro čtení implementovat `get` přístup jako člen Expression-těle. V takovém případě `get` se nepoužije klíčové slovo přistupující `return` ani klíčové slovo. Následující příklad implementuje vlastnost jen `Name` pro čtení jako člen Expression-těle.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 Počínaje C# 7,0, jak `get` a `set` přístupovým objektem lze implementovat jako členy Expression-těle. V takovém případě musí `get` být `set` k dispozici klíčová slova a. Následující příklad ilustruje použití definice textu výrazu pro přistupující objekty. Všimněte si, `return` že klíčové slovo se `get` u přístupového objektu nepoužívá.
 
  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Automaticky implementované vlastnosti

V některých případech vlastnosti `get` a `set` přistupující objekty přiřadí hodnotu nebo načítají hodnotu z pole pro zálohování bez zahrnutí další logiky. Pomocí automaticky implementovaných vlastností můžete zjednodušit kód, zatímco C# kompilátor transparentně poskytuje pole pro zálohování. 

Pokud má `get` `set` vlastnost i přístup, musí být oba implementovány automaticky. Automaticky implementovanou vlastnost definujete pomocí `get` klíčových slov a `set` , aniž byste museli poskytovat žádnou implementaci. Následující příklad opakuje předchozí, s tím rozdílem, `Name` že `Price` a jsou automaticky implementované vlastnosti. Všimněte si, že tento příklad také odebere parametrizovaný konstruktor, aby `SaleItem` objekty byly nyní inicializovány s voláním konstruktoru bez parametrů a inicializátoru [objektu](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Související oddíly  
  
- [Použití vlastností](./using-properties.md)  
  
- [Vlastnosti rozhraní](./interface-properties.md)  
  
- [Porovnání mezi vlastnostmi a indexery](../indexers/comparison-between-properties-and-indexers.md)  
  
- [Omezení přístupnosti přístupového objektu](./restricting-accessor-accessibility.md)  
  
- [Automaticky implementované vlastnosti](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [vlastnosti](~/_csharplang/spec/classes.md#properties) ve [ C# specifikaci jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Použití vlastností](./using-properties.md)
- [Indexery](../indexers/index.md)
- [získat klíčové slovo](../../language-reference/keywords/get.md)
- [Set – klíčové slovo](../../language-reference/keywords/set.md)
