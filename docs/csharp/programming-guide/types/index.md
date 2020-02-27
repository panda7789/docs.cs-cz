---
title: Typy – C# Průvodce programováním
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
ms.openlocfilehash: ade2cba857a1a32039f8fd07881f13f63f0dbe1a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628134"
---
# <a name="types-c-programming-guide"></a>Typy (Průvodce programováním v C#)

## <a name="types-variables-and-values"></a>Typy, proměnné a hodnoty

C#je jazyk silného typu. Každá proměnná a konstanta má typ, stejně jako každý výraz, který je vyhodnocen na hodnotu. Každý podpis metody určuje typ pro každý vstupní parametr a pro návratovou hodnotu. Knihovna tříd .NET definuje sadu předdefinovaných číselných typů i složitější typy, které reprezentují širokou škálu logických konstrukcí, jako je například systém souborů, síťová připojení, kolekce a pole objektů a data. Typický C# program používá typy z knihovny tříd a také uživatelsky definované typy, které modelují koncepty specifické pro doménu problému programu.

Informace uložené v typu mohou zahrnovat následující:

- Prostor úložiště, který proměnná typu vyžaduje.

- Maximální a minimální hodnoty, které může představovat.

- Členové (metody, pole, události atd.), které obsahuje.

- Základní typ, ze kterého dědí.

- Místo, kde bude přidělena paměť pro proměnné v době běhu.

- Druhy operací, které jsou povoleny.

Kompilátor používá informace o typu k ujištění, že všechny operace, které jsou provedeny ve vašem kódu, jsou *typově bezpečné*. Například pokud deklarujete proměnnou typu [int](../../language-reference/builtin-types/integral-numeric-types.md), kompilátor vám umožní použít proměnnou v operaci sčítání a odčítání. Pokud se pokusíte provést stejné operace s proměnnou typu [bool](../../language-reference/builtin-types/bool.md), kompilátor vygeneruje chybu, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideTypes#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#42)]

> [!NOTE]
> C a C++ vývojáři Všimněte si, že C#v není hodnota [bool](../../language-reference/builtin-types/bool.md) převoditelná na [int](../../language-reference/builtin-types/integral-numeric-types.md).

Kompilátor vloží informace o typu do spustitelného souboru jako metadata. Modul CLR (Common Language Runtime) používá tato metadata v době běhu k dalšímu zajištění bezpečnosti typu při přidělování a uvolňování paměti.

### <a name="specifying-types-in-variable-declarations"></a>Určení typů v deklaracích proměnných

Pokud deklarujete proměnnou nebo konstantu v programu, je nutné buď zadat její typ, nebo použít klíčové slovo [var](../../language-reference/keywords/var.md) , aby kompilátor mohl daný typ odvodit. Následující příklad ukazuje některé deklarace proměnných, které používají předdefinované číselné typy a komplexní uživatelsky definované typy:

