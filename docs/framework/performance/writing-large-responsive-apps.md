---
title: Psaní velkých a pohotově reagujících aplikací .NET Framework
description: Vytvářejte velké, reagující aplikace .NET nebo aplikace, které zpracovávají velké objemy dat, jako jsou například soubory nebo databáze.
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a9f5d50ad78b2b0bef0ece3c4fce47d2925aca5
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063754"
---
# <a name="writing-large-responsive-net-framework-apps"></a>Psaní velkých a pohotově reagujících aplikací .NET Framework

Tento článek poskytuje tipy pro zlepšení výkonu rozsáhlých aplikací .NET Framework, nebo aplikací, které zpracovávají velké objemy dat, jako jsou soubory nebo databáze. Tyto tipy přicházejí z přepisu kompilátorů C# a Visual Basic ve spravovaném kódu a tento článek obsahuje několik reálných příkladů z kompilátoru C#.
  
.NET Framework je vysoce produktivní pro vytváření aplikací. Výkonné a bezpečné jazyky a rozsáhlá kolekce knihoven usnadňují vytváření aplikací pro vysoce ovocné účely. Přináší ale odpovědnost za skvělou produktivitu. Měli byste použít veškerou sílu .NET Framework, ale v případě potřeby připravujte výkon svého kódu.
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Proč se nový výkon kompilátoru vztahuje na vaši aplikaci  
 Tým .NET Compiler Platform ("Roslyn") přepsal kompilátory jazyka C# a Visual Basic ve spravovaném kódu, aby poskytoval nová rozhraní API pro modelování a analýzu kódu, vytváření nástrojů a povolení mnohem rozsáhlejšího prostředí s kódováním kódu v aplikaci Visual Studio. Přepisování kompilátorů a sestavování prostředí sady Visual Studio na nových kompilátorech odhalilo užitečné přehledy výkonu, které platí pro všechny velké .NET Framework aplikace nebo aplikace, které zpracovávají velké množství dat. Nemusíte znát kompilátory, abyste mohli využívat přehledy a příklady z kompilátoru C#.
  
 Visual Studio používá rozhraní API kompilátoru k sestavení všech funkcí technologie IntelliSense, které uživatelé mají rádi, jako je například obarvení identifikátorů a klíčových slov, seznamy pro doplňování syntaxe, vlnovky pro chyby, tipy k parametrům, problémy s kódem a akce kódu. Visual Studio poskytuje tuto technickou podporu, zatímco vývojáři zadávají a mění kód a Visual Studio musí zůstat reagovat, zatímco kompilátor průběžně modeluje úpravy vývojářů kódu.
  
 Když koncoví uživatelé komunikují s vaší aplikací, očekávají, že budou reagovat. Psaní nebo zpracování příkazů by nikdy nemělo být blokované. V případě, že uživatel pokračuje v psaní, je nutné nápovědu rychle zobrazit nebo zadat. Vaše aplikace by se neměla blokovat vlákno uživatelského rozhraní s dlouhými výpočty, díky kterým se aplikace bude cítit pomalá.
  
 Další informace o kompilátorech Roslyn naleznete v sadě [SDK pro .NET Compiler Platform](../../csharp/roslyn-sdk/index.md).
  
## <a name="just-the-facts"></a>Jenom fakta  
 Při ladění výkonu a vytváření .NET Frameworkch aplikací s odezvou doporučujeme vzít v úvahu tato fakta.
  
