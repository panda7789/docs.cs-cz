---
title: Psaní velkých a pohotově reagujících aplikací .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f98d85e5fd01a631352f5db7bba6ed309449d68
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613515"
---
# <a name="writing-large-responsive-net-framework-apps"></a>Psaní velkých a pohotově reagujících aplikací .NET Framework
Tento článek poskytuje tipy pro zvýšení výkonu velkých aplikací rozhraní .NET Framework nebo aplikace, které zpracovávají velké množství dat, jako jsou soubory nebo databáze. Tyto tipy pocházejí z přepsání kompilátory C# i Visual Basic ve spravovaném kódu a tento článek obsahuje několik skutečné příklady z kompilátoru jazyka C#. 
  
 Rozhraní .NET Framework je vysoce produktivní pro vytváření aplikací. Jazyky výkonný a bezpečný a bohaté kolekci knihoven je vytváření aplikací s vysokou plodný. S skvělé kancelářské dodává odpovědnost. By měl používat všechny funkce rozhraní .NET Framework, ale buďte připraveni vyladit výkon vašeho kódu v případě potřeby. 
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Proč nový kompilátor výkonu platí pro vaši aplikaci  
 Tým .NET Compiler Platform ("Roslyn") rewrote jazyka C# a kompilátory jazyka Visual Basic v spravovaného kódu k poskytnutí nových rozhraní API pro modelování a analýza kódu, nástroje pro sestavování a umožňuje provoz mnohem širší, s ohledem na kód v sadě Visual Studio. Přepisování kompilátory a sestavování sady Visual Studio prostředí na nových kompilátory zjistí informace o užitečné výkonu, které se vztahují na všechny velké aplikace rozhraní .NET Framework nebo jakékoli aplikaci, která zpracovává velké množství dat. Nemusíte vědět o kompilátory využijte postřehů a příklady z kompilátoru jazyka C#. 
  
 Visual Studio používá kompilátor rozhraní API k vytvoření všechny funkce technologie IntelliSense, které máte rádi uživatele, například podtržení vlnovkou zabarvení identifikátory a klíčová slova, seznamy dokončení syntaxe, pro chyby, parametr tipy, potíží s kódem a akce kódu. Visual Studio poskytuje tuto nápovědu, zatímco jsou vývojáři psát a měnit jejich kód a sady Visual Studio musí stále reagovat, zatímco kompilátor průběžně modely kód, který vývojářům upravit. 
  
 Když koncoví uživatelé pracovat s vaší aplikací, očekávané bude reagovat. Nikdy by se zablokovat zadáním nebo zpracování příkazu. Nápovědu by měl automaticky otevře, rychle nebo vzdát-li i nadále uživatele při psaní. Vaše aplikace by měl předcházet zablokování vlákna uživatelského rozhraní s dlouhou výpočty, které aplikace může. 
  
 Další informace o kompilátory Roslyn najdete v tématu [sada SDK platformy kompilátoru .NET](../../csharp/roslyn-sdk/index.md).
  
## <a name="just-the-facts"></a>Pouze fakty  
 Vezměte v úvahu následující skutečnosti při ladění výkonu a vytváření přizpůsobivých aplikací rozhraní .NET Framework. 
  
