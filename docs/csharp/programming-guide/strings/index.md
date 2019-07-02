---
title: Řetězce - C# Průvodce programováním
ms.custom: seodec18
ms.date: 06/27/2019
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: 668b3b927ac059acf160f5d96e8fbc614f57ddff
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67503997"
---
# <a name="strings-c-programming-guide"></a>Řetězce (Průvodce programováním v C#)
Řetězec je objekt typu <xref:System.String> jehož hodnota je text. Interně, text se ukládá jako sekvenční jen pro čtení kolekcí <xref:System.Char> objekty. Neexistuje žádný znak null ukončující řetězec jazyka C#; na konci řetězec jazyka C# proto může obsahovat libovolný počet vložené znaky null ('\0'). <xref:System.String.Length%2A> Vlastnost řetězce představuje počet `Char` objekty obsahuje, není počet znaků Unicode. Chcete-li získat přístup k jednotlivým kódové body sady Unicode v řetězci, použijte <xref:System.Globalization.StringInfo> objektu.  
  
## <a name="string-vs-systemstring"></a>Řetězec vs. System.String  
 V jazyce C# `string` – klíčové slovo je alias pro <xref:System.String>. Proto `String` a `string` jsou ekvivalentní a můžete použít podle toho, která zásady vytváření názvů dáváte přednost. `String` Třída poskytuje řadu metod pro bezpečně vytváření, manipulaci a porovnávání řetězců. Kromě toho přetížení jazyka C# některé operátory pro zjednodušení běžné operace s řetězci. Další informace o klíčovém slově, naleznete v tématu [řetězec](../../../csharp/language-reference/keywords/string.md). Další informace o typu a jeho metody, naleznete v tématu <xref:System.String>.  
  
## <a name="declaring-and-initializing-strings"></a>Deklarace a inicializace řetězců  
 Můžete deklarovat a inicializovat řetězce různými způsoby, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#1)]  
  
 Všimněte si, že je velmi riskantní používat [nové](../../../csharp/language-reference/operators/new-operator.md) operátoru pro vytvoření objektu řetězce s výjimkou při inicializaci řetězce bez pole znaků.  
  
 Inicializuje řetězec s <xref:System.String.Empty> konstantní hodnoty pro vytvoření nového <xref:System.String> objektu, jehož řetězec o nulové délce. Řetězec literálu reprezentaci řetězce s nulovou délkou je "". Pomocí inicializace řetězců s <xref:System.String.Empty> hodnotu místo [null](../../../csharp/language-reference/keywords/null.md), můžete snížit riziko <xref:System.NullReferenceException> ke kterým dochází. Použití statické <xref:System.String.IsNullOrEmpty%28System.String%29> metodu k ověření hodnotu řetězce, než se pokusíte k němu přistupovat.  
  
