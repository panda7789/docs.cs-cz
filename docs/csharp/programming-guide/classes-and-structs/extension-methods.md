---
title: Metody rozšíření – Průvodce programováním v C#
ms.date: 03/19/2020
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 0f9c0f053e531a44640084a35dc5d8e844ee0b46
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803179"
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozšíření (Průvodce programováním v C#)

Metody rozšíření umožňují „přidávat“ metody ke stávajícím typům bez vytváření nového odvozeného typu, rekompilace nebo jiné změny původního typu. Rozšiřující metody jsou statické metody, ale jsou volány, jako by šlo o metody instance rozšířeného typu. Pro klientský kód napsaný v jazyce C#, F # a Visual Basic neexistuje žádný zřejmý rozdíl mezi voláním metody rozšíření a metodami definovanými v typu.

Nejběžnější metody rozšíření jsou operátory dotazů LINQ Standard, které přidávají funkce dotazů existujícím <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typům a. Chcete-li použít standardní operátory dotazu, nejprve je přeneste do rozsahu s `using System.Linq` direktivou. Pak jakýkoli typ, který implementuje, <xref:System.Collections.Generic.IEnumerable%601> má metody instance, jako například <xref:System.Linq.Enumerable.GroupBy%2A> , <xref:System.Linq.Enumerable.OrderBy%2A> , <xref:System.Linq.Enumerable.Average%2A> a tak dále. Tyto další metody lze zobrazit v dokončování příkazů technologie IntelliSense, pokud zadáte "tečka" po instanci <xref:System.Collections.Generic.IEnumerable%601> typu, například <xref:System.Collections.Generic.List%601> nebo <xref:System.Array> .

### <a name="orderby-example"></a>Příklad OrderBy

Následující příklad ukazuje, jak zavolat standardní metodu operátoru dotazu `OrderBy` na pole celých čísel. Výraz v závorkách je výraz lambda. Mnoho standardních operátorů dotazů přijímá výrazy lambda jako parametry, ale to není vyžadováno pro metody rozšíření. Další informace naleznete v tématu [lambda výrazy](../statements-expressions-operators/lambda-expressions.md).

[!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]

Metody rozšíření jsou definovány jako statické metody, ale jsou volány pomocí syntaxe metody instance. Jejich první parametr určuje, na který typ metoda pracuje. Tomuto parametru předchází [Tento](../../language-reference/keywords/this.md) modifikátor. Metody rozšíření jsou v oboru pouze v případě, že explicitně importujete obor názvů do zdrojového kódu s `using` direktivou.

Následující příklad ukazuje metodu rozšíření definovanou pro <xref:System.String?displayProperty=nameWithType> třídu. Je definovaný uvnitř nevnořené, neobecné statické třídy:

[!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]

`WordCount`Metoda rozšíření může být přenesena do rozsahu pomocí této `using` direktivy:

```csharp
using ExtensionMethods;
```

A může být volána z aplikace pomocí následující syntaxe:

```csharp
string s = "Hello Extension Methods";
int i = s.WordCount();
```

Metodu rozšíření ve vašem kódu vyvoláte pomocí syntaxe metody instance. Převodní jazyk (IL) generovaný kompilátorem překládá váš kód do volání statické metody. Princip zapouzdření není opravdu vyrušován. Metody rozšíření nemůžou přistupovat k privátním proměnným v typu, který rozšiřují.

Další informace naleznete v tématu [implementace a volání vlastní metody rozšíření](./how-to-implement-and-call-a-custom-extension-method.md).

Obecně platí, že budete pravděpodobně volat metody rozšíření mnohem častěji než implementace vlastního. Vzhledem k tomu, že metody rozšíření jsou volány pomocí syntaxe metody instance, není vyžadována žádná zvláštní znalost, abyste je mohli použít v klientském kódu. Chcete-li povolit metody rozšíření pro konkrétní typ, stačí přidat `using` direktivu pro obor názvů, ve kterém jsou metody definovány. Například pro použití standardních operátorů dotazu přidejte tuto `using` direktivu do kódu:

```csharp
using System.Linq;
```

(Je také možné, že budete muset přidat odkaz na System.Core.dll.) Všimněte si, že standardní operátory dotazu se teď zobrazují v IntelliSense jako další metody dostupné pro většinu <xref:System.Collections.Generic.IEnumerable%601> typů.

## <a name="binding-extension-methods-at-compile-time"></a>Vytváření vazeb na metody rozšíření v době kompilace

Metody rozšíření můžete použít k rozšíření třídy nebo rozhraní, nikoli však k jejich přepsání. Metoda rozšíření se stejným názvem a signaturou, jako má rozhraní nebo metoda třídy, nebude nikdy volána. V době kompilace mají metody rozšíření vždy nižší prioritu než metody instance definované v samotném typu. Jinými slovy, pokud typ obsahuje metodu s názvem a máte `Process(int i)` metodu rozšíření se stejnou signaturou, kompilátor bude vždy svázán s metodou instance. Pokud kompilátor narazí na vyvolání metody, nejprve vyhledá shodu v metodách instance tohoto typu. Pokud není nalezena žádná shoda, budou vyhledány jakékoli metody rozšíření, které jsou definovány pro daný typ, a budou připojeny k první vyhledané metodě rozšíření. Následující příklad znázorňuje, jakým způsobem kompilátor určuje, se kterou metodou rozšíření nebo metodou instance má vytvořit vazbu.

## <a name="example"></a>Příklad

Následující příklad znázorňuje pravidla, které u kompilátoru jazyka C# určují, zda vytvořit vazbu volání metody s metodou instance v rámci typu, nebo s metodou rozšíření. Statická třída `Extensions` obsahuje metody rozšíření definované pro jakýkoli typ, který implementuje `IMyInterface` . Třídy `A` , `B` a `C` implementují rozhraní.

`MethodB`Metoda rozšíření se nikdy nevolá, protože její název a signatura se přesně shodují s metodami, které už jsou implementované třídami.

Pokud kompilátor nemůže najít metodu instance s vyhovující signaturou, bude vytvořena vazba s vyhovující metodou rozšíření, pokud taková existuje.

[!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]

## <a name="common-usage-patterns"></a>Běžné vzorce použití

### <a name="collection-functionality"></a>Funkce kolekce

V minulosti bylo běžné vytvořit "třídy kolekcí", které implementovaly <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní pro daný typ a obsahovaly funkce, které se v kolekcích daného typu jednaly. Přestože při vytváření tohoto typu objektu kolekce není nic špatné, je možné dosáhnout stejné funkčnosti pomocí rozšíření na <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> . Rozšíření mají výhodu povolit volání funkce z jakékoli kolekce, jako je například <xref:System.Array?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> , která implementuje <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> Tento typ. Příklad tohoto použití pole typu Int32 najdete [výše v tomto článku](#orderby-example).

### <a name="layer-specific-functionality"></a>Funkce specifické pro vrstvu

Při použití průsvitek nebo jiného návrhu vrstvené aplikace je běžné mít sadu entit domény nebo Přenos dat objekty, které lze použít ke komunikaci napříč hranicemi aplikací. Tyto objekty obecně neobsahují žádné funkce nebo pouze minimální funkce, které se vztahují na všechny vrstvy aplikace. Metody rozšíření lze použít k přidání funkcionality, která je specifická pro každou vrstvu aplikace bez načítání objektu mimo jiné, než je potřeba nebo žádoucí v jiných vrstvách.

```csharp
public class DomainEntity
{
    public int Id { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
}

static class DomainEntityExtensions
{
    static string FullName(this DomainEntity value)
        => $"{value.FirstName} {value.LastName}";
}
```

### <a name="extending-predefined-types"></a>Rozšíření předdefinovaných typů

Místo vytváření nových objektů, pokud je třeba vytvořit opakovaně použitelná funkčnost, můžeme často rozlišit existující typ, například typ .NET nebo CLR. Pokud například nepoužíváme rozšiřující metody, můžeme vytvořit `Engine` `Query` třídu nebo k provedení dotazu na SQL Server, která může být volána z více míst v našem kódu. Místo toho však můžeme rozšířit <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> třídu pomocí rozšiřujících metod, aby bylo možné tento dotaz provést odkudkoli odkudkoli, máme připojení k SQL Server. Další příklady mohou být přidány do třídy společné funkce <xref:System.String?displayProperty=nameWithType> , rozšiřuje možnosti zpracování dat <xref:System.IO.File?displayProperty=nameWithType> objektů a a <xref:System.IO.Stream?displayProperty=nameWithType> <xref:System.Exception?displayProperty=nameWithType> objekty pro konkrétní funkce zpracování chyb. Tyto typy případů použití jsou omezené jenom představivost a dobrým smyslem.

Rozšíření předdefinovaných typů může být obtížné s `struct` typy, protože jsou předány podle hodnoty metodám. To znamená, že všechny změny struktury jsou provedeny na kopii struktury. Tyto změny nejsou po ukončení metody rozšíření viditelné. Počínaje jazykem C# 7,2 můžete přidat `ref` Modifikátor k prvnímu argumentu metody rozšíření. Přidání `ref` modifikátoru znamená, že první argument je předán odkazem. To umožňuje psát rozšiřující metody, které mění stav rozšířené struktury.

## <a name="general-guidelines"></a>Obecné pokyny

I když je stále vhodnější přidat funkce úpravou kódu objektu nebo odvozením nového typu pokaždé, když je to přijatelné a možné, je nutné, aby se metody rozšíření staly zásadní volbou pro vytváření opakovaně použitelných funkcí v rámci ekosystému .NET. Pro případy, kdy původní zdroj není pod vaším ovládacím prvkem, když je odvozený objekt nevhodný nebo nedostupný nebo pokud by se funkce nemusely vystavit nad rámec příslušného rozsahu, jsou rozšiřující metody vynikající volbou.

Další informace o odvozených typech naleznete v tématu [Dědičnost](./inheritance.md).

Při použití rozšiřující metody k rozšíření typu, jehož zdrojový kód neovládáte, spustíte riziko, že změna implementace typu způsobí, že vaše metoda rozšíření bude mít za následek přerušení.

Pokud implementujete metody rozšíření pro daný typ, mějte na paměti následující body:

- Metoda rozšíření nebude nikdy volána, pokud má stejnou signaturu jako metoda definovaná v typu.
- Dále jsou metody rozšíření přeneseny do rozsahu na úrovni oboru názvů. Například pokud máte více statických tříd, které obsahují metody rozšíření v jednom oboru názvů s názvem `Extensions` , budou všechny převedeny do rozsahu podle `using Extensions;` direktivy.

Chcete-li zamezit zvýšení čísla verze sestavení, neměli byste pro implementovanou knihovnu metody rozšíření používat. Pokud chcete přidat významné funkce do knihovny, pro kterou vlastníte zdrojový kód, postupujte podle pokynů rozhraní .NET pro správu verzí sestavení. Další informace naleznete v tématu [Správa verzí sestavení](../../../standard/assembly/versioning.md).

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Ukázky paralelního programování (zahrnuje mnoho ukázkových metod rozšíření)](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
- [Výrazy lambda](../statements-expressions-operators/lambda-expressions.md)
- [Přehled standardních operátorů dotazu](../concepts/linq/standard-query-operators-overview.md)
- [Pravidla převodu pro parametry instance a jejich dopad](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Interoperabilita metod rozšíření mezi jazyky](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Metody rozšíření a Delegáti curryfikované](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Vazba metody rozšíření a zasílání zpráv o chybách](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
