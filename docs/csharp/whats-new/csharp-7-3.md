---
title: Co je nového v C# 7,3
description: Přehled nových funkcí v C# 7,3
ms.date: 05/16/2018
ms.openlocfilehash: cd8f554516fb5078d9d2ed1eec787f36e8f4c7a7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174754"
---
# <a name="whats-new-in-c-73"></a>Co je nového v C# 7,3

K vydání verze C# 7,3 existují dva hlavní motivy. Jeden motiv nabízí funkce, které umožňují bezpečný kód jako nezabezpečený kód. Druhý motiv nabízí přírůstková vylepšení existujících funkcí. Kromě toho se v této verzi přidaly nové možnosti kompilátoru.

Následující nové funkce podporují motiv s lepším výkonem pro bezpečný kód:

- Můžete získat přístup k pevným polím bez připnutí.
- Můžete změnit přiřazení `ref` místních proměnných.
- Můžete použít inicializátory u `stackalloc` polí.
- Můžete použít `fixed` příkazy s jakýmkoli typem, který podporuje vzor.
- Můžete použít další obecná omezení.

V existujících funkcích byly provedeny následující vylepšení:

- Můžete testovat `==` a `!=` s typy řazené kolekce členů.
- Proměnné výrazu můžete použít ve více umístěních.
- Můžete přiřazovat atributy k poli pro zálohování s automaticky implementovanými vlastnostmi.
- Řešení metody, když se liší argumenty, které `in` byly vylepšeny.
- Řešení přetížení teď má méně dvojznačných případů.

Nové možnosti kompilátoru:

- `-publicsign`povolení podepisování softwaru open source (OSS) pro sestavení.
- `-pathmap`pro poskytnutí mapování pro zdrojové adresáře.

Zbývající část tohoto článku obsahuje podrobnosti a odkazy na Další informace o každé z těchto vylepšení. Pomocí globálního nástroje můžete prozkoumat tyto funkce ve vašem prostředí `dotnet try` :

1. Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *Try-Samples* .
1. Spusťte `dotnet try`.

## <a name="enabling-more-efficient-safe-code"></a>Povolení efektivnějšího bezpečného kódu

Měli byste být schopni psát kód v jazyce C#, který je proveden jako bezpečný kód, a to bezpečně. Bezpečný kód zabraňuje třídám chyb, jako jsou přetečení vyrovnávací paměti, osamocené ukazatele a další chyby přístupu k paměti. Tyto nové funkce rozšiřují možnosti ověřitelného bezpečného kódu. Snažte se zapisovat více kódu pomocí bezpečných konstrukcí. Tyto funkce usnadňují práci.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>`fixed`Pole indexování nevyžaduje připnutí.

Zvažte tuto strukturu:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

V dřívějších verzích jazyka C# bylo nutné připnout proměnnou pro přístup k jednomu z celých čísel, která jsou součástí `myFixedField` . Nyní následující kód zkompiluje bez připnutí proměnné `p` uvnitř samostatného `fixed` příkazu:

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

Proměnná `p` přistupuje k jednomu prvku v `myFixedField` . Nemusíte deklarovat samostatnou `int*` proměnnou. Všimněte si, že stále potřebujete `unsafe` kontext. V dřívějších verzích jazyka C# je nutné deklarovat druhý pevný ukazatel:

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

Další informace najdete v článku o [ `fixed` příkazu](../language-reference/keywords/fixed-statement.md).

### <a name="ref-local-variables-may-be-reassigned"></a>`ref`lokální proměnné se můžou znovu přiřadit.

Místní proměnné se teď dají `ref` znovu přiřadit, aby po inicializaci odkazovaly na různé instance. Nyní se zkompiluje následující kód:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Další informace najdete v článku o [ `ref` vrácených a `ref` místních](../programming-guide/classes-and-structs/ref-returns.md)hodnotách a na článku o [`foreach`](../language-reference/keywords/foreach-in.md) .

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc`pole podporují Inicializátory.

Při inicializaci je možné zadat hodnoty prvků v poli:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Nyní lze stejnou syntaxi použít pro pole, která jsou deklarována pomocí `stackalloc` :

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Další informace najdete v článku o [ `stackalloc` operátoru](../language-reference/operators/stackalloc.md) .

### <a name="more-types-support-the-fixed-statement"></a>Další typy podporují `fixed` příkaz.

`fixed`Příkaz podporuje omezené sady typů. Počínaje jazykem C# 7,3 každý typ, který obsahuje `GetPinnableReference()` metodu, která vrací `ref T` nebo `ref readonly T` může být `fixed` . Přidání této funkce znamená, že je `fixed` možné použít s <xref:System.Span%601?displayProperty=nameWithType> a související typy.

Další informace naleznete v článku o [ `fixed` příkazu](../language-reference/keywords/fixed-statement.md) v referenční příručce jazyka.

### <a name="enhanced-generic-constraints"></a>Rozšířená obecná omezení

Nyní můžete určit typ <xref:System.Enum?displayProperty=nameWithType> nebo <xref:System.Delegate?displayProperty=nameWithType> jako omezení základní třídy pro parametr typu.

Můžete také použít nové `unmanaged` omezení, chcete-li určit, že parametr typu musí být [nespravovaný typ](../language-reference/builtin-types/unmanaged-types.md), který nemůže mít hodnotu null.

Další informace najdete v článcích o [ `where` obecných omezeních](../language-reference/keywords/where-generic-type-constraint.md) a [omezeních parametrů typu](../programming-guide/generics/constraints-on-type-parameters.md).

Přidání těchto omezení do existujících typů je [nekompatibilní změna](version-update-considerations.md#incompatible-changes). Uzavřené obecné typy již nesmí splňovat tato nová omezení.

## <a name="make-existing-features-better"></a>Lepší zlepšení stávajících funkcí

Druhý motiv nabízí vylepšení funkcí v jazyce. Tyto funkce zvyšují produktivitu při psaní C#.

### <a name="tuples-support--and-"></a>Podpora řazených kolekcí členů `==` a`!=`

Typy řazené kolekce členů jazyka C# nyní podporují `==` a `!=` . Další informace naleznete v části [rovnost řazené kolekce členů](../language-reference/builtin-types/value-tuples.md#tuple-equality) v článku [typy řazené kolekce členů](../language-reference/builtin-types/value-tuples.md) .

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Připojení atributů k zálohovaným polím pro automaticky implementované vlastnosti

Tato syntaxe je teď podporovaná:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Atribut `SomeThingAboutFieldAttribute` se použije pro pole zálohování generované kompilátorem `SomeProperty` . Další informace najdete v tématu [atributy](../programming-guide/concepts/attributes/index.md) v průvodci programováním v C#.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in`rozhodujícího prvku rozlišení přetížení metody

