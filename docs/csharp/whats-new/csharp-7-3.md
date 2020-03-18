---
title: Co je nového v C# 7.3
description: Přehled nových funkcí v C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: ba4cea302d91b395e88940d087fcaed306920840
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204557"
---
# <a name="whats-new-in-c-73"></a>Co je nového v C# 7.3

Existují dvě hlavní témata verze Jazyka C# 7.3. Jeden motiv poskytuje funkce, které umožňují bezpečný kód být stejně výkonný jako nebezpečný kód. Druhý motiv poskytuje přírůstková vylepšení existujících funkcí. Kromě toho byly přidány nové možnosti kompilátoru v této verzi.

Následující nové funkce podporují téma lepšího výkonu pro bezpečný kód:

- K pevným polím můžete přistupovat bez připnutí.
- Můžete znovu `ref` přiřadit místní proměnné.
- Inicializátory `stackalloc` můžete použít na polích.
- Příkazy `fixed` můžete použít s libovolným typem, který podporuje vzorek.
- Můžete použít další obecná omezení.

Pro existující funkce byla provedena následující vylepšení:

- Můžete testovat `==` `!=` a s typy řazené kolekce členů.
- Proměnné výrazu můžete použít na více umístěních.
- Atributy můžete připojit k záložnímu poli automaticky implementovaných vlastností.
- Bylo vylepšeno rozlišení `in` metody, pokud se argumenty liší.
- Řešení přetížení má nyní méně nejednoznačných případů.

Nové možnosti kompilátoru jsou:

- `-publicsign`povolení podepisování sestav pomocí softwaru s otevřeným zdrojovým kódem (OSS).
- `-pathmap`pro vytvoření mapování zdrojových adresářů.

Zbývající část tohoto článku obsahuje podrobnosti a odkazy na další informace o každé z vylepšení. Tyto funkce můžete prozkoumat ve `dotnet try` vašem prostředí pomocí globálního nástroje:

