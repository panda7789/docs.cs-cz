---
title: Co je nového v C# 7,3
description: Přehled nových funkcí v C# 7,3
ms.date: 05/16/2018
ms.openlocfilehash: ba4cea302d91b395e88940d087fcaed306920840
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204557"
---
# <a name="whats-new-in-c-73"></a>Co je nového v C# 7,3

Verze C# 7,3 obsahuje dva hlavní motivy. Jeden motiv nabízí funkce, které umožňují bezpečný kód jako nezabezpečený kód. Druhý motiv nabízí přírůstková vylepšení existujících funkcí. Kromě toho se v této verzi přidaly nové možnosti kompilátoru.

Následující nové funkce podporují motiv s lepším výkonem pro bezpečný kód:

- Můžete získat přístup k pevným polím bez připnutí.
- Můžete znovu přiřadit `ref` lokální proměnné.
- Můžete použít inicializátory na `stackalloc` polích.
- Příkazy `fixed` lze použít s libovolným typem, který podporuje vzor.
- Můžete použít další obecná omezení.

V existujících funkcích byly provedeny následující vylepšení:

- Můžete testovat `==` a `!=` s typy řazené kolekce členů.
- Proměnné výrazu můžete použít ve více umístěních.
- Můžete přiřazovat atributy k poli pro zálohování s automaticky implementovanými vlastnostmi.
- Řešení metod, když se liší argumenty, `in` bylo vylepšeno.
- Řešení přetížení teď má méně dvojznačných případů.

Nové možnosti kompilátoru:

- `-publicsign`, aby se povolilo podepisování softwaru open source (OSS) pro sestavení.
- `-pathmap` k poskytnutí mapování pro zdrojové adresáře.

Zbývající část tohoto článku obsahuje podrobnosti a odkazy na Další informace o každé z těchto vylepšení. Tyto funkce můžete ve svém prostředí prozkoumat pomocí globálního nástroje `dotnet try`:

1. Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *Try-Samples* .
1. Spusťte `dotnet try`.

## <a name="enabling-more-efficient-safe-code"></a>Povolení efektivnějšího bezpečného kódu

Měli byste být schopni bezpečně C# psát kód, který provádí a také nezabezpečený kód. Bezpečný kód zabraňuje třídám chyb, jako jsou přetečení vyrovnávací paměti, osamocené ukazatele a další chyby přístupu k paměti. Tyto nové funkce rozšiřují možnosti ověřitelného bezpečného kódu. Snažte se zapisovat více kódu pomocí bezpečných konstrukcí. Tyto funkce usnadňují práci.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Indexování `fixed` polí nevyžaduje připnutí.

Zvažte tuto strukturu:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

V dřívějších verzích C#nástroje bylo nutné připnout proměnnou pro přístup k jednomu z celých čísel, která jsou součástí `myFixedField`. Nyní následující kód zkompiluje bez připnutí proměnné `p` uvnitř samostatného příkazu `fixed`:

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

Proměnná `p` přistupuje k jednomu prvku v `myFixedField`. Nemusíte deklarovat samostatnou `int*` proměnnou. Všimněte si, že stále potřebujete kontext `unsafe`. V dřívějších verzích C#nástroje je nutné deklarovat druhý pevný ukazatel:

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

Další informace najdete v článku o [příkazu`fixed`](../language-reference/keywords/fixed-statement.md).

### <a name="ref-local-variables-may-be-reassigned"></a>je možné znovu přiřadit `ref` lokální proměnné.

