---
title: Prohlídka oblastí v jazyce C# – hlavní oblasti
description: Novinka v jazyce C#? Seznamte se se základy jazyka.
ms.date: 08/06/2020
ms.openlocfilehash: f0e9bff144cc3c853a82f2ee6b400049df60683d
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88068520"
---
# <a name="major-language-areas"></a>Hlavní jazykové oblasti

## <a name="arrays-collections-and-linq"></a>Pole, kolekce a LINQ

C# a .NET poskytují mnoho různých typů kolekcí. Pole mají syntaxi definovanou jazykem. Typy obecných kolekcí jsou uvedeny v <xref:System.Collections.Generic?displayProperty=fullName> oboru názvů. Specializované kolekce zahrnují <xref:System.Span%601?displayProperty=nameWithType> pro přístup k souvislé paměti v bloku zásobníku a <xref:System.Memory%601?displayProperty=nameWithType> pro přístup k souvislé paměti na spravované haldě. Všechny kolekce, včetně polí, <xref:System.Span%601> a <xref:System.Memory%601> sdílí princip sjednocení pro iteraci. Použijete <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní. Tento princip sjednocení znamená, že libovolný typ kolekce lze použít s dotazy LINQ nebo jinými algoritmy. Metody zapisujete pomocí <xref:System.Collections.Generic.IEnumerable%601> a tyto algoritmy fungují s libovolnou kolekcí.

### <a name="arrays"></a>Pole

[***Pole***](../programming-guide/arrays/index.md) je datová struktura, která obsahuje počet proměnných, které jsou dostupné prostřednictvím počítaných indexů. Proměnné obsažené v poli, označované také jako ***prvky*** pole, jsou všechny stejného typu. Tento typ se nazývá ***typ elementu*** pole.

Typy polí jsou odkazové typy a deklarace proměnné pole jednoduše nastaví volné místo pro odkaz na instanci pole. Skutečné instance pole jsou vytvářeny dynamicky za běhu pomocí `new` operátoru. `new`Operace určuje ***délku*** nové instance pole, která je poté opravena po dobu života instance. Indexy prvků rozsahu pole od `0` do `Length - 1` . `new`Operátor automaticky inicializuje prvky pole na výchozí hodnotu, což je například nula pro všechny číselné typy a `null` pro všechny typy odkazů.

Následující příklad vytvoří pole `int` prvků, inicializuje pole a vytiskne obsah pole.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ArraysSample":::

Tento příklad vytvoří a pracuje na jednorozměrném ***poli***. C# podporuje také ***multidimenzionální pole***. Počet rozměrů typu pole, označovaný také jako ***rozměr*** typu pole, je jedna plus počet čárek napsaných mezi hranatými závorkami typu pole. Následující příklad přiděluje jednorozměrné, dvojrozměrné a trojrozměrné pole v uvedeném pořadí.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DeclareArrays":::

Pole `a1` obsahuje 10 prvků, `a2` pole obsahuje 50 (10 × 5) prvků a `a3` pole obsahuje 100 (10 × 5 × 2) prvků.
Typ elementu pole může být libovolný typ, včetně typu pole. Pole s prvky typu pole se někdy nazývá ***vícenásobné pole*** , protože délky polí elementů nemusí být stejné. Následující příklad přiděluje pole polí pro `int` :

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ArrayOfArrays":::

První řádek vytvoří pole se třemi prvky, každý typ `int[]` a každý s počáteční hodnotou `null` . Další řádky poté inicializují tři prvky s odkazy na jednotlivé instance pole s různou délkou.

`new`Operátor umožňuje zadat počáteční hodnoty prvků pole pomocí ***inicializátoru pole***, což je seznam výrazů zapsaných mezi oddělovači `{` a `}` . Následující příklad přiděluje a inicializuje `int[]` se třemi prvky.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeArray":::

Délka pole je odvozena od počtu výrazů mezi `{` a `}` . Deklarace lokální proměnné a pole lze dále zkrátit tak, aby se typ pole nemuselo přestavit.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeShortened":::

Oba předchozí příklady jsou ekvivalentní následujícímu kódu:

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeGenerated":::

`foreach`Příkaz lze použít k zobrazení výčtu prvků libovolné kolekce. Následující kód vytvoří výčet pole z předchozího příkladu:

:::code language="csharp" source="./snippets/shared/Features.cs" ID="EnumerateArray":::

`foreach`Příkaz používá <xref:System.Collections.Generic.IEnumerable%601> rozhraní, takže může pracovat s libovolnou kolekcí.

## <a name="string-interpolation"></a>Interpolace řetězců

[***Interpolace řetězců***](../language-reference/tokens/interpolated.md) v jazyce C# umožňuje formátovat řetězce definováním výrazů, jejichž výsledky jsou umístěny do řetězce formátu. Například následující příklad vytiskne teplotu v daném dni ze sady dat o počasí:

:::code language="csharp" source="./snippets/shared/Features.cs" ID="StringInterpolation":::

Interpolovaná řetězcová řetězec je deklarována pomocí `$` tokenu. Interpolace řetězců vyhodnocuje výrazy mezi `{` a `}` , následně převede výsledek na a `string` a nahradí text mezi závorkami výsledným řetězcem výrazu. `:`V prvním výrazu `{weatherData.Data:MM-DD-YYYY}` Určuje *řetězec formátu*. V předchozím příkladu určuje, že by mělo být datum Vytištěno ve formátu MM-DD-RRRR.

## <a name="pattern-matching"></a>Porovnávání vzorů

