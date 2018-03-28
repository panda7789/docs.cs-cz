---
title: Odkaz na sémantiku s typy hodnot
description: Porozumět funkcím jazyk, které bezpečně minimalizovat kopírování struktury
author: billwagner
ms.author: wiwagn
ms.date: 11/10/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 778897dc92f8a94178ebbbed7704c0dfe2397729
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="reference-semantics-with-value-types"></a>Odkaz na sémantiku s typy hodnot

Výhodou použití jiných typů hodnot je, že často vyhnout přidělení haldy.
Nevýhodou je, že se kopírují hodnotou. Tato kompromis znesnadňuje optimalizovat algoritmy, které působí na velké objemy dat. Nové funkce jazyka v C# 7.2 poskytují mechanismy, které umožňují průchodu odkazem sémantiku s typy hodnot. Pomocí těchto funkcí dobře minimalizovat obou přidělení a operace kopírování. Tento článek popisuje tyto nové funkce.

Velká část ukázkový kód v tomto článku ukazuje funkce přidané v C# 7.2. Chcete-li použít tyto funkce, je nutné nakonfigurovat projektu pro použití jazyka C# 7,2 nebo novější. Visual Studio můžete ho vyberte. Pro každý projekt, vyberte **projektu** z nabídky, pak **vlastnosti**. Vyberte **sestavení** a klikněte na **Upřesnit**. Z ní nakonfigurujte jazykové verzi. Vyberte buď "7.2" nebo "posledního".  Nebo můžete upravit *csproj* souboru a přidejte následující uzly:

```XML
  <PropertyGroup>
    <LangVersion>7.2</LangVersion>
  </PropertyGroup>
```

Můžete buď "7,2" nebo "posledního" pro hodnotu.

## <a name="passing-arguments-by-readonly-reference"></a>Předání argumentů odkazem jen pro čtení

C# 7.2 přidá `in` – klíčové slovo, aby doplňovala existující `ref` a `out` klíčová slova předání argumentů odkazem. `in` – Klíčové slovo určuje předání odkazem argument, ale zavolat metodu nedojde ke změně hodnota. 

Přidání poskytuje úplné termínů k vyjádření vašich představ návrhu. Typy hodnot se zkopírují, když uplyne volané metodě, když nezadáte žádný z následujících modifikátory podpis metody. Každý z těchto modifikátory Určuje, že typ hodnoty je předán odkazem, zabraňující kopie. Každý modifikátor vyjadřoval různých záměrů:

- `out`: Tato metoda nastaví hodnota argumentu použít jako tento parametr.
- `ref`: Tato metoda může nastavit hodnotu argumentu použít jako tento parametr.
- `in`: Tato metoda nedojde ke změně hodnoty argumentu použít jako tento parametr.

Přidat `in` modifikátor předat argument odkazem a deklarovat vašich představ návrhu předání argumentů odkazem, aby se zabránilo zbytečným kopírování. Nemáte v úmyslu použít jako tento argument objekt upravit. Následující kód ukazuje příklad metody, která by vypočítala vzdálenost mezi dvěma body v 3D prostoru. 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

Argumenty jsou dvě struktury, že každý obsahovat tři hodnoty Double. Datový typ double je 8 bajtů, takže každý argument je 24 bajtů. Zadáním `in` modifikátor, předáte 4bajtový nebo 8bajtový odkaz na těchto argumentů, v závislosti na architektuře počítače. Rozdíl ve velikosti je malý, ale ho můžete rychle přidat když aplikace zavolá tato metoda ve smyčce úzkou pomocí mnoha různých hodnot.
 
`in` Modifikátor doplňuje `out` a `ref` také jiné způsoby. Nelze vytvořit přetížení metody, které se liší pouze v přítomnosti z `in`, `out`, nebo `ref`. Tyto nové pravidel rozšířit stejné chování, která měla vždy definována pro `out` a `ref` parametry.

`in` Modifikátor mohou být použity u kteréhokoli člena, který používá parametry: metody, delegáti, lambdas, místní funkce, indexery, operátory.

Na rozdíl od `ref` a `out` argumenty, můžete pomocí literálových hodnot nebo konstanty pro argument `in` parametr. Navíc na rozdíl od `ref` nebo `out` parametr, nemusíte použít `in` modifikátor v lokalitě volání. Následující kód ukazuje dva příklady volání `CalculateDistance` metoda. První používá dva místní proměnné předaná odkaz. Druhá zahrnuje dočasné proměnné, vytvořené jako součást volání metody. 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