Nyní je možné znovu přiřadit `ref` národní prostředí, aby se po inicializaci odkazovaly na různé instance. Nyní se zkompiluje následující kód:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Další informace najdete v článku o [`ref` vrátí a `ref` národní prostředí](../programming-guide/classes-and-structs/ref-returns.md)a článku na [`foreach`](../language-reference/keywords/foreach-in.md).

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` pole podporují Inicializátory.

Při inicializaci je možné zadat hodnoty prvků v poli:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Nyní lze stejnou syntaxi použít pro pole, která jsou deklarována s `stackalloc`:

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Další informace najdete v článku o [operátoru`stackalloc`](../language-reference/operators/stackalloc.md) .

### <a name="more-types-support-the-fixed-statement"></a>Další typy podporují příkaz `fixed`.

Příkaz `fixed` podporuje omezené sady typů. Počínaje C# 7,3 se může `fixed`jakýkoli typ, který obsahuje metodu `GetPinnableReference()`, která vrací `ref T` nebo `ref readonly T`. Přidání této funkce znamená, že `fixed` lze použít s <xref:System.Span%601?displayProperty=nameWithType> a souvisejícími typy.

Další informace naleznete v článku o [příkazu`fixed`](../language-reference/keywords/fixed-statement.md) v tématu Referenční informace k jazyku.

### <a name="enhanced-generic-constraints"></a>Rozšířená obecná omezení

Nyní můžete zadat typ <xref:System.Enum?displayProperty=nameWithType> nebo <xref:System.Delegate?displayProperty=nameWithType> jako omezení základní třídy pro parametr typu.

Můžete také použít nové omezení `unmanaged`, chcete-li určit, že parametr typu musí být [nespravovaný typ](../language-reference/builtin-types/unmanaged-types.md), který nemůže mít hodnotu null.

Další informace najdete v článcích o [`where` obecných omezeních](../language-reference/keywords/where-generic-type-constraint.md) a [omezeních parametrů typu](../programming-guide/generics/constraints-on-type-parameters.md).

Přidání těchto omezení do existujících typů je [nekompatibilní změna](version-update-considerations.md#incompatible-changes). Uzavřené obecné typy již nesmí splňovat tato nová omezení.

## <a name="make-existing-features-better"></a>Lepší zlepšení stávajících funkcí

Druhý motiv nabízí vylepšení funkcí v jazyce. Tyto funkce zvyšují produktivitu při C#psaní.

### <a name="tuples-support--and-"></a>Řazené kolekce členů podporují `==` a `!=`

Typy C# řazené kolekce členů teď podporují `==` a `!=`. Další informace najdete v části týkající se [rovnosti](../tuples.md#equality-and-tuples) v článku o [řazených kolekcích členů](../tuples.md).

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Připojení atributů k zálohovaným polím pro automaticky implementované vlastnosti

Tato syntaxe je teď podporovaná:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Atribut `SomeThingAboutFieldAttribute` je použit pro pole zálohování generované kompilátorem pro `SomeProperty`. Další informace najdete v tématu [atributy](../programming-guide/concepts/attributes/index.md) v průvodci C# programováním.

### <a name="in-method-overload-resolution-tiebreaker"></a>rozhodujícího prvku rozlišení přetížení metod `in`

Při přidání modifikátoru `in`ho argumentu by tyto dvě metody způsobily nejednoznačnost:

```csharp
static void M(S arg);
static void M(in S arg);
```

Nyní je přetížení v hodnotě (první v předchozím příkladu) lepší než referenční verze metody ReadOnly. Chcete-li volat verzi s argumentem odkazu jen pro čtení, je nutné při volání metody použít modifikátor `in`.

> [!NOTE]
> Tato chyba byla implementována jako oprava chyby. Tato možnost již není jednoznačná, i když je jazyková verze nastavená na "7,2".

Další informace najdete v článku o [modifikátoru parametru`in`](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Rozšiřování proměnných výrazu v inicializátorech

Syntaxe přidaná v C# 7,0 pro povolení deklarací proměnných `out` byla rozšířena tak, aby zahrnovala Inicializátory polí, Inicializátory vlastností, Inicializátory konstruktorů a klauzule dotazu. Umožňuje kód, jako je například následující příklad:

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

1. Pokud skupina metod obsahuje instanci i statické členy, kompilátor zruší členy instance, pokud byla metoda vyvolána bez přijímače nebo kontextu instance. Kompilátor zahodí statické členy, pokud byla metoda vyvolána s příjemcem instance. Pokud není k dispozici žádný přijímač, kompilátor zahrnuje pouze statické členy ve statickém kontextu, jinak statických i členů instancí. Pokud je příjemce jednoznačně instance nebo typu, kompilátor zahrnuje obojí. Statický kontext, kde nelze použít příjemce instance implicitního `this`, zahrnuje tělo členů, pokud není definován žádný `this`, například statické členy, a místa, kde `this` nelze použít, jako jsou například Inicializátory polí a Inicializátory konstruktoru.
1. Pokud skupina metod obsahuje některé obecné metody, jejichž argumenty typu nesplňují jejich omezení, jsou tyto členy ze sady kandidátů odebrány.
1. Pro převod skupiny metod se ze sady odeberou metody kandidáta, jejichž návratový typ se neshoduje s návratovým typem delegáta.

Tuto změnu si všimnete pouze v případě, že při zjištění, která metoda je lepší, zjistíte méně chyb kompilátoru pro přetížení dvojznačných metod.

## <a name="new-compiler-options"></a>Nové možnosti kompilátoru

Nové možnosti kompilátoru podporují nové scénáře sestavení a DevOps pro C# programy.

### <a name="public-or-open-source-signing"></a>Veřejné nebo open source podepisování

Možnost kompilátoru `-publicsign` instruuje kompilátor, aby podepsal sestavení pomocí veřejného klíče. Sestavení je označeno jako signed, ale signatura je pořízena z veřejného klíče. Tato možnost umožňuje sestavit podepsaná sestavení z open source projektů pomocí veřejného klíče.

Další informace najdete v článku [možnost kompilátoru-publicsign](../language-reference/compiler-options/publicsign-compiler-option.md) .

### <a name="pathmap"></a>pathmap

Možnost kompilátoru `-pathmap` instruuje kompilátor, aby nahradil zdrojové cesty z prostředí sestavení s namapovanými zdrojovými cestami. Možnost `-pathmap` řídí zdrojovou cestu zapsanou kompilátorem do souborů PDB nebo pro <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.

Další informace najdete v článku [možnost kompilátoru-pathmap](../language-reference/compiler-options/pathmap-compiler-option.md) .
