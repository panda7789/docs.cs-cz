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
ms.openlocfilehash: 473109100c14f26d0e31b9f57513997044c5b2f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676819"
---
# <a name="properties-c-programming-guide"></a>Vlastnosti (Průvodce programováním v C#)

Vlastnost je člen, který poskytuje flexibilní mechanismus pro čtení, zápis nebo vypočítat hodnotu soukromé pole. Vlastnosti lze použít jako v případě, že jsou veřejné datové členy, ale jsou ve skutečnosti speciální volání metody *přistupující objekty*. Díky tomu dat snadno přístupná a přesto pomáhá zvýšit úroveň zabezpečení a flexibilita z metod.  

## <a name="properties-overview"></a>Přehled vlastností  
  
- Vlastnosti umožňují třídám vystavit veřejný způsob získání a nastavení hodnoty, při skrytí implementace nebo ověřovací kód.  
  
- A [získat](../../../csharp/language-reference/keywords/get.md) přistupující objekt vlastnosti se používá k vrácení hodnoty vlastnosti a [nastavit](../../../csharp/language-reference/keywords/set.md) přistupující objekt vlastnosti slouží k přiřazení nové hodnoty. Tyto přístupové objekty může mít různé úrovně přístupu. Další informace najdete v tématu [omezení přístupnosti přístupového objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
- [Hodnotu](../../../csharp/language-reference/keywords/value.md) – klíčové slovo se používá k definování přiřazené podle hodnoty `set` přistupujícího objektu.  
- Vlastnosti mohou být *čtení a zápis* (mají obě `get` a `set` přístupového objektu), *jen pro čtení* (mají `get` přístupový objekt, ale ne `set` přístupového objektu), nebo *jen pro zápis* (mají `set` přístupový objekt, ale ne `get` přistupující objekt). Vlastnosti jen pro zápis se vyskytují jen vzácně a jsou obvykle používány k omezení přístupu k citlivým datům.

- Jednoduché vlastnosti, které vyžadují žádný kód vlastního přistupujícího objektu dá implementovat buď jako definice těla výrazu, nebo jako [automaticky implementované vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).
 
## <a name="properties-with-backing-fields"></a>Vlastnosti s pomocná pole

Jeden základní vzor pro implementování vlastnost zahrnuje použití privátní pomocné pole pro nastavení nebo načtení hodnoty vlastnosti. `get` Přistupující objekt vrací hodnotu soukromé pole a `set` přistupující objekt může provádět některé ověřování dat před přiřazením hodnoty na soukromé pole. Oba přístupové objekty mohou také provádět některé převodu nebo výpočet data předtím, než je uložen nebo vrácena.

Následující příklad ukazuje tento model. V tomto příkladu `TimePeriod` třída představuje časový interval. Interně třídy ukládá časový interval v sekundách v soukromé pole s názvem `_seconds`. Čtení a zápis vlastnost s názvem `Hours` umožňuje zákazníkům určit časový interval v hodinách. Jak `get` a `set` přistupující objekty provést nezbytné převod mezi hodiny a sekundy. Kromě toho `set` přistupující k ověření dat a vyvolá <xref:System.ArgumentOutOfRangeException> Pokud počet hodin je neplatný. 
   
 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Definice textu výrazu  

 Přistupující objekty vlastnosti se často skládají jedním řádkem příkazů, které právě přiřadit nebo vrátí výsledek výrazu. Tyto vlastnosti můžete implementovat jako členy s výrazem v těle. Definice těla výrazu se skládají z `=>` symbol následovaný výraz, který má přiřadit nebo načíst z vlastnosti.

 Od verze C# 6, může implementovat vlastnosti jen pro čtení `get` přístupového objektu jako člena s výrazem v těle. V tomto případě, ani `get` – klíčové slovo přistupující objekt ani `return` – klíčové slovo se používá. Následující příklad implementuje jen pro čtení `Name` vlastnost jako člena s výrazem v těle.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 Od verze C# 7.0, jak `get` a `set` přístupový objekt je možné implementovat jako členy s výrazem v těle. V takovém případě `get` a `set` klíčová slova musí být k dispozici. Následující příklad ukazuje použití definice těla výrazu pro oba přistupující objekty. Všimněte si, že `return` – klíčové slovo se nepoužívá `get` přistupujícího objektu.
 
  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Automaticky implementované vlastnosti

V některých případech vlastnost `get` a `set` přistupující objekty pouze přiřadit hodnotu nebo načíst hodnotu z pole zálohování bez jakékoli další logiky. Pomocí automaticky implementovaných vlastností můžete zjednodušit kód přitom má kompilátor jazyka C# transparentně poskytují pole zálohování za vás. 

Pokud je vlastnost i `get` a `set` přístupový objekt, musí být automaticky implementované. Můžete definovat automaticky implementovanou vlastnost s použitím `get` a `set` klíčových slov bez zadání žádnou implementaci. V následujícím příkladu se opakuje předchozímu, s výjimkou, že `Name` a `Price` jsou automaticky implementované vlastnosti. Všimněte si, že v příkladu také odebere Parametrizovaný konstruktor, tak, aby `SaleItem` objekty se teď inicializují pomocí volání výchozího konstruktoru a [objektu inicializátoru](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Související oddíly  
  
-   [Použití vlastností](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Vlastnosti rozhraní](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Porovnání mezi vlastnostmi a indexery](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Omezení přístupnosti přístupového objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [Automaticky implementované vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [vlastnosti](~/_csharplang/spec/classes.md#properties) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Použití vlastností](../../../csharp/programming-guide/classes-and-structs/using-properties.md)
- [Indexery](../../../csharp/programming-guide/indexers/index.md)
- [Get – klíčové slovo](../../../csharp/language-reference/keywords/get.md)
- [set keyword](../../../csharp/language-reference/keywords/set.md)