Existuje několik způsobů, ve kterých kompilátor zajišťuje, které povaze jen pro čtení `in` argument je vynucená.  Nejprve zavolat metodu nelze přiřadit přímo `in` parametr. Nelze přiřadit přímo k žádné pole `in` parametr, pokud je tato hodnota `struct` typu. Kromě toho nelze předat `in` parametr pro jakékoli metoda pomocí `ref` nebo `out` modifikátor.
Tato pravidla vztahují na všechny pole `in` pole je zadán parametr, `struct` typu a parametr je také `struct` typu. Ve skutečnosti, platí následující pravidla pro přístup ke členu několik vrstev zadané typy na všech úrovních přístup ke členu `structs`. Kompilátor vynucuje, který `struct` typy předány jako `in` argumenty a jejich `struct` členové jsou jen pro čtení proměnné, když se použije jako argumenty pro jiné metody.

Použití `in` parametry zabraňuje náklady na potenciální výkon při kopie. Sémantika žádné volání metody nemění. Proto není potřeba zadat `in` modifikátor v lokalitě volání. Ale vynechání `in` modifikátor v lokalitě volání informuje kompilátor, že se může vytvořit kopii argument z následujících důvodů:

- Je implicitní převod, ale není identity konverzi z typ argumentu pro typ parametru.
- Argument je výraz, ale nemá žádné známé úložiště proměnné.
- Existuje přetížení, která se liší podle přítomnosti nebo absenci `in`. V takovém případě hodnota přetížení je lepší shodu.

Tato pravidla jsou užitečné při aktualizaci stávajícího kódu pro použití argumenty odkaz jen pro čtení. Uvnitř metody volané můžete volat libovolné metody instance, která používá hodnoty parametrů. V těchto případech kopii `in` parametr je vytvořena. Protože kompilátor můžete vytvořit dočasnou proměnnou pro žádné `in` parametr, můžete také zadat výchozí hodnoty pro jakékoli `in` parametr. Následující kód určuje počátek (bod 0,0) jako výchozí hodnota pro druhý bod:

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Chcete-li vynutit kompilátoru předání čtení pouze argumentů odkazem, zadejte `in` modifikačních na argumenty v lokalitě volání, jak je znázorněno v následujícím kódu:

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#ExplicitInArgument "Specifying an In argument")]

Toto chování je jednodušší použít `in` parametry v čase ve velkých základy kódu, kde je možné, zvýšení výkonu. Můžete přidat `in` modifikátor do signatur metoda první. Potom můžete přidat `in` modifikátor v callsites a vytvořit `readonly struct` typy Povolit kompilátor Vyhněte se vytváření Obranným kopie `in` parametry ve víc umístěních.

`in` Parametr označení lze také s odkazové typy nebo číselné hodnoty. Výhody v obou případech jsou však minimální, pokud existuje.

## <a name="ref-readonly-returns"></a>`ref readonly` Vrátí

Můžete také vrátí hodnotu typu odkazu, ale zakáže volající upravování tuto hodnotu. Použití `ref readonly` modifikátor vyjádřit záměr tohoto návrhu. Že jsou vrátí odkaz na existující data, ale neumožňuje úpravy upozorní čtečky. 

Kompilátor vynutí, že volající nelze změnit odkaz. Pokusy o přiřazení hodnoty přímo generovat chyby kompilace. Kompilátor však nemůže vědět, pokud žádné metodou member změní stav struct.
Aby se zajistilo, že objekt se nemění, kompilátor vytvoří kopii a volá člen odkazů pomocí tuto kopii. Všechny změny se na tuto Obranným kopii. 

Je pravděpodobné, který pomocí knihovny `Point3D` by často používají počátek napříč kódem. Všechny instance vytvoří nový objekt v zásobníku. To může být výhodné vytvoření konstanta a vrátit odkaz. Ale pokud vrátíte odkaz na interní úložiště, můžete vynutit, aby volající nelze upravit odkazované úložiště. Následující kód definuje vlastnosti jen pro čtení, která vrátí `readonly ref` k `Point3D` určující počátek.

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

Vytvoření kopie jen pro čtení ref návratový je snadné: právě přiřadit proměnné není deklarován s `ref readonly` modifikátor. Kompilátor generuje kód pro kopírování objektu jako součást přiřazení. 

Přiřadíte-li proměnnou, do které `ref readonly return`, můžete buď zadat `ref readonly` proměnnou nebo kopii-hodnota odkaz na jen pro čtení:

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

První přiřazení v předchozí kód vytvoří kopii `Origin` konstanta a přiřadí, které zkopírovat. Druhý přiřadí odkaz. Všimněte si, že `readonly` modifikátor musí být součástí deklarace proměnné. Odkaz, na který odkazuje nemůže být upraven. Pokusy o tak mít za následek chyby kompilace.

## <a name="readonly-struct-type"></a>`readonly struct` Typ

