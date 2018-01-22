---
title: "Psaní velkých a pohotově reagujících aplikací .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
manager: wpickett
ms.workload: wiwagn
ms.openlocfilehash: a33e065d9daa886c27cde31c8f16f9b9eaa45938
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="writing-large-responsive-net-framework-apps"></a>Psaní velkých a pohotově reagujících aplikací .NET Framework
Tento článek obsahuje tipy pro zvýšení výkonu velkých aplikací rozhraní .NET Framework, nebo aplikace, které zpracovávají velké množství dat, jako jsou soubory nebo databáze. Tyto tipy pocházet z přepisování C# a Visual Basic kompilátory ve spravovaném kódu a tento článek obsahuje několik příkladů skutečné z kompilátoru C#.  
  
 Rozhraní .NET Framework je vysoce výkonné pro vytváření aplikací.  Výkonný a bezpečné jazyky a bohaté kolekce knihovny zkontrolujte aplikace vytváření vysoce plodnou.  S skvělé produktivitu dodává zodpovědnost.  Musí používat všechny funkce rozhraní .NET Framework, ale mějte připravené informace o optimalizaci výkonu vašeho kódu v případě potřeby.  
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Proč nové výkonu kompilátoru platí pro vaši aplikaci  
 Týmem kompilátoru platformu .NET ("Roslyn") rewrote jazyka C# a kompilátory jazyka Visual Basic ve spravovaném kódu nabízí nová rozhraní API pro modelování a analýza kódu, nástroje pro vytváření a povolení prostředí mnohem širší, podporou kódu v sadě Visual Studio.  Přepisování kompilátory a sestavování sady Visual Studio narazí na nové kompilátory odhalilo užitečné performance Insight, které platí pro všechny velké rozhraní .NET Framework aplikace nebo jakékoli aplikaci, která zpracovává velké množství dat.  Nemusíte vědět o kompilátory využívat výhod přehledy a příklady z kompilátoru C#.  
  
 Visual Studio použije k vytvoření všech funkcí technologie IntelliSense, které uživatelé rádi, například podtržení vlnovkou zabarvení identifikátory a klíčová slova, seznamy dokončení syntaxe, chyb, parametr tipy, problémy kódu a kódu akce kompilátoru rozhraní API.  Visual Studio poskytuje této nápovědy, zatímco vývojáři jsou zadáním a změna jejich kódu a sady Visual Studio musí zůstat přizpůsobivý při kompilátor průběžně modelů kód, který vývojářům upravit.  
  
 Pokud vaši koncoví uživatelé komunikovat s vaší aplikací, jejich očekávat ho jako odpovídající.  Zadáním nebo zpracování příkazu by nikdy zablokovat.  Nápověda by měla překryvné rychle nebo uvolňovat, pokud uživatel pokračuje zadáním.  Aplikace by měla zabránění blokování vlákna uživatelského rozhraní s dlouhou výpočtů, které aplikace zaregistrované, pomalá.  
  
 Další informace o Roslyn kompilátory najdete [dotnet/roslyn](https://github.com/dotnet/roslyn) úložišti na Githubu.
 <!-- TODO: replace with link to Roslyn conceptual docs once that's published -->
  
## <a name="just-the-facts"></a>Právě tato fakta  
 Vezměte v úvahu následující skutečnosti při ladění výkonu a vytváření přizpůsobivý aplikací rozhraní .NET Framework.  
  
### <a name="fact-1-dont-prematurely-optimize"></a>Fakt 1: Není předčasně optimalizovat.  
 Psaní kódu, který je složitější, než je nutné způsobuje údržby, ladění a leštění náklady.  Zkušení programátoři mít intuitivní pochopit postup řešení problémů kódování a napsat kód, efektivnější.  Nicméně se někdy předčasně optimalizovat svůj kód.  Například zatřiďovací tabulku používají, když jednoduchých polí by stačit, nebo použijte složitá ukládání do mezipaměti, může nastat únik paměti místo jednoduše recomputing hodnoty.  I v případě, že jste programátory prostředí, doporučujeme testování výkonu a analyzovat kód, když najít problémy.  
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Fakt 2: Pokud jste nejsou měření, můžete se uhodnutí  
 Nemáte ležet profily a měření.  Profily zobrazit, zda je úplným načtením procesoru nebo jestli se zablokuje na v/v disku.  Profily uvedeno, jaký typ a velikost paměti, že přidělování a jestli je vaše procesoru výdaje mnoho času v [uvolňování paměti](../../../docs/standard/garbage-collection/index.md) (GC).  
  
 By měl nastavit výkonnostní cíle pro klíče zákazníka prostředí nebo scénářů, ve vaší aplikaci a zápis testů k měření výkonu.  Prozkoumat selhání testů s použitím metodu exponenciální: použití profilů k vás, můžete předpokládat, co může být problém a testování vaší předpoklad s experimentu nebo kód změnit.  Vytvořte měření výkonu standardních hodnot v čase s regulární testování, můžete izolovat změny, které způsobí regresí výkonu.  Blíží výkonu pracovní přísných způsobem, budete muset plýtvání časem při s aktualizacemi kódu, které nepotřebujete.  
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Fakt 3: Dobrý nástroje usnadňují všechny rozdílu  
 Dobrý nástroje umožňují rychle rozbalit největších problémů s výkonem (procesoru, paměti nebo disk) a nápovědy, vyhledejte kód, který způsobí, že tyto kritická místa.  Microsoft, jako dodává celou řadu nástrojů výkonu [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [nástroj pro analýzu Windows Phone](http://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), a [nástroje PerfView](http://www.microsoft.com/download/details.aspx?id=28567).  
  
 Nástroje PerfView je bezplatná a amazingly výkonný nástroj, který pomáhá zaměřit se na hloubkové problémy, jako je/v diskových operací GC – události a paměti.  Můžete zaznamenat související s výkonem [trasování událostí pro Windows](../../../docs/framework/wcf/samples/etw-tracing.md) událostí (ETW) a zobrazení snadno jednu aplikaci, podle procesu, na zásobníku a na vláken informace.  Nástroje PerfView ukazuje, kolik a jaký druh paměti přidělí vaší aplikace, a které funkce nebo volání zásobníky přispívat kolik k přidělení paměti. Podrobnosti najdete v tématu bohaté témata nápovědy, ukázky a videa, které jsou součástí nástroje (například [nástroje PerfView kurzy](http://channel9.msdn.com/Series/PerfView-Tutorial) na webu Channel 9).  
  
### <a name="fact-4-its-all-about-allocations"></a>Fakt 4: Všechno se točí kolem přidělení  
 Může si myslíte, že vytváření reaguje aplikace rozhraní .NET Framework je o algoritmů, například pomocí rychlé řazení místo bublin řazení, ale které se nevztahuje na případ.  Největších faktorem sestavení fungující aplikace je přidělování paměti, zejména v případě, že vaše aplikace je moc velká nebo zpracovává velké objemy dat.  
  
 Téměř všechny pracovní k vytvoření fungující IDE vyskytne s překladačem nové rozhraní API podílejí zabraňující přidělení a správě ukládání do mezipaměti strategie.  Trasování nástroje PerfView zobrazit výkon nové kompilátory jazyka C# a Visual Basic je zřídka procesoru vázána.  Kompilátory může být vstupně-výstupních operací vázaný při čtení stovky tisíc nebo miliony řádků kódu, čtení metadat, nebo generování generovaného kódu.  Uživatelské rozhraní se zpozdí vlákno jsou téměř všechny kvůli uvolnění paměti.  Uvolňování paměti rozhraní .NET Framework je vysoce vyladěných výkonu a většinu práce nemá současně, zatímco spouští kód aplikace.  Však můžete aktivovat jeden přidělení nákladné [gen2](../../../docs/standard/garbage-collection/fundamentals.md) kolekce, zastavování všechna vlákna.  
  
## <a name="common-allocations-and-examples"></a>Běžné přidělování a příklady  
 Příklady výrazů v této části jsou skryté přidělení, které se zobrazují malé.  Pokud velké aplikace provede výrazy dostatek časy, ale mohou příčiny stovky v megabajtech, i gigabajtů přidělení.  Například jedna minuta testy, které simulované zadáním pro vývojáře v editoru přidělené gigabajty paměti a vedla týmem výkonu a zaměřit se na zadání scénáře.  
  
### <a name="boxing"></a>Zabalení  
 [Zabalení](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) nastane, když hodnota typy, obvykle za provozu v zásobníku nebo v datech jsou struktury uzavřen do objektu.  To znamená přidělit objekt pro uložení dat a poté se vraťte ukazatel na objekt.  Rozhraní .NET Framework někdy oknech hodnoty z důvodu podpis metody nebo typ umístění úložiště.  Zabalení typ hodnoty v objektu přidělení paměti příčiny.  Mnoho zabalení operací můžete přispívat, megabajtech nebo gigabajtech přidělení do vaší aplikace, což znamená, že vaše aplikace způsobí, že další GC. Rozhraní .NET Framework a kompilátory jazyka vyhnout zabalení, pokud je to možné, ale někdy dojde při očekáváte minimálně.  
  
 Zabalení v nástroje PerfView najdete otevřete trasování a podívejte se na zásobníky alokační haldě GC pod názvem procesu vaší aplikace (Nezapomeňte, že nástroje PerfView sestavy o všech procesů).  Pokud se zobrazí typy jako <xref:System.Int32?displayProperty=nameWithType> a <xref:System.Char?displayProperty=nameWithType> v rámci přidělených jsou zabalení typů hodnot.  Výběr jedním z těchto typů zobrazí zásobníky a funkce, ve kterých jsou zabalená.  
  
 **Příklad 1: řetězcových metod a hodnotu argumenty typů**  
  
 Tento ukázkový kód ukazuje potenciálně nepotřebné a nadměrnému zabalení:  
  
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
  
 Tento kód poskytuje funkce protokolování, aby aplikace může zavolat `Log` funkce často, může být miliony časy.  Problém je, že volání `string.Format` překládá se <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> přetížení.  
  
 Toto přetížení vyžaduje rozhraní .NET Framework pro pole `int` hodnoty do objektů předejte toto volání metody.  Částečné opravu je volání `id.ToString()` a `size.ToString()` a předat všechny řetězce (které jsou objekty) `string.Format` volání.  Volání metody `ToString()` přidělit řetězec, ale, že přidělení přesto dojde v `string.Format`.  
  
 Zvažte to tuto základní volat na `string.Format` je právě zřetězení řetězců, takže může místo toho napište tento kód:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Ale tohoto řádku kódu zavádí zabalení přidělení, protože se zkompiluje do <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.  Rozhraní .NET Framework musí pole znak, který má být vyvolán literálu`Concat`  
  
 **Opravte například 1**  
  
 Dokončení opravy je jednoduché.  Právě nahradí znak literálu s řetězcový literál, který způsobuje žádné zabalení, protože řetězce jsou již objekty:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Příklad 2: zabalení výčtu**  
  
 V tomto příkladu je zodpovědná za obrovské množství přidělení nového kompilátory jazyka C# a Visual Basic z důvodu často používají typů výčtu, zejména v operacích vyhledávání slovníku.  
  
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
  
 Tento problém je velmi malé.  Nástroje PerfView by ohlásit jako <xref:System.Enum.GetHashCode> zabalení, protože metoda oknech základní reprezentaci typu výčtu důvodů implementace.  Pokud se podíváte úzce v nástroje PerfView, mohou se zobrazit dvě zabalení přidělení pro každé volání <xref:System.Enum.GetHashCode>.   Kompilátor vloží jednu a rozhraní .NET Framework vloží na druhý.  
  
 **Opravte například 2**  
  
 Můžete snadno vyhnout obou přidělení přetypování k základní reprezentaci před voláním <xref:System.Enum.GetHashCode>:  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Další běžné zdroj zabalení na výčtové typy je <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> metoda.  Argument předaný <xref:System.Enum.HasFlag%28System.Enum%29> má zabaleny.  Ve většině případů nahrazení volání <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> s bitové testu je jednodušší a bez přidělení.  
  
 První fakt výkonu mějte na paměti (to znamená, že nemáte optimalizace předčasně) a nespouštět přepisování všech vašich kódech tímto způsobem.    Mějte na paměti tyto zabalení nákladů, ale měnit kód až po profilace aplikace a hledání aktivní body.  
  
### <a name="strings"></a>Řetězce  
 Manipulace s řetězci jsou některé z největších culprits pro přidělení a jejich často zobrazí v nástroje PerfView v horní pět přidělení.  Programů používá řetězce pro serializaci JSON a rozhraní REST API.  Řetězce můžete použít jako programový konstanty pro spolupráci s systémy, pokud nelze použít výčtové typy.  Pokud vaše profilace ukazuje, že řetězce jsou vysoce ovlivňují výkon, vyhledejte volání <xref:System.String> metody, jako <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>a tak dále.  Pomocí <xref:System.Text.StringBuilder> předejdete náklady na vytvoření jeden řetězec z mnoha pomáhá částí, ale i přidělování <xref:System.Text.StringBuilder> objektu se může stát úzkým místem, které potřebujete ke správě.  
  
 **Příklad 3: operace s řetězci**  
  
 Kompilátor jazyka C# měl tento kód, který zapíše text formátovaný komentáře doc XML:  
  
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
  
 Uvidíte, že tento kód provede spoustu zacházení s řetězci.  Kód používá metod knihovny rozdělit řádky do samostatné řetězce, oříznout mezera, zkontrolujte, zda argument `text` je komentáře jazyka XML dokumentace a k extrahování dílčích řetězců z řádků.  
  
 Na první řádek uvnitř `WriteFormattedDocComment`, `text.Split` volání přiděluje nový element tři pole jako argument pokaždé, když je volána.  Kompilátor má vyvolat kód přidělit pokaždé, když toto pole.  Je to způsobeno kompilátor není známo, pokud <xref:System.String.Split%2A> ukládá pole někde kde pole by se mohly změnit jiným kódem, které by ovlivnily pozdější volání `WriteFormattedDocComment`.  Volání <xref:System.String.Split%2A> také přiděluje řetězec pro každý řádek v `text` a přiděluje další paměť k provedení operace.  
  
 `WriteFormattedDocComment`má tři volání <xref:System.String.TrimStart%2A> metoda.  Dva jsou v informacích o vnitřní smyčky, které duplicitní práci a přidělení.  Chcete-li nejhorší záleží, volání <xref:System.String.TrimStart%2A> metoda bez argumentů přiděluje prázdné pole (pro `params` parametr) kromě výsledném řetězci.  
  
 Nakonec je volání <xref:System.String.Substring%2A> metodu, která obvykle přiděluje nový řetězec.  
  
 **Opravte například 3**  
  
 Na rozdíl od předchozích příkladech nemůže malé úpravy opravit tyto přidělení.  Budete muset krok zpět, podívejte se na problém a bezkódovém přístupu jinak.  Například můžete všimnout, který argument `WriteFormattedDocComment()` je řetězec, který obsahuje všechny informace, které potřebuje metodu, takže kód udělat další indexování místo přidělování mnoho částečné řetězce.  
  
 Kompilátoru výkonu team řešit všechny tyto přidělení kódem takto:  
  
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
  
 První verze součásti `WriteFormattedDocComment()` přidělené pole, několik dílčích řetězců a oříznutý substring společně s prázdnou `params` pole.  Je také zkontrolovat `"///"`.  Revidovaný kód používá jenom indexování a přiděluje nic.  Najde první znak, který není mezera a kontroly znak po znaku zobrazíte, zda text začíná `"///"`.  Nový kód používá `IndexOfFirstNonWhiteSpaceChar` místo <xref:System.String.TrimStart%2A> vrátit první index (za zadaný počáteční index), kde dojde k neprázdný znak.  Oprava není dokončena, ale uvidíte, jak se má použít podobné opravy pro kompletního řešení.  Použitím tohoto přístupu napříč kódem, můžete odebrat všechny přidělení v `WriteFormattedDocComment()`.  
  
 **Příklad 4: StringBuilder**  
  
 Tento příklad používá <xref:System.Text.StringBuilder> objektu.  Název typu úplné pro obecné typy vygeneruje následující funkce:  
  
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
  
 Zaměřuje se na řádek, který vytvoří nový <xref:System.Text.StringBuilder> instance.  Kód způsobí, že přidělení pro `sb.ToString()` a interních přidělování v rámci <xref:System.Text.StringBuilder> implementace, ale nemůže ovládat těchto přidělení, pokud chcete, aby výsledném řetězci.  
  
 **Opravte například 4**  
  
 Chcete-li odstranit `StringBuilder` objektu přidělení, mezipaměti objekt.  I ukládání jediné instance, který může získat zahozeny může výrazně zvýšit výkon.  Toto je funkce nové implementace vynechání všechny kód s výjimkou nové první a poslední řádky:  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Klíčovými částmi jsou nové `AcquireBuilder()` a `GetStringAndReleaseBuilder()` funkce:  
  
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
  
 Protože nové kompilátory použít dělení na vlákna, použijte tyto implementace vlákno statické pole (<xref:System.ThreadStaticAttribute> atribut) do mezipaměti <xref:System.Text.StringBuilder>, a pravděpodobně můžete vynecháte `ThreadStatic` deklarace.  Vlákno statické pole obsahuje jedinečnou hodnotu pro každý podproces, který se spustí tento kód.  
  
 `AcquireBuilder()`Vrátí uložená v mezipaměti <xref:System.Text.StringBuilder> instance, pokud je jedna po vymazáním a nastavení pole nebo mezipaměti na hodnotu null.  V opačném `AcquireBuilder()` vytvoří novou instanci a vrátí ji, ponechat sadu pole nebo mezipaměti na hodnotu null.  
  
 Když jste hotovi s <xref:System.Text.StringBuilder> , zavoláte `GetStringAndReleaseBuilder()` získat výsledném řetězci, uložte <xref:System.Text.StringBuilder> instance v mezipaměti na pole a pak vrátí výsledek.  Je možné pro provedení znovu zadat Tento kód a vytvořte více <xref:System.Text.StringBuilder> objekty (i když k tomu jenom občas dojde).  Nástroje kód uloží jenom poslední vydané <xref:System.Text.StringBuilder> instance pro pozdější použití.  Tento jednoduchý ukládání do mezipaměti strategie výrazně snížit přidělení v nové kompilátory.  Součásti rozhraní .NET Framework a MSBuild ("MSBuild") podobný postup použít ke zlepšení výkonu.  
  
 Tato strategie jednoduché ukládání do mezipaměti dodržuje pravidla návrh dobrý mezipaměti, protože má velikost zakončení.  V původním, což znamená další náklady na údržbu je však nyní než další kód.  Ukládání do mezipaměti strategie by měl použít, pouze v případě, že jste nalezené problémy s výkonem a nástroje PerfView ukázaly, že <xref:System.Text.StringBuilder> přidělení jsou významné Přispěvatel.  
  
### <a name="linq-and-lambdas"></a>LINQ a lambdas  
 Pomocí Language-Integrated Query (LINQ) a lambda výrazů je skvělým příklad použití výkonné funkce, které může později zjistíte, že budete muset přepište kód přestane být významný dopad na výkon.  
  
 **Příklad 5: Lambdas, seznam\<T > a rozhraní IEnumerable\<T >**  
  
 Tento příklad používá [LINQ a kódu funkční stylu](http://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) symbol vyhledejte v kompilátoru modelu zadaný řetězec názvu:  
  
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
  
 Nové kompilátoru a prostředí IDE postavené na něm volat `FindMatchingSymbol()` velmi často a že jsou několik skrytá přidělení v tato funkce jediný řádek kódu.  Pro zjištění těchto přidělení, nejprve jediný řádek kódu funkce rozdělení na dva řádky:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 V prvním řádku [výrazu lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)`s => s.Name == name`[zavře přes](http://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) místní proměnné `name`.  To znamená, že kromě přidělování objekt pro [delegovat](~/docs/csharp/language-reference/keywords/delegate.md) , `predicate` obsahuje, kód přiděluje statická třída pro uložení prostředí, které jsou zaznamenány hodnotu `name`.  Kompilátor generuje kód takto:  
  
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
  
 Nyní podívejte se na volání `FirstOrDefault`. Tato metoda rozšíření na <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typ způsobuje přidělení příliš.  Protože `FirstOrDefault` trvá <xref:System.Collections.Generic.IEnumerable%601> objekt jako svůj první argument, můžete rozšířit volání následující kód (zjednodušená trochu diskusi):  
  
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
  
 `symbols` Proměnná má typ <xref:System.Collections.Generic.List%601>.  <xref:System.Collections.Generic.List%601> – Typ kolekce implementuje <xref:System.Collections.Generic.IEnumerable%601> a cleverly definuje enumerátor (<xref:System.Collections.Generic.IEnumerator%601> rozhraní), <xref:System.Collections.Generic.List%601> implementuje s `struct`.  Pomocí strukturou místo třídu znamená obvykle vyhnout rozdělení haldy, které se pak může ovlivnit výkon kolekce paměti.  Výčty jsou obvykle používány v jazyce `foreach` smyčky, která využívá strukturu enumerátor je vrácený v zásobníku volání.  Zvyšování ukazatel zásobníku volání aby uvolnil prostor pro objekt nemá vliv na způsob přidělení haldy nemá GC.  
  
 V případě rozšířená `FirstOrDefault` volání kód potřebuje volat `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>.  Přiřazení `symbols` k `enumerable` proměnné typu `IEnumerable<Symbol>` ztratí informace, které se objekt skutečné <xref:System.Collections.Generic.List%601>.  To znamená, že když kód načte enumerátor s `enumerable.GetEnumerator()`, rozhraní .NET Framework je pole vrácené struktura přiřadit ho k `enumerator` proměnné.  
  
 **Opravte například 5**  
  
 Oprava je přepsání `FindMatchingSymbol` šest řádků kódu, které jsou stále stručné sdělení, snadno přečíst a pochopit a snadnou údržbou nahraďte jeho jediný řádek kódu následujícím způsobem:  
  
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
  
 Tento kód nepoužívá rozšiřující metody, lambdas nebo výčty LINQ a budou vám účtovány žádné přidělení.  Nejsou žádné přidělení, protože kompilátor uvidíte, že `symbols` kolekce <xref:System.Collections.Generic.List%601> a může svázat výsledný enumerátor (strukturou) místní proměnné s správný typ. předejdete zabalení.  Původní verze této funkce se skvělé příklad výrazovou sílu jazyka C# a rozhraní .NET Framework na produktivitu.  Tato verze nové a efektivnější uchovává tyto vlastnosti bez přidání jakékoli složitý kód k údržbě.  
  
### <a name="async-method-caching"></a>Asynchronní metoda ukládání do mezipaměti  
 Další příklad ukazuje častých problémů, když se pokusíte použít výsledky uložené v mezipaměti v [asynchronní](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) metoda.  
  
 **Příklad 6: ukládání do mezipaměti v asynchronní metody**  
  
 Funkce Visual Studio IDE založený na nové kompilátory jazyka C# a Visual Basic často načtení stromy syntaxe a kompilátory použít asynchronní při tak zachovat přizpůsobivý Visual Studio.  Tady je první verze součásti kód, který může zapsat získat stromu syntaxe:  
  
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
  
 Uvidíte, že volání `GetSyntaxTreeAsync()` vytvoří `Parser`, analyzuje kód a potom se vrátí <xref:System.Threading.Tasks.Task> objekt, `Task<SyntaxTree>`.  Je nákladné část přidělování `Parser` instance a analýze kódu.  Funkce vrátí hodnotu <xref:System.Threading.Tasks.Task> , aby mohli volající await analýzy práce a uvolněte vlákna uživatelského rozhraní spolupracovat s vstup uživatele.  
  
 Několik funkcí sady Visual Studio může pokusit získat stejném stromu syntaxe tak může zapsat následující kód pro ukládání do mezipaměti analýzy výsledek ušetříte čas a přidělení.  Tento kód však způsobuje přidělení:  
  
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
  
 Uvidíte, že má nový kód s ukládáním do mezipaměti `SyntaxTree` pole s názvem `cachedResult`.  Pokud toto pole má hodnotu null, `GetSyntaxTreeAsync()` provádí práce a uloží výsledek v mezipaměti.  `GetSyntaxTreeAsync()`Vrátí `SyntaxTree` objektu.  Problém je, že když máte `async` – funkce typu `Task<SyntaxTree>`, a vrátí hodnotu typu `SyntaxTree`, kompilátor vydává kód přidělit úlohu pro uložení výsledek (pomocí `Task<SyntaxTree>.FromResult()`).  Úloha je označena jako dokončená a výsledkem je ihned k dispozici.  V kódu pro nové kompilátory <xref:System.Threading.Tasks.Task> objekty, které již byly dokončeny tak často to uchycení tyto přidělení zlepšila odezvu zaznamenatelný dopad došlo k chybě.  
  
 **Opravte například 6**  
  
 Chcete-li odebrat dokončené <xref:System.Threading.Tasks.Task> přidělení, můžete mezipaměti objekt úlohy dokončené výsledkem:  
  
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
  
 Tento kód změní typ `cachedResult` k `Task<SyntaxTree>` a využívá `async` pomocné funkce, která obsahuje původní kód `GetSyntaxTreeAsync()`.  `GetSyntaxTreeAsync()`Teď používá [null slučovací operátor](~/docs/csharp/language-reference/operators/null-conditional-operator.md) vrátit `cachedResult` , pokud není null.  Pokud `cachedResult` má hodnotu null, pak `GetSyntaxTreeAsync()` volání `GetSyntaxTreeUncachedAsync()` a ukládá do mezipaměti výsledek.  Všimněte si, že `GetSyntaxTreeAsync()` není await volání `GetSyntaxTreeUncachedAsync()` jako kód běžným způsobem.  Nepoužíváte await znamená že v případě `GetSyntaxTreeUncachedAsync()` vrátí jeho <xref:System.Threading.Tasks.Task> objekt, `GetSyntaxTreeAsync()` hned vrátí <xref:System.Threading.Tasks.Task>.  Nyní v mezipaměti výsledkem je, <xref:System.Threading.Tasks.Task>, takže neexistují žádné přidělení vrátit výsledky uložené v mezipaměti.  
  
### <a name="additional-considerations"></a>Další informace  
 Zde naleznete několik více bodů o možných problémech ve velkých aplikací nebo aplikace, které zpracovávají velké množství dat.  
  
 **Slovník**  
  
 Slovník ubiquitously slouží v mnoha aplikacích a když slovník jsou velmi vhodné a ze své podstaty efektivní.  Však se často používají nesprávně.  V sadě Visual Studio a nové kompilátory analýza ukazuje řadu slovníků obsahovala jeden element nebo byly prázdné.  Prázdná <xref:System.Collections.Generic.Dictionary%602> má deset polí a zabírá 48 bajtů v haldě na x86 počítače.  Slovník jsou skvělé, pokud potřebujete datová struktura mapování nebo asociovaných s konstanta čas vyhledávání.  Ale pokud máte pouze několik elementy, je odpady velké množství místa pomocí slovníku.  Místo toho, například je může interaktivně projděte `List<KeyValuePair\<K,V>>`, stejně tak rychlé.  Pokud používáte slovník pouze pro zatížení s daty a pak čtení z něj (velmi běžný vzor), pomocí seřazené pole vyhledávání N(log(N)) může být téměř jako rychlé, v závislosti na počtu prvky, které používáte.  
  
 **Třídy a struktury**  
  
 Způsobem třídy a struktury poskytují kompromis classic místa a času k ladění aplikací.  Třídy zpoplatněná 12 bajtů režijní náklady na x86 počítač i v případě, že mají žádná pole, ale jsou nenákladné předat kolem, protože trvá ukazatel odkazovat na instanci třídy.  Struktury žádné přidělení haldy dojít, pokud nejsou v do pole, ale když předat velké struktury jako argumenty funkce nebo návratové hodnoty, dojde čas procesoru atomicky zkopírujte všechny členy datové struktury.  Sledujte opakovaná volání vlastnosti, které vrátí struktury a mezipaměti vlastnosti na hodnotu v místní proměnné, aby se zabránilo nadměrnému data kopírování.  
  
 **Mezipaměti**  
  
 Běžné efektu výkonu je výsledky do mezipaměti.  Mezipaměť bez velikost zakončení nebo vyřazení zásad však může být nevrácenou pamětí.  Při zpracování velkých objemů dat, pokud přidržením velké množství paměti v mezipaměti, může způsobit uvolňování paměti pro přepsání výhod vaše vyhledávání z mezipaměti.  
  
 V tomto článku jsme probrali, jak byste měli vědět příznaky výkonu problémové místo, které může mít vliv na rychlost reakce vaší aplikace, hlavně pro velké systémům nebo systémům, které zpracovávají velké množství dat. Běžné culprits zahrnují zabalení, manipulace s řetězci, LINQ a lambda, ukládání do mezipaměti asynchronní metody ukládání do mezipaměti bez velikost limit nebo vyřazení zásady, nevhodných použití slovník a předávání kolem struktury.  Mějte na paměti čtyři fakty k ladění aplikací:  
  
-   Nemáte předčasně optimalizovat – produktivitu a ladit aplikace při rozpoznání problémy.  
  
-   Profily nejsou ležet – jste uhodnutí, pokud nejsou měření.  
  
-   Dobrý nástroje proveďte všechny rozdíl – stažení nástroje PerfView a vyzkoušejte ji.  
  
-   O přidělení – to znamená kde týmem platformy kompilátoru stráví většinu doba pro jejich zvýšení výkonu nové kompilátory je všechny.  
  
## <a name="see-also"></a>Viz také  
 [Video prezentace v tomto tématu](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)  
 [Průvodce začátečníka profilací výkonu](/visualstudio/profiling/beginners-guide-to-performance-profiling)  
 [Výkon](../../../docs/framework/performance/index.md)  
 [Tipy pro zvýšení výkonu rozhraní .NET](http://msdn.microsoft.com/library/ms973839.aspx)  
 [Nástroj pro analýzu výkonu Windows Phone](http://msdn.microsoft.com/magazine/hh781024.aspx)  
 [Najít kritická místa aplikace pomocí sady Visual Studio Profiler](http://msdn.microsoft.com/magazine/cc337887.aspx)  
 [Channel 9 kurzy nástroje PerfView](http://channel9.msdn.com/Series/PerfView-Tutorial)  
 [Tipy pro zvýšení výkonu vysoké úrovně](http://curah.microsoft.com/4604/improving-your-net-apps-startup-performance)  
 [DotNet/roslyn úložišti na Githubu](https://github.com/dotnet/roslyn)
