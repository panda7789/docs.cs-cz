---
title: Psaní velkých a pohotově reagujících aplikací .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 57f65feff5260cb83df5354f5d7ee1bad0babb3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180585"
---
# <a name="writing-large-responsive-net-framework-apps"></a>Psaní velkých a pohotově reagujících aplikací .NET Framework

Tento článek obsahuje tipy pro zlepšení výkonu velkých aplikací rozhraní .NET Framework nebo aplikací, které zpracovávají velké množství dat, jako jsou soubory nebo databáze. Tyto tipy pocházejí z přepisování kompilátorů jazyka C# a Visual Basic ve spravovaném kódu a tento článek obsahuje několik reálných příkladů z kompilátoru Jazyka C#.
  
Rozhraní .NET Framework je vysoce produktivní pro vytváření aplikací. Díky výkonným a bezpečným jazykům a bohaté sbírce knihoven je vytváření aplikací velmi plodné. Nicméně, s velkou produktivitou přichází odpovědnost. Měli byste použít všechny výkon rozhraní .NET Framework, ale být připraveni vyladit výkon kódu v případě potřeby.
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Proč se nový výkon kompilátoru vztahuje na vaši aplikaci  
 Tým .NET Compiler Platform ("Roslyn") přepsal kompilátory jazyka C# a Visual Basic ve spravovaném kódu, aby poskytoval nová rozhraní API pro modelování a analýzu kódu, vytváření nástrojů a povolení mnohem bohatších prostředí podporujících kód v sadě Visual Studio. Přepsání kompilátorů a vytváření prostředí sady Visual Studio na nových kompilátorech odhalilo užitečné přehledy výkonu, které jsou použitelné pro všechny velké aplikace rozhraní .NET Framework nebo pro jakoukoli aplikaci, která zpracovává velké množství dat. Nemusíte vědět o kompilátory využít přehledy a příklady z kompilátoru Jazyka C#.
  
 Visual Studio používá rozhraní API kompilátoru k vytvoření všech funkcí Technologie IntelliSense, které uživatelé milují, jako je vybarvení identifikátorů a klíčových slov, seznamy dokončení syntaxe, klikyháky pro chyby, tipy parametrů, problémy s kódem a akce kódu. Visual Studio poskytuje tuto nápovědu, zatímco vývojáři přidávají a mění svůj kód a Visual Studio musí zůstat responzivní, zatímco kompilátor neustále modeluje kód, který vývojáři upravují.
  
 Když vaši koncoví uživatelé interagují s vaší aplikací, očekávají, že bude reagovat. Psaní nebo zpracování příkazů by nikdy nemělo být blokováno. Nápověda by se měla rychle objevit nebo se vzdát, pokud uživatel pokračuje v psaní. Vaše aplikace by se měla vyhnout blokování vlákna uživatelského rozhraní s dlouhými výpočty, které dělají aplikaci pomalu.
  
 Další informace o kompilátorech Roslyn naleznete [v tématu .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).
  
## <a name="just-the-facts"></a>Jen fakta  
 Zvažte tato fakta při ladění výkonu a vytváření responzivních aplikací rozhraní .NET Framework.
  