Použití `ref readonly` k velkým provozem použití struktury může být plně dostačující.
Další dobu, můžete vytvořit neměnné struktura. Potom můžete vždy předat odkazem jen pro čtení. Aby postup odebere Obranným zkopíruje které se provádějí při přístupu k metodám struktury použít jako `in` parametr.

Můžete to udělat tak, že vytvoříte `readonly struct` typu. Můžete přidat `readonly` modifikátor k deklaraci struktura. Kompilátor vynucuje, aby se všichni její členové instance dané struktury `readonly`; `struct` musí být neměnitelný.

Existují další optimalizace pro `readonly struct`. Můžete použít `in` modifikátor v každé umístění kde `readonly struct` je argument. Kromě toho se můžete vrátit `readonly struct` jako `ref return` když se vrátí objekt, jehož životnost rozšiřuje nad rámec metoda vrací objekt.

Nakonec kompilátor generuje efektivnější kód při volání členy `readonly struct`: `this` odkaz, místo kopii příjemce, je vždy `in` parametr předaný odkazem na metodou member. Tato optimalizace uloží další kopírování při použití `readonly struct`. `Point3D` Skvělé kandidátem pro tuto změnu. Následující kód ukazuje aktualizované `ReadonlyPoint3D` strukturu:

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>`ref struct` Typ

Další související jazyk funkcí je schopnost deklarovat typ hodnoty, který musí být přidělena zásobníku. Jinými slovy tyto typy nikdy vytvořením v haldě jako člena jiné třídy. Primární motivace pro tuto funkci byl <xref:System.Span%601> a související struktury. <xref:System.Span%601> může obsahovat spravované ukazatel jako jeden z jejích členů, druhá je délka rozpětí. Je implementováno trochu jinak protože C# nepodporuje ukazatele na spravované paměti mimo kontextu unsafe. Všechny zápisu, které změní ukazatele a délka není atomic. To znamená <xref:System.Span%601> by podléhají mimo rozsah chyby nebo další narušení bezpečnosti typu není je omezená na jednom zásobníku. Kromě toho uvedení spravovaného ukazatel na haldě GC obvykle dojde k chybě během JIT.

Můžete mít podobné požadavky práce paměti vytvořené pomocí [ `stackalloc` ](language-reference/keywords/stackalloc.md) nebo při použití paměti z spolupráce rozhraní API. Můžete definovat vlastní `ref struct` typy těchto potřeb. V tomto článku najdete příklady použití `Span<T>` pro jednoduchost.

`ref struct` Deklarace deklaruje struktury tohoto typu musí být v zásobníku. Jazyk pravidla zajistit bezpečné používání těchto typů. Jiné typy deklarován jako `ref struct` zahrnují <xref:System.ReadOnlySpan%601>. 

Cílem zachování `ref struct` zadejte jako proměnnou přidělené zásobníku zavádí několik pravidel, která kompilátor vynucuje pro všechny `ref struct` typy.

- Nelze pole `ref struct`. Nelze přiřadit `ref struct` typ proměnné typu `object`, `dynamic`, nebo kterýkoli typ rozhraní.
- Nelze deklarovat `ref struct` jako člena třídy nebo normální struktury.
- Nelze deklarovat místní proměnné, které jsou `ref struct` typy v asynchronní metody. Je možné deklarovat v synchronních metod, které vracejí `Task`, `Task<T>` nebo typů úloh.
- Nelze deklarovat `ref struct` místní proměnné v iterátory.
- Nelze zachytit `ref struct` proměnných v výrazy lambda nebo lokální funkce.

Tato omezení Ujistěte se, nepoužívejte omylem `ref struct` způsobem, který může podporovat spravovaná halda.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` Typ

Deklarace struktury jako `readonly ref` kombinuje výhody a omezení `ref struct` a `readonly struct` delcarations. 

Následující příklad ukazuje deklaraci `readonly ref struct`.

```csharp
readonly ref struct ReadOnlyRefPoint2D
{
    public int X { get; }
    public int Y { get; }
    
    public ReadOnlyRefPoint2D(int x, int y) => (X, Y) = (x, y);
}
```

## <a name="conclusions"></a>Závěrů

Tato vylepšení pro jazyk C# jsou navrženy pro výkon kritické algoritmy, kde může být rozhodující k dosažení nezbytné výkonu přidělení paměti. Můžete zjistit, že často nepoužíváte tyto funkce v kódu, kterou píšete. Tato vylepšení, ale byly přijaty v mnoho míst v rozhraní .NET Framework. Jako zajistěte více rozhraní API pomocí těchto funkcí, uvidíte vaše vlastní aplikace zlepšit výkon.
