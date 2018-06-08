---
title: Co je nového v C# 7.3
description: Přehled nových funkcí v C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: 1d1aca2564c26315cf8b3af60a863ea3c70fd385
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827095"
---
# <a name="whats-new-in-c-73"></a>Co je nového v C# 7.3

Existují dvě hlavní motivy na vydání 7.3 C#. Jeden motiv poskytuje funkce, které umožňují bezpečné kódu, které původce jako nezabezpečený kód. Druhý motiv poskytuje postupných vylepšení stávajících funkcí. Kromě toho byly přidány nové možnosti kompilátoru v této verzi.

Následující nové funkce podporují motiv lepší výkon pro bezpečné kód:

- Pole pevné můžete přistupovat bez Připnutí.
- Můžete opětovně přiřadit `ref` místní proměnné.
- Inicializátory můžete použít na `stackalloc` pole.
- Můžete použít `fixed` příkazy s žádný typ, který podporuje vzor.
- Můžete vytvořit další obecná omezení.

Byly provedeny následující vylepšení stávajících funkcí:

- Můžete otestovat `==` a `!=` s typy řazené kolekce členů.
- Výraz proměnné můžete použít na více místech.
- Atributy může připojit k poli zálohování automaticky implementované vlastnosti.
- Metoda řešení, pokud se liší argumenty `in` se zlepšila.
- Řešení přetížení teď má méně dvojznačné případy.

Nové možnosti kompilátoru jsou:

- `-publicsign` Chcete-li povolit, otevřete zdroj softwaru (OSS) podepisování sestavení.
- `-pathmap` zadat mapování pro zdrojového adresáře.

Zbývající část tohoto článku poskytuje podrobnosti a odkazy na další informace o jednotlivých vylepšení.

## <a name="enabling-more-performant-safe-code"></a>Povolení více původce bezpečné kódu

Nyní byste měli mít psaní kódu jazyka C#, bezpečně provádějící i nezabezpečený kód. Bezpečné kód zabraňuje třídy chyb, jako je přetečení vyrovnávací paměti, ukazatele stray a dalších chyb přístupu k paměti. Tyto nové funkce rozšíření schopností ověřitelný kód bezpečné. Snažit zapsat informace z vašeho kódu pomocí bezpečné konstrukce. Tyto funkce ujistěte, že jednodušší.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Indexování `fixed` pole nevyžaduje Připnutí

Vezměte v úvahu tato struktura:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

V dřívějších verzích jazyka C#, je potřeba připnout proměnnou pro přístup k jedné celých čísel, které jsou součástí `myFixedField`. Následující kód zkompiluje teď v bezpečném kontextu:

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

Proměnná `p` přistupuje k jeden element ve `myFixedField`. Nemusíte samostatnou declare `int*` proměnné. Všimněte si, že budete potřebovat `unsafe` kontextu. V dřívějších verzích jazyka C# je třeba deklarovat druhý pevné ukazatel:

```csharp
class C
{
    static S s = new S();

    public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

Další informace najdete v článku na [ `fixed` příkaz](../language-reference/keywords/fixed-statement.md).

### <a name="ref-local-variables-may-be-reassigned"></a>`ref` lokální proměnné mohou být přiděleny.

Nyní `ref` místní hodnoty mohou být přiděleny k odkazování na různé instance po inicializaci. Následující kód nyní zkompiluje:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Další informace najdete v článku na [ `ref` vrátí a `ref` místní hodnoty –](../programming-guide/classes-and-structs/ref-returns.md).

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` pole podporují inicializátory

Bylo dříve možné zadat hodnoty pro elementy v matici, když je inicializovat:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Teď, může tento stejnou syntaxi použijí na pole, které jsou deklarovány s `stackalloc`:

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Další informace najdete v tématu [ `stackalloc` příkaz](../language-reference/keywords/stackalloc.md) článek v dokumentu.

### <a name="more-types-support-the-fixed-statement"></a>Další typy podporují `fixed` – příkaz

`fixed` Příkaz podporován omezenou sadu typy. Od verze jazyka C# 7.3, žádný typ, který obsahuje `GetPinnableReference()` metodu, která vrátí `ref T` nebo `ref readonly T` může být `fixed`. Přidání této funkce znamená, že `fixed` lze použít s <xref:System.Span%601?displayProperty=nameWithType> a související typy.

Další informace najdete v tématu [ `fixed` příkaz](../language-reference/keywords/fixed-statement.md) článek v dokumentu.

### <a name="enhanced-generic-constraints"></a>Rozšířené obecná omezení

Nyní můžete určit typ <xref:System.Enum?displayProperty=nameWithType> nebo <xref:System.Delegate?displayProperty=nameWithType> jako základní třída omezení pro parametr typu.

Můžete také použít nové `unmanaged` omezení, chcete-li určit, že musí být parametr typu **nespravované typu**. **Nespravované typu** je typ, který není typu odkazu a neobsahuje žádné odkaz na libovolnou úroveň vnoření.

