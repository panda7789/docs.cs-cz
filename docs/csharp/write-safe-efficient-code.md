---
title: Napište bezpečný a efektivní kód Jazyka C#
description: Nedávná vylepšení jazyka C# umožňují psát ověřitelný bezpečný kód, který výkon dříve spojen s nebezpečným kódem.
ms.date: 10/23/2018
ms.technology: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: bb53264f61192c042da469ba687da6c472e8c6d4
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506980"
---
# <a name="write-safe-and-efficient-c-code"></a>Napište bezpečný a efektivní kód Jazyka C#

Nové funkce v C# umožňují psát ověřitelný bezpečný kód s lepším výkonem. Pokud pečlivě použijete tyto techniky, méně scénářů vyžaduje nebezpečný kód. Tyto funkce usnadňují použití odkazů na typy hodnot jako argumenty metody a vrácené metody. Při bezpečném provedení tyto techniky minimalizují kopírování typů hodnot. Pomocí typů hodnot můžete minimalizovat počet přidělení a průchodů uvolňování paměti.

Velká část ukázkového kódu v tomto článku používá funkce přidané v c# 7.2. Chcete-li tyto funkce používat, je nutné nakonfigurovat projekt tak, aby používal c# 7.2 nebo novější. Další informace o nastavení jazykové verze naleznete [v tématu konfigurace jazykové verze](language-reference/configure-language-version.md).

Tento článek se zaměřuje na techniky pro efektivní správu zdrojů. Jednou z výhod použití typů hodnot je, že se často vyhýbají přidělení haldy. Nevýhodou je, že jsou kopírovány podle hodnoty. Tento kompromis ztěžuje optimalizaci algoritmů, které pracují s velkým množstvím dat. Nové jazykové funkce v jazyce C# 7.2 poskytují mechanismy, které umožňují bezpečný efektivní kód pomocí odkazů na typy hodnot. Tyto funkce můžete používat moudře, abyste minimalizovali přidělení i operace kopírování. Tento článek zkoumá tyto nové funkce.

Tento článek se zaměřuje na následující techniky správy zdrojů:

- Deklarovat a vyjádřit, že typ je **neměnný** a [`in`](language-reference/keywords/in-parameter-modifier.md) umožňuje kompilátoru uložit kopie při použití parametrů. [`readonly struct`](language-reference/keywords/readonly.md#readonly-struct-example)
- Pokud typ nemůže být neměnný, `struct` `readonly` deklarujte členy, kteří označují, že člen nemění stav.
- Použijte [`ref readonly`](language-reference/keywords/ref.md#reference-return-values) return, pokud je `struct` vrácená <xref:System.IntPtr.Size?displayProperty=nameWithType> hodnota větší než a doba trvání úložiště je větší než metoda vracející hodnotu.
- Pokud je velikost `readonly struct` a <xref:System.IntPtr.Size?displayProperty=nameWithType>větší než , měli `in` byste ji předat jako parametr z důvodů výkonu.
- Nikdy předat `struct` jako `in` parametr, pokud je `readonly` deklarován s `readonly` modifikátornebo metoda volá pouze členy struktury. Porušení tohoto pokynu může negativně ovlivnit výkon a může vést k obskurní chování.
- Použijte [`ref struct`](language-reference/keywords/ref.md#ref-struct-types), nebo `readonly ref struct` jako <xref:System.Span%601> <xref:System.ReadOnlySpan%601> nebo pracovat s pamětí jako posloupnost bajtů.

Tyto techniky vás nutí vyvážit dva konkurenční cíle s ohledem na **odkazy** a **hodnoty**. Proměnné, které jsou [typy odkazů](programming-guide/types/index.md#reference-types) obsahovat odkaz na umístění v paměti. Proměnné, které jsou [typy hodnot](programming-guide/types/index.md#value-types) přímo obsahují jejich hodnotu. Tyto rozdíly zdůrazňují klíčové rozdíly, které jsou důležité pro správu prostředků paměti. **Typy hodnot** jsou obvykle zkopírovány při předání do metody nebo vráceny z metody. Toto chování zahrnuje kopírování `this` hodnoty při volání členů typu hodnoty. Náklady na kopii se vztahují k velikosti typu. **Referenční typy** jsou přiděleny na spravované haldy. Každý nový objekt vyžaduje nové přidělení a následně musí být rekultivovány. Obě tyto operace nějakou dobu trvat. Odkaz je zkopírován, když je typ odkazu předán jako argument metodě nebo vrácen z metody.

Tento článek používá následující příklad koncept struktury 3D bodů vysvětlit tato doporučení:

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

Různé příklady používají různé implementace tohoto konceptu.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Deklarovat struktury jen pro čtení pro neměnné typy hodnot

Deklarování `struct` `readonly` pomocí modifikátorinformuje kompilátoru, že vaším záměrem je vytvořit neměnný typ. Kompilátor vynucuje toto rozhodnutí o návrhu pomocí následujících pravidel:

- Všichni členové pole musí být`readonly`
- Všechny vlastnosti musí být jen pro čtení, včetně automaticky implementovaných vlastností.

Tato dvě pravidla postačují `readonly struct` k zajištění toho, aby žádný člen této struktury neuměvoval stav této struktury. Je `struct` neměnný. Struktura `Point3D` může být definována jako neměnná struktura, jak je znázorněno v následujícím příkladu:

```csharp
readonly public struct ReadonlyPoint3D
{
    public ReadonlyPoint3D(double x, double y, double z)
    {
        this.X = x;
        this.Y = y;
        this.Z = z;
    }

    public double X { get; }
    public double Y { get; }
    public double Z { get; }
}
```

Postupujte podle tohoto doporučení vždy, když záměr návrhu je vytvořit neměnný typ hodnoty. Všechna vylepšení výkonu jsou další výhodou. Jasně `readonly struct` vyjadřuje váš záměr návrhu.

## <a name="declare-readonly-members-when-a-struct-cant-be-immutable"></a>Deklarovat členy pouze pro čtení, když struktura nemůže být neměnná

V C# 8.0 a novější, když struct typ je proměnlivý, měli byste `readonly`deklarovat členy, které nezpůsobují mutace být . Zvažte jinou aplikaci, která potřebuje strukturu 3D bodů, ale musí podporovat proměnlivost. Následující verze struktury 3D bodů `readonly` přidá modifikátor pouze těm členům, kteří strukturu nemění. Postupujte podle tohoto příkladu, když váš návrh musí podporovat změny struktury některými členy, ale stále chcete výhody vynucení pouze pro čtení u některých členů:

```csharp
public struct Point3D
{
    public Point3D(double x, double y, double z)
    {
        _x = x;
        _y = y;
        _z = z;
    }

    private double _x;
    public double X
    {
        readonly get => _x;
        set => _x = value;
    }

    private double _y;
    public double Y
    {
        readonly get => _y;
        set => _y = value;
    }

    private double _z;
    public double Z
    {
        readonly get => _z;
        set => _z = value;
    }

    public readonly double Distance => Math.Sqrt(X * X + Y * Y + Z * Z);

    public readonly override string ToString() => $"{X}, {Y}, {Z}";
}
```

Předchozí ukázka zobrazuje mnoho umístění, kde `readonly` můžete použít modifikátor: metody, vlastnosti a přístupové objekty vlastností. Pokud používáte automaticky implementované vlastnosti, `readonly` kompilátor `get` přidá modifikátor do přistupujícího objektu pro vlastnosti čtení a zápisu. Kompilátor přidá `readonly` modifikátor automaticky implementované deklarace vlastností pro vlastnosti s pouze přistupujícím objektem. `get`

Přidání `readonly` modifikátor u členů, které nemutují stav poskytuje dvě související výhody. Nejprve kompilátor vynucuje váš záměr. Tento člen nemůže mutovat stav struktury, ani nemůže získat přístup k členu, který není také označen `readonly`. Za druhé kompilátor nevytvoří obranné `in` kopie parametrů při `readonly` přístupu k členu. Kompilátor může tuto optimalizaci bezpečně provést, protože zaručuje, že `struct` člen není změněn. `readonly`

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>Použít `ref readonly return` příkazy pro velké struktury, pokud je to možné

Můžete vrátit hodnoty odkazem, pokud vrácená hodnota není místní pro metodu vrácení. Vrácení odkazem znamená, že je zkopírován pouze odkaz, nikoli struktura. V následujícím příkladu `Origin` vlastnost nemůže použít `ref` return, protože vrácená hodnota je místní proměnná:

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

Následující definice vlastnosti však může být vrácena odkazem, protože vrácená hodnota je statický člen:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

Nechcete, aby volající upravovali původ, takže byste měli `ref readonly`vrátit hodnotu pomocí :

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

Vrácení `ref readonly` umožňuje uložit kopírování větší struktury a zachovat neměnnost interních datových členů.

Na webu volání volající provést volbu `Origin` použít vlastnost `ref readonly` jako nebo jako hodnotu:

[!code-csharp[AssignRefReadonly](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

První přiřazení v předchozím kódu vytvoří kopii konstanty `Origin` a přiřadí tuto kopii. Druhý přiřadí odkaz. Všimněte `readonly` si, že modifikátor musí být součástí deklarace proměnné. Odkaz, na který odkazuje nelze změnit. Pokusy o to mít za následek chybu v době kompilace.

Modifikátor `readonly` je vyžadován `originReference`na prohlášení .

Kompilátor vynucuje, že volající nemůže změnit odkaz. Pokusy o přiřazení hodnoty přímo generují chybu v době kompilace. Kompilátor však nemůže vědět, pokud libovolná metoda člena upravuje stav struktury.
Chcete-li zajistit, že objekt není změněn, kompilátor vytvoří kopii a volá členské odkazy pomocí této kopie. Jakékoliv změny jsou na této obranné kopii.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>Použijte `in` modifikátor na `readonly struct` parametry větší než`System.IntPtr.Size`

Klíčové `in` slovo doplňuje `ref` existující `out` a klíčová slova předat argumenty odkazem. Klíčové `in` slovo určuje předání argumentu odkazem, ale volaná metoda hodnotu nezmění.

Tento dodatek poskytuje úplnou slovní zásobu vyjádřit svůj záměr návrhu.
Typy hodnot jsou zkopírovány při předání do volané metody, pokud v podpisu metody nezadáte žádný z následujících modifikátorů. Každý z těchto modifikátorů určuje, že proměnná je předána odkazem, čímž se zabrání kopii. Každý modifikátor vyjadřuje jiný záměr:

- `out`: Tato metoda nastaví hodnotu argumentu použitého jako tento parametr.
- `ref`: Tato metoda může nastavit hodnotu argumentu použitého jako tento parametr.
- `in`: Tato metoda nemění hodnotu argumentu použitého jako tento parametr.

Přidejte `in` modifikátor předat argument odkazem a deklarovat záměr návrhu předat argumenty odkazem, aby se zabránilo zbytečné kopírování. Nemáte v úmyslu změnit objekt použitý jako tento argument.

Tento postup často zlepšuje výkon pro typy hodnot <xref:System.IntPtr.Size?displayProperty=nameWithType>jen pro čtení, které jsou větší než . U jednoduchých`sbyte` `byte`typů `short` `ushort`( `int` `uint`, `long` `ulong`, `char` `float`, `double` `decimal` , `bool`, `enum` , , , , , a , a typy) jsou potenciální zvýšení výkonu minimální. Ve skutečnosti může snížit výkon pomocí pass-by-reference <xref:System.IntPtr.Size?displayProperty=nameWithType>pro typy menší než .

Následující kód ukazuje příklad metody, která vypočítá vzdálenost mezi dvěma body v 3D prostoru.

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Argumenty jsou dvě struktury, z nichž každá obsahuje tři doubles. Double je 8 bajtů, takže každý argument je 24 bajtů. Zadáním `in` modifikátoru předáte 4 bajtový nebo osmibajtový odkaz na tyto argumenty v závislosti na architektuře počítače. Rozdíl ve velikosti je malý, ale sečte se při volání této metody aplikace v těsné smyčce pomocí mnoha různých hodnot.

Modifikátor `in` `out` doplňuje `ref` a i jinými způsoby. Nelze vytvořit přetížení metody, které se liší pouze `in`v `out`přítomnosti `ref`, , nebo . Tato nová pravidla rozšířit stejné chování, `out` které `ref` bylo vždy definováno pro a parametry. Stejně `out` `ref` jako modifikátory a typy hodnot `in` nejsou zabaleny, protože je použit modifikátor.

Modifikátor `in` lze použít na libovolný člen, který přebírá parametry: metody, delegáti, lambdy, místní funkce, indexery, operátory.

Další vlastností `in` parametrů je, že můžete použít literálové `in` hodnoty nebo konstanty pro argument parametru. Také na `ref` rozdíl `out` od parametru nebo není `in` nutné použít modifikátor na webu volání. Následující kód ukazuje dva příklady `CalculateDistance` volání metody. První používá dvě místní proměnné předané odkazem. Druhý obsahuje dočasnou proměnnou vytvořenou jako součást volání metody.

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Existuje několik způsobů, ve kterém kompilátor vynucuje povahu `in` argumentu jen pro čtení.  Za prvé, volaná metoda nemůže přímo `in` přiřadit parametru. Nemůže přímo přiřadit žádné pole parametru, `in` pokud je `struct` tato hodnota typu. Kromě toho nelze předat `in` parametr žádné metodě `ref` pomocí `out` modifikátoru nebo.
Tato pravidla platí pro `in` libovolné pole parametru za `struct` předpokladu, že `struct` pole je typ a parametr je také typ. Ve skutečnosti tato pravidla platí pro více vrstev přístupu členů za `structs`předpokladu, že typy na všech úrovních přístupu členů jsou .
Kompilátor vynucuje, že `struct` typy předané jako `in` argumenty a jejich `struct` členové jsou proměnné jen pro čtení při použití jako argumenty pro jiné metody.

Použití `in` parametrů může zabránit potenciálním nákladům na výkon vytváření kopií. Nezmění sémantiku žádné volání metody. Proto není nutné zadat `in` modifikátor na webu volání. Vynechání `in` modifikátoru na webu volání informuje kompilátor, že je povoleno vytvořit kopii argumentu z následujících důvodů:

- Existuje implicitní převod, ale ne převod identity z typu argumentu na typ parametru.
- Argument je výraz, ale nemá známou proměnnou úložiště.
- Existuje přetížení, které se liší přítomností `in`nebo nepřítomností . V takovém případě je přetížení podle hodnoty lepší shodu.

Tato pravidla jsou užitečné při aktualizaci existujícího kódu pro použití argumentů odkazů jen pro čtení. Uvnitř volané metody můžete volat libovolnou metodu instance, která používá parametry hodnoty. V těchto případech je vytvořena `in` kopie parametru. Vzhledem k tomu, že kompilátor může vytvořit dočasnou proměnnou pro libovolný `in` parametr, můžete také zadat výchozí hodnoty pro libovolný `in` parametr. Následující kód určuje počátek (bod 0,0) jako výchozí hodnotu pro druhý bod:

[!code-csharp[InArgumentDefault](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Chcete-li vynutit, aby kompilátor předával `in` argumenty jen pro čtení odkazem, zadejte modifikátor argumentů na webu volání, jak je znázorněno v následujícím kódu:

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

Toto chování usnadňuje `in` přijmout parametry v průběhu času ve velkých základy kódu, kde je možné zvýšení výkonu. `in` Modifikátor nejprve přidáte k podpisům metody. Potom můžete přidat `in` modifikátor na `readonly struct` weby volání a vytvořit typy povolit kompilátoru, aby se zabránilo vytváření obranných `in` kopií parametrů ve více umístěních.

Označení `in` parametru lze také použít s typy odkazů nebo číselnými hodnotami. Nicméně, výhody v obou případech jsou minimální, pokud existují.

## <a name="avoid-mutable-structs-as-an-in-argument"></a>Vyhněte se proměnlivým `in` strukturám jako argumentu

Výše popsané techniky vysvětlují, jak se vyhnout kopiím vrácením odkazů a předávání mů e-li odkazovat. Tyto techniky fungují nejlépe, když `readonly struct` jsou typy argumentů deklarovány jako typy. V opačném případě musí kompilátor vytvořit **obranné kopie** v mnoha situacích k vynucení pouze pro čtení všech argumentů. Vezměme si následující příklad, který vypočítá vzdálenost 3D bodu od počátku:

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Struktura `Point3D` *není* jen pro čtení struktury. Existuje šest různých volání přístupu vlastností v těle této metody. Při prvním vyšetření jste si možná mysleli, že tyto přístupy jsou bezpečné. Koneckonců, `get` přistupující objekt by neměl měnit stav objektu. Ale neexistuje žádné jazykové pravidlo, které by to vynucova. Je to jen běžná konvence. Libovolný typ může `get` implementovat přistupujícího pole, které upravilo vnitřní stav. Bez záruky některých jazyků musí kompilátor vytvořit dočasnou kopii argumentu před voláním libovolného člena, který není označen modifikátorem. `readonly` Dočasné úložiště je vytvořeno v zásobníku, hodnoty argumentu jsou zkopírovány do dočasného úložiště a hodnota `this` je zkopírována do zásobníku pro každý přístup člena jako argument. V mnoha situacích tyto kopie poškodit výkon natolik, že pass-by-value je rychlejší než pass-by-readonly-reference, pokud typ argumentu `readonly struct` není a a metoda volá členy, které nejsou označeny `readonly`. Pokud označíte všechny metody, které nemění `readonly`stav struktury jako , kompilátor může bezpečně určit, že stav struktury není změněn a obranná kopie není potřeba.

Místo toho, pokud výpočet vzdálenosti používá neměnnou strukturu, `ReadonlyPoint3D`, dočasné objekty nejsou potřeba:

[!code-csharp[readonlyInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

Kompilátor generuje efektivnější kód při volání `readonly struct`členů `this` : Odkaz namísto kopie příjemce je `in` vždy parametr předaný odkazem na metodu člena. Tato optimalizace uloží kopírování při `readonly struct` použití `in` jako argument.

Jako argument byste neměli předávat `in` typ hodnoty s možnou hodnotou s možnou hodnotou. Typ <xref:System.Nullable%601> není deklarován jako struktura jen pro čtení. To znamená, že kompilátor musí generovat obranné kopie pro všechny `in` argumenty typu hodnoty s možnou hodnotou null předané metodě pomocí modifikátoru v deklaraci parametru.

Můžete vidět ukázkový program, který demonstruje rozdíly ve výkonu pomocí [BenchmarkDotNet](https://www.nuget.org/packages/BenchmarkDotNet/) v našem [úložišti ukázek](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) na GitHubu. Porovnává předání proměnlivé struktury podle hodnoty a odkazem s předáním neměnné struktury podle hodnoty a odkazem. Použití neměnné struktury a předat odkazem je nejrychlejší.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Použití `ref struct` typů pro práci s bloky nebo pamětí v jednom rámci zásobníku

Související funkce jazyka je schopnost deklarovat typ hodnoty, který musí být omezen na jeden rámec zásobníku. Toto omezení umožňuje kompilátoru provést několik optimalizací. Primární motivací pro <xref:System.Span%601> tuto funkci byla a související struktury. Z těchto vylepšení dosáhnete zlepšení min. pomocí nových a aktualizovaných <xref:System.Span%601> rozhraní API rozhraní .NET, která používají daný typ.

Můžete mít podobné požadavky práce [`stackalloc`](language-reference/operators/stackalloc.md) s pamětí vytvořené pomocí nebo při použití paměti z interop API. Pro tyto potřeby `ref struct` můžete definovat vlastní typy.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct`Typ

Deklarování struktury `readonly ref` jako kombinuje výhody `ref struct` a `readonly struct` omezení a prohlášení. Paměť používaná rozsahem jen pro čtení je omezena na jeden rámec zásobníku a paměť používanou pouze pro čtení nelze změnit.

## <a name="conclusions"></a>Závěry

Použití typů hodnot minimalizuje počet operací přidělení:

- Úložiště pro typy hodnot je zásobník přidělen pro místní proměnné a argumenty metody.
- Úložiště pro typy hodnot, které jsou členy jiných objektů je přidělena jako součást tohoto objektu, nikoli jako samostatné přidělení.
- Úložiště pro vrácené hodnoty typu hodnoty je přiděleno zásobníku.

Kontrast, že s typy odkazů v těchto stejných situacích:

- Úložiště pro typy odkazů jsou haldy přiděleny pro místní proměnné a argumenty metody. Odkaz je uložen v zásobníku.
- Úložiště pro referenční typy, které jsou členy jiných objektů jsou samostatně přiděleny na haldě. Obsahující objekt ukládá odkaz.
- Úložiště pro návratové hodnoty referenčního typu je přiděleno haldy. Odkaz na toto úložiště je uložen v zásobníku.

Minimalizace přidělení přichází s kompromisy. Zkopírujete více paměti, `struct` pokud je velikost větší než velikost odkazu. Odkaz je obvykle 64 bitů nebo 32 bitů a závisí na procesoru cílového počítače.

Tyto kompromisy mají obecně minimální dopad na výkon. Však pro velké struktury nebo větší kolekce, zvýšení dopadu na výkon. Dopad může být velký v těsných smyčkách a horkých cestách pro programy.

Tato vylepšení jazyka C# jsou určeny pro algoritmy kritické pro výkon, kde minimalizace přidělení paměti je hlavním faktorem při dosahování potřebného výkonu. Možná zjistíte, že tyto funkce často nepoužíváte v kódu, který píšete. Tato vylepšení však byla přijata v celém rozhraní .NET. Vzhledem k tomu, že stále více a více api využívají tyto funkce, uvidíte, že výkon vašich aplikací se zlepší.

## <a name="see-also"></a>Viz také

- [klíčové slovo ref](language-reference/keywords/ref.md)
- [Návratové hodnoty podle odkazu a lokální proměnné podle odkazu](programming-guide/classes-and-structs/ref-returns.md)
