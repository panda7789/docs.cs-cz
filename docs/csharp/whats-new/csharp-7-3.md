---
title: Co je nového v jazyce C# 7.3
description: Přehled nových funkcí v jazyce C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: f97bda11d1da3f6deb4597c8d7742fd47e9cf15f
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58028683"
---
# <a name="whats-new-in-c-73"></a>Co je nového v jazyce C# 7.3

Existují dva hlavní motivy na verzi C# 7.3. Jeden motiv poskytuje funkce, které umožňují bezpečný kód, které funguje jako nezabezpečený kód. Druhý motiv poskytuje několik postupných vylepšení stávajících funkcí. Kromě toho byly přidány nové možnosti kompilátoru v této verzi.

Následující nové funkce podporují motiv lepší výkon pro bezpečný kód:

- Oprava pole máte přístup bez Připnutí.
- Můžete opětovně přiřazovat `ref` lokální proměnné.
- Inicializátory můžete použít na `stackalloc` pole.
- Můžete použít `fixed` příkazy s libovolný typ, který podporuje vzoru.
- Můžete použít další obecná omezení.

Byly provedeny následující vylepšení stávajících funkcí:

- Můžete otestovat `==` a `!=` s typy řazené kolekce členů.
- Proměnné výrazů můžete použít na více místech.
- Atributy mohou připojit k pomocné pole automaticky implementované vlastnosti.
- Metoda rozlišení při argumenty liší `in` byla vylepšena.
- Řešení přetížení má nyní méně dvojznačné případy.

Nové možnosti kompilátoru jsou:

- `-publicsign` Chcete-li povolit, Open Source Software (OSS) podepisování sestavení.
- `-pathmap` Chcete-li zadat mapování pro adresáře zdrojových souborů.

Zbývající část tohoto článku poskytuje podrobnosti a odkazy na další informace o každé vylepšení.

## <a name="enabling-more-efficient-safe-code"></a>Povolení efektivnější bezpečný kód

Je třeba schopni napsat kód jazyka C#, bezpečně, který funguje stejně dobře jako nezabezpečený kód. Nouzový kód se vyhnete třídy chyb, jako je například přetečení vyrovnávací paměti, ukazatele stray a další chyby přístupu k paměti. Tyto nové funkce rozšířili schopnosti ověřitelný bezpečný kód. Snažit se psát více kódu pomocí bezpečné konstrukce. Tyto funkce to usnadní.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Indexování `fixed` pole nevyžaduje Připnutí

Vezměte v úvahu tuto strukturu:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

V dřívějších verzích jazyka C#, jste museli připnout proměnnou pro přístup k jedné celých čísel, které jsou součástí `myFixedField`. Nyní, následující kód zkompiluje bez Připnutí proměnné `p` uvnitř samostatné `fixed` – příkaz:

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

Proměnná `p` přistupuje k jeden prvek `myFixedField`. Není nutné pro deklaraci samostatné `int*` proměnné. Všimněte si, že se můžete stále potřebovat `unsafe` kontextu. V dřívějších verzích jazyka C# musíte deklarovat ukazatel druhý pevné:

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

Další informace najdete v článku na [ `fixed` příkaz](../language-reference/keywords/fixed-statement.md).

### <a name="ref-local-variables-may-be-reassigned"></a>`ref` může být přeřazen lokální proměnné

Nyní `ref` k odkazování na různých instancích po jejich inicializaci může být přeřazen místních hodnot. Následující kód nyní kompiluje:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Další informace najdete v článku na [ `ref` vrátí a `ref` lokální](../programming-guide/classes-and-structs/ref-returns.md)a v článku věnovaném [ `foreach` ](../language-reference/keywords/foreach-in.md).

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` pole podporují inicializátory

Je možné zadat hodnoty pro prvky v poli, když ji inicializovat:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Nyní, stejné syntaxe lze použít u polí, které jsou deklarovány pomocí `stackalloc`:

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Další informace najdete v tématu [ `stackalloc` příkaz](../language-reference/keywords/stackalloc.md) článek v referenční příručka jazyka.

### <a name="more-types-support-the-fixed-statement"></a>Podpora dalších typů `fixed` – příkaz

`fixed` Příkaz podporován omezenou sadu typů. Od verze C# 7.3, libovolný typ, který obsahuje `GetPinnableReference()` metodu, která vrací `ref T` nebo `ref readonly T` může být `fixed`. Přidání této funkce znamená, že `fixed` jde použít s <xref:System.Span%601?displayProperty=nameWithType> a souvisejících typů.

Další informace najdete v tématu [ `fixed` příkaz](../language-reference/keywords/fixed-statement.md) článek v referenční příručka jazyka.

### <a name="enhanced-generic-constraints"></a>Vylepšené obecná omezení

Teď můžete zadat typ <xref:System.Enum?displayProperty=nameWithType> nebo <xref:System.Delegate?displayProperty=nameWithType> jako základní třída omezení parametru typu.

Můžete také použít novou `unmanaged` omezení, chcete-li určit, že musí být parametr typu **nespravovaný typ**. **Nespravovaný typ** je typ, který není typem odkazu a neobsahuje jakéhokoliv odkazového typu na libovolné úrovni vnoření.

Další informace najdete v článcích na [ `where` obecná omezení](../language-reference/keywords/where-generic-type-constraint.md) a [omezení parametrů typů](../programming-guide/generics/constraints-on-type-parameters.md).

Přidání k existujícím typům těchto omezení je [nekompatibilní změna](version-update-considerations.md#incompatible-changes). Uzavřených obecných typů pravděpodobně přestane splňovat tyto nové omezení.

## <a name="make-existing-features-better"></a>Vylepšit stávajících funkcí

Druhý motiv přináší vylepšení v oblasti funkce v jazyce. Tyto funkce, zvyšují produktivitu při psaní C#.

### <a name="tuples-support--and-"></a>Podpora řazených kolekcí členů `==` a `!=`

C# řazené kolekce členů typů teď podporují `==` a `!=`. Další informace najdete v oddílu, mezi které patří [rovnosti](../tuples.md#equality-and-tuples) v článku věnovaném [řazených kolekcí členů](../tuples.md).

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Připojit atributy na pomocné pole automaticky implementované vlastnosti

Tato syntaxe se teď podporuje:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Atribut `SomeThingAboutFieldAttribute` platí pro generovaný kompilátorem pomocné pole `SomeProperty`. Další informace najdete v tématu [atributy](../programming-guide/concepts/attributes/index.md) v Průvodci programovacího jazyka C#.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in` rozhodujícího prvku rozlišení přetížení – metoda