### <a name="fact-1-dont-prematurely-optimize"></a>Fakt 1: nezralá optimalizace  
 Psaní kódu, který je složitější než IT oddělení musí mít za následek údržbu, ladění a proleštění nákladů. Zkušení programátoři mají intuitivní podrobnější informace o řešení problémů s kódováním a psaní efektivnějšího kódu. Někdy ale předčasně optimalizují svůj kód. Například používají zatřiďovací tabulku, když by bylo stačit jednoduché pole, nebo použití složitého ukládání do mezipaměti, které by mohlo způsobit nevracení paměti místo pouhého přepočítání hodnot. I v případě, že jste programátorem zkušeností, měli byste otestovat výkon a analyzovat kód při hledání problémů.
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Fakt 2: Pokud se neměříte, odhaduje se  
 Profily a měření neleží. V části profily se dozvíte, jestli je procesor plně načtený nebo jestli jste zablokovali v/v disku. V části profily se dozvíte, jaký typ a kolik paměti přidělujete a jestli váš procesor stráví spoustu času v [uvolňování paměti](../../standard/garbage-collection/index.md) (GC).
  
 Měli byste nastavit cíle výkonu pro klíčové zkušenosti zákazníků a scénáře v aplikaci a zapsat testy pro měření výkonu. Prozkoumat neúspěšné testy pomocí vědecké metody: pomocí profilů vás povedete, vyslovují, co problém může být, a otestování své hypotézy pomocí experimentu nebo změny kódu. Pomocí pravidelného testování můžete stanovit základní měření výkonu směrného plánu, abyste mohli izolovat změny, které způsobují regrese ve výkonu. Tím, že se přiblížíte k výkonu v rámci striktního způsobu, se vyhnete plýtvání časem s aktualizacemi kódu, které nepotřebujete.
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Fakt 3: dobré nástroje vedou ke všem rozdílům  
 Kvalitní nástroje umožňují rychle přejít k největším problémům s výkonem (procesor, paměť nebo disk) a pomůžou vám najít kód, který způsobuje Tato kritická místa. Společnost Microsoft dodává řadu nástrojů pro výkon, jako je například [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) a [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).
  
 PerfView je bezplatný a úžasné výkonný nástroj, který vám pomůže soustředit se na hloubkové problémy, jako jsou vstupně-výstupní operace disku, události GC a paměť. Můžete zachytit události trasování událostí souvisejících s výkonem [pro Windows](../wcf/samples/etw-tracing.md) (ETW) a snadno zobrazit jednotlivé aplikace, jednotlivé procesy, balíčky a informace o vláknech. PerfView ukazuje, kolik paměti a jaký typ paměti vaše aplikace přiděluje a které funkce nebo zásobníky volání přispívají k tomu, kolik je přidělení paměti. Podrobnosti najdete v tématech s bohatou nápovědu, ukázky a videa, která jsou součástí tohoto nástroje (například [kurzy PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) na Channel 9).
  
### <a name="fact-4-its-all-about-allocations"></a>Fakt 4: vše o přiděleních  
 Možná si myslíte, že sestavování reakce .NET Framework aplikace je vše o algoritmech, jako je například použití rychlého řazení místo řazení bublin, ale to není případ. Největší faktor v sestavování reakce aplikace přiděluje paměť, zejména v případě, že je vaše aplikace velmi rozsáhlá nebo zpracovává velké objemy dat.
  
 Skoro veškerá práce, která se má sestavit, reaguje prostředí IDE s novými rozhraními API kompilátoru, která se týkají zamezení přidělení a správě strategií ukládání do mezipaměti. Trasování PerfView ukazují, že výkon nových kompilátorů jazyka C# a Visual Basic je málo vázaný na procesor. Kompilátory můžou být vázané na vstupně-výstupní operace při čtení stovek tisíců nebo milionů řádků kódu, čtení metadat nebo generování generovaného kódu. Zpoždění vlákna uživatelského rozhraní jsou skoro všechny z důvodu uvolňování paměti. Uvolňování .NET Framework GC je vysoce vyladěné pro výkon a provádí většinu jeho práce současně, zatímco se spouští kód aplikace. Jedno přidělení ale může aktivovat nákladný [Gen2](../../standard/garbage-collection/fundamentals.md) kolekci, takže se zastaví všechna vlákna.
  