Další informace najdete v článcích na [ `where` obecná omezení](../language-reference/keywords/where-generic-type-constraint.md) a [omezení parametrů typů](../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="make-existing-features-better"></a>Vylepšit stávajících funkcí

Druhý motiv poskytuje přináší vylepšení funkcí v jazyce. Tyto funkce zlepšit produktivitu při zápisu C#.

### <a name="tuples-support--and-"></a>Podpora řazených kolekcí členů `==` a `!=`

C# řazenou kolekci členů typy teď podporují `==` a `!=`. Další informace najdete v části zahrnut [rovnosti](../tuples.md#equality-and-tuples) v článku na [řazených kolekcí členů](../tuples.md).

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Přiřadit atributy pole zálohování pro automaticky implementované vlastnosti

Se teď podporuje tuto syntaxi:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Atribut `SomeThingAboutFieldAttribute` se použije na pole Základní kompilátoru generované pro `SomeProperty`. Další informace najdete v tématu [atributy](../programming-guide/concepts/attributes/index.md) v příručce programovacího jazyka C#.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in` tiebreaker rozlišení přetížení – metoda

Když `in` modifikátor argument byl přidán, tyto dvě metody způsobí to nejednoznačnost:

```csharp
static void M(S arg);
static void M(in S arg);
```

Nyní hodnotou (nejprve v předchozím příkladu) je lepší, než přetížení verzí odkaz jen pro čtení. K volání na verzi s argumentem odkaz jen pro čtení, je nutné zahrnout `in` modifikátor při volání metody.

> [!NOTE]
> Tato možnost byla implementovaná jako oprava chyb. To už je nejednoznačný i s jazyková verze nastavena na "7.2".

Další informace najdete v článku na [ `in` – modifikátor parametrů](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Rozšíření proměnných výrazu v inicializátory

Syntaxe přidali v C# 7.0 umožňuje `out` deklarace proměnných rozšířilo zahrnout pole inicializátory, vlastnost inicializátory, inicializátory konstruktoru, a dotaz klauzule. Umožňuje kódu, například v následujícím příkladu:

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
   public D(int i) : B(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a>Vylepšené přetížení kandidáty

V každé verzi pravidel řešení přetížení aktualizovat na situace, kdy volání metod nejednoznačný mít na volbu "zřejmé". Tato verze přináší tři nové pravidel pomohou kompilátoru vyberte zřejmé možnost:

1. Pokud skupina metoda obsahuje instanci a statické členy, kompilátor zahodí členů instance, pokud metoda byla volána bez příjemce instance nebo kontextu. Kompilátor zahodí statické členy, pokud metoda byla volána s příjemce instance. Když není žádný příjemce, kompilátor zahrnuje pouze statické členy ve statickém kontextu, v opačném případě statické a instanci členy. Když příjemce je ambiguously instance nebo typu, kompilátor zahrnuje obě. Statickém kontextu, kde implicitní `this` příjemce instanci nelze použít, obsahuje tělo členů, kde ne `this` definované, například statické členy, jakož i kdy, kde `this` nelze použít, jako je například pole inicializátory a Inicializátory konstruktoru.
1. Pokud metoda skupina obsahuje některé obecné metody, jejichž argumenty typu nesplňují jejich omezení, tito členové budou odebrány ze sady candidate.
1. Pro převod skupin metoda candidate metody, jejichž návratový typ se neshoduje společně s ním vrátí typ se odeberou ze sady.

Tato změna můžete si všimnout pouze protože najdete méně chyby kompilátoru o přetížení metody nejednoznačný když jste si jisti, jakou metodu je lepší.

## <a name="new-compiler-options"></a>Nové možnosti kompilátoru

Nové možnosti kompilátoru podporu nového sestavení a DevOps scénáře pro programy C#.

### <a name="public-or-open-source-signing"></a>Veřejné nebo podepisování Open Source

`-publicsign` – Možnost kompilátoru dává pokyn kompilátoru k podepsání sestavení pomocí veřejného klíče. Sestavení je označena jako podepsané, ale podpis jsou převzaty z veřejného klíče. Tato možnost umožňuje vytvářet podepsaná sestavení z projektů open-source pomocí veřejného klíče.

Další informace najdete v tématu [- publicsign – možnost kompilátoru](../language-reference/compiler-options/publicsign-compiler-option.md) článku.

### <a name="pathmap"></a>pathmap

`-pathmap` – Možnost kompilátoru dává pokyn kompilátoru nahradit mapovat zdrojových cest zdrojových cest z prostředí sestavení. `-pathmap` Možnost ovládací prvky podle kompilátor zapisují do souboru PDB soubory nebo pro zdrojovou cestu <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.

Další informace najdete v tématu [- pathmap – možnost kompilátoru](../language-reference/compiler-options/pathmap-compiler-option.md) článku.