### <a name="fact-1-dont-prematurely-optimize"></a>Fakt 1: Neoptimalizujte předčasně  
 Psaní kódu, který je složitější, než je třeba, které mají být vzniknou náklady na údržbu, ladění a leštění. Zkušení programátoři mají intuitivní přehled o tom, jak řešit problémy s kódováním a psát efektivnější kód. Někdy však předčasně optimalizují svůj kód. Používají například tabulku hash, když by stačilo jednoduché pole, nebo používají složité ukládání do mezipaměti, které může unikat paměť namísto pouhého opětovného výpočtu hodnot. I když jste programátor zkušeností, měli byste otestovat výkon a analyzovat kód, když zjistíte problémy.
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Fakt 2: Pokud neměříte, hádáte  
 Profily a měření nelžou. Profily ukazují, zda je procesor plně načten nebo zda jste blokováni vstupně-diskem. Profily vám řeknou, jaký druh a kolik paměti přidělujete a zda procesor tráví spoustu času v [uvolňování paměti](../../standard/garbage-collection/index.md) (GC).
  
 Měli byste nastavit cíle výkonu pro klíčové zkušenosti zákazníků nebo scénáře ve vaší aplikaci a psát testy pro měření výkonu. Prozkoumejte neúspěšné testy pomocí vědecké metody: použijte profily, které vás provedou, předpokládají, jaký problém by mohl být, a otestujte hypotézu pomocí experimentu nebo změny kódu. Stanovit základní měření výkonu v průběhu času s pravidelným testováním, takže můžete izolovat změny, které způsobují regrese ve výkonu. Tím, že se přiblížíte k práci s výkonem přísným způsobem, vyhnete se plýtvání časem s aktualizacemi kódu, které nepotřebujete.
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Fakt 3: Dobré nástroje, aby celý rozdíl  
 Dobré nástroje umožňují rychle přejít k podrobnostem o největších problémech s výkonem (procesor, paměť nebo disk) a pomoci vám najít kód, který způsobuje tato kritická místa. Společnost Microsoft dodává různé nástroje pro výkon, například [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) a [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).
  
 PerfView je bezplatný a úžasně výkonný nástroj, který vám pomůže zaměřit se na hluboké problémy, jako je disk V/O, GC události a paměť. Můžete zachytit události sledování událostí související s [výkonem pro Windows](../wcf/samples/etw-tracing.md) (ETW) a snadno zobrazit na aplikaci, na proces, na zásobník a informace o vlákně. PerfView ukazuje, kolik a jaký druh paměti vaše aplikace přiděluje a které funkce nebo zásobníky volání přispívají, kolik přidělení paměti. Podrobnosti najdete v tématech s bohatou nápovědou, ukázkách a videích, které jsou součástí nástroje (například [kurzy PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) na kanálu 9).
  
### <a name="fact-4-its-all-about-allocations"></a>Fakt 4: Je to všechno o přidělení  
 Můžete si myslet, že vytváření responzivní aplikace rozhraní .NET Framework je o algoritmech, jako je například použití rychlého řazení namísto řazení bublin, ale to není tento případ. Největším faktorem při vytváření responzivní aplikace je přidělování paměti, zejména když je vaše aplikace velmi velká nebo zpracovává velké množství dat.
  
 Téměř všechny práce na vytváření responzivních prostředí IDE s novými rozhraními API kompilátoru zahrnovaly předcházení přidělení a správu strategií ukládání do mezipaměti. PerfView trasování ukazují, že výkon nové c# a visual basic kompilátory je zřídka vázaný na procesor. Kompilátory mohou být vázány vstupně-výstupními moduly při čtení stovek tisíc nebo milionů řádků kódu, čtení metadat nebo vyzařování generovaného kódu. Zpoždění vlákna uživatelského rozhraní jsou téměř všechny z důvodu uvolňování paměti. .NET Framework GC je vysoce naladěn na výkon a provádí velkou část své práce souběžně při spuštění kódu aplikace. Jediné přidělení však může aktivovat kolekci nákladné [gen2,](../../standard/garbage-collection/fundamentals.md) zastavení všech vláken.
  
## <a name="common-allocations-and-examples"></a>Společné příděly a příklady  
 Ukázkové výrazy v této části mají skryté přidělení, které se zobrazují malé. Pokud však velká aplikace spustí výrazy dostatečně krát, mohou způsobit stovky megabajtů, dokonce i gigabajtů přidělení. Například jednominutové testy, které simulovaly psaní vývojáře v editoru, přidělily gigabajty paměti a vedly tým výkonu k zaměření na scénáře psaní.
  
### <a name="boxing"></a>Zabalení  
 [K zabalení](../../csharp/programming-guide/types/boxing-and-unboxing.md) dochází, když typy hodnot, které normálně žijí v zásobníku nebo v datových strukturách, jsou zabaleny do objektu. To znamená, že přidělíte objekt k uložení dat a potom vrátíte ukazatel na objekt. Rozhraní .NET Framework někdy krabice hodnoty z důvodu podpisu metody nebo typ umístění úložiště. Obtékání typu hodnoty v objektu způsobí přidělení paměti. Mnoho operací zabalení může do vaší aplikace přispívat megabajty nebo gigabajty přidělení, což znamená, že vaše aplikace způsobí více řadičů domény. Rozhraní .NET Framework a kompilátory jazyka vyhnout zabalení, pokud je to možné, ale někdy se to stane, když nejméně očekávat.
  
 Chcete-li zobrazit zabalení v PerfView, otevřete trasování a podívejte se na GC Haldy Alloc zásobníky pod název procesu vaší aplikace (pamatujte, PerfView sestavy na všechny procesy). Pokud se zobrazí <xref:System.Int32?displayProperty=nameWithType> <xref:System.Char?displayProperty=nameWithType> typy jako a pod přidělení, jsou zabalení typy hodnot. Výběr jednoho z těchto typů se zobrazí zásobníky a funkce, ve kterých jsou zabaleny.
  
 **Příklad 1: metody řetězce a argumenty typu hodnoty**  
  
 Tento ukázkový kód ilustruje potenciálně zbytečné a nadměrné zabalení:  
  