1. Nainstalujte globální nástroj [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Klonovat úložiště [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *try-samples.*
1. Spusťte `dotnet try`.

## <a name="enabling-more-efficient-safe-code"></a>Povolení efektivnějšího bezpečného kódu

Měli byste být schopni napsat kód Jazyka C# bezpečně, který provádí, stejně jako nebezpečný kód. Bezpečný kód zabraňuje třídy chyb, jako je například přetečení vyrovnávací paměti, zbloudilé ukazatele a další chyby přístupu do paměti. Tyto nové funkce rozšiřují možnosti ověřitelného bezpečného kódu. Snažte se psát více kódu pomocí bezpečných konstrukcí. Tyto funkce to usnadňují.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Indexování `fixed` polí nevyžaduje připnutí

Vezměme si tuto strukturu:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

V dřívějších verzích jazyka C# je třeba připnout proměnnou pro `myFixedField`přístup k jednomu z celá čísla, které jsou součástí . Nyní se zkompiluje následující `p` kód bez `fixed` připnutí proměnné uvnitř samostatného příkazu:

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

Proměnná `p` přistupuje jeden prvek v `myFixedField`. Není nutné deklarovat `int*` samostatnou proměnnou. Všimněte si, `unsafe` že stále potřebujete kontext. V dřívějších verzích jazyka C# je třeba deklarovat druhý pevný ukazatel:

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

Další informace naleznete v článku [ `fixed` ](../language-reference/keywords/fixed-statement.md)na prohlášení .

### <a name="ref-local-variables-may-be-reassigned"></a>`ref`místní proměnné mohou být přeřazeny

Nyní `ref` místní obyvatelé mohou být znovu přiřazeny odkazovat na různé instance po inicializování. Následující kód nyní zkompiluje:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Další informace naleznete v článku o [ `ref` vrácení a `ref` místní obyvatelé](../programming-guide/classes-and-structs/ref-returns.md)a článek o [`foreach`](../language-reference/keywords/foreach-in.md).

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc`pole podporují inicializátory

Při inicializaci pole jste mohli zadat hodnoty prvků v poli:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Nyní, že stejná syntaxe lze použít `stackalloc`na pole, která jsou deklarována s :

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Další informace naleznete v článku [ `stackalloc` operátora.](../language-reference/operators/stackalloc.md)

### <a name="more-types-support-the-fixed-statement"></a>Prohlášení podporují `fixed` další typy

Příkaz `fixed` podporuje omezenou sadu typů. Počínaje C# 7.3, libovolný typ, který obsahuje `GetPinnableReference()` metodu, která vrací `ref T` nebo `ref readonly T` může být `fixed`. Přidání této funkce `fixed` znamená, <xref:System.Span%601?displayProperty=nameWithType> že lze použít s a související typy.

Další informace naleznete [ `fixed` ](../language-reference/keywords/fixed-statement.md) v článku prohlášení v odkazu na jazyk.

### <a name="enhanced-generic-constraints"></a>Rozšířená obecná omezení

Nyní můžete zadat <xref:System.Enum?displayProperty=nameWithType> typ <xref:System.Delegate?displayProperty=nameWithType> nebo jako omezení základní třídy pro parametr typu.

Můžete také použít `unmanaged` nové omezení, chcete-li určit, že parametr typu musí být [neslaný typ](../language-reference/builtin-types/unmanaged-types.md)s hodnotou nesprávou, kterou nelze utnout .

Další informace naleznete v článcích o [ `where` obecných omezeních](../language-reference/keywords/where-generic-type-constraint.md) a [omezeních parametrů typu](../programming-guide/generics/constraints-on-type-parameters.md).

Přidání těchto omezení do existujících typů je [nekompatibilní změna](version-update-considerations.md#incompatible-changes). Uzavřené obecné typy již nemusí splňovat tato nová omezení.

## <a name="make-existing-features-better"></a>Vylepšete stávající funkce

Druhý motiv poskytuje vylepšení funkcí v jazyce. Tyto funkce zvyšují produktivitu při psaní jazyka C#.

### <a name="tuples-support--and-"></a>Podpora n-tia `==` a`!=`

C# řazené `==` kolekce `!=`členů typy nyní podporují a . Další informace naleznete v části týkající se [rovnosti](../tuples.md#equality-and-tuples) v článku [o řazených kolekcí členů](../tuples.md).

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Připojení atributů k záložním polím pro automaticky implementované vlastnosti

Tato syntaxe je nyní podporována:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Atribut `SomeThingAboutFieldAttribute` je použit pro kompilátor generované `SomeProperty`záložní pole pro . Další informace naleznete v [atributy](../programming-guide/concepts/attributes/index.md) v c# programovací průvodce.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in`metoda řešení přetížení tiebreaker

Při `in` přidání modifikátor argumentu by tyto dvě metody způsobit nejednoznačnost:

```csharp
static void M(S arg);
static void M(in S arg);
```

Nyní podle hodnoty (první v předchozím příkladu) přetížení je lepší než podle referenční verze pouze pro čtení. Chcete-li volat verzi s referenčním argumentem `in` jen pro čtení, musíte při volání metody zahrnout modifikátor.

> [!NOTE]
> To bylo implementováno jako oprava chyby. To již není nejednoznačné ani s jazykovou verzí nastavenou na "7.2".

Další informace naleznete v článku o [ `in` modifikátoru parametrů](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Rozšířit proměnné výrazu v inicializátorech

Syntaxe přidaná v C# `out` 7.0 povolit deklarace proměnných byla rozšířena tak, aby zahrnovala inicializátory polí, inicializátory vlastností, inicializátory konstruktérů a klauzule dotazu. Umožňuje kód, například následující příklad:

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a>Vylepšení kandidátů přetížení

V každé verzi pravidla řešení přetížení získat aktualizovány k řešení situacích, kdy nejednoznačné vyvolání metody mají "zřejmou" volbu. Tato verze přidá tři nová pravidla, která kompilátoru pomohou vybrat jasnou volbu:

1. Pokud skupina metod obsahuje instance i statické členy, kompilátor zahodí členy instance, pokud byla metoda vyvolána bez příjemce instance nebo kontextu. Kompilátor zahodí statické členy, pokud byla metoda vyvolána s příjemcem instance. Pokud neexistuje žádný příjemce, kompilátor obsahuje pouze statické členy ve statickém kontextu, jinak statické členy i členy instance. Pokud je příjemce nejednoznačně instancí nebo typem, kompilátor obsahuje obojí. Statický kontext, kde `this` nelze použít implicitní instance příjemce, zahrnuje `this` tělo členů, kde není definována, `this` jako jsou statické členy, stejně jako místa, kde nelze použít, jako jsou inicializační pole a konstruktor-inicializátory.
1. Pokud skupina metod obsahuje některé obecné metody, jejichž argumenty typu nesplňují jejich omezení, jsou tito členové odebráni z kandidátské sady.
1. Pro převod skupiny metod jsou ze sady odebrány metody, jejichž návratový typ neodpovídá návratovému typu delegáta.

Tuto změnu si všimnete pouze proto, že najdete méně chyb kompilátoru pro přetížení nejednoznačné metody, když jste si jisti, která metoda je lepší.

## <a name="new-compiler-options"></a>Nové možnosti kompilátoru

Nové možnosti kompilátoru podporují nové scénáře sestavení a DevOps pro programy Jazyka C#.

### <a name="public-or-open-source-signing"></a>Veřejné nebo open source podepisování

Možnost `-publicsign` kompilátoru instruuje kompilátor podepsat sestavení pomocí veřejného klíče. Sestavení je označeno jako podepsané, ale podpis je převzat z veřejného klíče. Tato možnost umožňuje vytvářet podepsaná sestavení z open source projektů pomocí veřejného klíče.

Další informace naleznete v článku [možnosti kompilátoru -publicsign.](../language-reference/compiler-options/publicsign-compiler-option.md)

### <a name="pathmap"></a>mapa cesty

Možnost `-pathmap` kompilátoru instruuje kompilátor nahradit zdrojové cesty z prostředí sestavení mapovanými zdrojovými cestami. Tato `-pathmap` možnost řídí zdrojovou cestu napsanou kompilátorem do souborů PDB nebo pro <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>soubor .

Další informace naleznete v článku [možnosti kompilátoru -pathmap.](../language-reference/compiler-options/pathmap-compiler-option.md)