Jazyk C# poskytuje výrazy pro [***porovnávání vzorů***](../pattern-matching.md) pro dotazování stavu objektu a spouštění kódu na základě tohoto stavu. Můžete zkontrolovat typy a hodnoty vlastností a polí, abyste určili, kterou akci chcete provést. `switch`Výraz je primární výraz pro porovnávání vzorů.

## <a name="delegates-and-lambda-expressions"></a>Delegáti a výrazy lambda

[***Typ delegáta***](../delegates-overview.md) představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem. Delegáti umožňují zacházet s metodami jako s entitami, které lze přiřadit proměnným a předávat jako parametry. Delegáti jsou podobní pojmu ukazatelů na funkce nalezených v některých jiných jazycích. Na rozdíl od ukazatelů na funkce jsou delegáti objektově orientovaný a typově bezpečný.

Následující příklad deklaruje a používá typ delegáta s názvem `Function` .

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DelegateExample":::

Instance `Function` typu delegáta může odkazovat na jakoukoli metodu, která přebírá `double` argument a vrací `double` hodnotu. `Apply`Metoda použije daný prvek `Function` pro prvky a `double[]` vrátí `double[]` výsledek. V `Main` metodě `Apply` se používá k použití tří různých funkcí na `double[]` .

Delegát může odkazovat buď na statickou metodu (například `Square` nebo `Math.Sin` v předchozím příkladu), nebo na metodu instance (například `m.Multiply` v předchozím příkladu). Delegát, který odkazuje na metodu instance, také odkazuje na konkrétní objekt a když je metoda instance vyvolána prostřednictvím delegáta, bude tento objekt `this` ve volání.

Delegáty lze také vytvořit pomocí anonymních funkcí, což jsou "vložené metody", které jsou vytvořeny při deklaraci. Anonymní funkce mohou zobrazit místní proměnné okolních metod. Následující příklad nevytvoří třídu:

:::code language="csharp" source="./snippets/shared/Features.cs" ID="UseDelegate":::

Delegát neví ani nezáleží na třídě metody, na kterou odkazuje. Všechny tyto věci jsou, že odkazovaná metoda má stejné parametry a návratový typ jako delegát.

## <a name="async--await"></a>Async/await

Jazyk C# podporuje asynchronní programy se dvěma klíčovými slovy: `async` a `await` . Přidáte `async` modifikátor do deklarace metody pro deklaraci metody je asynchronní. `await`Operátor instruuje kompilátor, aby na výsledek dokončil asynchronní čekání. Ovládací prvek se vrátí volajícímu a metoda vrátí strukturu, která spravuje stav asynchronní práce. Struktura je obvykle <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> , ale může to být libovolný typ, který podporuje model await. Tyto funkce umožňují napsat kód, který se čte jako jeho synchronní protějšek, ale provádí se asynchronně. Například následující kód stáhne domovskou stránku [dokumentace Microsoftu](https://docs.microsoft.com):

:::code language="csharp" source="./snippets/shared/Features.cs" ID="AsyncExample":::

Tento malý vzorek ukazuje hlavní funkce pro asynchronní programování:

- Deklarace metody obsahuje `async` modifikátor.
- Tělo metody `await` s vrácenou `GetByteArrayAsync` metodou
- Typ zadaný v `return` příkazu odpovídá argumentu typu v `Task<T>` deklaraci metody. (Metoda, která vrací `Task` příkaz, by použila `return` příkazy bez argumentů).

## <a name="attributes"></a>Atributy

Typy, členy a další entity v programu v jazyce C# podporují modifikátory, které řídí určité aspekty jejich chování. Například přístupnost metody je řízena pomocí `public` `protected` `internal` modifikátorů,, a `private` . Jazyk C# tuto funkci generalizuje tak, aby uživatelsky definované typy deklarativních informací mohly být připojeny k programovým entitám a načteny v době běhu. Programy určují tyto dodatečné deklarativní informace definováním a použitím [***atributů***](../programming-guide/concepts/attributes/index.md).

Následující příklad deklaruje `HelpAttribute` atribut, který lze umístit do entit programu, aby poskytoval odkazy na jeho přidruženou dokumentaci.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DefineAttribute":::

Všechny třídy atributů jsou odvozeny ze <xref:System.Attribute> základní třídy poskytované knihovnou .NET. Atributy lze použít zadáním jejich názvu spolu s případnými argumenty uvnitř hranatých závorek těsně před přidruženou deklarací. Pokud název atributu končí `Attribute` , Tato část názvu může být vynechána při odkazování na atribut. Například `HelpAttribute` lze použít následujícím způsobem.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="UseAttributes":::

Tento příklad připojí `HelpAttribute` ke `Widget` třídě. Přidá další `HelpAttribute` do `Display` metody ve třídě. Veřejné konstruktory třídy atributu určují informace, které je nutné zadat při připojení atributu k entitě programu. Další informace lze poskytnout odkazem na veřejné vlastnosti pro čtení a zápis třídy atributu (například odkaz na `Topic` vlastnost dříve).

Metadata definovaná atributy lze číst a manipulovat za běhu pomocí reflexe. Pokud je požadován konkrétní atribut pomocí této techniky, konstruktor třídy atributu je vyvolán s informacemi poskytnutými ve zdroji programu a výslednou instancí atributu je vrácen. Pokud byly k dispozici další informace prostřednictvím vlastností, jsou tyto vlastnosti nastaveny na zadané hodnoty před vrácením instance atributu.

Následující příklad kódu ukazuje, jak získat `HelpAttribute` instance přidružené ke `Widget` třídě a její `Display` metodě.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ReadAttributes":::

## <a name="learn-more"></a>Další informace

Další informace o C# můžete prozkoumat vyzkoušením některého z našich [kurzů](../tutorials/index.md).

>[!div class="step-by-step"]
>[Předchozí](program-building-blocks.md)