```csharp  
public class Logger  
{  
    public static void WriteLine(string s) { /*...*/ }  
}  
  
public class BoxingExample  
{  
    public void Log(int id, int size)  
    {  
        var s = string.Format("{0}:{1}", id, size);  
        Logger.WriteLine(s);  
    }  
}  
```  
  
 Tento kód poskytuje funkce protokolování, takže `Log` aplikace může volat funkci často, možná milionkrát. Problém je, že `string.Format` volání řeší <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> přetížení.
  
 Toto přetížení vyžaduje rozhraní .NET Framework zaokříznout `int` hodnoty do objektů předat volání této metody. Částečná oprava je `id.ToString()` `size.ToString()` volání a předání všech řetězců (které `string.Format` jsou objekty) volání. Volání `ToString()` přiděluje řetězec, ale toto přidělení se stane stejně uvnitř `string.Format`.
  
 Můžete zvážit, že toto základní volání `string.Format` je pouze zřetězení řetězce, takže místo toho můžete napsat tento kód:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Tento řádek kódu však zavádí přidělení zabalení, <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>protože zkompiluje do . Rozhraní .NET Framework musí zaokřovat literál znaku, který vyvolá`Concat`  
  
 **Opravit například 1**  
  
 Kompletní oprava je jednoduchá. Stačí nahradit literál znaku literál řetězcem, který nevzniká žádné zabalení, protože řetězce jsou již objekty:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Příklad 2: enum boxing**  
  
 Tento příklad byl zodpovědný za obrovské množství přidělení v nové kompilátory jazyka C# a Visual Basic z důvodu časté hojné použití typů výčtu, zejména ve slovníku vyhledávací operace.
  
```csharp  
public enum Color  
{  
    Red, Green, Blue  
}  
  
public class BoxingExample  
{  
    private string name;  
    private Color color;  
    public override int GetHashCode()  
    {  
        return name.GetHashCode() ^ color.GetHashCode();  
    }  
}  
```  
  
 Tento problém je velmi jemný. PerfView by to <xref:System.Enum.GetHashCode> hlásit jako zabalení, protože metoda boxy základní reprezentace typu výčtu, z důvodů implementace. Pokud se podíváte pozorně v PerfView, může se <xref:System.Enum.GetHashCode>zobrazit dvě přidělení zabalení pro každé volání . Kompilátor vloží jeden a rozhraní .NET Framework vloží druhou.
  
 **Oprava například 2**  
  
 Můžete snadno vyhnout obě přidělení obsazení majestátu před voláním <xref:System.Enum.GetHashCode>:  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Dalším běžným zdrojem zabalení na <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> typy výčtu je metoda. Argument předaný <xref:System.Enum.HasFlag%28System.Enum%29> musí být zabalen. Ve většině případů nahrazení <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> volání bitovým testem je jednodušší a bez přidělení.
  
 Mějte na paměti první fakt výkonu (to znamená, nepředčasně optimalizovat) a nezačínejte přepisovat veškerý kód tímto způsobem. Uvědomte si tyto náklady na box, ale změnit kód pouze po profilování aplikace a hledání horkých míst.
  
### <a name="strings"></a>Řetězce  
 Řetězec manipulace jsou některé z největších viníků pro přidělení a často se zobrazí v PerfView v prvních pěti přidělení. Programy používají řetězce pro serializaci, JSON a REST API. Řetězce můžete použít jako programové konstanty pro spolupráci se systémy, když nelze použít typy výčtu. Pokud profilování ukazuje, že řetězce mají velký vliv <xref:System.String> na <xref:System.String.Format%2A>výkon, <xref:System.String.Split%2A> <xref:System.String.Join%2A>vyhledejte volání metod, jako jsou například , <xref:System.String.Substring%2A> <xref:System.String.Concat%2A>, , a tak dále. Použití, <xref:System.Text.StringBuilder> aby se zabránilo náklady na vytvoření jednoho řetězce z <xref:System.Text.StringBuilder> mnoha kusů pomáhá, ale i přidělení objektu se může stát kritickým bodem, který je třeba spravovat.
  
 **Příklad 3: operace řetězce**  
  
 Kompilátor Jazyka C# měl tento kód, který zapisuje text formátovaného komentáře dokumentu XML:  
  
