---
title: Referenční sémantika s typy hodnot
description: Funkce jazyka, které minimalizují kopírování struktury bezpečně pochopit
ms.date: 11/10/2017
ms.custom: mvc
ms.openlocfilehash: f241219994d7a03192a4aea69b912bf1ac5ed29c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133737"
---
# <a name="reference-semantics-with-value-types"></a>Referenční sémantika s typy hodnot

Výhodou použití typů hodnot je, že často vyhnout přidělení haldy.
Nevýhodou je, že se zkopírují podle hodnoty. Tato kompromis učiní obtížnější pro optimalizaci algoritmů, které pracují na velkých objemů dat. Nové funkce jazyků v jazyce C# 7.2 poskytují mechanismy, které umožňují pass referenční sémantika s typy hodnot. Pomocí těchto funkcí dobře minimalizovat obou přidělení a operací kopírování. Tento článek se věnuje tyto nové funkce.

Většina ukázek kódu v tomto článku ukazuje funkce přidané v jazyce C# 7.2. Pokud chcete používat tyto funkce, je nutné nakonfigurovat projektu pro použití jazyka C# 7.2 nebo novější. Další informace o nastavení jazykové verze naleznete v tématu [konfigurace jazyková verze](language-reference/configure-language-version.md).

## <a name="passing-arguments-by-readonly-reference"></a>Předání argumentů odkazem jen pro čtení

C# 7.2 přidá `in` – klíčové slovo k doplnění stávající `ref` a `out` klíčových slov pro předání argumentů odkazem. `in` – Klíčové slovo určuje předání argumentu podle odkazu, ale volaná metoda neupravuje hodnotu. 

Toto přidání poskytuje úplné slovníku pro vyjádření záměr vašeho návrhu. Typy hodnot se zkopírují po uplynutí volané metody, pokud nezadáte žádné následující modifikátory v podpisu metody. Každá z těchto modifikátorů Určuje, že typ hodnoty je předána odkazem, jak se vyhnout kopírování. Každý modifikátor vyjadřuje různých záměr:

- `out`: Tato metoda nastaví hodnotu argument použitý jako tento parametr.
- `ref`: Tato metoda může nastavit hodnotu argument použitý jako tento parametr.
- `in`: Tato metoda neupravuje hodnotu argument použitý jako tento parametr.

Přidat `in` modifikátor předat argument odkazem a deklarovat vaším záměrem návrhu předání argumentů odkazem, aby předešel zbytečnému kopírování. Nechcete změnit objekt použitý jako tento argument. Následující kód ukazuje příklad metodu, která vypočítá vzdálenost mezi dvěma body v 3D prostoru. 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

Argumenty jsou dvě struktury, že každý obsahuje tří hodnot datového typu Double. Double je 8 bajtů, takže každý argument je 24 bajtů. Zadáním `in` modifikátor, předáte odkaz bajt 4 nebo 8 bajtů na tyto argumenty, v závislosti na architektuře počítače. Rozdíl velikosti je malý, ale ji můžete rychle přidat po aplikace volá tuto metodu v těsné smyčce pomocí mnoha různých hodnot.
 
`in` Modifikační komplementy `out` a `ref` i jinými způsoby. Nelze vytvořit přetížení metody, která se liší pouze v nichž se nachází z `in`, `out`, nebo `ref`. Tato nová pravidla rozšíření stejné chování, která měla vždy definována pro `out` a `ref` parametry.

`in` Modifikátor se můžou vztahovat k libovolnému členovi, která přebírá parametry: metody, delegáti, lambda výrazy, místní funkce, indexery, operátory.

Na rozdíl od `ref` a `out` argumenty, můžete použít hodnoty literálu nebo konstanty pro argument `in` parametru. Navíc na rozdíl od `ref` nebo `out` parametr, není nutné použít `in` modifikátor na lokalitu volání. Následující kód ukazuje, dva příklady volání `CalculateDistance` metody. První způsob využívá dvě místní proměnné, které jsou předány podle odkazu. Druhá zahrnuje dočasnou proměnnou vytvořených jako součást volání metody. 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

Existuje několik způsobů, ve kterých kompilátor pak zajistí, které povahy jen pro čtení `in` argument bude vynucovat.  Za prvé, volané metody nejde přiřadit přímo `in` parametru. Nelze přiřadit přímo z některého z polí `in` parametr, když je tato hodnota `struct` typu. Kromě toho nelze předat `in` parametr pomocí libovolné metody `ref` nebo `out` modifikátor.
Tato pravidla platí pro všechny oblasti `in` pole je zadán parametr, `struct` typ a parametrem je také `struct` typu. Ve skutečnosti, tato pravidla platí pro několik úrovní přístupu ke členu poskytuje, jsou tyto typy na všech úrovních přístupu ke členu `structs`. Vynucuje kompilátor `struct` typů předané jako `in` argumenty a jejich `struct` členy jsou jen pro čtení proměnné, když se použije jako argumentů jiným metodám.