## <a name="common-allocations-and-examples"></a>Běžné alokace a příklady  
 Ukázkové výrazy v této části mají skryté alokace, které se jeví jako malé. Pokud ale velké aplikace vykoná výrazy dostatečně dlouho, může to způsobit stovky megabajtů, dokonce i gigabajtů. Například jednorázové testy, které simulují psaní vývojářů v editoru, přidělené gigabajty paměti a vedli výkonnostnímu týmu, aby se zaměřili na psaní scénářů.
  
### <a name="boxing"></a>Zabalení  
 [Zabalení](../../csharp/programming-guide/types/boxing-and-unboxing.md) nastane, pokud jsou typy hodnot, které jsou normálně živé v zásobníku nebo v datových strukturách zabaleny do objektu. To znamená, že přidělíte objektu pro uchovávání dat a potom vrátíte ukazatel na objekt. .NET Framework jsou někdy hodnoty polí z důvodu signatury metody nebo typu umístění úložiště. Zabalením typu hodnoty v objektu dojde k přidělení paměti. Mnohé operace zabalení můžou do vaší aplikace přispívat megabajtů a gigabajty přidělení, což znamená, že vaše aplikace bude způsobit větší GC. .NET Framework a kompilátory jazyka zabraňují zabalení, je-li to možné, ale někdy k tomu dojde, pokud je k dispozici alespoň po očekávání.
  
 Chcete-li zobrazit zabalení v PerfView, otevřete trasování a podívejte se na alokační zásobníky haldy GC v názvu procesu vaší aplikace (Nezapomeňte, PerfView sestavy pro všechny procesy). Pokud se zobrazí typy jako <xref:System.Int32?displayProperty=nameWithType> a <xref:System.Char?displayProperty=nameWithType> v části přidělení, jsou typy hodnot zabalení. Když vyberete jeden z těchto typů, zobrazí se zásobníky a funkce, ve kterých jsou zabalené.
  
 **Příklad 1: metody řetězce a argumenty typu hodnoty**  
  
 Tento vzorový kód ilustruje potenciálně zbytečný a nadměrný zabalení:  
  
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
  
 Tento kód poskytuje funkce protokolování, takže aplikace může `Log` často zavolat funkci, možná miliony časů. Problém je, že volání `string.Format` překládá na <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> přetížení.
  
 Toto přetížení vyžaduje, aby pole .NET Framework k zadání `int` hodnot do objektů, aby je bylo možné předat tomuto volání metody. Částečnou opravu je zavolat `id.ToString()` a `size.ToString()` předat všechny řetězce (které jsou objekty) `string.Format` volání. Volání `ToString()` přidělí řetězec, ale toto přidělení bude provedeno i v rámci `string.Format` .
  
 Můžete zvážit, že toto základní volání `string.Format` je pouze zřetězení řetězců, takže můžete místo toho napsat tento kód:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Nicméně tento řádek kódu zavádí přidělení zabalení, protože se kompiluje do <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29> . .NET Framework musí být vyvolán znakový literál.`Concat`  
  
 **Opravit příklad 1**  
  
 Kompletní oprava je jednoduchá. Pouze nahraďte znakový literál řetězcovým literálem, který nevyvolává zabalení, protože řetězce jsou již objekty:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Příklad 2: zabalení výčtu**  
  
 Tento příklad zodpovídá za obrovské množství přidělení v nových kompilátorech C# a Visual Basic z důvodu častého použití typů výčtu, zejména při operacích vyhledávání ve slovníku.
  
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
  
 Tento problém je velice jemný. PerfView by tuto zprávu nahlásil jako <xref:System.Enum.GetHashCode> zabalení, protože v případě důvodů implementace jsou v polích metoda základní reprezentace typu výčtu. Pokud se podrobněji podíváte v PerfView, může se pro každé volání na. zobrazit dvě přidělení zabalení <xref:System.Enum.GetHashCode> . Kompilátor vloží jeden a .NET Framework vloží druhý.
  
 **Oprava pro příklad 2**  
  
 Můžete snadno zabránit tomu, aby se obě přidělení přetypování do základní reprezentace před voláním <xref:System.Enum.GetHashCode> :  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Dalším běžným zdrojem zabalení pro výčtové typy je <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> metoda. Argument předaný do <xref:System.Enum.HasFlag%28System.Enum%29> musí být zabalen. Ve většině případů je nahrazení volání <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> s bitovým testem jednodušší a bez přidělení.
  
 Zajistěte si první fakt o výkonu (to znamená, že se předčasně neoptimalizují) a nespustí se tímto způsobem přepis veškerého kódu. Pamatujte na tyto náklady na zabalení, ale změňte kód pouze po profilaci aplikace a nalezení aktivních bodů.
  