```csharp  
public void WriteFormattedDocComment(string text)  
{  
    string[] lines = text.Split(new[] { "\r\n", "\r", "\n" },  
                                StringSplitOptions.None);  
    int numLines = lines.Length;  
    bool skipSpace = true;  
    if (lines[0].TrimStart().StartsWith("///"))  
    {  
        for (int i = 0; i < numLines; i++)  
        {  
            string trimmed = lines[i].TrimStart();  
            if (trimmed.Length < 4 || !char.IsWhiteSpace(trimmed[3]))  
            {  
                skipSpace = false;  
                break;  
            }  
        }  
        int substringStart = skipSpace ? 4 : 3;  
        for (int i = 0; i < numLines; i++)  
            WriteLine(lines[i].TrimStart().Substring(substringStart));  
    }  
    else { /* ... */ }  
```  
  
 Můžete vidět, že tento kód provádí mnoho manipulace s řetězci. Kód používá metody knihovny k rozdělení řádků do samostatných řetězců, `text` k oříznutí prázdného místa, ke kontrole, zda je argument emblém dokumentace XML, a k extrahování podřetězců z řádků.
  
 Na prvním řádku `WriteFormattedDocComment`uvnitř `text.Split` volání přiděluje nové pole tří prvků jako argument pokaždé, když je volána. Kompilátor musí vyzařovat kód pro přidělení tohoto pole pokaždé. Důvodem je, že kompilátor <xref:System.String.Split%2A> neví, pokud ukládá pole někde, kde pole může být `WriteFormattedDocComment`změněn jiným kódem, což by ovlivnilo pozdější volání . Volání <xref:System.String.Split%2A> také přiděluje řetězec pro `text` každý řádek v a přiděluje další paměti k provedení operace.
  
 `WriteFormattedDocComment`má tři volání <xref:System.String.TrimStart%2A> metody. Dva jsou ve vnitřních smyčkách, které duplikují práci a přidělení. Aby toho nebylo málo, volání <xref:System.String.TrimStart%2A> metody bez argumentů přiděluje prázdné pole (pro `params` parametr) kromě výsledku řetězce.
  
 Nakonec je volání <xref:System.String.Substring%2A> metody, která obvykle přiděluje nový řetězec.
  
 **Opravit například 3**  
  
 Na rozdíl od předchozích příkladů malé úpravy nelze opravit tyto přidělení. Musíte ustoupit, podívat se na problém a přistupovat k němu jinak. Například si všimnete, že `WriteFormattedDocComment()` argument je řetězec, který má všechny informace, které metoda potřebuje, takže kód může provést více indexování namísto přidělení mnoho dílčích řetězců.
  
 Výkonnostní tým kompilátoru řešil všechny tyto přidělení s kódem, jako je tento:  
  
```csharp  
private int IndexOfFirstNonWhiteSpaceChar(string text, int start) {  
    while (start < text.Length && char.IsWhiteSpace(text[start])) start++;  
    return start;  
}  
  
private bool TrimmedStringStartsWith(string text, int start, string prefix) {  
    start = IndexOfFirstNonWhiteSpaceChar(text, start);  
    int len = text.Length - start;  
    if (len < prefix.Length) return false;  
    for (int i = 0; i < len; i++)  
    {  
        if (prefix[i] != text[start + i]) return false;  
    }  
    return true;  
}  
  
// etc...
```  
  
 První verze `WriteFormattedDocComment()` přidělené pole, několik podřetězců a oříznuté podřetězec spolu `params` s prázdným polem. Také zkontroloval "///". Revidovaný kód používá pouze indexování a nepřiděluje nic. Najde první znak, který není prázdné místo a potom zkontroluje znak po znaku, aby zjistil, zda řetězec začíná "///". Nový kód `IndexOfFirstNonWhiteSpaceChar` používá <xref:System.String.TrimStart%2A> místo vrátit první index (po zadaném indexu start), kde dojde k neprázdné místo znaku. Oprava není dokončena, ale můžete vidět, jak použít podobné opravy pro úplné řešení. Použitím tohoto přístupu v celém kódu můžete `WriteFormattedDocComment()`odebrat všechna přidělení v aplikaci .
  
 **Příklad 4: StringBuilder**  
  
 Tento příklad <xref:System.Text.StringBuilder> používá objekt. Následující funkce generuje úplný název typu pro obecné typy:  
  