Použití `in` parametry se vyhnete potenciální výkon náklady na vytváření kopií. Sémantika jakékoli volání metody nezmění. Proto není potřeba zadat `in` modifikátor na lokalitu volání. Ale vynechá `in` modifikátor na lokalitu volání informuje kompilátor, že ji může vytvořit kopii argumentu z následujících důvodů:

- Je implicitní převod, ale není identity konverzi z typu argumentu na typ parametru.
- Argument je výraz, ale nemá žádné známé úložiště proměnné.
- Existuje přetížení, která se liší podle přítomnosti nebo nepřítomnosti `in`. V takovém případě hodnota přetížení představuje lepší shodu.

Tato pravidla jsou užitečné, když aktualizujete existující kód, jak používat argumenty odkazu pouze pro čtení. Uvnitř volané metody lze volat jakékoli metody instance, která používá parametry s hodnotou. V těchto případech kopii `in` parametr se vytvoří. Protože kompilátor může vytvořit dočasnou proměnnou pro všechny `in` parametr, můžete také určit výchozí hodnoty pro všechny `in` parametru. Následující kód určuje jako výchozí hodnotu pro druhý bod počátku (bod 0; 0):

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Chcete-li vynutit, aby kompilátor mohl předat další argumenty pouze podle odkazu, zadejte `in` modifikačních na argumenty při volání webu, jak je znázorněno v následujícím kódu:

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#ExplicitInArgument "Specifying an In argument")]

Toto chování je snazší přijmout `in` parametry v čase ve velkých základů kódu, kde je možné zvýšení výkonu. Přidáte `in` modifikátor podpisy metod první. Potom můžete přidat `in` modifikátor na callsites a vytvořit `readonly struct` typy umožňující vyhnout se vytváření obranná kopie kompilátor `in` parametry na více místech.

`in` Parametr označení lze také s typy odkazů nebo číselné hodnoty. Ale v obou případech je minimální, pokud existuje.

## <a name="ref-readonly-returns"></a>`ref readonly` Vrátí

Můžete také vrátit odkazem, typ hodnoty, ale zakázat volající v upravování této hodnoty. Použití `ref readonly` modifikátor vyjádřit záměr tohoto návrhu. Čtenáři upozorní, že se vrací odkazem na existující data, ale neumožňuje úpravy. 

Kompilátor vynucuje, volající nemůžete měnit odkaz. Se pokusí přiřadit hodnotu přímo generovat chybu v době kompilace. Kompilátor však nemůže vědět, pokud libovolné metody člen změní stav struktury.
Aby bylo zajištěno, že objekt není upraven, kompilátor vytvoří kopii a volá člen odkazů pomocí nástroje tuto kopii. Všechny změny se do tohoto obranná kopie. 

Je pravděpodobné, který pomocí knihovny `Point3D` by často používají původu v kódu. Každá instance vytvoří nový objekt v zásobníku. Může být výhodné vytvořit konstantu a vrátit odkazem. Ale pokud vrátíte odkaz na interní úložiště, můžete vynutit, aby volající nelze upravit odkazované úložiště. Následující kód definuje vlastnost jen pro čtení, která vrací `readonly ref` k `Point3D` , který určuje původ.

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

Vytvoření kopie jen pro čtení ref návratový je jednoduché: stačí ji přiřadit proměnná není deklarovaná pomocí `ref readonly` modifikátor. Kompilátor generuje kód má objekt kopírovat jako součást tohoto přiřazení. 

Když přiřadíte proměnnou, která `ref readonly return`, můžete zadat buď `ref readonly` proměnnou nebo podle hodnoty kopie odkazu pouze pro čtení:

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

První přiřazení v předchozím kódu vytvoří kopii `Origin` konstantě a přiřadí, které kopírují. Druhá přiřadí odkaz. Všimněte si, že `readonly` modifikátor musí být součástí deklarace proměnné. Odkaz, na který odkazuje, nemůže být upraven. O to mít za následek chybu v době kompilace.

## <a name="readonly-struct-type"></a>`readonly struct` Typ

