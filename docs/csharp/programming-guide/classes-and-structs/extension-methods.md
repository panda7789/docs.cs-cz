---
title: Metody rozšíření – průvodce programováním jazyka C#
ms.date: 03/19/2020
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 0b35ad523fc7f0949cb5243edbdc50cd3e927999
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249217"
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozšíření (Průvodce programováním v C#)

Metody rozšíření umožňují „přidávat“ metody ke stávajícím typům bez vytváření nového odvozeného typu, rekompilace nebo jiné změny původního typu. Rozšiřující metody jsou statické metody, ale jsou volány, jako by byly instance metody na rozšířený typ. Pro kód klienta napsaný v jazyce C#, F# a Visual Basic, neexistuje žádný zjevný rozdíl mezi voláním metody rozšíření a metodami definovanými v typu.

Nejběžnější metody rozšíření jsou linq standardní dotaz operátory, které <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> přidávají funkce dotazu na existující a typy. Chcete-li použít standardní operátory dotazu, `using System.Linq` nejprve je uvést do oboru pomocí směrnice. Pak libovolný typ, <xref:System.Collections.Generic.IEnumerable%601> který implementuje <xref:System.Linq.Enumerable.GroupBy%2A>zdá <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.Average%2A>mít instance metody, jako je například , , a tak dále. Tyto další metody můžete vidět v příkazu IntelliSense dokončení, když <xref:System.Collections.Generic.IEnumerable%601> zadáte "tečka" za instanci typu, jako <xref:System.Collections.Generic.List%601> je například nebo <xref:System.Array>.

### <a name="orderby-example"></a>OrderBy Příklad

Následující příklad ukazuje, jak volat `OrderBy` metodu operátoru standardního dotazu v poli celá čísla. Výraz v závorkách je výraz lambda. Mnoho operátorů standardní dotaz ubírají lambda výrazy jako parametry, ale to není požadavek pro metody rozšíření. Další informace naleznete v tématu [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).

[!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]

Metody rozšíření jsou definovány jako statické metody, ale jsou volány pomocí syntaxe metody instance. Jejich první parametr určuje, na kterém typu metoda pracuje. Parametru předchází [tento](../../language-reference/keywords/this.md) modifikátor. Metody rozšíření jsou pouze v oboru, když explicitně importovat obor názvů do zdrojového kódu pomocí `using` směrnice.

Následující příklad ukazuje metodu rozšíření <xref:System.String?displayProperty=nameWithType> definovanou pro třídu. Je definována uvnitř nevnořené, neobecné statické třídy:

[!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]

Metoda `WordCount` rozšíření může být uvedena `using` do oblasti působnosti s touto směrnicí:

```csharp
using ExtensionMethods;
```

A může být volána z aplikace pomocí následující syntaxe:

```csharp
string s = "Hello Extension Methods";
int i = s.WordCount();
```

Metodu rozšíření v kódu vyvoláte se syntaxí metody instance. Zprostředkující jazyk (IL) generovaný kompilátorem převede váš kód do volání statické metody. Princip zapouzdření není ve skutečnosti porušován. Rozšiřující metody nemají přístup k soukromým proměnným v typu, který rozšiřují.

Další informace naleznete v [tématu Jak implementovat a volat vlastní metodu rozšíření](./how-to-implement-and-call-a-custom-extension-method.md).

Obecně platí, že budete pravděpodobně volat metody rozšíření mnohem častěji než implementace vlastní. Vzhledem k tomu, že metody rozšíření jsou volány pomocí syntaxe metody instance, není vyžadována žádná zvláštní znalost, abyste je mohli použít v klientském kódu. Chcete-li povolit metody rozšíření pro `using` určitý typ, stačí přidat direktivu pro obor názvů, ve kterém jsou definovány metody. Chcete-li například použít standardní operátory dotazů, přidejte tuto `using` direktivu do kódu:

```csharp
using System.Linq;
```

(Možná budete muset také přidat odkaz na soubor System.Core.dll.) Všimněte si, že standardní operátory dotazů se nyní zobrazují <xref:System.Collections.Generic.IEnumerable%601> v aplikaci IntelliSense jako další metody, které jsou k dispozici pro většinu typů.

## <a name="binding-extension-methods-at-compile-time"></a>Vytváření vazeb na metody rozšíření v době kompilace

Metody rozšíření můžete použít k rozšíření třídy nebo rozhraní, nikoli však k jejich přepsání. Metoda rozšíření se stejným názvem a signaturou, jako má rozhraní nebo metoda třídy, nebude nikdy volána. V době kompilace mají metody rozšíření vždy nižší prioritu než metody instance definované v samotném typu. Jinými slovy, pokud má typ `Process(int i)`metodu s názvem a máte metodu rozšíření se stejným podpisem, kompilátor se vždy sváže s metodou instance. Pokud kompilátor narazí na vyvolání metody, nejprve vyhledá shodu v metodách instance tohoto typu. Pokud není nalezena žádná shoda, budou vyhledány jakékoli metody rozšíření, které jsou definovány pro daný typ, a budou připojeny k první vyhledané metodě rozšíření. Následující příklad znázorňuje, jakým způsobem kompilátor určuje, se kterou metodou rozšíření nebo metodou instance má vytvořit vazbu.

## <a name="example"></a>Příklad

Následující příklad znázorňuje pravidla, které u kompilátoru jazyka C# určují, zda vytvořit vazbu volání metody s metodou instance v rámci typu, nebo s metodou rozšíření. Statická `Extensions` třída obsahuje rozšiřující metody definované `IMyInterface`pro libovolný typ, který implementuje . `A`Třídy `B`, `C` a všechny implementovat rozhraní.

Metoda `MethodB` rozšíření je nikdy volána, protože její název a podpis přesně odpovídají metodám, které již byly implementovány třídami.

Když kompilátor nemůže najít metodu instance s odpovídajícím podpisem, sváže se s odpovídající metodou rozšíření, pokud existuje.

[!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]

## <a name="common-usage-patterns"></a>Běžné vzory použití

### <a name="collection-functionality"></a>Funkce kolekce

V minulosti bylo běžné vytvořit "Třídy kolekce", které <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> implementovaly rozhraní pro daný typ a obsahovaly funkce, které fungovaly na kolekcích tohoto typu. I když není nic špatného na vytvoření tohoto typu objektu kolekce, stejné <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>funkce lze dosáhnout pomocí rozšíření na . Rozšíření mají tu výhodu, že umožňuje funkce, které mají <xref:System.Array?displayProperty=nameWithType> být <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> volány <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> z libovolné kolekce, jako je například nebo který implementuje na tento typ. Příklad tohoto použití pole Int32 lze nalézt [dříve v tomto článku](#orderby-example).

### <a name="layer-specific-functionality"></a>Funkce specifické pro vrstvu

Při použití architektury cibule nebo jiné vrstvené aplikace návrhu, je běžné mít sadu entit domény nebo přenosu dat objekty, které lze použít ke komunikaci přes hranice aplikace. Tyto objekty obecně neobsahují žádné funkce nebo pouze minimální funkce, které platí pro všechny vrstvy aplikace. Rozšiřující metody lze použít k přidání funkce, která je specifická pro každou aplikační vrstvu bez načtení objektu pomocí metod, které nejsou potřeba nebo jsou žádoucí v jiných vrstvách.

```aspx-csharp
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

Spíše než vytváření nových objektů při opakovaně použitelné funkce je třeba vytvořit, můžeme často rozšířit existující typ, jako je například .NET Framework nebo CLR typu. Jako příklad pokud nepoužíváme metody rozšíření, můžeme vytvořit `Engine` `Query` nebo třídy provést práci provádění dotazu na SQL Server, který může být volána z více míst v našem kódu. Nicméně můžeme místo <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> toho rozšířit třídu pomocí rozšiřujících metod k provedení tohoto dotazu z libovolného místa, kde máme připojení k SERVERU SQL. Dalšími příklady mohou být přidání <xref:System.String?displayProperty=nameWithType> běžných funkcí do třídy, <xref:System.IO.Stream?displayProperty=nameWithType> rozšíření <xref:System.Exception?displayProperty=nameWithType> možností zpracování dat objektů <xref:System.IO.File?displayProperty=nameWithType> a objektů a objektů pro konkrétní funkce zpracování chyb. Tyto typy případů použití jsou omezeny pouze vaší představivostí a zdravým rozumem.

Rozšíření předdefinovaných typů může `struct` být obtížné s typy, protože jsou předány hodnotou metodám. To znamená, že všechny změny struktury jsou provedeny na kopii struktury. Tyto změny nejsou viditelné po ukončení metody rozšíření. Počínaje C# 7.2, můžete `ref` přidat modifikátor k prvnímu argumentu metody rozšíření. Přidání `ref` modifikátoru znamená, že první argument je předán odkazem. To umožňuje psát metody rozšíření, které mění stav struktury, která je rozšířena.

## <a name="general-guidelines"></a>Obecné pokyny

I když je stále považováno za vhodnější přidat funkce úpravou kódu objektu nebo odvozením nového typu, kdykoli je to rozumné a možné, metody rozšíření se staly klíčovou možností pro vytváření opakovaně použitelných funkcí v celé .NET Ekosystému. Pro ty případy, kdy původní zdroj není pod vaší kontrolou, když odvozený objekt je nevhodné nebo nemožné, nebo když funkce by neměla být vystaveny mimo jeho příslušný rozsah, Extension metody jsou vynikající volbou.

Další informace o odvozených typech naleznete v [tématu Dědičnost](./inheritance.md).

Při použití metody rozšíření rozšířit typ, jehož zdrojový kód, který nejste pod kontrolou, riskujete, že změna v implementaci typu způsobí, že se metoda rozšíření přeruší.

Pokud implementujete metody rozšíření pro daný typ, nezapomeňte na následující body:

- Metoda rozšíření nebude nikdy volána, pokud má stejnou signaturu jako metoda definovaná v typu.
- Dále jsou metody rozšíření přeneseny do rozsahu na úrovni oboru názvů. Například pokud máte více statických tříd, které obsahují `Extensions`metody rozšíření v jednom oboru názvů `using Extensions;` s názvem , budou všechny uvedeny do oboru směrnice.

Chcete-li zamezit zvýšení čísla verze sestavení, neměli byste pro implementovanou knihovnu metody rozšíření používat. Pokud chcete přidat významné funkce do knihovny, jejíž zdrojový kód vlastníte, měli byste postupovat podle standardních pokynů pro rozhraní .NET Framework pro správu verzí sestavení. Další informace naleznete v [tématu Správa verzí sestavení](../../../standard/assembly/versioning.md).

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Ukázky paralelního programování (mezi ně patří mnoho ukázkových metod rozšíření)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Lambda výrazy](../statements-expressions-operators/lambda-expressions.md)
- [Přehled standardních operátorů dotazu](../concepts/linq/standard-query-operators-overview.md)
- [Pravidla převodu parametrů instance a jejich dopad](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Metody rozšíření Interoperabilita mezi jazyky](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Rozšiřující metody a curried delegáti](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Vazby metody rozšíření a hlášení chyb](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
