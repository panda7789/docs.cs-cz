---
title: Typy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- value types [C#]
- reference types [C#]
- types [C#]
- C# language, data types
- common type system [C#]
- data types [C#]
- C# language, types
- strong typing [C#]
ms.assetid: f782d7cc-035e-4500-b1b1-36a9881130ad
ms.openlocfilehash: 15f3a774255923aba83f15700540369040c02dcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338715"
---
# <a name="types-c-programming-guide"></a>Typy (Průvodce programováním v C#)
## <a name="types-variables-and-values"></a>Typy, proměnných a hodnot  
 C# je jazyk silného typu. Všechny proměnné a konstanta má typ, stejně jako každý výraz, který se vyhodnotí na hodnotu. Každý podpis metody Určuje typ pro každý vstupní parametr a návratovou hodnotu. Knihovna tříd rozhraní .NET definuje sadu předdefinovaných číselnými typy a také více komplexní typy, které představují širokou škálu Logická konstrukce, jako je například systém souborů, připojení k síti, kolekce a pole objektů a dat. Typické programu v C# používá typy z knihovny tříd a uživatelem definované typy, které model koncepty, které jsou specifické pro program problém domény.  
  
 Informace uložené v typu patří:  
  
-   Prostor úložiště, který vyžaduje proměnné typu.  
  
-   Maximální a minimální hodnoty, které může představovat.  
  
-   Členy (metody, pole, události a tak dále), které obsahuje.  
  
-   Základní typ, který dědí z.  
  
-   Umístění, kde se přidělí paměť pro proměnné v době běhu.  
  
-   Typy operací, které jsou povoleny.  
  
 Kompilátor používá informace o typu a ujistěte se, že jsou všechny operace, které se provádí v kódu *bezpečnost typů*. Například, pokud deklarace proměnné typu [int](../../../csharp/language-reference/keywords/int.md), kompilátor umožňuje dále používat proměnné a operace odčítání. Pokud se pokusíte provést tyto stejné operace v proměnné typu [bool](../../../csharp/language-reference/keywords/bool.md), kompilátor vygeneruje chybu, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideTypes#42](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_1.cs)]  
  
> [!NOTE]
>  Jazyk C a C++ vývojáře, Všimněte si, že v jazyce C#, [bool](../../../csharp/language-reference/keywords/bool.md) není převoditelná na [int](../../../csharp/language-reference/keywords/int.md).  
  
 Kompilátor vloží informace o typu do spustitelného souboru jako metadata. Modul CLR (CLR) používá aby metadata v době běhu k další zajistit bezpečnost typů, při přiděluje a uvolňuje volné paměti.  
  
### <a name="specifying-types-in-variable-declarations"></a>Určení typů v deklarace proměnných  
 Když deklarovat proměnnou nebo konstantní v programu, musíte buď zadat typ, nebo použít [var](../../../csharp/language-reference/keywords/var.md) – klíčové slovo umožníte kompilátoru odvození typu. Následující příklad ukazuje některé deklarace proměnných, které používají integrované číselnými typy a komplexní uživatelem definované typy:  
  
 [!code-csharp[csProgGuideTypes#36](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_2.cs)]  
  
 Typy metoda parametry a návratové hodnoty jsou určené v podpis metody. Následující podpis ukazuje metodu, která vyžaduje [int](../../../csharp/language-reference/keywords/int.md) jako vstupní argument a vrátí řetězec:  
  
 [!code-csharp[csProgGuideTypes#35](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_3.cs)]  
  
 Po je deklarovaná proměnné, nelze ji znovu deklarované s nový typ a nelze přiřadit hodnotu, která není kompatibilní s příslušným deklarovaným typem. Například nelze deklarovat [int](../../../csharp/language-reference/keywords/int.md) a přiřaďte ho logickou hodnotu z [true](../../../csharp/language-reference/keywords/true-literal.md). Hodnoty však můžete převést na jiné typy, např. Pokud jsou přiřazovány nové proměnné nebo předány jako argumenty metoda. A *typ – převod* této nemá příčina ztrátě dat se provádí automaticky kompilátorem. Vyžaduje převod, který může způsobit ztrátu dat *přetypování* ve zdrojovém kódu.  
  
 Další informace najdete v tématu [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="built-in-types"></a>Vestavěné typy  
 C# obsahuje standardní sadu předdefinovaných číselnými typy představují celá čísla, číslo s plovoucí čárkou bodu hodnoty, logické výrazy, textových znaků, desetinná čísla a dalších typů dat. Existují také předdefinované `string` a `object` typy. Tyto jsou k dispozici pro použití v libovolné aplikaci C#. Další informace o předdefinovaných typů najdete v tématu [referenční tabulky pro typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Vlastní typy  
 Můžete použít [struktura](../../../csharp/language-reference/keywords/struct.md), [třída](../../../csharp/language-reference/keywords/class.md), [rozhraní](../../../csharp/language-reference/keywords/interface.md), a [výčtu](../../../csharp/language-reference/keywords/enum.md) konstrukty, které vytvořit vlastní typy. Knihovna tříd rozhraní .NET, samotné je kolekce vlastních typů od společnosti Microsoft, který můžete použít ve svých vlastních aplikacích. Ve výchozím nastavení jsou k dispozici v libovolné aplikaci C# nejčastěji používané typy v knihovně tříd. Jiné jsou k dispozici pouze v případě, že explicitně přidat odkaz na projekt na sestavení, ve kterém jsou definovány. Po kompilátor obsahuje odkaz na sestavení, můžou deklarovat proměnné (a konstanty) z typů deklarované v této sestavě ve zdrojovém kódu. Další informace najdete v tématu [knihovna tříd rozhraní .NET](../../../standard/class-library-overview.md).  
  
## <a name="the-common-type-system"></a>Obecný systém typů  
 Je důležité pochopit dva základní body o systém typů v rozhraní .NET:  
  
-   Podporuje se zásadou dědičnosti. Typy můžete odvozena od ostatních typů názvem *základní typy*. Odvozený typ dědí (s určitými omezeními), metody, vlastnosti a ostatním členům základního typu. Základní typ můžete zase odvozen od jiný typ, ve kterém případ odvozený typ dědí členů oba základní typy v hierarchii dědičnosti. Všechny typy, včetně předdefinovaných číselnými typy, jako například <xref:System.Int32?displayProperty=nameWithType> (C# – klíčové slovo: [int](../../../csharp/language-reference/keywords/int.md)), jsou odvozeny nakonec z jedné základní typ, který je <xref:System.Object?displayProperty=nameWithType> (C# – klíčové slovo: [objekt](../../../csharp/language-reference/keywords/object.md)). Tato hierarchie jednotná typ je volána [obecný systém typů](../../../standard/base-types/common-type-system.md) (STS). Další informace o dědičnosti v jazyce C#, najdete v části [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
-   Každý typ v CTS je definován jako buď *typ hodnoty* nebo *odkazují na typ*. To zahrnuje všechny vlastní typy v knihovně tříd rozhraní .NET a také vlastní uživatelem definované typy. Typy, které se definují pomocí [struktura](../../../csharp/language-reference/keywords/struct.md) – klíčové slovo jsou typy hodnot, jsou předdefinované číselnými typy `structs`. Typy, které se definují pomocí [třída](../../../csharp/language-reference/keywords/class.md) – klíčové slovo je odkaz na typy. Typy odkazů a hodnotových typů mají různá pravidla kompilaci a různé chování v běhu.  
  
 Následující obrázek znázorňuje vztahy mezi typy hodnot a typy odkazů v CTS.  
  
 ![Typy hodnot a typy odkazu](../../../csharp/programming-guide/types/media/valuetypescts.png "ValueTypesCTS")  
Hodnotové nebo odkazové typy v CTS  
  
> [!NOTE]
>  Uvidíte, že nejčastěji používané typy jsou všechny uspořádány do <xref:System> oboru názvů. Obor názvů, ve kterém se nachází typ má však žádný vztah k tom, zda je hodnota typu nebo typu odkazu.  
  
### <a name="value-types"></a>Typy hodnot  
 Typy hodnot odvozena od <xref:System.ValueType?displayProperty=nameWithType>, která je odvozena z <xref:System.Object?displayProperty=nameWithType>. Typy, které jsou odvozeny od <xref:System.ValueType?displayProperty=nameWithType> chovají specifickým v modulu CLR. Hodnota typu proměnné přímo obsahovat jejich hodnoty, které znamená, že je paměť přidělená vložený v jakémkoli kontextu je deklarovaná proměnnou. Neexistuje žádné přidělení haldy samostatný nebo Režijní náklady na shromažďování uvolňování paměti pro typ hodnoty proměnné.  
  
 Existují dvě kategorie typů hodnot: [struktura](../../../csharp/language-reference/keywords/struct.md) a [výčtu](../../../csharp/language-reference/keywords/enum.md).  
  
 Předdefinované číselnými typy jsou struktury a mají vlastnosti a metody, které dostanete:  
  
```csharp  
// Static method on type Byte.  
byte b = Byte.MaxValue;  
```  
  
 Ale deklarace a k nim přiřadíte hodnoty, jako kdyby byly jednoduché typy neagregačními:  
  
```csharp  
byte num = 0xA;  
int i = 5;  
char c = 'Z';  
```  
  
 Typy hodnot jsou *zapečetěné*, což znamená, například, že nelze odvodit typ z <xref:System.Int32?displayProperty=nameWithType>, a nelze definovat struktury dědění z jakékoli uživatelsky definované třídy, nebo struktura, protože struktury může dědit vlastnosti pouze z <xref:System.ValueType?displayProperty=nameWithType> . Struktury však můžete implementovat jednu nebo více rozhraní. Může odevzdat typu Struktura k typu rozhraní; To způsobí, že *zabalení* operace obtékat spravovaná halda struktura uvnitř objekt typu odkaz. Operace zabalení dojít, když na metodu, která přebírá předáte typ hodnoty <xref:System.Object?displayProperty=nameWithType> jako vstupní parametr. Další informace najdete v tématu [zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
 Můžete použít [struktura](../../../csharp/language-reference/keywords/struct.md) – klíčové slovo k vytvoření vlastních typů vlastní hodnotu. Obvykle struktury slouží jako kontejner pro malou sadu související proměnné, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/index_4.cs)]  
  
 Další informace o strukturách najdete v tématu [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md). Další informace o typech hodnota v rozhraní .NET najdete v tématu [typy hodnot](../../../csharp/language-reference/keywords/value-types.md).  
  
 Je kategorie typů hodnot [výčtu](../../../csharp/language-reference/keywords/enum.md). Výčet definuje sadu s názvem celočíselné konstanty. Například <xref:System.IO.FileMode?displayProperty=nameWithType> výčet v knihovně tříd rozhraní .NET obsahuje sadu s názvem konstantní celá čísla, které určují, jak by měla otevřít soubor. Jak je znázorněno v následujícím příkladu je definována:  
 
 [!code-csharp[csProgGuideTypes#44](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_5.cs)]  
  
 `System.IO.FileMode.Create` Konstanta má hodnotu 2. Název však má mnohem větší smysl pro člověka čtení zdrojový kód a z toho důvodu je je vhodnější použít výčty místo konstantní literál čísla. Další informace naleznete v tématu <xref:System.IO.FileMode?displayProperty=nameWithType>.  
  
 Dědí všechny výčty <xref:System.Enum?displayProperty=nameWithType>, který dědí z <xref:System.ValueType?displayProperty=nameWithType>. Všechna pravidla, která se týkají struktury platí také pro výčty. Další informace o výčty najdete v tématu [výčtové typy](../../../csharp/programming-guide/enumeration-types.md).  
  
### <a name="reference-types"></a>Typy odkazů  
 Typ, který je definován jako [třída](../../../csharp/language-reference/keywords/class.md), [delegovat](../../../csharp/language-reference/keywords/delegate.md), pole, nebo [rozhraní](../../../csharp/language-reference/keywords/interface.md) je *odkazují na typ*. Za běhu, když deklarovat proměnnou typu odkaz, proměnná obsahuje hodnotu [null](../../../csharp/language-reference/keywords/null.md) dokud explicitně vytvořit objekt pomocí [nové](../../../csharp/language-reference/keywords/new.md) operátor, nebo ji přiřadit objekt, který byl jinde vytvořené pomocí `new`, jak je znázorněno v následujícím příkladu:
  
```csharp  
MyClass mc = new MyClass();  
MyClass mc2 = mc;  
```  
   Rozhraní musí být inicializován společně s objektu třídy, který implementuje ho. Pokud `MyClass` implementuje `IMyInterface`, vytvořte instanci `IMyInterface` jak je znázorněno v následujícím příkladu:  
  
```csharp  
IMyInterface iface = new MyClass();  
```  
  
 Při vytvoření objektu je paměť přidělená v spravovaná halda a proměnná obsahuje pouze odkaz na objekt umístění. Typy v haldě spravované vyžadují režijní náklady na jejich přidělení i při jsou uvolnit pomocí funkce správy paměti automatické modulu CLR, která se označuje jako *uvolňování paměti*. Ale je také vysoce optimalizovaný uvolňování paměti a ve většině scénářů nevytvoří problémy výkonem. Další informace o uvolňování paměti najdete v tématu [Automatická správa paměti](../../../standard/automatic-memory-management.md).  
  
 Všechna pole jsou odkazové typy, i když jsou jejich elementů typů hodnot. Pole implicitně odvozena od <xref:System.Array?displayProperty=nameWithType> třídy, ale nikoli deklarace a jejich používání s zjednodušenou syntaxi, který je zadán v jazyce C#, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideTypes#45](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_6.cs)]  
  
 Typy odkazů, plně podporovat dědičnosti. Při vytváření třídy lze dědit z jakéhokoli rozhraní nebo třídu, která není definován jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md), a ostatní třídy lze dědit z vaší třídy a přepsat virtuální metody. Další informace o tom, jak vytvořit vlastní třídy najdete v tématu [třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md). Další informace o dědičnosti a virtuální metody najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="types-of-literal-values"></a>Typy hodnot literálu  
 V jazyce C# literálových hodnot z kompilátoru přijímat typu. Můžete určit, jak by měla být zadána číselný literál připojením písmeno na konec číslo. Například k určení, že hodnota 4.56 by měl být považovány za plovoucí desetinné čárky, připojit "f" nebo "F" po číslo: `4.56f`. Pokud je připojen žádný písmeno, kompilátor odvodí typ literál. Další informace o tom, které lze určit typy přípony písmeno, najdete na stránkách odkaz pro jednotlivé typy v [typy hodnot](../../../csharp/language-reference/keywords/value-types.md).  
  
 Protože jsou zadány literály, a všechny typy odvození nakonec z <xref:System.Object?displayProperty=nameWithType>, můžete napsat a kompilace kódu, například následující:  
  
 [!code-csharp[csProgGuideTypes#37](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_7.cs)]  
  
## <a name="generic-types"></a>Obecné typy  
 Typ lze deklarovat s jedním nebo více *parametry typu* slouží jako zástupný symbol pro skutečný typ ( *konkrétní typ*), kód klienta bude poskytovat při vytváření instance typu. Tyto typy jsou označovány jako *obecné typy*. Například typ formátu .NET <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> má jeden parametr typu, který podle konvence je přiřazen název *T*. Při vytváření instance typu, je třeba zadat typ objektů, které bude obsahovat seznam, například řetězec:  
 
```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```
 Použití parametru typu umožňuje opakovaně použít stejnou třídu pro uložení všech typ elementu, aniž by bylo nutné převést každý element na [objekt](../../../csharp/language-reference/keywords/object.md). Obecné třídy kolekcí se nazývají *silného typu kolekce* protože kompilátor zná konkrétní typ elementů kolekci a může vygenerovat chybu v kompilaci v případě, například pokusíte přidat do celéčíslo`stringList` objektu v předchozím příkladu. Další informace najdete v tématu [obecné typy](../../../csharp/programming-guide/generics/index.md).  
  
## <a name="implicit-types-anonymous-types-and-nullable-types"></a>Implicitní typy, anonymní typy a typy podporující hodnoty Null  
 Jak jsme uvedli dříve, můžete implicitně zadat místní proměnné (ale ne členy třídy) pomocí [var](../../../csharp/language-reference/keywords/var.md) – klíčové slovo. Proměnná typu stále obdrží při kompilaci, ale typ zajišťuje kompilátoru. Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 V některých případech je nepraktické vytvoření pojmenovaného typu pro jednoduché sady souvisejících hodnot, které nemáte v úmyslu k uložení nebo předejte mimo hranice metoda. Můžete vytvořit *anonymní typy* pro tento účel. Další informace najdete v tématu [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Typy hodnot obyčejnou nemůže mít hodnotu [null](../../../csharp/language-reference/keywords/null.md). Ale můžete vytvořit typy s možnou hodnotou Null hodnot připojení `?` po typu. Například `int?` je `int` typ, který může mít hodnotu [null](../../../csharp/language-reference/keywords/null.md). V CTS, s možnou hodnotou Null typy jsou instance typu Obecná struktura <xref:System.Nullable%601?displayProperty=nameWithType>. Typy s možnou hodnotou Null jsou zvláště užitečné, když jsou předávání dat do a z databáze, ve kterých může být číselné hodnoty null. Další informace najdete v tématu [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v následujících tématech:  
  
-   [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
  
-   [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
  
-   [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
  
-   [Obecné typy](../../../csharp/programming-guide/generics/index.md)  

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Převod datových typů XML](../../../standard/data/xml/conversion-of-xml-data-types.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)
