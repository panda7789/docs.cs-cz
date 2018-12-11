---
title: Zápis bezpečný a účinný C# kódu
description: Poslední vylepšení C# jazyk umožňují také napsat bezpečného kódu s možností ověření, že výkon bylo dřív přidružené nezabezpečený kód.
ms.date: 10/23/2018
ms.custom: mvc
ms.openlocfilehash: 35d9cf89d8ba2ddb673554a76eb33ae59b178b42
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245685"
---
# <a name="write-safe-and-efficient-c-code"></a>Zápis bezpečný a účinný C# kódu

Nové funkce v C# umožňují také napsat ověřitelný kód bezpečně s lepším výkonem. Pokud použijete pečlivě těchto technik, méně scénáře vyžadují nezabezpečený kód. Tyto funkce usnadnění použití odkazů na typy hodnot jako argumenty metody a metoda vrátí hodnotu. Po dokončení bezpečně, minimalizovat těchto technik kopírování hodnotové typy. Pomocí typů hodnot lze minimalizovat počet přidělování a uvolňování paměti kolekce předá.

Většina ukázek kódu v tomto článku používá funkce přidané ve C# 7.2. Pokud chcete používat tyto funkce, je nutné nakonfigurovat projektu pro použití C# 7.2 nebo novější. Další informace o nastavení jazykové verze, najdete v části [konfigurace jazyková verze](language-reference/configure-language-version.md).

Tento článek se zaměřuje na techniky pro efektivní resource management. Jednou z výhod použití jiných typů hodnot je, že často vyhnout přidělení haldy. Nevýhodou je, že nezkopírují podle hodnoty. Tato kompromis učiní obtížnější pro optimalizaci algoritmů, které pracují na velkých objemů dat. Nový jazyk funkce v C# 7.2 poskytují mechanismy, které umožňují bezpečné efektivní kódu pomocí odkazů na typy hodnot. Pomocí těchto funkcí dobře minimalizovat obou přidělení a operací kopírování. Tento článek se věnuje tyto nové funkce.

Tento článek se týká následujících postupů správy prostředků:

- Deklarace [ `readonly struct` ](language-reference/keywords/readonly.md#readonly-struct-example) vyjádřit, že je typem **neměnné** a umožňuje kompilátoru se uložit kopie při použití [ `in` ](language-reference/keywords/in-parameter-modifier.md) parametry.
- Použití [ `ref readonly` ](language-reference/keywords/ref.md#reference-return-values) vrácené v případě, že návratová hodnota je `struct` větší než <xref:System.IntPtr.Size?displayProperty=nameWithType> a životního cyklu úložiště je větší než metoda vrátí hodnotu.
- Pokud velikost `readonly struct` je větší než <xref:System.IntPtr.Size?displayProperty=nameWithType>, je třeba předat ji jako `in` parametr z důvodů výkonu.
- Nikdy předat `struct` jako `in` parametr Pokud je deklarovaná s `readonly` modifikátor protože mohou negativně ovlivnit výkon a může vést k skrytého chování.
- Použití [ `ref struct` ](language-reference/keywords/ref.md#ref-struct-types), nebo `readonly ref struct` například <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601> pro práci s pamětí jako sekvence bajtů.

Tyto postupy požadovat, abyste pro dvě konkurenční cíle s ohledem na **odkazy** a **hodnoty**. Proměnné, které jsou [referenční typy](programming-guide/types/index.md#reference-types) uložení odkazu na umístění v paměti. Proměnné, které jsou [typů hodnot](programming-guide/types/index.md#value-types) přímo obsahují své hodnoty. Tyto rozdíly zvýrazněte klíčové rozdíly, které jsou důležité pro správu paměťových prostředků. **Typy hodnot** jsou obvykle kopírovat, pokud je předána metodě nebo vrátil z metody. Toto chování zahrnuje kopírování hodnoty `this` při volání metody členy typu hodnoty. Náklady na kopírování se týká velikosti typu. **Odkazování na typy** jsou přidělovány na spravované haldě. Každý nový objekt vyžaduje nové přidělení a následně musí být získány zpět. Tato operace trvat dobu. Odkaz je zkopírován, pokud typ odkazu je předán jako argument k metodě nebo vrátil z metody.

Tento článek používá následující příklad konceptu struktura 3D bodu vysvětlit tato doporučení:

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

Různé příklady používají různé implementace tohoto konceptu.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Deklarace struktur jen pro čtení pro neměnné hodnotových typech

Deklarace `struct` pomocí `readonly` modifikátor informuje kompilátor, že je máte v úmyslu vytvořit neumlčitelným typem. Kompilátor vynucuje tuto rozhodnutí o návrhu na základě následujících pravidel:

- Musí být všechna pole členů `readonly`
- Všechny vlastnosti musí být jen pro čtení, včetně automaticky implementované vlastnosti.

Tyto dvě pravidla jsou dostatečné pro Ujistěte se, že žádný člen `readonly struct` změní stav této struktury. `struct` Je neměnný. `Point3D` Strukturu můžete nadefinovat jako neměnné struktury, jak je znázorněno v následujícím příkladu:

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

Pokaždé, když máte v úmyslu návrhu, je vytvoření neměnný hodnota typu, postupujte podle tohoto doporučení. Žádná zlepšení výkonu jsou dodatečná výhoda. `readonly struct` Jasně vyjadřuje máte v úmyslu návrhu.

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>Použití `ref readonly return` příkazy pro velké struktury, pokud je to možné

Pokud je vrácená hodnota není místní pro metodu vracející může vracet hodnoty podle odkazů. Vrácení podle odkazu znamená, že je zkopírován pouze odkaz, není struktury. V následujícím příkladu `Origin` vlastnost nelze použít `ref` vrátit, protože se vrací hodnotu místní proměnné:

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

Následující definici vlastnosti mohou však vrátit odkazem, protože vrácená hodnota je statický člen:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

Nechcete, aby volající úpravy počátek, takže by měl vrátit hodnotu `readonly ref`:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

Vrací `ref readonly` umožňuje uložit kopírování větší struktury a zachovat neměnnosti interní datové členy.

V lokalitě volání volající výběru možnosti použít `Origin` vlastnosti jako datový typ `readonly ref` ani jako typ hodnoty:

[!code-csharp[AssignRefReadonly](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

První přiřazení v předchozím kódu vytvoří kopii `Origin` konstantě a přiřadí, které kopírují. Druhá přiřadí odkaz. Všimněte si, že `readonly` modifikátor musí být součástí deklarace proměnné. Odkaz, na který odkazuje, nemůže být upraven. O to mít za následek chybu v době kompilace.

`readonly` Modifikátor se vyžaduje u deklarace `originReference`.

Kompilátor vynucuje, volající nemůžete měnit odkaz. Se pokusí přiřadit hodnotu přímo generovat chybu v době kompilace. Kompilátor však nemůže vědět, pokud libovolné metody člen změní stav struktury.
Aby bylo zajištěno, že objekt není upraven, kompilátor vytvoří kopii a volá člen odkazů pomocí nástroje tuto kopii. Všechny změny se do tohoto obranná kopie.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>Použít `in` modifikátor `readonly struct` parametry, které jsou větší než `System.IntPtr.Size`

`in` – Klíčové slovo doplňuje stávající `ref` a `out` klíčových slov pro předání argumentů odkazem. `in` – Klíčové slovo určuje předání argumentu podle odkazu, ale volaná metoda nezmění hodnotu.

Toto přidání poskytuje úplné slovníku pro vyjádření záměr vašeho návrhu.
Typy hodnot se zkopírují po uplynutí volané metody, pokud nezadáte žádné následující modifikátory v podpisu metody. Každá z těchto modifikátorů Určuje, že proměnná je předána odkazem, jak se vyhnout kopírování. Každý modifikátor vyjadřuje různých záměr:

- `out`: Tato metoda nastaví hodnotu argument použitý jako tento parametr.
- `ref`: Tato metoda může nastavit hodnotu argument použitý jako tento parametr.
- `in`: Tato metoda nezmění hodnotu argument použitý jako tento parametr.

Přidat `in` modifikátor předat argument odkazem a deklarovat vaším záměrem návrhu předání argumentů odkazem, aby předešel zbytečnému kopírování. Nemáte v úmyslu změnit objekt použitý jako tento argument.

Tento postup často zvyšuje výkon u typů hodnot jen pro čtení, které jsou větší než <xref:System.IntPtr.Size?displayProperty=nameWithType>. Pro jednoduché typy (`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` a `bool`, a `enum` typy), jsou minimial všechny potenciální zvýšení výkonu. Ve skutečnosti, může se snížit výkon pomocí pass-by-reference pro typy menší než <xref:System.IntPtr.Size?displayProperty=nameWithType>.

Následující kód ukazuje příklad metodu, která vypočítá vzdálenost mezi dvěma body v 3D prostoru.

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Argumenty jsou dvě struktury, že každý obsahuje tří hodnot datového typu Double. Double je 8 bajtů, takže každý argument je 24 bajtů. Zadáním `in` modifikátor, předáte 4 bajtů nebo 8 bajtů odkaz na tyto argumenty, v závislosti na architektuře počítače. Rozdíl velikosti je malý, ale přidá, když vaše aplikace volá tuto metodu v těsné smyčce pomocí mnoha různých hodnot.

`in` Modifikační komplementy `out` a `ref` i jinými způsoby. Nelze vytvořit přetížení metody, která se liší pouze v nichž se nachází z `in`, `out`, nebo `ref`. Tato nová pravidla rozšíření stejné chování, která měla vždy definována pro `out` a `ref` parametry. Podobně jako `out` a `ref` modifikátory, typy hodnot nejsou zabalená, protože `in` modifikátor se použije.

`in` Modifikátor se můžou vztahovat k libovolnému členovi, která přebírá parametry: metody, delegáti, lambda výrazy, místní funkce, indexery, operátory.

Další funkce `in` parametrů je, že může používat literálními hodnotami nebo konstanty pro argument `in` parametru. Navíc na rozdíl od `ref` nebo `out` parametr, není nutné použít `in` modifikátor na lokalitu volání. Následující kód ukazuje, dva příklady volání `CalculateDistance` metody. První způsob využívá dvě místní proměnné, které jsou předány podle odkazu. Druhá zahrnuje dočasnou proměnnou vytvořených jako součást volání metody.

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Existuje několik způsobů, ve kterých kompilátor vynucuje povahy jen pro čtení `in` argument.  Za prvé, volané metody nejde přiřadit přímo `in` parametru. Nelze přiřadit přímo z některého z polí `in` parametr, když je tato hodnota `struct` typu. Kromě toho nelze předat `in` parametr pomocí libovolné metody `ref` nebo `out` modifikátor.
Tato pravidla platí pro všechny oblasti `in` pole je zadán parametr, `struct` typ a parametrem je také `struct` typu. Ve skutečnosti, tato pravidla platí pro několik úrovní přístupu ke členu poskytuje, jsou tyto typy na všech úrovních přístupu ke členu `structs`.
Vynucuje kompilátor `struct` typů předané jako `in` argumenty a jejich `struct` členy jsou jen pro čtení proměnné, když se použije jako argumentů jiným metodám.

Použití `in` parametry se můžete vyhnout potenciální výkon náklady na vytváření kopií. Sémantika jakékoli volání metody nezmění. Proto není nutné určit `in` modifikátor na lokalitu volání. Vynechání `in` modifikátor na lokalitu volání informuje kompilátor, že se může vytvořit kopii argumentu z následujících důvodů:

- Existuje implicitní převod, ale není identity konverzi z typu argumentu na typ parametru.
- Argument je výraz, ale není zaškrtnuta možnost známé úložiště proměnné.
- Existuje přetížení, která se liší podle přítomnosti nebo nepřítomnosti `in`. V takovém případě hodnota přetížení představuje lepší shodu.

Tato pravidla jsou užitečné, když aktualizujete existující kód, jak používat argumenty odkazu pouze pro čtení. Uvnitř volané metody lze volat jakékoli metody instance, která používá parametry s hodnotou. V těchto případech kopii `in` parametr se vytvoří. Protože kompilátor může vytvořit dočasnou proměnnou pro všechny `in` parametr, můžete také určit výchozí hodnoty pro všechny `in` parametru. Následující kód určuje jako výchozí hodnotu pro druhý bod počátku (bod 0; 0):

[!code-csharp[InArgumentDefault](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Chcete-li vynutit, aby kompilátor mohl předat argumenty jen pro čtení pomocí odkazu, zadejte `in` modifikátor argumenty při volání webu, jak je znázorněno v následujícím kódu:

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

Toto chování je snazší přijmout `in` parametry v čase ve velkých základů kódu, kde je možné zvýšení výkonu. Přidáte `in` modifikátor podpisy metod první. Potom můžete přidat `in` modifikátor na volání lokalit a vytvoření `readonly struct` typy umožňující vyhnout se vytváření obranná kopie kompilátor `in` parametry na více místech.

`in` Parametr označení lze také s typy odkazů nebo číselné hodnoty. Ale v obou případech je minimální, pokud existuje.

## <a name="never-use-mutable-structs-as-in-in-argument"></a>Nikdy nepoužívejte proměnlivé struktury jako v `in` argument

Technik popsaných výše vysvětlují, jak se vyhnout kopie vrací odkazy a předáním hodnoty podle odkazu. Tyto techniky fungují lépe, když typy argumentů jsou deklarovány jako `readonly struct` typy. V opačném případě musí kompilátor vytvořit **obranná kopie** v mnoha situacích k vynucení jen pro čtení ness žádné argumenty. Zvažte následující příklad, který vypočítá vzdálenost 3D bodu ze zdroje:

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

`Point3D` Struktura je *není* struktury jen pro čtení. Existuje šest hovorů přístup jiné vlastnosti v textu této metody. Na první zkoumání budete možná jste si mysleli, že tyto přístupy byly bezpečné. Po všech `get` přistupující objekt neměli měnit stav objektu. Ale neexistuje žádné pravidlo jazyka, které, který vynucuje. Je pouze běžné konvence. Může implementovat libovolný typ `get` přístupový objekt, který změnit vnitřní stav. Bez některé záruku jazyka musí kompilátor vytvoření dočasné kopie argumentu před voláním jakékoli členské. Dočasné úložiště se vytvoří v zásobníku, jsou zkopírovány hodnoty argumentu do dočasného úložiště a zkopírování hodnoty do zásobníku pro každý přístup ke členu jako `this` argument. V mnoha situacích, tyto kopie poškodit výkonu dostatečně této pass podle hodnot je rychlejší než pass podle jen pro čtení odkazu není typ argumentu `readonly struct`.

Místo toho, pokud výpočet vzdálenost používá neměnné struktury `ReadonlyPoint3D`, dočasné objekty nejsou potřeba:

[!code-csharp[readonlyInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

Kompilátor generuje kód efektivnější při volání členy `readonly struct`: `this` Odkaz, namísto kopírování příjemce, je vždy `in` parametr předaný odkazem na metodu member. Tato optimalizace uloží kopírování při použití `readonly struct` jako `in` argument.

Zobrazí se ukázkový program, který ukazuje, rozdíly ve výkonu pomocí [Benchmark.net](https://www.nuget.org/packages/BenchmarkDotNet/) v našich [úložiště ukázek](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) na Githubu. Porovná předáním proměnlivé struktury podle hodnoty a podle reference s předáním neměnné struktury podle hodnoty a podle reference. Je nejrychlejším způsobem použití neměnné struktury a předání odkazem.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Použití `ref struct` typy pro práci s bloky nebo paměti na jeden zásobníku

Funkce související jazyk je možnost deklarovat hodnotový typ, který musí být omezen na blok zásobníku jeden. Toto omezení umožňuje kompilátoru provést několik optimalizací. Byl primární motivace pro tuto funkci <xref:System.Span%601> a související struktury. Vylepšení výkonu z těchto vylepšení dosáhnete pomocí nové a aktualizované rozhraní API pro .NET, které usnadňují používání <xref:System.Span%601> typu.

Máte podobné požadavky na práci s pamětí, které jsou vytvořené pomocí [ `stackalloc` ](language-reference/keywords/stackalloc.md) nebo při použití paměti z vzájemné spolupráce rozhraní API. Můžete definovat vlastní `ref struct` typy pro tyto potřeby.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` Typ

Deklarace struktury jako `readonly ref` kombinuje výhody a omezení `ref struct` a `readonly struct` deklarace. Paměť používanou rozpětí jen pro čtení je omezen na blok zásobníku jednoho a paměť používanou rozpětí jen pro čtení nelze upravit.

## <a name="conclusions"></a>Závěry

Pomocí typů hodnot minimalizuje počet přidělení operací:

- Úložiště pro typy hodnot je přiděleny pro místní proměnné a argumenty metody.
- Jako součást tohoto objektu, nikoli jako samostatné přidělení je přiděleno úložiště pro typy hodnot, které jsou členy jiné objekty.
- Úložiště pro typ hodnoty vrácené hodnoty je přiděleny.

Oproti, typy odkazů v těchto stejných situacích:

- Úložiště pro typy odkazů jsou haldy přidělené pro místní proměnné a argumenty metody. Odkaz je uložen v zásobníku.
- Úložiště pro typy odkazů, které jsou členy jiné objekty samostatně přidělují na haldě. Objekt obsahující uchovává odkaz.
- Úložiště pro odkaz na typ vrácené hodnoty je haldy přidělené. Odkaz na toto úložiště je uložen v zásobníku.

Minimalizace přidělení se dodává s kompromisy. Kopírování větší množství paměti při velikost `struct` je větší než velikost odkaz. Odkaz je obvykle 64 bitů nebo 32 bitů a závisí na procesoru cílového počítače.

Tyto poměry obecně mít minimální vliv zatížení vliv. Pro velké struktury nebo větší kolekce, zvyšuje dopad na výkon. Dopad mohou být velké v těsné smyčky a horké cesty pro programy.

Těchto vylepšení C# jazyka jsou navrženy pro algoritmů výkon kritických-li minimalizovat přidělení paměti je hlavním faktorem při dosažení nezbytné výkonu. Může se stát, že není často používají tyto funkce v kódu, který píšete. Nicméně tato vylepšení byla přijata v celém rozhraní .NET. Provádění více rozhraní API z těchto funkcí používat, zobrazí se výkon vašich aplikací, zlepšit.

## <a name="see-also"></a>Viz také:

- [REF – klíčové slovo](language-reference/keywords/ref.md)
- [Návratové a místní referenční hodnoty](programming-guide/classes-and-structs/ref-returns.md)