Když `in` byl přidán modifikátor argument, tyto dvě metody by způsobit nejednoznačnost:

```csharp
static void M(S arg);
static void M(in S arg);
```

Nyní podle hodnoty (první v předchozím příkladu) je lepší než přetížení odkaz verze jen pro čtení. Pro volání verze s argumentem reference jen pro čtení, je nutné zahrnout `in` modifikátor při volání metody.

> [!NOTE]
> To bylo implementováno jako oprava chyby. To už je nejednoznačný i přes jazykové verze nastavena na "7.2".

Další informace najdete v článku na [ `in` modifikátor parametru](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Rozšíření proměnných výrazu v inicializátorech

Syntaxe v jazyce C# 7.0 umožňuje přidat `out` deklarace proměnných rozšířilo a obsahovat Inicializátory pole, vlastnosti, inicializátory konstruktoru a klauzulí dotazů. To umožňuje kódu jako v následujícím příkladu:

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

### <a name="improved-overload-candidates"></a>Vylepšené přetížení kandidáty

V každé verzi pravidla rozlišení přetížení aktualizovat na situace, kdy mají "viditelných" volba volání metod nejednoznačný. Tato verze přidává tři nová pravidla ke kompilátoru vyberte jasnou volbou:

1. Pokud skupina metoda obsahuje instanci a statické členy, kompilátor zahodí členy instance, pokud metoda byla vyvolána bez instance příjemce nebo kontextu. Kompilátor zahodí statické členy, pokud metoda byla vyvolána s přijímače instance. Pokud není žádný příjemce, kompilátor obsahuje pouze statické členy ve statickém kontextu, v opačném případě statických a členy instance. Když příjemce ambiguously instance nebo typ, kompilátor obsahuje. Statického kontextu, kde je implicitní `this` příjemce instanci nelze použít, obsahuje tělo členů, pokud `this` je definován, jako je například statické členy, jakož i kdy, kde `this` nelze použít, jako je například Inicializátory polí a Inicializátory konstruktoru.
1. Pokud metoda skupina obsahuje některé obecné metody, jejichž argumentů typu nevyhovuje požadavkům jejich omezení, tyto členy, se odeberou ze sady Release candidate.
1. Pro skupiny převod metody vrátí metody Release candidate, jejíž návratový typ neshoduje s delegáta typu se odeberou ze sady.

Tato změna všimnout pouze vzhledem k tomu, že zjistíte méně chyb kompilátoru pro přetížení metody nejednoznačný když jste si jisti, jakou metodu je lepší.

## <a name="new-compiler-options"></a>Nové možnosti kompilátoru

Nové možnosti kompilátoru podporují scénáře DevOps a nové sestavení pro programy C#.

### <a name="public-or-open-source-signing"></a>Veřejný nebo podepisování Open Source

`-publicsign` – Možnost kompilátoru instruuje kompilátor, aby podepište sestavení pomocí veřejného klíče. Sestava je označena jako podepsané, ale signatura je převzata z veřejného klíče. Tato možnost vám umožní sestavovat podepsaná sestavení z open-source projektů pomocí veřejného klíče.

Další informace najdete v tématu [– možnost kompilátoru - publicsign](../language-reference/compiler-options/publicsign-compiler-option.md) článku.

### <a name="pathmap"></a>pathmap

`-pathmap` – Možnost kompilátoru instruuje kompilátor, aby nahraďte mapované zdrojových cest zdrojových cest z prostředí pro sestavení. `-pathmap` Možnost řídí napsaný v kompilátoru pro soubory PDB nebo pro zdrojovou cestu <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.

Další informace najdete v tématu [– možnost kompilátoru - pathmap](../language-reference/compiler-options/pathmap-compiler-option.md) článku.