Použití `ref readonly` vysokým provozem používá struktury mohou být dostatečné.
Jindy, můžete vytvořit neměnné struktury. Potom můžete vždy předat odkazem. jenom pro čtení. Které se provádějí, že postup odebere obranné zkopíruje, při přístupu k metody struktury použít jako `in` parametru.

Můžete to udělat tak, že vytvoříte `readonly struct` typu. Můžete přidat `readonly` Modifikátor pro deklaraci struktury. Kompilátor vynucuje, aby všichni členové instance struktury jsou `readonly`; `struct` musí být neměnitelný.

Další optimalizace `readonly struct`. Můžete použít `in` modifikátor na jakémkoliv místě kde `readonly struct` je argumentem. Kromě toho se můžete vrátit `readonly struct` jako `ref return` jsou při vrácení objektu, jehož doba života sahá nad rámec metoda vrací objekt.

A konečně, kompilátor vygeneruje kód efektivnější při volání členy `readonly struct`: `this` odkaz, namísto kopírování příjemce, je vždy `in` parametr předaný odkazem na metodu member. Tato optimalizace uloží další kopírování při použití `readonly struct`. `Point3D` Je vynikající kandidát pro tuto změnu. Následující kód ukazuje aktualizovanou `ReadonlyPoint3D` struktury:

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>`ref struct` Typ

Další související jazyk funkcí je schopnost deklarovat typ hodnoty, které musí být přiděleny. Jinými slovy tyto typy může nikdy být vytvořen na haldě jako člena jiné třídy. Byl primární motivace pro tuto funkci <xref:System.Span%601> a související struktury. <xref:System.Span%601> může obsahovat spravovaného ukazatele jako jeden z jejích členů, druhá je délka značky span. Je implementován trochu jinak než C# nepodporuje odkazy na spravované paměti mimo nezabezpečený kontext. Žádné zápisu, která se mění ukazatele a délka není atomické. To znamená, že <xref:System.Span%601> by podléhají mimo rozsah chyby nebo jiné porušení bezpečnosti typu byly, není omezen na blok zásobníku jeden. Kromě toho uvedení spravovaného ukazatele na haldě uvolňování paměti obvykle dojde k chybě během JIT.

Máte podobné požadavky na práci s pamětí, které jsou vytvořené pomocí [ `stackalloc` ](language-reference/keywords/stackalloc.md) nebo při použití paměti z vzájemné spolupráce rozhraní API. Můžete definovat vlastní `ref struct` typy pro tyto potřeby. V tomto článku vidíte příklad použití `Span<T>` pro zjednodušení.

`ref struct` Deklarace deklaruje strukturu tohoto typu musí být v zásobníku. Jazyk pravidla zajistit bezpečné používání těchto typů. Jiné typy deklarované jako `ref struct` zahrnují <xref:System.ReadOnlySpan%601>. 

Cílem vedení `ref struct` zadejte jako proměnnou přidělený na zásobník zavádí několik pravidel, které kompilátor vynucuje pro všechny `ref struct` typy.

- Nelze pole `ref struct`. Nelze přiřadit `ref struct` typ proměnné typu `object`, `dynamic`, nebo libovolný typ rozhraní.
- Nelze deklarovat `ref struct` jako člen třídy nebo struktury normální.
- Nelze deklarovat lokální proměnné, které jsou `ref struct` typy v asynchronních metodách. Můžete je deklarovat v synchronní metody, které vracejí `Task`, `Task<T>` nebo typy podobné úlohám.
- Nelze deklarovat `ref struct` lokální proměnné iterátory.
- Nelze zachytit `ref struct` proměnné ve výrazech lambda nebo místní funkce.

Tato omezení zajistit nepoužijete omylem `ref struct` způsobem, který může převést na spravované haldě.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` Typ

Deklarace struktury jako `readonly ref` kombinuje výhody a omezení `ref struct` a `readonly struct` deklarace. 

Následující příklad ukazuje deklaraci `readonly ref struct`.

```csharp
readonly ref struct ReadOnlyRefPoint2D
{
    public int X { get; }
    public int Y { get; }
    
    public ReadOnlyRefPoint2D(int x, int y) => (X, Y) = (x, y);
}
```

## <a name="conclusions"></a>Závěry

Tato vylepšení pro jazyk C# jsou navržené pro kritické algoritmy výkonu kde přidělení paměti může být nezbytné k dosažení nezbytné výkonu. Může se stát, že není často používají tyto funkce v kódu, který píšete. Tato vylepšení však byly přijaty v mnoha umístěních v rozhraní .NET Framework. Provádění více rozhraní API z těchto funkcí používat, zobrazí se výkon vašich vlastních aplikací vylepšit.