### <a name="fact-1-dont-prematurely-optimize"></a>Fakt 1: Neoptimalizovat předčasně ukončen.  
 Psaní kódu, který je složitější, než se musí se jednat o vznikají náklady na údržbu, ladění a leštění náklady. Zkušení programátoři mít intuitivní pochopit, jak vyřešit problémy psaní kódu a psaní kódu efektivnější. Ale jsou někdy předčasně optimalizovat svůj kód. Například používají tabulku hash při jednoduchém poli by stačit, nebo použijte složité ukládání do mezipaměti, který může nastat únik paměti namísto jednoduše recomputing hodnoty. I v případě, že jste programátor prostředí, by měl test výkonu a analýzu kódu při vyhledání potíží. 
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Fakt 2: Pokud nejsou měření, že uhodnutí  
 Nemusíte být profily a měření. Profily ukazují, jestli CPU je plně načten nebo určuje, zda jste blokováno při vstupně-výstupních operací disku. Profily můžete zjistit, jaký typ a kolik paměti máte přidělení a zda procesoru tráví spoustu času v [uvolňování](../../../docs/standard/garbage-collection/index.md) (GC). 
  
 By měl nastavit prostředí nebo scénáře výkonnostních cílů pro zákazníků ve vaší aplikaci a psaní testů k měření výkonu. Prozkoumat selhání testů s použitím vědecké metody: použití profilů na vás, co může být problém, vyslovují hypotézy o jejich a testovat vaše hypotézu s experiment nebo změny kódu. Vytvořte standardní hodnoty měření výkonu v čase s pravidelné testování tak může izolovat změny, které způsobují regrese výkonu. Výkon pracovních blíží přísné způsobem, budete vyhnete plýtvání časem se aktualizace kódu, které nepotřebujete. 
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Fakt 3: Vhodné nástroje vytvářejí všechny rozdíl  
 Vhodné nástroje umožňují rychle přejít k největší problémy s výkonem (procesor, paměť nebo disk) a pomohou vyhledat kód, který způsobí, že tyto kritické body. Microsoft se dodává s celou řadou nástrojů výkonu, jako [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [nástroj pro analýzu Windows Phone](https://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), a [PerfView](https://www.microsoft.com/download/details.aspx?id=28567). 
  
 PerfView je zadarmo. je neuvěřitelně výkonné nástroj, který pomůže zaměřit se na podrobné problémy, jako je / v disku, GC – události a paměti. Můžete zaznamenat související s výkonem [události trasování pro Windows](../../../docs/framework/wcf/samples/etw-tracing.md) událostí (ETW) a zobrazení snadno na aplikaci, proces, na zásobníku a na informace o vlákně. PerfView ukazuje, kolik a jaký druh paměti přidělí vaši aplikaci a které funkce nebo volání zásobníků přispívat množství služeb pro přidělení paměti. Podrobnosti najdete v tématu bohaté témata nápovědy, ukázky a videa, které jsou součástí nástroje (například [PerfView kurzy](https://channel9.msdn.com/Series/PerfView-Tutorial) na webu Channel 9). 
  
### <a name="fact-4-its-all-about-allocations"></a>Fakt 4: Všechno se točí kolem přidělení  
 Si možná myslíte, že vytváření rychlou odezvou aplikace rozhraní .NET Framework se točí kolem algoritmy, například pomocí rychlé řazení namísto bublinu řazení, ale to není případ. Největší faktorem při vytváření responzivní aplikace je přidělování paměti, zejména v případě, že vaše aplikace je moc velká, nebo zpracovává velké objemy dat. 
  
 Téměř všechny pracovní vytvářet interaktivní IDE prostředí kompilátor nové rozhraní API podílejí vyhnout rozdělení a správu strategií ukládání do mezipaměti. Trasování PerfView zobrazení výkonu nové kompilátory C# a Visual Basic je málokdy závislá na procesoru. Kompilátory mohou být vstupně-výstupní operace při čtení stovky, tisíce nebo miliony řádků kódu, vázaná čtení metadat, nebo výstupu generovaného kódu. Uživatelské rozhraní se zpozdí vlákna jsou téměř všechny kvůli uvolňování paměti. Uvolňování paměti rozhraní .NET Framework je vysoce optimalizovaných pro výkon a udělá velkou část práce současně, zatímco spustí kód aplikace. Však můžete aktivovat jednu alokovanou nákladné [gen2](../../../docs/standard/garbage-collection/fundamentals.md) kolekce zastavení všech vláken. 
  
## <a name="common-allocations-and-examples"></a>Běžné přidělení a příklady  
 Příklady výrazů v této části jsou skryté přidělení, které se zobrazí malá. Pokud velké aplikace provede výrazy dostatek vícekrát, ale mohou způsobí, že stovek megabajtů, dokonce i gigabajtů přidělení. Například minutu trvající testy, které simulované vývojáře psaní v editoru gigabajtů paměti přidělené a vedla tým výkonu a zaměřte se na psaní scénáře. 
  
### <a name="boxing"></a>Zabalení  
 [Zabalení](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) nastane, pokud hodnota typy, které obvykle za provozu v zásobníku nebo v datové struktury jsou zabaleny v objektu. To znamená přidělit objekt pro uložení dat a pak se vraťte ukazatel na objekt. Rozhraní .NET Framework někdy pole hodnot, protože signatura metody nebo typu umístění úložiště. Zabalení typu hodnoty během přidělování paměti způsobí, že objekt. Mnoho operací zabalení může přispět, megabajtech nebo gigabajtech přidělení do vaší aplikace, což znamená, že vaše aplikace způsobí, že další GC. Rozhraní .NET Framework a kompilátory jazyka vyhnout zabalení, pokud je to možné, ale někdy to se stane, když očekáváte nejméně. 
  
 Zabalení v PerfView zobrazíte otevřít trasování a podívejte se na zásobníky alokační haldy GC v rámci vaší aplikace, název procesu (Nezapomeňte, že PerfView sestavy o všech procesů). Pokud se zobrazí typy jako <xref:System.Int32?displayProperty=nameWithType> a <xref:System.Char?displayProperty=nameWithType> v rámci přidělených jsou zabalení typů hodnot. Výběrem jedné z těchto typů zobrazí zásobníky a funkce, ve kterých jsou zabaleny. 
  
 **Příklad 1: řetězcových metod a hodnotu argumentů**  
  
 Tento ukázkový kód ukazuje potenciálně zbytečné a rostly zabalení:  
  
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
  
 Tento kód poskytuje funkce protokolování, takže aplikace mohou volat `Log` funkce často, možná miliony časy. Problém je, že volání `string.Format` překládá <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> přetížení. 
  
 Toto přetížení vyžaduje rozhraní .NET Framework do pole `int` hodnoty do objektů předejte toto volání metody. Částečné opravy je volání `id.ToString()` a `size.ToString()` a všechny řetězce (které jsou objekty) předat `string.Format` volání. Volání `ToString()` přidělit řetězce, ale, že přidělování bude přesto došlo v `string.Format`. 
  
 Můžete zvážit, který tuto základní volání `string.Format` je právě zřetězení řetězců, takže místo toho můžete například napsat tento kód:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Však tento řádek kódu zavádí zabalení přidělení, protože zkompiluje pro <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>. Rozhraní .NET Framework musí pole znakový literál k vyvolání `Concat`  
  
 **Oprava Příklad 1**  
  
 Dokončení opravy je jednoduché. Stačí nahradíte literálu s řetězcovým literálem, znak, který protože řetězce jsou již objekty s sebou nese náklady bez zabalení:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Příklad 2: zabalení výčtu**  
  
 V tomto příkladu je odpovědná za obrovské množství přidělení v nové kompilátory C# a Visual Basic z důvodu často používají výčtové typy, zejména ve slovníku operace vyhledávání. 
  
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
  
 Tento problém je velmi malý. PerfView zasílat zprávy jako <xref:System.Enum.GetHashCode> zabalení, protože metoda polích podkladové reprezentace typu výčtu důvodů implementace. Úzce podíváte v PerfView, může se zobrazit dvě zabalení přidělení pro každé volání <xref:System.Enum.GetHashCode>. Kompilátor vloží jednu a rozhraní .NET Framework vloží druhé. 
  
 **Oprava například 2**  
  
 Můžete snadno vyhnout obou přidělení přetypování na podkladové reprezentace před voláním <xref:System.Enum.GetHashCode>:  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Další běžné příčiny zabalení na typy výčtu je <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> metody. Argument předaný do <xref:System.Enum.HasFlag%28System.Enum%29> musí být pevně určený. Ve většině případů, nahraďte volání <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> bitový testu je jednodušší a bez přidělení. 
  
 První fakt výkonu mějte na paměti (to znamená, neoptimalizovat předčasně ukončen) a nespouštět přepisování váš kód tímto způsobem. Mějte na náklady na tyto zabalení, ale změna kódu až po profilování vaší aplikace a vyhledání aktivní body. 
  
### <a name="strings"></a>Řetězce  
 Manipulace s řetězci jsou některé z největších culprits pro přidělení a často zobrazí v PerfView v pěti hlavních přidělení. Programy pomocí řetězce pro serializaci JSON a REST API. Řetězce můžete použít jako programový konstanty pro spolupráci s systémy, pokud nelze použít typy výčtu. Pokud vaše profilování ukazuje řetězce vysoce ovlivňuje výkon, vyhledejte volání <xref:System.String> metody jako <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, a tak dále. Pomocí <xref:System.Text.StringBuilder> náklady na vytvoření jednoho řetězce z mnoha pomáhá kusů, ale i přidělování, aby <xref:System.Text.StringBuilder> objekt může být kritickým bodem, který je potřeba spravovat. 
  
 **Příklad 3: operace s řetězci**  
  
 Kompilátor jazyka C# má tento kód, který zapíše text formátovaný komentář dokumentace XML:  
  
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
  
 Uvidíte, že tento kód provádí spoustu zacházení s řetězci. Tento kód použije metody knihovny rozdělit řádky do samostatných řetězců, oříznout prázdný znak, chcete-li zkontrolovat, zda je argument `text` je komentáře dokumentace XML a k extrahování podřetězců z řádků. 
  
 Na prvním řádku uvnitř `WriteFormattedDocComment`, `text.Split` volání pokaždé, když je volána přidělí nové pole třech prvcích jako argument. Generovat kód pro přidělení pokaždé, když toto pole má kompilátor. Důvodem je, že kompilátor nebude vědět, pokud <xref:System.String.Split%2A> ukládá pole někde ve kterém může upravit pole jiným kódem, který bude mít vliv na pozdější volání `WriteFormattedDocComment`. Volání <xref:System.String.Split%2A> také přiděluje řetězec pro každý řádek v `text` a přiděluje další paměť k provedení této operace. 
  
 `WriteFormattedDocComment` má tři volání <xref:System.String.TrimStart%2A> metody. Jsou dva ve vnitřní smyčky, které duplikují práce a přidělení. Aby věcech ještě hůř, volání <xref:System.String.TrimStart%2A> metoda bez argumentů přiděluje prázdné pole (pro `params` parametr) kromě výsledek řetězce. 
  
 Součástí je volání <xref:System.String.Substring%2A> metodu, která obvykle přiděluje nový řetězec. 
  
 **Oprava například 3**  
  
 Na rozdíl od předchozích příkladech nelze opravit malými úpravami tyto přidělení. Potřebujete chcete zastav, podívejte se na problém a postupovat jinak. Například, uvidíte, že argument `WriteFormattedDocComment()` je řetězec, který obsahuje všechny informace, které potřebuje metodě, takže kód by mohl provést další indexování namísto přidělení mnoho částečné řetězce. 
  
 Tým výkonu kompilátoru řešeny tyto přidělení kódem takto:  
  
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
  
 První verze `WriteFormattedDocComment()` přidělené pole, více dílčích podřetězců a zkrácená podřetězec spolu s prázdnou `params` pole. Také kontroluje pro "/ / / / /". Upravený kód používá pouze indexování a přiděluje žádnou akci. Vyhledá první znak, který není prázdným znakem a poté ověří znak po znaku zobrazíte, pokud řetězec začíná symbolem "/ / / / /". Nový kód používá `IndexOfFirstNonWhiteSpaceChar` místo <xref:System.String.TrimStart%2A> vrátit první index (za zadaný počáteční index), kde dochází k znaku prázdný znak. Oprava není úplný, ale můžete zjistit, jak použít podobné opravy pro kompletní řešení. Při použití tohoto přístupu napříč kódem můžete odebrat všechna přidělení v `WriteFormattedDocComment()`. 
  
 **Příklad 4: StringBuilder**  
  
 Tento příklad používá <xref:System.Text.StringBuilder> objektu. Následující funkce generuje úplný název typu pro obecné typy:  
  
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
  
 Zaměřuje se na řádek, který vytvoří nový <xref:System.Text.StringBuilder> instance. Kód způsobí, že přidělení pro `sb.ToString()` a interní přidělení v rámci <xref:System.Text.StringBuilder> implementaci, ale nemůžete ovládat těchto přidělení, pokud má řetězec výsledek. 
  
 **Oprava například 4**  
  
 Chcete-li vyřešit `StringBuilder` objekt přidělování, objekt do mezipaměti. I ukládání jediné instance, která může získat zahozeny může výrazně zvýšit výkon. Toto je novou implementaci funkce vynechání veškerý kód s výjimkou nové první a poslední řádky:  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Jsou klíčové části nové `AcquireBuilder()` a `GetStringAndReleaseBuilder()` funkce:  
  
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
  
 Protože kompilátory nové použít dělení na vlákna, tyto implementace použít pole vlákna (<xref:System.ThreadStaticAttribute> atribut) do mezipaměti <xref:System.Text.StringBuilder>, a pravděpodobně můžete vynecháte `ThreadStatic` deklarace. Vlákno statické pole má jedinečnou hodnotu pro každý podproces, který se spustí tento kód. 
  
 `AcquireBuilder()` Vrátí v mezipaměti <xref:System.Text.StringBuilder> instance, pokud existuje, po zrušení a pole nebo mezipaměti nastavíte na hodnotu null. V opačném případě `AcquireBuilder()` vytvoří novou instanci a vrací, opuštění sady polí nebo mezipaměti na hodnotu null. 
  
 Až budete mít s <xref:System.Text.StringBuilder> , volání `GetStringAndReleaseBuilder()` získat výsledek řetězce, uložte <xref:System.Text.StringBuilder> instanci v poli nebo mezipaměti a potom vrátí výsledky. Je možné znovu zadat Tento kód a vytvořit několik <xref:System.Text.StringBuilder> objekty (i když tomu zřídka dojde). Kód uloží jenom poslední vydání <xref:System.Text.StringBuilder> instance pro pozdější použití. Tento jednoduchý strategií ukládání do mezipaměti výrazně snížit přidělení v kompilátorech, které nový. Součásti rozhraní .NET Framework a MSBuild ("MSBuild") podobný postup použít ke zlepšení výkonu. 
  
 Tento jednoduchý strategií ukládání do mezipaměti dodržuje návrh dobrý mezipaměti vzhledem k tomu, že má limit velikosti. Existuje ale více kódu nyní než v původním, což znamená další náklady na údržbu. Můžete přijmout strategií ukládání do mezipaměti pouze v případě, že jste nalezen problém s výkonem a PerfView ukázala, že <xref:System.Text.StringBuilder> přidělení je významným přispěvatelem. 
  
### <a name="linq-and-lambdas"></a>LINQ a výrazy lambda  
Language-Integrated Query (LINQ), ve spojení s lambda výrazy, je příkladem funkcí produktivitu. Ale jeho použití může mít významný dopad na výkon v čase a je možné, že budete muset revize kódu.
  
 **Příklad 5: Výrazy lambda, seznam\<T >, IEnumerable a\<T >**  
  
 Tento příklad používá [LINQ a funkční stylu kódu](https://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) najít symbol v modelu kompilátoru dle názvu řetězce:  
  
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
  
 Nový kompilátor a prostředí IDE založená na něm volání `FindMatchingSymbol()` velmi často a že jsou několik skrytých přidělení v této funkce jediný řádek kódu. Prozkoumat tyto přidělení, nejprve jediný řádek kódu funkce rozdělení na dva řádky:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 V prvním řádku [výraz lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [zavře přes](https://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) lokální proměnná `name`. To znamená, že kromě objekt pro přidělování [delegovat](~/docs/csharp/language-reference/keywords/delegate.md) , který `predicate` obsahuje kód přiděluje statická třída pro uložení prostředí, který zachycuje hodnoty `name`. Kompilátor generuje kód podobný tomuto:  
  
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
  
 Dva `new` přidělení (jeden pro třídu prostředí) a jeden pro delegáta jsou nyní explicitní. 
  
 Nyní se podívejte na volání `FirstOrDefault`. Tato metoda rozšíření na <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typ s sebou nese náklady přidělení příliš. Protože `FirstOrDefault` přebírá <xref:System.Collections.Generic.IEnumerable%601> objektu jako svůj první argument, můžete rozbalit volání následující kód (zjednodušené trochu pro diskuse):  
  
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
  
 `symbols` Proměnná má typ <xref:System.Collections.Generic.List%601>. <xref:System.Collections.Generic.List%601> Implementuje typ kolekce <xref:System.Collections.Generic.IEnumerable%601> a cleverly definuje enumerátor (<xref:System.Collections.Generic.IEnumerator%601> rozhraní), který <xref:System.Collections.Generic.List%601> implementuje s `struct`. Používání struktury namísto třídy znamená, že je obvykle velmi riskantní libovolná přidělení haldy, které pak může ovlivnit výkon kolekce uvolnění paměti. Enumerátory se obvykle používají pro jazyk `foreach` smyčku, která používá strukturu enumerátor je vrácená v zásobníku volání. Zvyšování ukazatel zásobníku volání, aby uvolnil prostor pro objekt nemá vliv na způsob přidělení haldy provádí uvolňování paměti. 
  
 V případě rozbalených `FirstOrDefault` volání, kód je nutné volat `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>. Přiřazení `symbols` k `enumerable` proměnné typu `IEnumerable<Symbol>` nedochází ke ztrátě informací, které je objekt, který vede <xref:System.Collections.Generic.List%601>. To znamená, že když kód načte čítač s `enumerable.GetEnumerator()`, musíme pole vrácené struktury a přiřaďte k rozhraní .NET Framework `enumerator` proměnné. 
  
 **Oprava například 5**  
  
 Je nutné přepsat `FindMatchingSymbol` následujícím způsobem nahraďte šest řádků kódu, které jsou stále stručné, snadno čitelný a pochopit a snadnou údržbou jeho jediný řádek kódu:  
  
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
  
 Tento kód nepoužívá rozšiřující metody, lambda výrazy nebo enumerátory LINQ, a to s sebou nese náklady bez přidělení. Nejsou žádné přidělení, protože kompilátor může vidět, že `symbols` je kolekce <xref:System.Collections.Generic.List%601> a může svázat výsledné enumerátor (struktury) na místní proměnnou s správný typ, aby se zabránilo zabalení. Původní verze této funkce bylo skvělé příklad a výrazové Možnosti C# a produktivity rozhraní .NET Framework. Tato verze nové a efektivnější zachová tyto kvality bez přidání jakékoli složitý kód pro údržbu. 
  
### <a name="async-method-caching"></a>Asynchronní metoda ukládání do mezipaměti  

Následující příklad znázorňuje běžný problém při pokusu o použití výsledky uložené v mezipaměti v [asynchronní](../../csharp/programming-guide/concepts/async/index.md) metody.
  
 **Příklad 6: ukládání do mezipaměti v asynchronních metodách**  
  
 Funkce Visual Studio IDE založená na nové kompilátory C# a Visual Basic často načíst syntaxe stromy a kompilátory použít operátory async přitom zajistit rychlou odezvou sady Visual Studio. Zde je první verze kódu, který můžete například napsat získat strom syntaxe:  
  
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
  
 Uvidíte, že volání `GetSyntaxTreeAsync()` vytvoří instanci `Parser`, analyzuje kód a potom vrátí <xref:System.Threading.Tasks.Task> objektu, `Task<SyntaxTree>`. Přidělení části nákladné `Parser` instance a analýzu kódu. Funkce vrátí <xref:System.Threading.Tasks.Task> tak, aby volající může await analýzy práce a uvolnit vlákno uživatelského rozhraní bude reagovat na vstup uživatele. 
  
 Několik funkcí sady Visual Studio může pokusit získat stejné stromu syntaxe, tak můžete například napsat následující kód pro ukládání do mezipaměti výsledek analýzy jak šetřit čas i přidělení. Tento kód však způsobuje přidělení:  
  
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
  
 Uvidíte, že má nový kód s ukládáním do mezipaměti `SyntaxTree` pole s názvem `cachedResult`. Když toto pole má hodnotu null, `GetSyntaxTreeAsync()` provádí a uloží výsledek v mezipaměti. `GetSyntaxTreeAsync()` Vrátí `SyntaxTree` objektu. Problém je, že až budete mít `async` – funkce typu `Task<SyntaxTree>`, a vrátí hodnotu typu `SyntaxTree`, kompilátor generuje kód pro přidělení úlohu pro uchování výsledku (s použitím `Task<SyntaxTree>.FromResult()`). Úkolu označena jako dokončená a výsledek je ihned k dispozici. V kódu pro nové kompilátory <xref:System.Threading.Tasks.Task> objekty, které již byly dokončeny tak často, který oprava těchto přidělení lepší odezvy výrazně došlo k chybě. 
  
 **Oprava například 6**  
  
 Chcete-li odebrat dokončenou <xref:System.Threading.Tasks.Task> přidělení, můžete ukládat do mezipaměti objekt úlohy s výsledkem dokončené:  
  
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
  
 Tento kód změní typ `cachedResult` k `Task<SyntaxTree>` a využívá `async` pomocná funkce, která obsahuje původní kód `GetSyntaxTreeAsync()`. `GetSyntaxTreeAsync()` nyní používá [null operátor sloučení](../../csharp/language-reference/operators/null-coalescing-operator.md) vrátit `cachedResult` Pokud není null. Pokud `cachedResult` má hodnotu null, pak `GetSyntaxTreeAsync()` volání `GetSyntaxTreeUncachedAsync()` a ukládá do mezipaměti výsledek. Všimněte si, že `GetSyntaxTreeAsync()` nebude očekávat volání `GetSyntaxTreeUncachedAsync()` jako kód obvykle. Bez použití operátoru await znamená, že `GetSyntaxTreeUncachedAsync()` vrátí jeho <xref:System.Threading.Tasks.Task> objektu, `GetSyntaxTreeAsync()` okamžitě vrátí <xref:System.Threading.Tasks.Task>. Nyní je výsledky uložené v mezipaměti <xref:System.Threading.Tasks.Task>, aby vás nečekala žádná přidělení vrátit výsledky uložené v mezipaměti. 
  
### <a name="additional-considerations"></a>Další informace  
 Tady je několik dalších bodů o potenciálních problémů v aplikacích pro velké nebo aplikace, které zpracovávají velké množství dat. 
  
 **slovníky**  
  
 Slovníky se ubiquitously používají v mnoha aplikacích a i když jsou slovníky příliš pohodlné a ze své podstaty efektivní. Však často slouží nesprávně. V sadě Visual Studio a nové kompilátory analýza ukazuje mnoho slovníků obsahovala jeden element nebo byla prázdná. Prázdná <xref:System.Collections.Generic.Dictionary%602> deset pole a zabírá aspoň 48 bajtů v haldě na x x86 počítače. Slovníky se skvěle hodí, když potřebujete mapování nebo asociativní datová struktura s vyhledávaní v konstantním čase. Ale pokud máte pouze několik elementů, můžete odpadu velké množství místa pomocí slovníku. Místo toho, například je iterativní vyhledat `List<KeyValuePair\<K,V>>`, stejně tak rychle. Pokud používáte jenom pro zatížení s daty a pak si můžete přečíst z něj (velmi běžný vzor) slovník, pomocí vyhledávání N(log(N)) seřazené pole může být skoro tak rychle, v závislosti na počtu prvků, které používáte. 
  
 **Třídy a struktury**  
  
 V režimu třídy a struktury poskytují kompromis classic místa a času pro ladění vaší aplikace. Třídy se vám účtovat 12 bajtů režijní náklady na x x86 počítače i v případě, že nemají žádná pole, ale jsou cenově předávat, protože pouze bere ukazatel pro odkazování na instanci třídy. Pokud nejsou zabaleny, ale když předat velké struktury jako argumenty funkce nebo návratové hodnoty, může zabrat určitý čas procesoru atomicky zkopírovat všechny datové členy struktury se vám účtovat struktury bez přidělení haldy. Dávejte pozor na opakovaná volání vlastnosti, které vrátí struktury a hodnotu vlastnosti v místní proměnné, aby se zabránilo nadměrnému kopírování dat do mezipaměti. 
  
 **Mezipaměti**  
  
 Běžné zdvih výkonu se výsledky do mezipaměti. Bez zásady cap nebo vyřazení velikost mezipaměti však může být nevracení paměti. Při zpracování velkých objemů dat, pokud můžete blokovat velké množství paměti v mezipaměti, může způsobit uvolňování paměti pro přepsání výhody v mezipaměti vyhledávání. 
  
 V tomto článku jsme zmínili, jak byste měli vědět příznaky problémové místo výkonu, které může mít vliv na rychlost reakce vaší aplikace, zejména u velkých systémy nebo systémy, které zpracovávají velké množství dat. Běžné culprits zahrnují zabalení, manipulace s řetězci, LINQ a lambda, ukládání do mezipaměti v asynchronních metodách, ukládání do mezipaměti bez zásad omezení nebo vyřazení velikost, nesprávné použití slovníky a předávání kolem struktury. Mějte na paměti čtyři faktů pro ladění vaší aplikace:  
  
-   Nemáte předčasně optimalizovat – produktivitu a ladit vaši aplikaci při odhalit problémy. 
  
-   Profily nejsou leží – při odhadování, pokud nejsou měření. 
  
-   Vhodné nástroje všechny záleží na tom – stáhnout PerfView a vyzkoušejte si to. 
  
-   To všechno je o přidělení – to znamená ve kterém tým platformy kompilátoru trvání většinu svého času zlepšení výkonu nové kompilátory. 
  
## <a name="see-also"></a>Viz také:

- [Video prezentace v tomto tématu](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)  
- [Průvodce začátečníka profilací výkonu](/visualstudio/profiling/beginners-guide-to-performance-profiling)  
- [Výkon](../../../docs/framework/performance/index.md)  
- [Tipy ke zvýšení výkonu rozhraní .NET](https://msdn.microsoft.com/library/ms973839.aspx)  
- [Nástroj pro analýzu výkonu Windows Phone](https://msdn.microsoft.com/magazine/hh781024.aspx)  
- [Vyhledat problémová místa aplikace pomocí sady Visual Studio Profiler](https://msdn.microsoft.com/magazine/cc337887.aspx)  
- [Na webu Channel 9 kurzů PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial)  
- [.NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md)
- [DotNet/roslyn úložišti na Githubu](https://github.com/dotnet/roslyn)