```csharp  
public class Example  
{  
    // Constructs a name like "SomeType<T1, T2, T3>"  
    public string GenerateFullTypeName(string name, int arity)  
    {  
        StringBuilder sb = new StringBuilder();  
  
        sb.Append(name);  
        if (arity != 0)  
        {  
            sb.Append("<");  
            for (int i = 1; i < arity; i++)  
            {  
                sb.Append("T"); sb.Append(i.ToString()); sb.Append(", ");  
            }  
            sb.Append("T"); sb.Append(i.ToString()); sb.Append(">");  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
 Fokus je na řádku, <xref:System.Text.StringBuilder> který vytvoří novou instanci. Kód způsobí přidělení `sb.ToString()` a vnitřní přidělení <xref:System.Text.StringBuilder> v rámci implementace, ale nelze řídit tato přidělení, pokud chcete výsledek řetězce.
  
 **Oprava například 4**  
  
 Chcete-li `StringBuilder` opravit přidělení objektu, uvěnujte objekt do mezipaměti. Dokonce i ukládání do mezipaměti jedné instance, která by mohla dostat vyhodit může výrazně zlepšit výkon. Toto je nová implementace funkce, vynechání veškerý kód s výjimkou nové první a poslední řádky:  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Klíčovými částmi `AcquireBuilder()` jsou `GetStringAndReleaseBuilder()` nové a funkce:  
  
```csharp  
[ThreadStatic]  
private static StringBuilder cachedStringBuilder;  
  
private static StringBuilder AcquireBuilder()  
{  
    StringBuilder result = cachedStringBuilder;  
    if (result == null)  
    {  
        return new StringBuilder();  
    }  
    result.Clear();  
    cachedStringBuilder = null;  
    return result;  
}  
  
private static string GetStringAndReleaseBuilder(StringBuilder sb)  
{  
    string result = sb.ToString();  
    cachedStringBuilder = sb;  
    return result;  
}  
```  
  
 Vzhledem k tomu, že nové kompilátory používají<xref:System.ThreadStaticAttribute> podproces, tyto <xref:System.Text.StringBuilder>implementace používají statické pole `ThreadStatic` podprocesu (atribut) k ukládání do mezipaměti a pravděpodobně můžete zprostit deklarace. Pole statické vlákno obsahuje jedinečnou hodnotu pro každé vlákno, které spustí tento kód.
  
 `AcquireBuilder()`vrátí instanci uloženou v mezipaměti, <xref:System.Text.StringBuilder> pokud existuje, po vymazání a nastavení pole nebo mezipaměti na hodnotu null. V `AcquireBuilder()` opačném případě vytvoří novou instanci a vrátí ji, přičemž pole nebo mezipaměti nastavena na hodnotu null.
  
 Po dokončení s <xref:System.Text.StringBuilder> , volání `GetStringAndReleaseBuilder()` získat výsledek řetězce, <xref:System.Text.StringBuilder> uložte instanci v poli nebo mezipaměti a potom vrátit výsledek. Je možné pro spuštění znovu zadat tento kód <xref:System.Text.StringBuilder> a vytvořit více objektů (i když to zřídka se stane). Kód uloží pouze poslední <xref:System.Text.StringBuilder> vydané instance pro pozdější použití. Tato jednoduchá strategie ukládání do mezipaměti výrazně snížila přidělení v nových kompilátorech. Části rozhraní .NET Framework a MSBuild ("MSBuild") používají podobnou techniku ke zlepšení výkonu.
  
 Tato jednoduchá strategie ukládání do mezipaměti dodržuje dobrý design mezipaměti, protože má velikostní čepici. Existuje však více kódu nyní než v originále, což znamená více nákladů na údržbu. Strategii ukládání do mezipaměti byste měli přijmout pouze v případě, že jste <xref:System.Text.StringBuilder> našli problém s výkonem a PerfView ukázalo, že přidělení jsou významným přispěvatelem.
  
### <a name="linq-and-lambdas"></a>LINQ a lambdas  
Jazykově integrovaný dotaz (LINQ), ve spojení s výrazy lambda, je příkladem funkce produktivity. Jeho použití však může mít významný vliv na výkon v průběhu času a může být nutné přepsat kód.
  
 **Příklad 5: Lambdas, Seznam\<T>\<a IEnumerable T>**  
  
 Tento příklad používá [linq a kód funkčního stylu](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) k nalezení symbolu v modelu kompilátoru, který je uveden v řetězci názvu:  
  
```csharp  
class Symbol {  
    public string Name { get; private set; }  
    /*...*/  
}  
  