Při `in` Přidání modifikátoru argumentu by tyto dvě metody způsobily nejednoznačnost:

```csharp
static void M(S arg);
static void M(in S arg);
```

Nyní je přetížení v hodnotě (první v předchozím příkladu) lepší než referenční verze metody ReadOnly. Chcete-li volat verzi s argumentem odkazu jen pro čtení, je nutné `in` při volání metody použít modifikátor.

> [!NOTE]
> Tato chyba byla implementována jako oprava chyby. Tato možnost již není jednoznačná, i když je jazyková verze nastavená na "7,2".

Další informace naleznete v článku o [ `in` modifikátoru parametru](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Rozšiřování proměnných výrazu v inicializátorech

Syntaxe přidaná v C# 7,0 pro povolení `out` deklarací proměnných byla rozšířena tak, aby zahrnovala Inicializátory polí, Inicializátory vlastností, Inicializátory konstruktorů a klauzule dotazu. Umožňuje kód, jako je například následující příklad:

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

V každém vydání se pravidla rozlišení přetížení aktualizují na situace, kdy nejednoznačná vyvolání metod mají "zřejmou" volbu. Tato verze přidává tři nová pravidla, která kompilátoru pomůžou vybrat zjevné možnosti:

1. Pokud skupina metod obsahuje instanci i statické členy, kompilátor zruší členy instance, pokud byla metoda vyvolána bez přijímače nebo kontextu instance. Kompilátor zahodí statické členy, pokud byla metoda vyvolána s příjemcem instance. Pokud není k dispozici žádný přijímač, kompilátor zahrnuje pouze statické členy ve statickém kontextu, jinak statických i členů instancí. Pokud je příjemce jednoznačně instance nebo typu, kompilátor zahrnuje obojí. Statický kontext, kde `this` nelze použít implicitního přijímače instance, zahrnuje tělo členů, pokud `this` není definována žádná, například statické členy, a místa, kde `this` nelze použít, například Inicializátory polí a Inicializátory konstruktoru.
1. Pokud skupina metod obsahuje některé obecné metody, jejichž argumenty typu nesplňují jejich omezení, jsou tyto členy ze sady kandidátů odebrány.
1. Pro převod skupiny metod se ze sady odeberou metody kandidáta, jejichž návratový typ se neshoduje s návratovým typem delegáta.

Tuto změnu si všimnete pouze v případě, že při zjištění, která metoda je lepší, zjistíte méně chyb kompilátoru pro přetížení dvojznačných metod.

## <a name="new-compiler-options"></a>Nové možnosti kompilátoru

Nové možnosti kompilátoru podporují nové scénáře sestavení a DevOps pro programy v jazyce C#.

### <a name="public-or-open-source-signing"></a>Veřejné nebo open source podepisování

`-publicsign`Možnost kompilátoru instruuje kompilátor, aby podepsal sestavení pomocí veřejného klíče. Sestavení je označeno jako signed, ale signatura je pořízena z veřejného klíče. Tato možnost umožňuje sestavit podepsaná sestavení z open source projektů pomocí veřejného klíče.

Další informace najdete v článku [možnost kompilátoru-publicsign](../language-reference/compiler-options/publicsign-compiler-option.md) .

### <a name="pathmap"></a>pathmap

`-pathmap`Možnost kompilátoru instruuje kompilátor, aby nahradil zdrojové cesty z prostředí sestavení s namapovanými zdrojovými cestami. `-pathmap`Možnost řídí zdrojovou cestu zapsanou kompilátorem do souborů PDB nebo pro <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> .

Další informace najdete v článku [možnost kompilátoru-pathmap](../language-reference/compiler-options/pathmap-compiler-option.md) .
