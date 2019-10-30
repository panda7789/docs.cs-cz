---
title: Zápis bezpečného a C# efektivního kódu
description: Nedávná vylepšení C# jazyka umožňují psát ověřitelný bezpečný kód, který byl dříve přidružen k nezabezpečenému kódu.
ms.date: 10/23/2018
ms.technology: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: 3dc3213cf24f4cdd8f0f1b7752263b4a609b2fa2
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039632"
---
# <a name="write-safe-and-efficient-c-code"></a>Zápis bezpečného a C# efektivního kódu

Nové funkce v C# umožňují psát ověřitelný bezpečný kód s lepším výkonem. Pokud tyto techniky pečlivě použijete, bude méně scénářů vyžadovat nezabezpečený kód. Tyto funkce usnadňují použití odkazů na typy hodnot jako argumenty metody a návratové metody. Po bezpečném provedení tyto techniky minimalizují kopírování hodnotových typů. Pomocí typů hodnot můžete minimalizovat počet přidělení a průchodů uvolňování paměti.

Většina vzorového kódu v tomto článku používá funkce přidané v C# 7,2. Chcete-li tyto funkce používat, je nutné nakonfigurovat projekt tak C# , aby používal 7,2 nebo novější. Další informace o nastavení jazykové verze najdete v tématu [Konfigurace jazykové verze](language-reference/configure-language-version.md).

Tento článek se zaměřuje na techniky pro efektivní správu prostředků. Jednou z výhod použití hodnotových typů je, že často brání přidělení haldy. Nevýhodou je, že se zkopírují podle hodnoty. Tyto kompromisy usnadňují optimalizaci algoritmů, které pracují s velkými objemy dat. Nové funkce jazyka v C# 7,2 poskytují mechanismy, které umožňují bezpečný efektivní kód pomocí odkazů na typy hodnot. Pomocí těchto funkcí můžete minimalizovat operace přidělování i kopírování. Tento článek popisuje tyto nové funkce.

Tento článek se zaměřuje na následující techniky správy prostředků:

- Deklarovat [`readonly struct`](language-reference/keywords/readonly.md#readonly-struct-example) pro vyjádření, že typ je **neměnný** a umožňuje kompilátoru ukládat kopie při použití parametrů [`in`](language-reference/keywords/in-parameter-modifier.md) .
- Pokud typ nemůže být neměnný, deklarujte `struct` členů `readonly` k označení toho, že člen nemění stav.
- Použijte [`ref readonly`](language-reference/keywords/ref.md#reference-return-values) vrátit, pokud je návratová hodnota `struct` větší než <xref:System.IntPtr.Size?displayProperty=nameWithType> a životnost úložiště je větší než metoda, která vrací hodnotu.
- Pokud je velikost `readonly struct` větší než <xref:System.IntPtr.Size?displayProperty=nameWithType>, měli byste ji předat jako parametr `in` z důvodů výkonu.
- Nikdy nepředávejte `struct` jako parametr `in`, pokud není deklarován s modifikátorem `readonly` nebo metoda volá pouze `readonly` členů struktury. Porušení těchto pokynů může negativně ovlivnit výkon a může vést k zakrytí chování.
- Pro práci s pamětí jako posloupnosti bajtů použijte [`ref struct`](language-reference/keywords/ref.md#ref-struct-types)nebo `readonly ref struct`, jako je například <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601>.

Tyto techniky vynutí vyrovnávání dvou konkurenčních cílů s ohledem na **reference** a **hodnoty**. Proměnné, které jsou [odkazové typy](programming-guide/types/index.md#reference-types) , uchovávají odkaz na umístění v paměti. Proměnné, které jsou [typy hodnot](programming-guide/types/index.md#value-types) přímo obsahují jejich hodnotu. Tyto rozdíly zvýrazňují klíčové rozdíly, které jsou důležité pro správu paměťových prostředků. **Typy hodnot** jsou obvykle zkopírovány, když jsou předány metodě nebo vráceny z metody. Toto chování zahrnuje kopírování hodnoty `this` při volání členů typu hodnoty. Náklady na kopii se týkají velikosti typu. **Typy odkazů** jsou přiděleny na spravovanou haldu. Každý nový objekt vyžaduje nové přidělení a následně musí být uvolněn. Obě tyto operace probírají čas. Odkaz je zkopírován, pokud je typ odkazu předán jako argument metodě nebo vrácen z metody.

Tento článek používá následující vzorový koncept struktury 3D bodů pro vysvětlení těchto doporučení:

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

Různé příklady používají různé implementace tohoto konceptu.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Deklarovat struktury ReadOnly pro neměnné hodnoty typů

Deklarace `struct` pomocí modifikátoru `readonly` informuje kompilátor, že váš záměr je vytvořit neměnný typ. Kompilátor vynutil toto rozhodnutí o návrhu pomocí následujících pravidel:

- Všechny členy polí musí být `readonly`
- Všechny vlastnosti musí být jen pro čtení, včetně automaticky implementovaných vlastností.

Tato dvě pravidla jsou dostačující, aby se zajistilo, že žádný člen `readonly struct` nemění stav této struktury. `struct` je neměnný. `Point3D` struktura může být definována jako neproměnlivá struktura, jak je znázorněno v následujícím příkladu:

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

Toto doporučení použijte vždy, když je záměrem návrhu vytvořit neměnný typ hodnoty. Další výhodou je zvýšení výkonu. `readonly struct` jasně vyjadřuje záměr návrhu.

## <a name="declare-readonly-members-when-a-struct-cant-be-immutable"></a>Deklarovat členy jen pro čtení, pokud struktura nemůže být neměnná

V C# 8,0 a novějších platí, že pokud je typ struktury proměnlivý, měli byste deklarovat členy, které nezpůsobí, že by mutace byly`readonly`. Například následující je proměnlivá varianta struktury 3D bodů:

```csharp
public struct Point3D
{
    public Point3D(double x, double y, double z)
    {
        this.X = x;
        this.Y = y;
        this.Z = z;
    }

    private double _x;
    public double X 
    { 
        readonly get { return _x;}; 
        set { _x = value; }
    }
    
    private double _y;
    public double Y 
    { 
        readonly get { return _y;}; 
        set { _y = value; }
    }

    private double _z;
    public double Z 
    { 
        readonly get { return _z;}; 
        set { _z = value; }
    }

    public readonly double Distance => Math.Sqrt(X * X + Y * Y + Z * Z);

    public readonly override string ToString() => $"{X, Y, Z }";
}
```

Předchozí příklad ukazuje mnoho umístění, kde lze použít modifikátor `readonly`: metody, vlastnosti a přistupující objekty vlastností. Použijete-li automaticky implementované vlastnosti, kompilátor přidá modifikátor `readonly` k přístupovému objektu `get` pro čtení a zápis vlastností. Kompilátor přidá modifikátor `readonly` pro automaticky implementované deklarace vlastností pro vlastnosti, které mají pouze přistupující objekt `get`.

Přidání modifikátoru `readonly` do členů, kteří nepoužívají stav, poskytuje dvě související výhody. Za prvé vynutil kompilátor váš záměr. Tento člen nemůže být součástí stavu struktury, ani nemůže přistupovat ke členu, který není označen také jako `readonly`. Za druhé kompilátor při přístupu ke členu `readonly` nevytvoří obrannou linií kopie parametrů `in`. Kompilátor může tuto optimalizaci bezpečně provést, protože zaručuje, že `readonly` člen nemění `struct`.

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>Pokud je to možné, používejte příkazy `ref readonly return` pro velké struktury.

Hodnoty můžete vrátit odkazem, pokud hodnota vracená není lokální vůči návratové metodě. Vrácení odkazem znamená, že je zkopírován pouze odkaz, nikoli struktura. V následujícím příkladu vlastnost `Origin` nemůže použít `ref` vrácení, protože vrácená hodnota je místní proměnná:

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

Následující definici vlastnosti však lze vrátit odkazem, protože vrácená hodnota je statický člen:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

Nechcete, aby volající měnili počátek, takže byste měli vrátit hodnotu `readonly ref`:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

Vrácení `ref readonly` umožňuje uložit kopírování větších struktur a zachovat neměnnosti vašich interních datových členů.

Na webu volání využije volající možnost použít vlastnost `Origin` jako `readonly ref` nebo jako hodnotu:

[!code-csharp[AssignRefReadonly](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

První přiřazení v předchozím kódu vytvoří kopii `Origin` konstanty a přiřadí tuto kopii. Druhý přiřadí odkaz. Všimněte si, že modifikátor `readonly` musí být součástí deklarace proměnné. Odkaz, na který se odkazuje, se nedá změnit. Pokusí se to provést za účelem chyby při kompilaci.

V deklaraci `originReference`je vyžadován modifikátor `readonly`.

Kompilátor vynutil, že volající nemůže upravit odkaz. Pokusí se přiřadit hodnotu přímo generovat chybu při kompilaci. Kompilátor však nemůže zjistit, zda jakákoli metoda člena mění stav struktury.
Aby se zajistilo, že se objekt nezměnil, kompilátor vytvoří kopii a zavolá odkazy členů pomocí této kopie. Jakékoli úpravy této obrannou linií kopie.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>Použijte modifikátor `in` pro `readonly struct` parametrů větších než `System.IntPtr.Size`

Klíčové slovo `in` doplňuje existující `ref` a `out` klíčová slova, aby předávala argumenty odkazem. Klíčové slovo `in` určuje předání argumentu odkazem, ale volaná metoda neupravuje hodnotu.

Tento doplněk poskytuje úplný slovník pro vyjádření záměru návrhu.
Typy hodnot jsou zkopírovány při předání do volané metody, pokud nezadáte žádné z následujících modifikátorů v signatuře metody. Každý z těchto modifikátorů určuje, že proměnná je předána odkazem, který vyloučí kopii. Každý modifikátor vyjadřuje jiný záměr:

- `out`: Tato metoda nastaví hodnotu argumentu použitého jako tento parametr.
- `ref`: Tato metoda může nastavit hodnotu argumentu použitého jako tento parametr.
- `in`: Tato metoda neupravuje hodnotu argumentu použitého jako tento parametr.

Přidejte modifikátor `in`, který předává argument odkazem a deklaruje záměr návrhu k předání argumentů odkazem, aby nedocházelo k zbytečnému kopírování. Nebudete mít v úmyslu upravovat objekt použitý jako argument.

Tento postup často vylepšuje výkon pro typy hodnot ReadOnly, které jsou větší než <xref:System.IntPtr.Size?displayProperty=nameWithType>. Pro jednoduché typy (`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` a `bool`a `enum` typy) , všechny potenciální nárůsty výkonu jsou minimální. Ve skutečnosti se výkon může snížit pomocí předávacího odkazu pro typy menší než <xref:System.IntPtr.Size?displayProperty=nameWithType>.

Následující kód ukazuje příklad metody, která vypočítá vzdálenost mezi dvěma body v 3D prostoru.

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Argumenty jsou dvě struktury, které obsahují tři dvojité. Dvojitá přesnost je 8 bajtů, takže každý argument je 24 bajtů. Zadáním modifikátoru `in` předáte do těchto argumentů odkaz na 4 bajty nebo 8 bajtů v závislosti na architektuře počítače. Rozdíl velikosti je malý, ale přidává se, když vaše aplikace volá tuto metodu v těsné smyčce pomocí řady různých hodnot.

Modifikátor `in` doplňuje `out` a `ref` jiným způsobem. Nelze vytvořit přetížení metody, která se liší pouze v přítomnosti `in`, `out`nebo `ref`. Tato nová pravidla rozšíří stejné chování, které bylo vždy definováno pro parametry `out` a `ref`. Podobně jako modifikátory `out` a `ref` nejsou typy hodnot zabalené, protože je použit modifikátor `in`.

Modifikátor `in` lze použít pro libovolného člena, který přebírá parametry: metody, delegáty, výrazy lambda, místní funkce, indexery, operátory.

Další funkcí `in` parametrů je, že pro argument `in` parametr můžete použít literálové hodnoty nebo konstanty. Navíc na rozdíl od `ref` nebo `out` parametr není nutné použít modifikátor `in` na webu volání. Následující kód ukazuje dva příklady volání metody `CalculateDistance`. První používá dvě místní proměnné předané odkazem. Druhý zahrnuje dočasnou proměnnou vytvořenou jako součást volání metody.

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Existuje několik způsobů, jak kompilátor vynutil charakter `in` argument jen pro čtení.  První z nich volaná metoda se nemůže přímo přiřadit k parametru `in`. Nelze ji přímo přiřadit k žádnému poli `in` parametr, pokud je tato hodnota typu `struct`. Kromě toho nemůžete předat parametr `in` žádné metodě pomocí modifikátoru `ref` nebo `out`.
Tato pravidla platí pro každé pole parametru `in`, pokud je pole typem `struct` a parametr je také `struct` typ. Ve skutečnosti platí, že tato pravidla se použijí pro přístup k více vrstvám členů, přičemž typy na všech úrovních přístupu členů jsou `structs`.
Kompilátor vynutil, že `struct` typy předávané jako `in` argumenty a jejich `struct` členové jsou proměnné jen pro čtení, pokud se používají jako argumenty pro jiné metody.

Použití parametrů `in` se může vyhnout potenciálním nákladům na výkon při vytváření kopií. Nemění sémantiku žádného volání metody. Proto není nutné zadávat modifikátor `in` na webu volání. Vynechání modifikátoru `in` na webu volání informuje kompilátor, že je povoleno vytvořit kopii argumentu z následujících důvodů:

- Existuje implicitní převod, ale nikoli převod identity z typu argumentu na typ parametru.
- Argument je výraz, ale nemá známou proměnnou úložiště.
- Existuje přetížení, které se liší podle přítomnosti nebo nepřítomnosti `in`. V takovém případě je přetížení podle hodnot lepší shodu.

Tato pravidla jsou užitečná, když aktualizujete existující kód tak, aby používal argumenty odkazu jen pro čtení. Uvnitř volané metody můžete zavolat libovolnou metodu instance, která používá parametry hodnot. V těchto případech je vytvořena kopie parametru `in`. Vzhledem k tomu, že kompilátor může vytvořit dočasnou proměnnou pro libovolný parametr `in`, můžete také zadat výchozí hodnoty pro libovolný parametr `in`. Následující kód určuje počátek (bod 0, 0) jako výchozí hodnotu pro druhý bod:

[!code-csharp[InArgumentDefault](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Chcete-li vynutit, aby kompilátor předal argumenty jen pro čtení odkazem, určete `in` modifikátor u argumentů na webu volání, jak je znázorněno v následujícím kódu:

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

Toto chování usnadňuje přijímání parametrů `in` v průběhu času v rozsáhlých základech kódu, kde je možné nárůst výkonu. Nejprve přidáte modifikátor `in` k podpisům metod. Pak můžete přidat modifikátor `in` na webech volání a vytvořit `readonly struct` typy a povolit tak kompilátoru, aby se zabránilo vytváření obrannou linií kopií parametrů `in` ve více umístěních.

Označení parametru `in` lze také použít s odkazovým typem nebo číselnými hodnotami. Výhody v obou případech jsou však minimální, pokud existují.

## <a name="never-use-mutable-structs-as-in-in-argument"></a>Nikdy nepoužívejte proměnlivé struktury jako v argumentu `in`

Výše popsané techniky vysvětlují, jak se vyhnout kopiím vrácením odkazů a předáním hodnot odkazem. Tyto techniky fungují nejlépe, pokud jsou typy argumentů deklarovány jako `readonly struct` typy. V opačném případě kompilátor musí vytvořit **obrannou linií kopie** v mnoha situacích, aby se vynutila vlastnost ReadOnly-Ness všech argumentů. Vezměte v úvahu následující příklad, který vypočítá vzdálenost prostorového bodu od počátku:

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Struktura *`Point3D` není struktura* jen pro čtení. V těle této metody je k dispozici šest různých volání přístupu k vlastnostem. Při prvním zkoumání jste si možná mysleli, že tyto přístupy byly bezpečné. Po všech případech přistupující objekt `get` by neměl upravovat stav objektu. Nejedná se ale o žádné jazykové pravidlo, které to vynutilo. Je to jenom běžná konvence. Libovolný typ může implementovat přistupující objekt `get`, který změnil vnitřní stav. Bez záruky jazyka musí kompilátor vytvořit dočasnou kopii argumentu před voláním libovolného člena. Dočasné úložiště je vytvořeno v zásobníku, hodnoty argumentu jsou zkopírovány do dočasného úložiště a hodnota je zkopírována do zásobníku pro každý přístup člena jako argument `this`. V mnoha situacích tyto kopie poškozují výkon, takže pokud typ argumentu není `readonly struct`, je průchozí hodnota rychlejší než odkaz Pass-by-ReadOnly.

Místo toho, pokud výpočet vzdálenosti používá neproměnlivou strukturu `ReadonlyPoint3D`, dočasné objekty nejsou potřeba:

[!code-csharp[readonlyInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

Kompilátor generuje efektivnější kód při volání členů `readonly struct`: `this` odkaz namísto kopie příjemce je vždy parametr `in` předaný odkazem na metodu člena. Tato optimalizace ukládá kopírování při použití `readonly struct` jako argumentu `in`.

Nemůžete předat typ hodnoty s možnou hodnotou null jako argument `in`. Typ <xref:System.Nullable%601> není deklarován jako struktura jen pro čtení. To znamená, že kompilátor musí generovat obrannou linií kopie pro libovolný argument typu hodnoty s možnou hodnotou null předaný metodě pomocí modifikátoru `in` v deklaraci parametru.

Můžete si prohlédnout ukázkový program, který ukazuje rozdíly v výkonu pomocí [BenchmarkDotNet](https://www.nuget.org/packages/BenchmarkDotNet/) v našem [úložišti ukázek](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) na GitHubu. Porovná předání proměnlivé struktury podle hodnoty a odkazu s předáním neměnné struktury podle hodnoty a odkazu. Použití neproměnlivé struktury a předávání odkazem je nejrychlejší.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Použití typů `ref struct` pro práci s bloky nebo pamětí v jednom bloku zásobníku

Související funkce jazyka je schopnost deklarovat typ hodnoty, který musí být omezen na jeden rámec zásobníku. Toto omezení umožňuje kompilátoru provést několik optimalizací. Primární motivace pro tuto funkci byla <xref:System.Span%601> a související struktury. Zvýšení výkonu z těchto vylepšení dosáhnete pomocí nových a aktualizovaných rozhraní API .NET, která využívají <xref:System.Span%601>ho typu.

Můžete mít podobné požadavky na práci s pamětí vytvořenou pomocí [`stackalloc`](language-reference/operators/stackalloc.md) nebo při použití paměti z rozhraní API pro interoperabilitu. Pro tyto potřeby můžete definovat vlastní typy `ref struct`.

## <a name="readonly-ref-struct-type"></a>typ `readonly ref struct`

Deklarace struktury jako `readonly ref` kombinuje výhody a omezení deklarace `ref struct` a `readonly struct`. Paměť využitá rozsahem jen pro čtení je omezená na jeden rámec zásobníku a paměť, kterou používá rozsah jen pro čtení, se nedá změnit.

## <a name="conclusions"></a>Závěry

Použití typů hodnot minimalizuje počet operací přidělení:

- Úložiště pro typy hodnot je zásobník přidělený pro lokální proměnné a argumenty metody.
- Úložiště pro typy hodnot, které jsou členy jiných objektů, je přiděleno jako součást tohoto objektu, nikoli jako samostatné přidělení.
- Úložiště pro návratové hodnoty typu hodnoty je přiděleno zásobníku.

Rozdíl mezi typy odkazů v těchto situacích:

- Úložiště pro typy odkazů je halda přidělená pro lokální proměnné a argumenty metody. Odkaz je uložený v zásobníku.
- Úložiště pro typy odkazů, které jsou členy jiných objektů, je samostatně přiděleno na haldu. Obsahující objekt ukládá odkaz.
- Úložiště pro návratové hodnoty typu odkazu je přidělena halda. Odkaz na toto úložiště je uložený v zásobníku.

Minimalizace přidělení přináší s kompromisy. Pokud je velikost `struct` větší než velikost odkazu, zkopírujete více paměti. Odkaz obvykle je 64 bitů nebo 32 bitů a závisí na procesoru cílového počítače.

Tyto kompromisy mají obvykle minimální dopad na výkon. U rozsáhlých struktur nebo větších kolekcí se ale zvyšuje dopad na výkon. Dopad může být velký v těsných smyčkách a horké cesty pro programy.

Tato vylepšení C# jazyka jsou navržena pro kritické algoritmy výkonu, kde minimalizace přidělení paměti je významným faktorem při dosahování potřebného výkonu. Možná zjistíte, že tyto funkce nepoužíváte často v kódu, který píšete. Tato vylepšení se ale přijala v rámci .NET. Díky většímu množství rozhraní API využívají tyto funkce, ale můžete zlepšit výkon aplikací.

## <a name="see-also"></a>Viz také:

- [ref – klíčové slovo](language-reference/keywords/ref.md)
- [Návratové a místní referenční hodnoty](programming-guide/classes-and-structs/ref-returns.md)