class Compiler {  
    private List<Symbol> symbols;  
    public Symbol FindMatchingSymbol(string name)  
    {  
        return symbols.FirstOrDefault(s => s.Name == name);  
    }  
}  
```  
  
 Nový kompilátor a prostředí IDE `FindMatchingSymbol()` postavené na něm volání velmi často a existuje několik skrytých přidělení v této funkce jeden řádek kódu. Chcete-li zkontrolovat tyto přidělení, nejprve rozdělit funkci jeden řádek kódu do dvou řádků:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 V prvním řádku [lambda výraz](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [zavře přes](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) `name`místní proměnné . To znamená, že kromě přidělení objektu pro [delegáta,](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) který `predicate` drží, kód přiděluje statickou `name`třídu pro uložení prostředí, které zachycuje hodnotu . Kompilátor generuje kód takto:  
  
```csharp  
// Compiler-generated class to hold environment state for lambda  
private class Lambda1Environment  
{  
    public string capturedName;  
    public bool Evaluate(Symbol s)  
    {  
        return s.Name == this.capturedName;  
    }  
}  
  
// Expanded Func<Symbol, bool> predicate = s => s.Name == name;  
Lambda1Environment l = new Lambda1Environment() { capturedName = name };  
var predicate = new Func<Symbol, bool>(l.Evaluate);  
```  
  
 Dvě `new` přidělení (jeden pro třídu prostředí a jeden pro delegáta) jsou nyní explicitní.
  
 Nyní se podívejte `FirstOrDefault`na volání do . Tato metoda rozšíření <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> na typu vznikne přidělení příliš. Protože `FirstOrDefault` má <xref:System.Collections.Generic.IEnumerable%601> objekt jako svůj první argument, můžete rozšířit volání na následující kód (zjednodušený bit pro diskusi):  
  
```csharp  
// Expanded return symbols.FirstOrDefault(predicate) ...
     IEnumerable<Symbol> enumerable = symbols;  
     IEnumerator<Symbol> enumerator = enumerable.GetEnumerator();  
     while(enumerator.MoveNext())  
     {  
         if (predicate(enumerator.Current))  
             return enumerator.Current;  
     }  
     return default(Symbol);  
```  
  
 Proměnná `symbols` má <xref:System.Collections.Generic.List%601>typ . Typ <xref:System.Collections.Generic.List%601> kolekce <xref:System.Collections.Generic.IEnumerable%601> implementuje a chytře definuje čítač (rozhraní),<xref:System.Collections.Generic.IEnumerator%601> který <xref:System.Collections.Generic.List%601> implementuje `struct`s . Použití struktury namísto třídy znamená, že se obvykle vyhnete přidělení haldy, což může ovlivnit výkon uvolňování paměti. Čítače výčtu se obvykle používají `foreach` s smyčkou jazyka, který používá strukturu čítače výčtu, jak je vrácena v zásobníku volání. Zvýšení ukazatele zásobníku volání, aby se uvolnilo místo pro objekt, nemá vliv na gc tak, jak přidělení haldy nemá.
  
 V případě rozšířenévolání `FirstOrDefault` kód musí volat `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>. Přiřazení `symbols` `enumerable` proměnné typu `IEnumerable<Symbol>` ztratí informace o tom, že <xref:System.Collections.Generic.List%601>skutečný objekt je . To znamená, že když kód načte `enumerable.GetEnumerator()`čítač s , rozhraní .NET Framework `enumerator` musí zaokřovat vrácenou strukturu a přiřadit ji proměnné.
  
 **Oprava například 5**  
  
 Oprava je přepsat `FindMatchingSymbol` takto, nahrazení jeho jeden řádek kódu se šesti řádky kódu, které jsou stále stručné, snadno čitelné a srozumitelné a snadno udržovatelné:  
  
```csharp  
public Symbol FindMatchingSymbol(string name)  
    {  
        foreach (Symbol s in symbols)  
        {  
            if (s.Name == name)  
                return s;  
        }  
        return null;  
    }  
```  
  
 Tento kód nepoužívá linq rozšíření metody, lambdas nebo čítače výčtu a vznikne žádné přidělení. Neexistují žádné přidělení, protože kompilátor `symbols` může vidět, že kolekce je <xref:System.Collections.Generic.List%601> a může vázat výsledný čítač výčtu (struktura) na místní proměnnou se správným typem, aby se zabránilo zabalení. Původní verze této funkce byla skvělým příkladem expresivní výkon Jazyka C# a produktivitu rozhraní .NET Framework. Tato nová a efektivnější verze zachovává tyto vlastnosti bez přidání jakéhokoli složitého kódu pro údržbu.
  
