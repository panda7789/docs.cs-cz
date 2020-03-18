---
title: Typy – průvodce programováním jazyka C#
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
ms.openlocfilehash: 2fec7b5c36173bf4a99b35cc2bf9e3ca26354a11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399740"
---
# <a name="types-c-programming-guide"></a>Typy (Průvodce programováním v C#)

## <a name="types-variables-and-values"></a>Typy, proměnné a hodnoty

C# je jazyk silného typu. Každá proměnná a konstanta má typ, stejně jako každý výraz, který je vyhodnocen na hodnotu. Každý podpis metody určuje typ pro každý vstupní parametr a pro vrácenou hodnotu. Knihovna tříd .NET definuje sadu předdefinovaných číselných typů a také složitější typy, které představují širokou škálu logických konstrukcí, jako je například systém souborů, síťová připojení, kolekce a pole objektů a data. Typický program jazyka C# používá typy z knihovny tříd, stejně jako uživatelem definované typy, které modelují koncepty, které jsou specifické pro problémovou doménu programu.

Informace uložené v typu mohou zahrnovat následující:

- Úložný prostor, který vyžaduje proměnná typu.

- Maximální a minimální hodnoty, které může představovat.

- Členové (metody, pole, události a tak dále), které obsahuje.

- Základní typ, ze kterých dědí.

- Umístění, kde bude paměť pro proměnné přidělena v době běhu.

- Druhy operací, které jsou povoleny.

Kompilátor používá informace o typu k ujistěte se, že všechny operace, které jsou prováděny ve vašem kódu jsou *typově bezpečné*. Například pokud deklarujete proměnnou typu [int](../../language-reference/builtin-types/integral-numeric-types.md), kompilátor umožňuje použít proměnnou navíc a odčítání operace. Pokud se pokusíte provést stejné operace s proměnnou typu [bool](../../language-reference/builtin-types/bool.md), kompilátor vygeneruje chybu, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideTypes#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#42)]

> [!NOTE]
> C a C++ vývojáři, všimněte si, že v Jazyce C#, [bool](../../language-reference/builtin-types/bool.md) není konvertibilní [int](../../language-reference/builtin-types/integral-numeric-types.md).

Kompilátor vloží informace o typu do spustitelného souboru jako metadata. Modul CLR (COMMON Language runtime) používá tato metadata za běhu k dalšímu zajištění bezpečnosti typů při připřidělování a deklaracích paměti.

### <a name="specifying-types-in-variable-declarations"></a>Určení typů v deklaracích proměnných

Když deklarujete proměnnou nebo konstantu v programu, musíte buď zadat její typ, nebo pomocí klíčového slova [var,](../../language-reference/keywords/var.md) aby kompilátor odvodil typ. Následující příklad ukazuje některé deklarace proměnných, které používají předdefinované číselné typy i složité uživatelem definované typy:

[!code-csharp[csProgGuideTypes#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#36)]

Typy parametrů metody a vrácené hodnoty jsou určeny v podpisu metody. Následující podpis zobrazuje metodu, která vyžaduje [int](../../language-reference/builtin-types/integral-numeric-types.md) jako vstupní argument a vrátí řetězec:

[!code-csharp[csProgGuideTypes#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#35)]

Po deklarování proměnné nelze znovu deklarovat s novým typem a nelze jí přiřadit hodnotu, která není kompatibilní s deklarovaným typem. Například nelze deklarovat [int](../../language-reference/builtin-types/integral-numeric-types.md) a pak mu `true`přiřadit logickou hodnotu . Hodnoty však mohou být převedeny na jiné typy, například když jsou přiřazeny k novým proměnným nebo předány jako argumenty metody. *Převod typu,* který nezpůsobí ztrátu dat, provádí automaticky kompilátor. Převod, který může způsobit ztrátu dat vyžaduje *přetypávání* ve zdrojovém kódu.

Další informace naleznete v [tématu Casting a Typ převody](./casting-and-type-conversions.md).

## <a name="built-in-types"></a>Předdefinované typy

C# poskytuje standardní sadu předdefinovaných číselných typů představujících celá čísla, hodnoty s plovoucí desetinnou čárkou, logické výrazy, textové znaky, desetinné hodnoty a další typy dat. K dispozici jsou `string` také `object` vestavěné a typy. Ty jsou k dispozici pro použití v libovolném programu Jazyka C#. Úplný seznam předdefinovaných typů naleznete [v tématu Předdefinované typy](../../language-reference/builtin-types/built-in-types.md).

## <a name="custom-types"></a>Vlastní typy

Konstrukce [struktury](../../language-reference/builtin-types/struct.md), [třídy](../../language-reference/keywords/class.md), [rozhraní](../../language-reference/keywords/interface.md)a [výčtu](../../language-reference/builtin-types/enum.md) slouží k vytvoření vlastních typů. Samotná knihovna tříd .NET je kolekce vlastních typů poskytovaných společností Microsoft, které můžete použít ve vlastních aplikacích. Ve výchozím nastavení jsou nejčastěji používané typy v knihovně tříd k dispozici v libovolném programu jazyka C#. Jiné budou k dispozici pouze v případě, že explicitně přidáte odkaz na projekt do sestavení, ve kterém jsou definovány. Poté, co kompilátor má odkaz na sestavení, můžete deklarovat proměnné (a konstanty) typů deklarovaných v tomto sestavení ve zdrojovém kódu. Další informace naleznete [v tématu .NET Class Library](../../../standard/class-library-overview.md).

## <a name="the-common-type-system"></a>Společný typový systém

Je důležité pochopit dva základní body o systému typů v rozhraní .NET:

- Podporuje princip dědičnosti. Typy mohou být odvozeny z jiných typů, *nazývaných základní typy*. Odvozený typ dědí (s určitými omezeními) metody, vlastnosti a další členy základního typu. Základní typ může zase odvodit z jiného typu, v takovém případě odvozený typ dědí členy obou základních typů v hierarchii dědičnosti. Všechny typy, včetně předdefinovaných <xref:System.Int32?displayProperty=nameWithType> číselných typů, například (c# klíčové slovo: [int](../../language-reference/builtin-types/integral-numeric-types.md)), nakonec odvodit z jednoho základního typu, který je <xref:System.Object?displayProperty=nameWithType> (C# klíčové slovo: [objekt).](../../language-reference/builtin-types/reference-types.md) Tato jednotná hierarchie typů se nazývá [společný systém typů](../../../standard/base-types/common-type-system.md) (CTS). Další informace o dědičnosti v c# naleznete v [tématu Dědičnost](../classes-and-structs/inheritance.md).

- Každý typ v CTS je definován jako *typ hodnoty* nebo *typ odkazu*. To zahrnuje všechny vlastní typy v knihovně tříd .NET a také vlastní uživatelem definované typy. Typy, které definujete pomocí klíčového slova [strukturovat,](../../language-reference/builtin-types/struct.md) jsou typy hodnot; všechny předdefinované číselné `structs`typy jsou . Typy, které definujete pomocí klíčového slova [třídy,](../../language-reference/keywords/class.md) jsou typy odkazů. Typy odkazů a typy hodnot mají různá pravidla kompilace a různé chování za běhu.

Následující obrázek znázorňuje vztah mezi typy hodnot a typy odkazů v CTS.

Následující obrázek znázorňuje typy hodnot a typy odkazů v CTS:

![Snímek obrazovky s typy hodnot CTS a typy odkazů](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> Můžete vidět, že nejčastěji používané typy jsou <xref:System> uspořádány v oboru názvů. Obor názvů, ve kterém je typ obsažen, však nemá žádný vztah k tomu, zda se jedná o typ hodnoty nebo typ odkazu.

### <a name="value-types"></a>Typy hodnot

Typy hodnot <xref:System.ValueType?displayProperty=nameWithType>jsou odvozeny <xref:System.Object?displayProperty=nameWithType>z , které jsou odvozeny z . Typy, které <xref:System.ValueType?displayProperty=nameWithType> jsou odvozeny z mají zvláštní chování v CLR. Proměnné typu hodnoty přímo obsahují jejich hodnoty, což znamená, že paměť je přidělena v řádku v jakémkoli kontextu, ve kterém je proměnná deklarována. Neexistuje žádná samostatná registrace přidělení nebo ukládání paměti režie pro proměnné typu hodnoty.

Existují dvě kategorie typů hodnot: [struct](../../language-reference/builtin-types/struct.md) a [enum](../../language-reference/builtin-types/enum.md).

Předdefinované číselné typy jsou struktury a mají vlastnosti a metody, ke kterým máte přístup:

```csharp
// Static method on type byte.
byte b = byte.MaxValue;
```

Ale deklarujete a přiřazujete jim hodnoty, jako by se jednalo o jednoduché neagregační typy:

```csharp
byte num = 0xA;
int i = 5;
char c = 'Z';
```

Typy hodnot jsou *zapečetěny*, což například znamená, <xref:System.Int32?displayProperty=nameWithType>že nelze odvodit typ z , a nelze definovat strukturu dědit <xref:System.ValueType?displayProperty=nameWithType>z libovolné uživatelem definované třídy nebo struktury, protože struktura může dědit pouze z . Struktura však můžete implementovat jedno nebo více rozhraní. Struct můžete přetypovat na libovolný typ rozhraní, který implementuje; to *způsobí, že* operace zabalení zabalit strukturu uvnitř objektu typu odkazu na spravované haldy. Zabalení operace dojít, když předáte typ <xref:System.Object?displayProperty=nameWithType> hodnoty na metodu, která trvá nebo jakýkoli typ rozhraní jako vstupní parametr. Další informace naleznete v [tématu Box a rozbalení](./boxing-and-unboxing.md).

Klíčové slovo [strukturování](../../language-reference/builtin-types/struct.md) slouží k vytvoření vlastních typů hodnot. Struktura se obvykle používá jako kontejner pro malou sadu souvisejících proměnných, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Další informace o strukturách naleznete v tématu [Structure types](../../language-reference/builtin-types/struct.md). Další informace o typech hodnot naleznete v [tématu Value types](../../language-reference/builtin-types/value-types.md).

Další kategorie typů hodnot je [výčt .](../../language-reference/builtin-types/enum.md) Výčtu definuje sadu pojmenovaných integrální konstanty. <xref:System.IO.FileMode?displayProperty=nameWithType> Výčet v knihovně tříd .NET například obsahuje sadu pojmenovaných konstantních čísel, která určují, jak má být soubor otevřen. Je definována tak, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideTypes#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#44)]

Konstanta `System.IO.FileMode.Create` má hodnotu 2. Název je však mnohem smysluplnější pro lidi čtení zdrojového kódu a z tohoto důvodu je lepší použít výčty namísto konstantní literál čísla. Další informace naleznete v tématu <xref:System.IO.FileMode?displayProperty=nameWithType>.

Všechny výčty <xref:System.Enum?displayProperty=nameWithType>dědí z <xref:System.ValueType?displayProperty=nameWithType>, který dědí z . Všechna pravidla, která se vztahují na struktury platí také pro výčty. Další informace o výčty naleznete v [tématu Typy výčtů](../../language-reference/builtin-types/enum.md).

### <a name="reference-types"></a>Odkazové typy

Typ, který je definován jako [třída](../../language-reference/keywords/class.md), [delegát](../../language-reference/builtin-types/reference-types.md), pole nebo [rozhraní,](../../language-reference/keywords/interface.md) je *typ odkazu*. Za běhu, když deklarujete proměnnou typu odkazu, proměnná obsahuje hodnotu [null,](../../language-reference/keywords/null.md) dokud explicitně nevytvoříte objekt `new`pomocí [nového](../../language-reference/operators/new-operator.md) operátoru, nebo mu přiřadíte objekt, který byl vytvořen jinde pomocí , jak je znázorněno v následujícím příkladu:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Rozhraní musí být inicializováno společně s objektem třídy, který jej implementuje. Pokud `MyClass` implementuje `IMyInterface`, můžete `IMyInterface` vytvořit instanci, jak je znázorněno v následujícím příkladu:

```csharp
IMyInterface iface = new MyClass();
```

Při vytvoření objektu je paměť přidělena na spravované haldě a proměnná obsahuje pouze odkaz na umístění objektu. Typy na spravované haldy vyžadují režii, jak při přidělení, tak při jejich uvolnění funkcí automatické správy paměti CLR, která je známá jako *uvolňování paměti*. Uvolňování paměti je však také vysoce optimalizované a ve většině scénářů nevytváří problém s výkonem. Další informace o uvolňování paměti naleznete v [tématu Automatická správa paměti](../../../standard/automatic-memory-management.md).

Všechna pole jsou typy odkazů, i v případě, že jejich prvky jsou typy hodnot. Pole implicitně odvozené <xref:System.Array?displayProperty=nameWithType> z třídy, ale deklarovat a používat je se zjednodušenou syntaxi, která je k dispozici C#, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideTypes#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#45)]

Typy odkazů plně podporují dědičnost. Při vytváření třídy můžete dědit z jakéhokoli jiného rozhraní nebo třídy, která není definována jako [zapečetěné](../../language-reference/keywords/sealed.md)a jiné třídy mohou dědit z vaší třídy a přepsat virtuální metody. Další informace o tom, jak vytvořit vlastní třídy, naleznete v [tématu Třídy a structs](../classes-and-structs/index.md). Další informace o dědičnosti a virtuálních metodách naleznete v [tématu Dědičnost](../classes-and-structs/inheritance.md).

## <a name="types-of-literal-values"></a>Typy literálových hodnot

V C# literál hodnoty přijímat typ z kompilátoru. Můžete určit, jak má být číselný literál zadán, připojením dopisu na konec čísla. Chcete-li například určit, že hodnota 4.56 by měla být považována za float, připojit `4.56f`"f" nebo "F" za číslo: . Pokud není připojeno žádné písmeno, kompilátor odvodí typ literálu. Další informace o typech, které lze zadat pomocí přípon s písmeny, naleznete [v tématu Integral numer types](../../language-reference/builtin-types/integral-numeric-types.md) a [Floating-point numeric types](../../language-reference/builtin-types/floating-point-numeric-types.md).

Vzhledem k tomu, že literály jsou <xref:System.Object?displayProperty=nameWithType>zadány a všechny typy jsou nakonec odvozeny z , můžete psát a kompilovat kód, například následující:

[!code-csharp[csProgGuideTypes#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#37)]

## <a name="generic-types"></a>Obecné typy

Typ může být deklarován s jedním nebo více *parametry typu,* které slouží jako zástupný symbol pro skutečný typ *(konkrétní typ),* který klientský kód poskytne při vytvoření instance typu. Tyto typy se nazývají *obecné typy*. Například typ <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> .NET má jeden parametr typu, který podle konvence je uveden název *T*. Při vytváření instance typu určíte typ objektů, které bude seznam obsahovat, například řetězec:

```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```

Použití parametru type umožňuje znovu použít stejnou třídu pro uložení libovolného typu prvku, aniž by bylo nutné převést každý prvek na [objekt](../../language-reference/builtin-types/reference-types.md). Obecné kolekce třídy se nazývají *kolekce silného typu,* protože kompilátor zná konkrétní typ kolekce prvků a může vyvolat chybu v době kompilace, `stringList` pokud se například pokusíte přidat celé číslo k objektu v předchozím příkladu. Další informace naleznete [v tématu Generics](../generics/index.md).

## <a name="implicit-types-anonymous-types-and-nullable-value-types"></a>Implicitní typy, anonymní typy a typy hodnot s možnou hodnotou s hodnotou, jejíž hodnotu lze uvážit

Jak již bylo uvedeno dříve, můžete implicitně zadat místní proměnnou (ale ne členy třídy) pomocí klíčového slova [var.](../../language-reference/keywords/var.md) Proměnná stále přijímá typ v době kompilace, ale typ je poskytován kompilátorem. Další informace naleznete [v tématu Implicitně zadané místní proměnné](../classes-and-structs/implicitly-typed-local-variables.md).

V některých případech je nepohodlné vytvořit pojmenovaný typ pro jednoduché sady souvisejících hodnot, které nemáte v úmyslu ukládat nebo předat mimo hranice metody. Pro tento účel můžete vytvořit *anonymní typy.* Další informace naleznete [v tématu Anonymní typy](../classes-and-structs/anonymous-types.md).

Běžné typy hodnot nemohou mít hodnotu [null](../../language-reference/keywords/null.md). Můžete však vytvořit typy hodnot s `?` možnou hodnotou s možnou hodnotou podle připojení a za typ. Například `int?` je `int` typ, který může mít také hodnotu [null](../../language-reference/keywords/null.md). Typy hodnot s možnou hodnotou null <xref:System.Nullable%601?displayProperty=nameWithType>jsou instance typu obecné struktury . Typy hodnot s možnou hodnotou s hodnotou null jsou užitečné zejména při předávání dat do a z databází, ve kterých mohou být číselné hodnoty null. Další informace naleznete v tématu [Nullable typy hodnot](../../language-reference/builtin-types/nullable-value-types.md).

## <a name="related-sections"></a>Související oddíly

Další informace najdete v následujících tématech:

- [Přetypování a převody typů](./casting-and-type-conversions.md)

- [Zabalení a rozbalení](./boxing-and-unboxing.md)

- [Použití typu dynamic](./using-type-dynamic.md)

- [Typy hodnot](../../language-reference/builtin-types/value-types.md)

- [Odkazové typy](../../language-reference/keywords/reference-types.md)

- [Třídy a struky](../classes-and-structs/index.md)

- [Anonymní typy](../classes-and-structs/anonymous-types.md)

- [Obecné typy](../generics/index.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../../language-reference/index.md)
- [Programovací příručka jazyka C#](../index.md)
- [Převod datových typů XML](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Integrální typy](../../language-reference/builtin-types/integral-numeric-types.md)