### <a name="strings"></a>Řetězce  
 Manipulace s řetězci jsou některé z největších culprits pro přidělení a často se zobrazují v PerfView v horních pěti přiděleních. Programy používají řetězce pro serializaci, JSON a rozhraní REST API. Můžete použít řetězce jako programové konstanty pro spolupráci se systémy, když nemůžete použít typy výčtu. Když profilace znázorňuje, že řetězce mají vysoce ovlivněný výkon, hledejte volání metod, jako například,,, <xref:System.String> <xref:System.String.Format%2A> <xref:System.String.Concat%2A> <xref:System.String.Split%2A> <xref:System.String.Join%2A> , <xref:System.String.Substring%2A> a tak dále. Použití <xref:System.Text.StringBuilder> , aby se předešlo nákladům na vytvoření jednoho řetězce z mnoha kusů, ale i přidělení <xref:System.Text.StringBuilder> objektu se může stát kritickým bodem, který potřebujete spravovat.
  
 **Příklad 3: operace s řetězci**  
  
 Kompilátor jazyka C# měl tento kód, který zapisuje text formátovaného komentáře XML dokumentu:  
  
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
  
 Můžete vidět, že tento kód provede mnoho manipulace s řetězci. Kód používá metody knihovny pro rozdělení řádků do samostatných řetězců, pro oříznutí prázdných znaků, pro kontrolu, zda `text` je argument komentář k dokumentaci XML a extrahování podřetězců z řádků.
  
 Na prvním řádku uvnitř `WriteFormattedDocComment` , `text.Split` volání přidělí nové pole tří prvků jako argument pokaždé, když je volána. Kompilátor musí vygenerovat kód pro každé přidělení tohoto pole. Důvodem je, že kompilátor neví, zda je pole <xref:System.String.Split%2A> uloženo, kde může být pole upraveno jiným kódem, což by ovlivnilo pozdější volání `WriteFormattedDocComment` . Volání pro <xref:System.String.Split%2A> také přiděluje řetězec pro každý řádek v `text` a přiděluje další paměť k provedení operace.
  
 `WriteFormattedDocComment`má tři volání <xref:System.String.TrimStart%2A> metody. Dva jsou ve vnitřních smyčkách, které duplikují práci a přidělení. Aby byly věci horší, volání <xref:System.String.TrimStart%2A> metody bez argumentů přidělí prázdné pole (pro `params` parametr) Kromě výsledku řetězce.
  
 Nakonec existuje volání <xref:System.String.Substring%2A> metody, která obvykle přiděluje nový řetězec.
  
 **Oprava pro příklad 3**  
  
 Na rozdíl od předchozích příkladů malé úpravy nemůžou tyto alokace opravit. Budete se muset vrátit zpátky, podívat se na problém a přistupovat k němu jinak. Například si všimnete, že argument `WriteFormattedDocComment()` je řetězec, který obsahuje všechny informace, které metoda potřebuje, takže kód by mohl provést větší indexování místo přidělení mnoha částečných řetězců.
  
 Tým výkonu kompilátoru projedná všechna tato přidělení s kódem podobným tomuto:  
  
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
  
 První verze `WriteFormattedDocComment()` přiděleného pole, několik podřetězců a oříznutý dílčí řetězec spolu s prázdným `params` polem. Také je zaškrtnuté políčko///. Revidovaný kód používá pouze indexování a přiděluje nic. Vyhledá první znak, který není prázdný, a poté zkontroluje znak podle znaku, aby bylo možné zjistit, zda řetězec začíná řetězcem "///". Nový kód používá `IndexOfFirstNonWhiteSpaceChar` místo <xref:System.String.TrimStart%2A> k vrácení prvního indexu (po zadaném počátečním indexu), kde se vyskytuje neprázdný znak. Oprava není dokončena, ale můžete si prohlédnout, jak použít podobné opravy pro kompletní řešení. Použitím tohoto přístupu v rámci kódu můžete odebrat všechna přidělení v `WriteFormattedDocComment()` .
  
 **Příklad 4: StringBuilder**  
  
 V tomto příkladu se používá <xref:System.Text.StringBuilder> objekt. Následující funkce generuje úplný název typu pro obecné typy:  
  
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
  
 Fokus je na řádku, který vytvoří novou <xref:System.Text.StringBuilder> instanci. Kód způsobí přidělení `sb.ToString()` a interní přidělení v rámci <xref:System.Text.StringBuilder> implementace, ale nemůžete řídit tato přidělení, pokud chcete výsledek řetězce.
  
 **Oprava – příklad 4**  
  
 Chcete-li opravit `StringBuilder` přidělení objektu, mezipaměť objektu. I když mezipaměť jedné instance, která může být vyvolána, může výrazně zvýšit výkon. Jedná se o novou implementaci funkce a vynechání veškerého kódu s výjimkou nového prvního a posledního řádku:  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Hlavní části jsou nové `AcquireBuilder()` `GetStringAndReleaseBuilder()` funkce a:  
  
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
  
 Vzhledem k tomu, že nové kompilátory používají dělení na vlákna, tyto implementace používají pole s statickým vláknem ( <xref:System.ThreadStaticAttribute> atribut) pro ukládání do mezipaměti <xref:System.Text.StringBuilder> a pravděpodobně si můžete vzdání `ThreadStatic` deklarace. Pole static vlákna obsahuje jedinečnou hodnotu pro každé vlákno, které provádí tento kód.
  
 `AcquireBuilder()`Vrátí instanci uloženou v mezipaměti <xref:System.Text.StringBuilder> , pokud ji vymažete a nastavíte pole nebo mezipaměť na hodnotu null. V opačném případě `AcquireBuilder()` vytvoří novou instanci a vrátí ji, aby pole nebo mezipaměť bylo nastaveno na hodnotu null.
  
 Až budete hotovi <xref:System.Text.StringBuilder> , zavoláte, `GetStringAndReleaseBuilder()` abyste získali výsledek řetězce, uložili <xref:System.Text.StringBuilder> instanci v poli nebo mezipaměti a potom vrátí výsledek. Je možné, že spuštění tohoto kódu znovu zadáte a vytvoříte více <xref:System.Text.StringBuilder> objektů (i když se to zřídka stane). Kód uloží pouze poslední vydanou <xref:System.Text.StringBuilder> instanci pro pozdější použití. Tato jednoduchá strategie ukládání do mezipaměti významně snižuje přidělení v nových kompilátorech. Části .NET Framework a MSBuild ("MSBuild") používají podobnou techniku pro zlepšení výkonu.
  
 Tato jednoduchá strategie ukládání do mezipaměti dodržuje dobrý návrh mezipaměti, protože má limit velikosti. Existuje však více kódů, než je původní, což znamená vyšší náklady na údržbu. Strategii ukládání do mezipaměti byste měli přijmout jenom v případě, že jste zjistili problém s výkonem a PerfView ukazuje, že <xref:System.Text.StringBuilder> přidělení jsou významným přispěvatelem.
  