### <a name="async-method-caching"></a>Ukládání do mezipaměti asynchronní metody  

Následující příklad ukazuje běžný problém při pokusu o použití výsledků v mezipaměti v [asynchronní](../../csharp/programming-guide/concepts/async/index.md) metodě.
  
 **Příklad 6: ukládání do mezipaměti v asynchronních metodách**  
  
 Visual Studio IDE funkce postavené na nové kompilátory Jazyka C# a Visual Basic často načítat stromy syntaxe a kompilátory použít asynchronní při tom, aby Visual Studio reagovat. Zde je první verze kódu, který můžete napsat, abyste získali strom syntaxe:  
  
```csharp  
class SyntaxTree { /*...*/ }  
  
class Parser { /*...*/  
    public SyntaxTree Syntax { get; }  
    public Task ParseSourceCode() { /*...*/ }  
}  
  
class Compilation { /*...*/  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 Můžete vidět, `GetSyntaxTreeAsync()` že volání konkretizuje `Parser`, analyzuje kód <xref:System.Threading.Tasks.Task> a `Task<SyntaxTree>`pak vrátí objekt, . Nákladné část je přidělení `Parser` instance a analýzy kódu. Funkce vrátí <xref:System.Threading.Tasks.Task> tak, aby volající můžete čekat na práci analýzy a uvolnit vlákno uživatelského rozhraní, které mají být citlivé na vstup uživatele.
  
 Několik funkcí sady Visual Studio se může pokusit získat stejný strom syntaxe, takže můžete napsat následující kód pro uložení výsledku analýzy do mezipaměti, abyste ušetřili čas a přidělení. Tento kód však vzniká přidělení:  
  
```csharp  
class Compilation { /*...*/  
  
    private SyntaxTree cachedResult;  
  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        if (this.cachedResult == null)  
        {  
            var parser = new Parser(); // allocation  
            await parser.ParseSourceCode(); // expensive  
            this.cachedResult = parser.Syntax;  
        }  
        return this.cachedResult;  
    }  
}  
```  
  
 Uvidíte, že nový kód s `SyntaxTree` ukládáním `cachedResult`do mezipaměti má pole s názvem . Pokud je toto `GetSyntaxTreeAsync()` pole null, provádí práci a ukládá výsledek do mezipaměti. `GetSyntaxTreeAsync()`vrátí `SyntaxTree` objekt. Problém je, že pokud `async` máte `Task<SyntaxTree>`funkci typu a vrátíte `SyntaxTree`hodnotu typu , kompilátor vydává kód pro `Task<SyntaxTree>.FromResult()`přidělení Task uchovávat výsledek (pomocí ). Úkol je označen jako dokončený a výsledek je okamžitě k dispozici. V kódu pro nové kompilátory objekty, <xref:System.Threading.Tasks.Task> které již byly dokončeny došlo tak často, že oprava těchto přidělení výrazně zlepšila odezvu.
  
 **Oprava například 6**  
  
 Chcete-li <xref:System.Threading.Tasks.Task> odebrat dokončené přidělení, můžete uložit objekt Task do mezipaměti s dokončeným výsledkem:  
  
```csharp  
class Compilation { /*...*/  
  
    private Task<SyntaxTree> cachedResult;  
  
    public Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        return this.cachedResult ??
               (this.cachedResult = GetSyntaxTreeUncachedAsync());  
    }  
  
    private async Task<SyntaxTree> GetSyntaxTreeUncachedAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 Tento kód změní `cachedResult` typ `Task<SyntaxTree>` do a `async` používá pomocnou funkci, `GetSyntaxTreeAsync()`která obsahuje původní kód z aplikace . `GetSyntaxTreeAsync()`Nyní používá [null coalescing](../../csharp/language-reference/operators/null-coalescing-operator.md) `cachedResult` operátor vrátit, pokud není null. Pokud `cachedResult` je null, pak `GetSyntaxTreeAsync()` volá `GetSyntaxTreeUncachedAsync()` a ukládá výsledek. Všimněte `GetSyntaxTreeAsync()` si, že nečeká `GetSyntaxTreeUncachedAsync()` volání jako kód by normálně. Nepoužíváte await znamená, že když `GetSyntaxTreeUncachedAsync()` vrátí svůj <xref:System.Threading.Tasks.Task> objekt, `GetSyntaxTreeAsync()` okamžitě vrátí <xref:System.Threading.Tasks.Task>. Nyní je výsledek uložený <xref:System.Threading.Tasks.Task>v mezipaměti , takže neexistují žádné přidělení vrátit výsledek mezipaměti.
  