## <a name="immutability-of-string-objects"></a>Neměnnost řetězcových objektů  
 Řetězcových objektů jsou *neměnné*: nedá se změnit po vytvoření. Všechny <xref:System.String> metody a operátory jazyka C#, které patrně upravují řetězec ve skutečnosti výsledky jsou vráceny ve nový objekt řetězce. V následujícím příkladu když obsah `s1` a `s2` jsou zřetězeny a vytvoří jeden řetězec, jsou dva řetězce původní verzí bez úprav. `+=` Operátor vytvoří nový řetězec, který obsahuje kombinované obsah. Tento nový objekt je přiřazená k proměnné `s1`a původní objekt, který byl přiřazen `s1` se uvolní pro uvolnění paměti, protože žádná proměnná uchovává odkaz na to.  
  
 [!code-csharp[csProgGuideStrings#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#2)]  
  
 Protože je řetězec "úpravy" ve skutečnosti novou vytváření řetězců, musíte použít upozornění při vytváření odkazů na řetězce. Je-li vytvořit odkaz na řetězec a potom "upravit" původního řetězce, bude pokračovat odkaz tak, aby odkazoval na původní objekt místo nový objekt, který byl vytvořen, pokud byla změněna řetězec. Následující kód ukazuje toto chování:  
  
 [!code-csharp[csProgGuideStrings#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#25)]  
  
 Další informace o vytváření nových řetězců, které jsou založeny na úpravy, jako je například hledat a nahrazovat operace u původního řetězce najdete v tématu [jak: Změna obsahu řetězce](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Pravidelné a Verbatim řetězcové literály  
 Používejte regulární řetězcové literály, když je nutné vložit řídicí znaky, které jsou k dispozici v jazyce C#, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#3)]  
  
 Používejte verbatim řetězce pro lepší čitelnost a pohodlí při textový řetězec obsahuje zpětné lomítko znaků, například cesty k souborům. Protože doslovném řetězci zachovat jako součást řetězce textu znaky nového řádku, můžete použít k inicializaci víceřádkových řetězců. Vkládat uvozovky uvnitř doslovný řetězec pomocí dvojitých uvozovek. Následující příklad ukazuje některé běžné použití doslovném řetězci:  
  
 [!code-csharp[csProgGuideStrings#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#4)]  
  
## <a name="string-escape-sequences"></a>Řetězec řídicí sekvence  
  
|Řídicí sekvence|Název znaku|Kódování Unicode|  
|---------------------|--------------------|----------------------|  
|\\'|jednoduché uvozovky|0x0027|  
|\\"|dvojité uvozovky|0x0022|  
|\\\\ |Zpětné lomítko|0x005C|  
|\0|Null|0x0000|  
|\a|Výstrahy|0x0007|  
|\b|Backspace|0x0008|  
|\f|Posun strany|0x000C|  
|\n|Nový řádek|0x000A|  
|\r|Návrat na začátek řádku|0x000D|  
|\t|Horizontální tabulátor|0x0009|  
|\U|Řídicí sekvence Unicode (UTF-32)|`\U00nnnnnn` (například `\U0001F47D` = "&#x1F47D;")|  
|\u|Řídicí sekvence Unicode (UTF-16)|`\unnnn` (například `\u0041` = "A")|  
|\v|Vertikální tabulátor|0x000B|  
|\x|Řídicí sekvence Unicode podobný "\u" s výjimkou s proměnnou délkou.|`\x0041` nebo `\x41` = "A"|  
  
> [!WARNING]
>  Při použití `\x` řídicí sekvence a určení nižší než 4 číslic v šestnáctkové soustavě, pokud jsou znaky, které bezprostředně následují řídicí sekvenci platné hexadecimální číslice (například 0-9, A-F a a-f), budou interpretovány jako součást řídicí sekvence. Například `\xA1` vytvoří "&#161;", což je bod kódu U + 00A1. Ale pokud následující znak je "A" nebo "a", pak řídicí sekvence se místo toho interpretovat jako `\xA1A` a vytvářet "&#x0A1A;", což je bod kódu U + 0A1A. V takovém případě zadáte všechny 4 číslic v šestnáctkové soustavě (třeba `\x00A1` ), nebude moct všechny možné špatného.  
  
> [!NOTE]
>  V době kompilace doslovném řetězci jsou převedeny na běžné řetězce s stejné řídicí sekvence. Proto pokud doslovný řetězec zobrazení v okně kukátko ladicího programu, zobrazí se řídicí znaky, které byly přidány pomocí kompilátoru, ne verbatim verzi ze zdrojového kódu. Například doslovném řetězci `@"C:\files.txt"` se zobrazí v okně kukátko jako "C:\\\files.txt".  
  
## <a name="format-strings"></a>Formátovací řetězce  
 Formátovací řetězec je řetězec, jehož obsah se určují dynamicky za běhu. Formátovací řetězce jsou vytvořeny vložením *interpolovaných výrazů* nebo zástupné symboly ve složených závorkách v rámci řetězce. Vše uvnitř složených závorek (`{...}`) bude vyhodnocena na hodnotu a výstup jako formátovaný řetězec za běhu. Existují dvě metody k vytvoření řetězce formátu: řetězec interpolace a složené formátování.

### <a name="string-interpolation"></a>Interpolace řetězců
K dispozici v C# 6.0 a novějším, [ *interpolovaných řetězců* ](../../language-reference/tokens/interpolated.md) jsou určeny `$` speciálních znaků a obsahovat interpolované výrazy do složených závorek. Pokud jste ještě na interpolaci řetězce, najdete v článku [interpolace - C# interaktivního kurzu](../../tutorials/exploration/interpolated-strings.yml) a získejte rychlý přehled.

Interpolace řetězců použijte ke zlepšení čitelnosti a udržovatelnosti kódu. Interpolace řetězců dosáhnete stejných výsledků jako `String.Format` metody, ale zvyšuje snadnost použití a vložené nejasnostem.

[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringInterpolation)]

### <a name="composite-formatting"></a>Složené formátování
<xref:System.String.Format%2A?displayProperty=nameWithType> Využívá zástupné symboly v závorkách pro vytvoření řetězce formátu. Tento příklad vrátí podobný výstup jako na metodu interpolace řetězce využité nad.
  
[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringFormat)]

Další informace o formátování typy .NET najdete v části [formátovací typy v .NET](../../../standard/base-types/formatting-types.md).
  
## <a name="substrings"></a>Podřetězců  
 Dílčí řetězec je posloupnost znaků, které jsou obsaženy v řetězci. Použití <xref:System.String.Substring%2A> metodu pro vytvoření nového řetězce z část původní řetězec. Můžete vyhledat jeden nebo více výskytů dílčí řetězec s použitím <xref:System.String.IndexOf%2A> metody. Použití <xref:System.String.Replace%2A> metoda nahraďte všechny výskyty zadaným podřetězcem nový řetězec. Podobně jako <xref:System.String.Substring%2A> metody <xref:System.String.Replace%2A> ve skutečnosti vrátí nový řetězec a nezmění původní řetězec. Další informace najdete v tématu [postupy: vyhledávání řetězců](../../how-to/search-strings.md) a [jak: Změna obsahu řetězce](../../how-to/modify-string-contents.md).  
  
 [!code-csharp[csProgGuideStrings#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#9)]  
  
## <a name="accessing-individual-characters"></a>Přístup ke jednotlivým znakům  
 Zápis pole s hodnotou indexu můžete získat přístup jen pro čtení na jednotlivé znaky, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#8)]  
  
 Pokud <xref:System.String> metody se neposkytuje funkce, které potřebujete k úpravě jednotlivých znaků v řetězci, můžete použít <xref:System.Text.StringBuilder> objekt upravit jednotlivé znaky "místní" a pak vytvořte nový řetězec k uložení výsledků pomocí <xref:System.Text.StringBuilder> metody. V následujícím příkladu se předpokládá, že musí určitým způsobem upravit původní řetězec a poté uložit výsledky pro budoucí použití:  
  
 [!code-csharp[csProgGuideStrings#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#27)]  
  
## <a name="null-strings-and-empty-strings"></a>Řetězce s hodnotou Null a prázdné řetězce  
 Prázdný řetězec je instance <xref:System.String?displayProperty=nameWithType> objekt obsahující nulové znaky. Prázdné řetězce představují prázdné textové pole se často používají v různých programovacích scénářů. Můžete volat metody na prázdné řetězce, protože jde o platný <xref:System.String?displayProperty=nameWithType> objekty. Prázdné řetězce jsou inicializovány následujícím způsobem:  
  
```  
string s = String.Empty;  
```  
  
 Naopak řetězec null neodkazuje na instanci <xref:System.String?displayProperty=nameWithType> objektu a jakýkoliv pokus o volání metody na řetězec s hodnotou null způsobí, že <xref:System.NullReferenceException>. Můžete však použít řetězce s hodnotou null v operace porovnání a zřetězení s dalšími řetězci. Následující příklady znázorňují někdy, v nichž odkaz na řetězec s hodnotou null nemá a nezpůsobí výjimku, která je vyvolána:  
  
 [!code-csharp[csProgGuideStrings#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#20)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Pro vytváření rychlého řetězců pomocí StringBuilder  
 Operace s řetězci v .NET je vysoce optimalizovaných a ve většině případů nemají vliv výrazně výkonu. V některých případech například úzkou smyčky, které jsou spuštěny mnoha stovek nebo tisíců časy, ale operace s řetězci může ovlivnit výkon. <xref:System.Text.StringBuilder> Třída vytvoří vyrovnávací paměti pro řetězec, který nabízí lepší výkon, pokud aplikace provádí mnoho manipulace s řetězci. <xref:System.Text.StringBuilder> Řetězec umožňuje také něco změnit přiřazení jednotlivých znaků, předdefinovaných řetězec datového typu se nepodporuje. Tento kód například změní obsah řetězce bez vytvoření nového řetězce:  
  
 [!code-csharp[csProgGuideStrings#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#15)]  
  
 V tomto příkladu <xref:System.Text.StringBuilder> objektu se používá k vytvoření řetězce z sadu číselné typy:  
  
 [!code-csharp[TestStringBuilder#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/TestStringBuilder.cs)]
  
## <a name="strings-extension-methods-and-linq"></a>Řetězce a metod rozšíření LINQ  
 Protože <xref:System.String> typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, můžete použít rozšiřující metody definované v <xref:System.Linq.Enumerable> třídy na řetězce. Aby se zabránilo nepořádku visual, tyto metody jsou vyloučené z IntelliSense pro značku <xref:System.String> typu, ale jsou nicméně k dispozici. Můžete také použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech na řetězce dotazů. Další informace najdete v tématu [LINQ a řetězce](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Postupy: Změna obsahu řetězce](../../how-to/modify-string-contents.md)|Ukazuje techniky transformace řetězce a změnit obsah řetězce.|  
|[Postupy: Porovnávání řetězců](../../how-to/compare-strings.md)|Ukazuje, jak k provádění pořadí a jazykové verze konkrétní porovnání řetězců.|  
|[Postupy: Řetězení více řetězců](../../how-to/concatenate-multiple-strings.md)|Ukazuje různé způsoby, jak spojit víc řetězce do jednoho.|
|[Postupy: Analýza řetězců metodou String.Split](../../how-to/parse-strings-using-split.md)|Obsahuje příklady kódu, které ukazují, jak používat `String.Split` metodu pro analýzu řetězce.|  
|[Postupy: Hledání řetězců](../../how-to/search-strings.md)|Vysvětluje způsob používání vyhledávání určitý text nebo vzory v řetězcích.|  
|[Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|Ukazuje, jak bezpečně analyzovat řetězec zjistíte, zda má platnou číselnou hodnotu.|  
|[Interpolace řetězců](../../language-reference/tokens/interpolated.md)|Popisuje funkci interpolace řetězce, která poskytuje pohodlné syntaxe na formát řetězce.|
|[Základní operace s řetězci](../../../../docs/standard/base-types/basic-string-operations.md)|Obsahuje odkazy na témata, které používají <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> provádět základní operace s řetězci.|  
|[Analýza řetězců](../../../standard/base-types/parsing-strings.md)|Popisuje, jak převést řetězcové reprezentace základní typy .NET k instancím typu odpovídající typy.|  
|[Analýza řetězců data a času v .NET](../../../standard/base-types/parsing-datetime.md)|Ukazuje, jak převést řetězec jako "01/24/2008" k <xref:System.DateTime?displayProperty=nameWithType> objektu.|  
|[Porovnávání řetězců](../../../../docs/standard/base-types/comparing.md)|Obsahuje informace o tom, jak porovnat řetězce a poskytuje příklady v C# a Visual Basic.|  
|[Používání třídy StringBuilder](../../../standard/base-types/stringbuilder.md)|Popisuje, jak vytvářet a upravovat pomocí dynamické řetězcových objektů <xref:System.Text.StringBuilder> třídy.|  
|[LINQ a řetězce](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)|Poskytuje informace o tom, jak provádět různé operace s řetězci pomocí dotazů LINQ.|  
|[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)|Obsahuje odkazy na témata, která popisují konstrukce programování v jazyce C#.|  