[!code-csharp[csProgGuideTypes#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#36)]

Typy parametrů metody a návratové hodnoty jsou uvedeny v signatuře metody. Následující signatura ukazuje metodu, která vyžaduje [int](../../language-reference/builtin-types/integral-numeric-types.md) jako vstupní argument a vrací řetězec:

[!code-csharp[csProgGuideTypes#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#35)]

Po deklarování proměnné nemůže být znovu deklarována s novým typem a nelze jí přiřadit hodnotu, která není kompatibilní s deklarovaným typem. Například nelze deklarovat [int](../../language-reference/builtin-types/integral-numeric-types.md) a přiřadit jí logickou hodnotu `true`. Hodnoty lze však převést na jiné typy, například když jsou přiřazeny k novým proměnným nebo předány jako argumenty metody. *Konverze typu* , která nezpůsobí ztrátu dat, je automaticky prováděna kompilátorem. Převod, který může způsobit ztrátu dat, vyžaduje *přetypování* ve zdrojovém kódu.

Další informace naleznete v tématu [přetypování a převody typu](./casting-and-type-conversions.md).

## <a name="built-in-types"></a>Předdefinované typy

C#poskytuje standardní sadu předdefinovaných číselných typů k vyjádření celých čísel, hodnot s plovoucí desetinnou čárkou, logických výrazů, textových znaků, desetinných hodnot a dalších typů dat. K dispozici jsou také předdefinované `string` a `object` typy. Jsou k dispozici pro použití v jakémkoli C# programu. Úplný seznam předdefinovaných typů naleznete v tématu [vestavěné typy](../../language-reference/builtin-types/built-in-types.md).

## <a name="custom-types"></a>Vlastní typy

Použijete konstrukce [struct](../../language-reference/builtin-types/struct.md), [Class](../../language-reference/keywords/class.md), [Interface](../../language-reference/keywords/interface.md)a [Enum](../../language-reference/builtin-types/enum.md) k vytvoření vlastních typů. Samotná knihovna tříd .NET je kolekce vlastních typů poskytovaných Microsoftem, které můžete použít ve svých vlastních aplikacích. Ve výchozím nastavení jsou nejčastěji používané typy v knihovně tříd k dispozici v jakémkoli C# programu. Ostatní budou k dispozici pouze v případě, že explicitně přidáte odkaz na projekt do sestavení, ve kterém jsou definovány. Poté, co má kompilátor odkaz na sestavení, můžete deklarovat proměnné (a konstanty) typů deklarovaných v tomto sestavení ve zdrojovém kódu. Další informace naleznete v tématu [Knihovna tříd .NET](../../../standard/class-library-overview.md).

## <a name="the-common-type-system"></a>Obecný systém typů

Je důležité porozumět dvěma základním bodům o systému typů v .NET:

- Podporuje princip dědičnosti. Typy mohou být odvozeny od jiných typů, které se nazývají *základní typy*. Odvozený typ dědí (s určitými omezeními) metody, vlastnosti a další členy základního typu. Základní typ může být odvozen z jiného typu. v takovém případě odvozený typ dědí členy obou základních typů v rámci své Hierarchie dědičnosti. Všechny typy, včetně předdefinovaných číselných typů, jako je napříkladC# <xref:System.Int32?displayProperty=nameWithType> (klíčové slovo: [int](../../language-reference/builtin-types/integral-numeric-types.md)), jsou odvozeny z jednoho základního typu, kterýC# je <xref:System.Object?displayProperty=nameWithType> (klíčové slovo: [Object](../../language-reference/builtin-types/reference-types.md)). Tato hierarchie sjednoceného typu se nazývá CTS ( [Common Type System](../../../standard/base-types/common-type-system.md) ). Další informace o dědičnosti v C#naleznete v tématu [Dědičnost](../classes-and-structs/inheritance.md).

- Každý typ v CTS je definován buď jako *typ hodnoty* , nebo jako *typ odkazu*. To zahrnuje všechny vlastní typy v knihovně tříd .NET a také vlastní uživatelsky definované typy. Typy, které definujete pomocí klíčového slova [struct](../../language-reference/builtin-types/struct.md) , jsou typy hodnot; všechny předdefinované číselné typy jsou `structs`. Typy, které definujete pomocí klíčového slova [Class](../../language-reference/keywords/class.md) , jsou odkazové typy. Typy odkazů a typy hodnot mají odlišná pravidla kompilace a jiné chování za běhu.

Následující ilustrace znázorňuje vztah mezi typy hodnot a typy odkazů v CTS.

Následující obrázek znázorňuje typy hodnot a typy odkazů v CTS:

![Snímek obrazovky zobrazující typy hodnot CTS a odkazové typy](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> Můžete vidět, že nejčastěji používané typy jsou uspořádány v oboru názvů <xref:System>. Obor názvů, ve kterém je typ obsažen, ale nemá žádný vztah k tomu, zda se jedná o typ hodnoty nebo typ odkazu.

### <a name="value-types"></a>Typy hodnot

Typy hodnot jsou odvozeny z <xref:System.ValueType?displayProperty=nameWithType>, které jsou odvozeny z <xref:System.Object?displayProperty=nameWithType>. Typy, které jsou odvozeny od <xref:System.ValueType?displayProperty=nameWithType> mají zvláštní chování v modulu CLR. Proměnné typu hodnoty přímo obsahují jejich hodnoty, což znamená, že je paměť přidělena vloženému v jakémkoli kontextu, kdy je proměnná deklarována. Neexistuje žádné samostatné přidělení haldy nebo režie uvolňování paměti pro proměnné typu hodnoty.

Existují dvě kategorie typů hodnot: [struct](../../language-reference/builtin-types/struct.md) a [Enum](../../language-reference/builtin-types/enum.md).

Předdefinované číselné typy jsou struktury a mají vlastnosti a metody, ke kterým máte přístup:

```csharp
// Static method on type byte.
byte b = byte.MaxValue;
```

Ale deklarujete a přiřadíte jim hodnoty, jako kdyby byly jednoduché neagregované typy:

```csharp
byte num = 0xA;
int i = 5;
char c = 'Z';
```

Typy hodnot jsou *zapečetěné*, což znamená, že nemůžete odvodit typ z <xref:System.Int32?displayProperty=nameWithType>a nemůžete definovat strukturu, která by dědila z jakékoli uživatelsky definované třídy nebo struktury, protože struktura může dědit pouze z <xref:System.ValueType?displayProperty=nameWithType>. Struktura však může implementovat jedno nebo více rozhraní. Typ struktury můžete přetypovat na libovolný typ rozhraní, který implementuje; To způsobí, že operace *zabalení* zabalí strukturu uvnitř objektu typu reference na spravované haldě. K operacím zabalení dojde, když předáte typ hodnoty metodě, která přijímá <xref:System.Object?displayProperty=nameWithType> nebo libovolný typ rozhraní jako vstupní parametr. Další informace naleznete v tématu [zabalení a rozbalení](./boxing-and-unboxing.md).

Klíčové slovo [struct](../../language-reference/builtin-types/struct.md) můžete použít k vytvoření vlastních typů hodnot. Struktura se obvykle používá jako kontejner pro malou sadu souvisejících proměnných, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Další informace o strukturách naleznete v tématu [structs](../classes-and-structs/structs.md). Další informace o typech hodnot naleznete v tématu [typy hodnot](../../language-reference/builtin-types/value-types.md).

Druhá kategorie typů hodnot je [Enum](../../language-reference/builtin-types/enum.md). Výčet definuje sadu pojmenovaných celočíselných konstant. Například výčet <xref:System.IO.FileMode?displayProperty=nameWithType> v knihovně tříd .NET obsahuje sadu pojmenovaných celých čísel, která určují, jak by měl být soubor otevřen. Je definován tak, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideTypes#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#44)]

`System.IO.FileMode.Create` konstanta má hodnotu 2. Název je však mnohem smysluplnější pro lidi, kteří čtou zdrojový kód, a z tohoto důvodu je lepší používat výčty namísto konstantních literálových čísel. Další informace naleznete v tématu <xref:System.IO.FileMode?displayProperty=nameWithType>.

Všechny výčty dědí z <xref:System.Enum?displayProperty=nameWithType>, které dědí z <xref:System.ValueType?displayProperty=nameWithType>. Všechna pravidla, která platí pro struktury, platí také pro výčty. Další informace o výčtech naleznete v tématu [výčtové typy](../../language-reference/builtin-types/enum.md).

### <a name="reference-types"></a>Odkazové typy

Typ, který je definován jako [Třída](../../language-reference/keywords/class.md), [delegát](../../language-reference/builtin-types/reference-types.md), pole nebo [rozhraní](../../language-reference/keywords/interface.md) , je *odkazový typ*. V době běhu, pokud deklarujete proměnnou typu odkazu, proměnná obsahuje hodnotu [null](../../language-reference/keywords/null.md) , dokud explicitně nevytvoříte objekt pomocí operátoru [New](../../language-reference/operators/new-operator.md) , nebo přiřaďte objekt, který byl vytvořen jinde pomocí `new`, jak je znázorněno v následujícím příkladu:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Rozhraní musí být inicializováno společně s objektem třídy, který jej implementuje. Pokud `MyClass` implementuje `IMyInterface`, vytvoříte instanci `IMyInterface`, jak je znázorněno v následujícím příkladu:

```csharp
IMyInterface iface = new MyClass();
```

Při vytvoření objektu je paměť přidělena spravované haldě a proměnná obsahuje pouze odkaz na umístění objektu. Typy na spravované haldě vyžadují režii při jejich přidělování a v případě, že jsou uvolněny automatickou funkcí správy paměti modulu CLR, která se označuje jako *uvolňování*paměti. Uvolňování paměti je ale také vysoce optimalizované a ve většině scénářů nevytváří problém s výkonem. Další informace o uvolňování paměti najdete v tématu [Automatická správa paměti](../../../standard/automatic-memory-management.md).

Všechna pole jsou odkazové typy, a to i v případě, že jejich prvky jsou typy hodnot. Pole jsou implicitně odvozena od třídy <xref:System.Array?displayProperty=nameWithType>, ale deklarujete je a použijete s zjednodušenou syntaxí, C#která je poskytována, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideTypes#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#45)]

Typy odkazů plně podporují dědičnost. Při vytváření třídy můžete dědit z jakéhokoli jiného rozhraní nebo třídy, která není definována jako [sealed](../../language-reference/keywords/sealed.md), a jiné třídy mohou dědit z vaší třídy a přepsat vaše virtuální metody. Další informace o tom, jak vytvořit vlastní třídy, naleznete v tématu [třídy a struktury](../classes-and-structs/index.md). Další informace o dědičnosti a virtuálních metodách naleznete v tématu [Dědičnost](../classes-and-structs/inheritance.md).

## <a name="types-of-literal-values"></a>Typy hodnot literálů

V C#rozhraní hodnoty literálu obdrží typ z kompilátoru. Můžete určit, jak se má číselný literál zadat připojením písmene ke konci čísla. Například chcete-li určit, že hodnota 4,56 by měla být považována za float, přidejte "f" nebo "F" za číslo: `4.56f`. Pokud není připojeno žádné písmeno, kompilátor odvodí typ literálu. Další informace o tom, které typy lze zadat pomocí přípon písmen, naleznete v části [integrální číselné typy](../../language-reference/builtin-types/integral-numeric-types.md) a [číselné typy s plovoucí desetinnou](../../language-reference/builtin-types/floating-point-numeric-types.md)čárkou.

Vzhledem k tomu, že jsou zadány literály a všechny typy jsou odvozeny od <xref:System.Object?displayProperty=nameWithType>, můžete napsat a zkompilovat kód, například následující:

[!code-csharp[csProgGuideTypes#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#37)]

## <a name="generic-types"></a>Obecné typy

Typ lze deklarovat s jedním nebo více *parametry typu* , které slouží jako zástupný text pro skutečný typ ( *konkrétní typ*), který klientský kód poskytne při vytváření instance typu. Tyto typy se nazývají *Obecné typy*. Například typ .NET <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> má jeden parametr typu, který je podle konvence dán názvem *t*. Při vytváření instance typu zadáte typ objektů, které bude seznam obsahovat, například řetězec:

```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```

Použití parametru typu umožňuje znovu použít stejnou třídu pro uchování libovolného typu elementu, aniž by bylo nutné převést každý prvek na [Object](../../language-reference/builtin-types/reference-types.md). Třídy obecné kolekce se nazývají *kolekce se silnými* typy, protože kompilátor zná konkrétní typ prvků kolekce a může vyvolat chybu v době kompilace, pokud se například pokusíte přidat celé číslo do objektu `stringList` v předchozím příkladu. Další informace najdete v tématu [Obecné typy](../generics/index.md).

## <a name="implicit-types-anonymous-types-and-nullable-value-types"></a>Implicitní typy, anonymní typy a typy hodnot s možnou hodnotou null

Jak bylo uvedeno dříve, můžete implicitně napsat místní proměnnou (ale ne členy třídy) pomocí klíčového slova [var](../../language-reference/keywords/var.md) . Proměnná stále přijímá typ v době kompilace, ale typ je poskytován kompilátorem. Další informace naleznete v tématu [implicitně typované lokální proměnné](../classes-and-structs/implicitly-typed-local-variables.md).

V některých případech je nevhodné vytvořit pojmenovaný typ pro jednoduché sady souvisejících hodnot, které nechcete ukládat nebo předávat mimo hranice metody. Pro tento účel můžete vytvořit *anonymní typy* . Další informace najdete v tématu [anonymní typy](../classes-and-structs/anonymous-types.md).

Typy běžných hodnot nemohou mít hodnotu [null](../../language-reference/keywords/null.md). Můžete však vytvořit typy hodnot s možnou hodnotou null, a to tak, že po typu napřipojíte `?`. Například `int?` je `int` typ, který může mít také hodnotu [null](../../language-reference/keywords/null.md). Typy s možnou hodnotou null jsou instancemi obecného typu struktury <xref:System.Nullable%601?displayProperty=nameWithType>. Typy hodnot s možnou hodnotou null jsou obzvláště užitečné, Pokud předáváte data do a z databází, ve kterých mohou být číselné hodnoty null. Další informace naleznete v tématu [typy hodnot s možnou hodnotou null](../../language-reference/builtin-types/nullable-value-types.md).

## <a name="related-sections"></a>Související oddíly

Další informace najdete v následujících tématech:

- [Přetypování a převody typů](./casting-and-type-conversions.md)

- [Zabalení a rozbalení](./boxing-and-unboxing.md)

- [Použití typu dynamic](./using-type-dynamic.md)

- [Typy hodnot](../../language-reference/builtin-types/value-types.md)

- [Odkazové typy](../../language-reference/keywords/reference-types.md)

- [Třídy a struktury](../classes-and-structs/index.md)

- [Anonymní typy](../classes-and-structs/anonymous-types.md)

- [Obecné typy](../generics/index.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [C#Odkaz](../../language-reference/index.md)
- [Průvodce programováním v C#](../index.md)
- [Převod datových typů XML](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Celočíselné typy](../../language-reference/builtin-types/integral-numeric-types.md)