### <a name="additional-considerations"></a>Další aspekty  
 Tady je několik dalších bodů o potenciálních problémech ve velkých aplikacích nebo aplikacích, které zpracovávají velké množství dat.
  
 **Slovníky**  
  
 Slovníky se používají všudypřítomně v mnoha programech, a když slovníky jsou velmi pohodlné a ze své podstaty efektivní. Často se však používají nevhodně. V sadě Visual Studio a nové kompilátory analýza ukazuje, že mnoho slovníků obsahovaljeden prvek nebo byly prázdné. Prázdné <xref:System.Collections.Generic.Dictionary%602> má deset polí a zabírá 48 bajtů na haldě na x86 počítači. Slovníky jsou skvělé, když potřebujete mapování nebo asociativní strukturu dat s konstantní masovou vyhledávání. Pokud však máte jen několik prvků, ztrácíte spoustu místa pomocí slovníku. Místo toho, například, můžete iterativně `List<KeyValuePair\<K,V>>`podívat přes , stejně rychle. Pokud používáte slovník pouze k načtení dat a potom číst z něj (velmi běžný vzor), pomocí seřazené pole s N(log(N)) vyhledávání může být téměř stejně rychle, v závislosti na počtu prvků, které používáte.
  
 **Třídy vs. struktury**  
  
 Třídy a struktury svým způsobem poskytují klasický kompromis prostor/čas pro ladění aplikací. Třídy vynakládat 12 bajtů režie na x86 počítač i v případě, že nemají žádná pole, ale jsou levné předat, protože trvá pouze ukazatel odkazovat na instanci třídy. Struktury nevznikají žádné přidělení haldy, pokud nejsou v rámečku, ale při předání velkých struktur jako argumenty funkce nebo vrácené hodnoty, trvá čas procesoru atomicky zkopírovat všechny datové členy struktur. Dávejte pozor na opakované volání vlastností, které vracejí struktury, a ukládat hodnotu vlastnosti do mezipaměti v místní proměnné, aby se zabránilo nadměrnému kopírování dat.
  
 **Caches**  
  
 Běžným trikem s výkonem je ukládání výsledků do mezipaměti. Mezipaměť bez omezení velikosti nebo zásady vyřazení však může být nevracení paměti. Při zpracování velkého množství dat, pokud podržíte velké množství paměti v mezipaměti, můžete způsobit uvolňování paměti přepsat výhody vyhledávání v mezipaměti.
  
 V tomto článku jsme diskutovali o tom, jak byste měli být vědomi příznaků kritického místa výkonu, které mohou ovlivnit odezvu vaší aplikace, zejména pro velké systémy nebo systémy, které zpracovávají velké množství dat. Mezi běžné viníky patří boxování, manipulace s řetězci, LINQ a lambda, ukládání do mezipaměti v asynchronních metodách, ukládání do mezipaměti bez omezení velikosti nebo zásady vyřazení, nevhodné používání slovníků a předávání struktur. Mějte na paměti čtyři fakta pro ladění aplikací:  
  
- Neoptimalizujte předčasně – buďte produktivní a vylaďte aplikaci, když naprvní místo najdete problémy.
  
- Profily nelžou - hádáte, pokud neměříte.
  
- Dobré nástroje, aby celý rozdíl - download PerfView a vyzkoušet.
  
- Je to všechno o přidělení – to je místo, kde tým platformy kompilátoru strávil většinu svého času zlepšováním výkonu nových kompilátorů.
  
## <a name="see-also"></a>Viz také

- [Video z prezentace tohoto tématu](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [Začátečníci Průvodce profilování výkonu](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Výkon](index.md)
- [Tipy pro zvýšení výkonu rozhraní .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))
- [Kanál 9 PerfView výukové programy](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [Sada SDK platformy kompilátoru ROZHRANÍ .NET](../../csharp/roslyn-sdk/index.md)
- [dotnet/roslyn repo na GitHubu](https://github.com/dotnet/roslyn)