### <a name="linq-and-lambdas"></a>LINQ a výrazy lambda  
Jazykově integrovaný dotaz (LINQ), ve spojení s lambda výrazy, je příkladem funkce produktivita. Jeho použití ale může mít významný dopad na výkon v průběhu času a může se stát, že budete muset přepsat kód.
  
 **Příklad 5: výrazy lambda, seznamy \<T> a IEnumerable\<T>**  
  
 V tomto příkladu se používá [kód jazyka LINQ a funkčního stylu](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) k nalezení symbolu v modelu kompilátoru s daným názvem řetězec:  
  
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
  
 Nový kompilátor a prostředí IDE, které jsou postaveny na `FindMatchingSymbol()` tomto volání, jsou velmi často a v jediném řádku kódu této funkce je několik skrytých přidělení. Chcete-li tyto alokace prostudovat, nejprve jednotlivé řádky této funkce rozdělte na dva řádky:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 V prvním řádku se [výraz lambda](../../csharp/language-reference/operators/lambda-expressions.md) `s => s.Name == name` [zavře nad](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) místní proměnnou `name` . To znamená, že kromě přidělení objektu [delegáta](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) , který `predicate` obsahuje, kód přiděluje statickou třídu pro uchování prostředí, které zachycuje hodnotu `name` . Kompilátor generuje kód podobný následujícímu:  
  
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
  
 Dvě `new` alokace (jedna pro třídu prostředí a jeden pro delegáta) jsou nyní explicitní.
  
 Nyní se podívejte na volání `FirstOrDefault` . Tato metoda rozšíření u typu vychází z <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> přidělení. Vzhledem k tomu `FirstOrDefault` , že přebírá <xref:System.Collections.Generic.IEnumerable%601> objekt jako svůj první argument, můžete zavolat na následující kód (zjednodušený bit pro diskuzi):  
  
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
  
 `symbols`Proměnná má typ <xref:System.Collections.Generic.List%601> . <xref:System.Collections.Generic.List%601>Typ kolekce implementuje <xref:System.Collections.Generic.IEnumerable%601> a cleverly definuje enumerátor ( <xref:System.Collections.Generic.IEnumerator%601> rozhraní), který <xref:System.Collections.Generic.List%601> implementuje s `struct` . Použití struktury namísto třídy znamená, že se obvykle vyhnete jakémukoli přidělení haldy, což pak může ovlivnit výkon uvolňování paměti. Enumerátory se obvykle používají se `foreach` smyčkou jazyka, která používá strukturu výčtu, jak je vrácena v zásobníku volání. Zvýšení ukazatele zásobníku volání, aby uvolnil prostor pro objekt, nemá vliv na uvolňování paměti způsobem, jakým provádí přidělení haldy.
  
 V případě rozšířeného `FirstOrDefault` volání musí kód volat `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601> . Přiřazení `symbols` `enumerable` proměnné typu `IEnumerable<Symbol>` ztratí informace, které jsou aktuálním objektem <xref:System.Collections.Generic.List%601> . To znamená, že když kód načte enumerátor s `enumerable.GetEnumerator()` , .NET Framework musí zařadit vrácenou strukturu k `enumerator` proměnné.
  
 **Oprava – příklad 5**  
  
 Oprava má přepsat `FindMatchingSymbol` následujícím způsobem a nahradit tak jeden řádek kódu šestými řádky kódu, které jsou stále stručnější, snadno čitelné a srozumitelnější a snadno udržovatelnější:  
  
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
  
 Tento kód nepoužívá metody rozšíření LINQ, výrazy lambda nebo enumerátory a nevyvolává žádné přidělení. Neexistují žádné přidělení, protože kompilátor uvidí, že `symbols` kolekce je <xref:System.Collections.Generic.List%601> a může vytvořit vazby výsledného enumerátoru (struktury) na místní proměnnou se správným typem, aby nedošlo k zabalení. Původní verze této funkce byla skvělým příkladem exprese jazyka C# a produktivity .NET Framework. Tato nová a efektivnější verze zachovává tyto kvality bez přidání jakéhokoliv komplexního kódu, který se má zachovat.
  
### <a name="async-method-caching"></a>Ukládání asynchronní metody do mezipaměti  

Následující příklad ukazuje běžný problém při pokusu o použití výsledků v mezipaměti v [asynchronní](../../csharp/programming-guide/concepts/async/index.md) metodě.
  
 **Příklad 6: ukládání do mezipaměti v asynchronních metodách**  
  
 Funkce integrovaného vývojového prostředí sady Visual Studio, které jsou založené na nových kompilátorech C# a Visual Basic často načítají stromy syntaxe a kompilátory používají asynchronní použití při reakci sady Visual Studio. Zde je první verze kódu, který můžete napsat pro získání stromu syntaxe:  
  
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
  
 Můžete vidět, že volání `GetSyntaxTreeAsync()` instance a `Parser` , analyzuje kód a potom vrátí <xref:System.Threading.Tasks.Task> objekt, `Task<SyntaxTree>` . Nákladná část přiděluje `Parser` instanci a analyzuje kód. Funkce vrátí <xref:System.Threading.Tasks.Task> , aby volající mohli očekávat, že analýza funguje, a uvolní vlákno uživatelského rozhraní, které bude reagovat na vstup uživatele.
  
 Několik funkcí sady Visual Studio se může pokusit získat stejný strom syntaxe, takže můžete napsat následující kód pro uložení výsledků analýzy do mezipaměti a ušetřit tak čas a přidělení. Tento kód ale při přidělení:  
  
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
  
 Vidíte, že nový kód s ukládáním do mezipaměti má `SyntaxTree` pole s názvem `cachedResult` . Pokud je toto pole null, `GetSyntaxTreeAsync()` provede práci a uloží výsledek do mezipaměti. `GetSyntaxTreeAsync()`Vrátí `SyntaxTree` objekt. Problém je, že pokud máte `async` funkci typu `Task<SyntaxTree>` a vrátíte hodnotu typu `SyntaxTree` , kompilátor vygeneruje kód pro přidělení úkolu pro uchování výsledku (pomocí `Task<SyntaxTree>.FromResult()` ). Úkol je označený jako dokončený a výsledek je hned dostupný. V kódu pro nové kompilátory <xref:System.Threading.Tasks.Task> došlo k objektům, které již byly dokončeny, a to často, aby tato přidělení zvýšila odezvu na upozornění.
  
 **Oprava pro příklad 6**  
  
 Chcete-li odebrat dokončené <xref:System.Threading.Tasks.Task> přidělení, můžete uložit objekt úlohy do mezipaměti s dokončeným výsledkem:  
  
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
  
 Tento kód změní typ `cachedResult` na `Task<SyntaxTree>` a využívá `async` pomocnou funkci, která obsahuje původní kód z `GetSyntaxTreeAsync()` . `GetSyntaxTreeAsync()`Nyní pomocí [operátoru slučování null](../../csharp/language-reference/operators/null-coalescing-operator.md) vrátí, `cachedResult` Pokud není null. Pokud `cachedResult` je null, potom `GetSyntaxTreeAsync()` volání `GetSyntaxTreeUncachedAsync()` a uloží výsledek do mezipaměti. Všimněte si, že `GetSyntaxTreeAsync()` neočekává volání `GetSyntaxTreeUncachedAsync()` jako kód obvykle. Bez použití operátoru await znamená, že když `GetSyntaxTreeUncachedAsync()` vrátí svůj <xref:System.Threading.Tasks.Task> objekt, `GetSyntaxTreeAsync()` okamžitě vrátí <xref:System.Threading.Tasks.Task> . Výsledkem je, že v mezipaměti je výsledek <xref:System.Threading.Tasks.Task> , takže neexistují žádné alokace k vrácení výsledku v mezipaměti.
  
### <a name="additional-considerations"></a>Další aspekty  
 Tady je několik dalších bodů, které se týkají potenciálních problémů ve velkých aplikacích nebo aplikacích, které zpracovávají velké množství dat.
  
 **Slovníky**  
  
 Slovníky se v mnoha programech používají ubiquitously a i když jsou slovníky velmi pohodlné a v podstatě efektivní. Jsou ale často používány nevhodně. V aplikaci Visual Studio a nových kompilátorech ukazuje analýza mnoho slovníků obsahuje jeden element nebo byl prázdný. Prázdné <xref:System.Collections.Generic.Dictionary%602> pole má deset polí a zabírá 48 bajtů v haldě na počítači x86. Slovníky jsou skvělé, pokud potřebujete mapování nebo asociativní datovou strukturu s vyhledáváním v čase. Pokud ale máte jenom několik prvků, zařadíte spoustu místa pomocí slovníku. Místo toho můžete například iterativním způsobem prohledat `List<KeyValuePair\<K,V>>` , stejně jako rychle. Použijete-li slovník pouze k načtení s daty a pak ho z něj přečtete (velmi běžný vzor), může být v závislosti na počtu prvků, které používáte, možná skoro stejně rychlé.
  
 **Třídy vs. struktury**  
  
 V takovém případě třídy a struktury poskytují pro optimalizaci vašich aplikací klasický prostor a čas. Třídy účtují 12 bajtů režie na počítači x86 i v případě, že nemají žádná pole, ale mají nenákladné předávat, protože přebírají jenom ukazatel na odkazování na instanci třídy. Struktury neúčtují žádné přidělení haldy, pokud nejsou zabalené, ale pokud předáte velké struktury jako argumenty funkce nebo návratové hodnoty, bere čas procesoru k atomické kopírování všech datových členů struktur. Podívejte se na opakující se volání vlastností, které vracejí struktury, a do mezipaměti hodnoty vlastnosti v místní proměnné, aby nedocházelo k nadměrnému kopírování dat.
  
 **Caches**  
  
 Běžným zdvihem výkonu je ukládání výsledků do mezipaměti. Mezipaměť bez omezení velikosti nebo zásad odstraňování ale může být nevracení paměti. Při zpracování velkých objemů dat můžete v případě, že máte v mezipamětech na velké množství paměti, způsobit, že shromažďování paměti přepíše výhody hledání uložených v mezipaměti.
  
 V tomto článku jsme probrali, jak byste měli být vědomi kritických příznaků výkonu, které mohou ovlivnit rychlost odezvy vaší aplikace, zejména pro velké systémy nebo systémy, které zpracovávají velké množství dat. Mezi Běžné culprits patří zabalení, manipulace s řetězci, LINQ a lambda, ukládání do mezipaměti v asynchronních metodách, ukládání do mezipaměti bez omezení velikosti nebo zásad vyřazení, nevhodné použití slovníků a předávání okolo struktur. Mějte na paměti čtyři fakta pro optimalizaci vašich aplikací:  
  
- Nezralá optimalizace – Buďte produktivní a optimalizujte svou aplikaci při navýšení problémů.
  
- Profily neleží – Pokud se neměříte, budete odhadem.
  
- Dobré nástroje provedou všechny rozdíly – Stáhněte si PerfView a vyzkoušejte si to.
  
- Je to vše o přidělení – to znamená, že tým platformy pro kompilátor vytrvalo většinu času, který zlepšuje výkon nových kompilátorů.
  
## <a name="see-also"></a>Viz také

- [Video o prezentaci tohoto tématu](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [Příručka pro začátečníky k profilaci výkonu](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Výkon](index.md)
- [Tipy pro zvýšení výkonu rozhraní .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))
- [Kurzy PerfView pro Channel 9](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [Sada .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md)
- [dotnet/Roslyn úložiště na GitHubu](https://github.com/dotnet/roslyn)
