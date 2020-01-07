---
title: Řetězce – C# Průvodce programováním
ms.custom: seodec18
ms.date: 06/27/2019
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: 46820fe4137f5080b956cd1345d3e95c2e06f9ca
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635077"
---
# <a name="strings-c-programming-guide"></a>Řetězce (Průvodce programováním v C#)
Řetězec je objekt typu <xref:System.String> jehož hodnota je text. Interně je text uložen jako sekvenční kolekce objektů <xref:System.Char> jen pro čtení. Na konci C# řetězce se nenachází ukončovací znak null; C# řetězec tedy může obsahovat libovolný počet vložených znaků null (' \ 0 '). Vlastnost <xref:System.String.Length%2A> řetězce představuje počet `Char` objektů, které obsahuje, nikoli počet znaků Unicode. Pro přístup k jednotlivým bodům kódu Unicode v řetězci použijte objekt <xref:System.Globalization.StringInfo>.  
  
## <a name="string-vs-systemstring"></a>řetězec vs. System. String  
 V C#nástroji je klíčové slovo `string` alias pro <xref:System.String>. Proto jsou `String` a `string` ekvivalentní a můžete použít libovolné konvence pojmenování, které dáváte přednost. Třída `String` poskytuje mnoho metod pro bezpečné vytváření, manipulaci a porovnávání řetězců. Kromě toho C# jazyk přetěžuje některé operátory pro zjednodušení běžných operací s řetězci. Další informace o klíčovém slově naleznete v tématu [String](../../language-reference/builtin-types/reference-types.md). Další informace o typu a jeho metodách naleznete v tématu <xref:System.String>.  
  
## <a name="declaring-and-initializing-strings"></a>Deklarace a inicializace řetězců  
 Můžete deklarovat a inicializovat řetězce různými způsoby, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#1)]  
  
 Všimněte si, že nepoužíváte operátor [New](../../language-reference/operators/new-operator.md) k vytvoření objektu String s výjimkou toho, že inicializujete řetězec s polem znaků.  
  
 Inicializujte řetězec s hodnotou <xref:System.String.Empty> konstantou pro vytvoření nového objektu <xref:System.String>, jehož řetězec má nulovou délku. Řetězcové vyjádření řetězce s nulovou délkou je "". Inicializací řetězců s hodnotou <xref:System.String.Empty> namísto hodnoty [null](../../language-reference/keywords/null.md)můžete snížit pravděpodobnost výskytu <xref:System.NullReferenceException>. Použijte metodu static <xref:System.String.IsNullOrEmpty%28System.String%29> k ověření hodnoty řetězce před tím, než se pokusíte o přístup k němu.  
  
## <a name="immutability-of-string-objects"></a>Neměnnosti objektů řetězců  
 Objekty řetězce jsou *neměnné*: po vytvoření již nelze změnit. Všechny metody <xref:System.String> a C# operátory, které se zobrazí pro úpravu řetězce, ve skutečnosti vrátí výsledek v novém objektu String. V následujícím příkladu, když je obsah `s1` a `s2` zřetězený tak, aby pomohly vytvořit jeden řetězec, jsou tyto dva původní řetězce nezměněny. Operátor `+=` vytvoří nový řetězec, který obsahuje kombinovaný obsah. Tento nový objekt je přiřazen k proměnné `s1`a původní objekt, který byl přiřazen `s1` je uvolněn pro uvolňování paměti, protože na něj nedrží žádné jiné proměnné.  
  
 [!code-csharp[csProgGuideStrings#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#2)]  
  
 Vzhledem k tomu, že je řetězec "úpravy" ve skutečnosti vytvoření nového řetězce, je nutné při vytváření odkazů na řetězce použít upozornění. Vytvoříte-li odkaz na řetězec a pak "" Upravit "původní řetězec, odkaz bude nadále ukazovat na původní objekt namísto nového objektu, který byl vytvořen při úpravě řetězce. Toto chování je znázorněno v následujícím kódu:  
  
 [!code-csharp[csProgGuideStrings#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#25)]  
  
 Další informace o tom, jak vytvořit nové řetězce, které jsou založeny na úpravách, jako je například operace hledání a nahrazení v původním řetězci, naleznete v tématu [How to Modify String String](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Regulární a doslovné řetězcové literály  
 Použijte regulární řetězcové literály v případě, že je nutné vložit C#řídicí znaky poskytnuté pomocí, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#3)]  
  
 Používejte doslovné řetězce pro usnadnění a lepší čitelnost, pokud text řetězce obsahuje znaky zpětného lomítka, například v cestách k souboru. Vzhledem k tomu, že doslovné řetězce uchovávají znaky nového řádku jako součást textu řetězce, lze je použít k inicializaci víceřádkových řetězců. Pomocí dvojitých uvozovek vložte uvozovky do doslovného řetězce. Následující příklad ukazuje některé běžné použití pro doslovné řetězce:  
  
 [!code-csharp[csProgGuideStrings#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#4)]  
  
## <a name="string-escape-sequences"></a>Řetězcové řídicí sekvence  
  
|Řídicí sekvence|Název znaku|Kódování Unicode|  
|---------------------|--------------------|----------------------|  
|\\'|Jednoduchá uvozovka|0x0027|  
|\\"|Dvojité uvozovky|0x0022|  
|\\\\ |Zpětné lomítko|0x005C|  
|\0|Null|0x0000|  
|\a|Výstraha|0x0007|  
|\b|Backspace|0x0008|  
|\f|Informační kanál formuláře|0x000C|  
|\n|Nový řádek|0x000A|  
|\r|Návrat na začátek řádku|0x000D|  
|\t|Horizontální tabulátor|0x0009|  
|\v|Vertikální tabulátor|0x000B|  
|\u|Řídicí sekvence Unicode (UTF-16)|`\uHHHH` (rozsah: 0000-FFFF; příklad: `\u00E7` = "ç")|  
|\U|Řídicí sekvence Unicode (UTF-32)|`\U00HHHHHH` (rozsah: 000000-10FFFF; příklad: `\U0001F47D` = "&#x1F47D;")|  
|\x|Řídicí sekvence Unicode podobně jako "\u" s výjimkou proměnné délky|`\xH[H][H][H]` (rozsah: 0-FFFF; příklad: `\x00E7` nebo `\x0E7` nebo `\xE7` = "ç")|  
  
> [!WARNING]
> Při použití řídicí sekvence `\x` a zadání méně než 4 hex číslic, pokud jsou znaky, které bezprostředně následují řídicí sekvence, platné šestnáctkové číslice (tj. 0-9, A-F a a-F), budou interpretovány jako součást řídicí sekvence. Například `\xA1` vytvoří "&#161;", což je kódový bod U + 00A1. Nicméně, pokud je další znak "A" nebo "a", pak bude řídicí sekvence místo interpretovat jako `\xA1A` a vytvoří "&#x0A1A;", což je kódový bod U + 0A1A. V takových případech zadáním všech 4 hex číslic (například `\x00A1`) zabráníte případnému případnému mylnému výkladu.  
  
> [!NOTE]
> V době kompilace jsou doslovné řetězce převedeny na běžné řetězce se všemi stejnými řídicími sekvencemi. Proto pokud si v okně kukátka ladicího programu zobrazíte doslovné řetězce, zobrazí se řídicí znaky, které byly přidány kompilátorem, nikoli doslovné verze ze zdrojového kódu. Například řetězec doslovného `@"C:\files.txt"` se zobrazí v okně kukátka jako "C:\\\files.txt".  
  
## <a name="format-strings"></a>Řetězce formátu  
 Formátovací řetězec je řetězec, jehož obsah je za běhu určen dynamicky. Řetězce formátu jsou vytvářeny vložením *interpolované výrazy* nebo zástupných symbolů do složených závorek v rámci řetězce. Vše uvnitř složených závorek (`{...}`) se přeloží na hodnotu a výstup jako formátovaný řetězec za běhu. Existují dvě metody vytváření řetězců formátu: interpolace řetězce a složené formátování.

### <a name="string-interpolation"></a>Interpolace řetězců
K dispozici v C# 6,0 a novějších, [*interpolované řetězce*](../../language-reference/tokens/interpolated.md) jsou označeny `$` speciálním znakem a zahrnují interpolované výrazy v závorkách. Pokud s interpolací řetězce začínáte, přečtěte si rychlý přehled v [kurzu C# o interpolaci řetězců – interaktivní](../../tutorials/exploration/interpolated-strings.yml) .

Použijte interpolaci řetězců pro zlepšení čitelnosti a udržovatelnosti kódu. Interpolace řetězců dosahuje stejných výsledků jako metoda `String.Format`, ale zlepšuje snadné použití a vkládání na základě průhlednosti.

[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringInterpolation)]

### <a name="composite-formatting"></a>Složené formátování
<xref:System.String.Format%2A?displayProperty=nameWithType> používá zástupné symboly v závorkách k vytvoření formátovacího řetězce. Tento příklad vede k podobným výstupům výše použitým způsobem interpolace řetězce.
  
[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringFormat)]

Další informace o formátování typů .NET naleznete [v tématu formátování typů v rozhraní .NET](../../../standard/base-types/formatting-types.md).
  
## <a name="substrings"></a>Podřetězců  
 Podřetězec je libovolná sekvence znaků, která je obsažena v řetězci. Použijte metodu <xref:System.String.Substring%2A> k vytvoření nového řetězce z části původního řetězce. Jeden nebo více výskytů podřetězce můžete vyhledat pomocí metody <xref:System.String.IndexOf%2A>. Použijte metodu <xref:System.String.Replace%2A>, chcete-li nahradit všechny výskyty zadaného podřetězce novým řetězcem. Podobně jako metoda <xref:System.String.Substring%2A>, <xref:System.String.Replace%2A> ve skutečnosti vrátí nový řetězec a původní řetězec neupraví. Další informace naleznete v tématu [jak hledat řetězce](../../how-to/search-strings.md) a [jak upravit obsah řetězce](../../how-to/modify-string-contents.md).
  
 [!code-csharp[csProgGuideStrings#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#9)]  
  
## <a name="accessing-individual-characters"></a>Přístup k jednotlivým znakům  
 Pomocí notace Array s hodnotou indexu můžete získat přístup k jednotlivým znakům jen pro čtení, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#8)]  
  
 Pokud metody <xref:System.String> neposkytují funkce, které je nutné pro úpravu jednotlivých znaků v řetězci, lze použít objekt <xref:System.Text.StringBuilder> pro úpravu jednotlivých znaků "In-Place" a poté vytvořit nový řetězec pro uložení výsledků pomocí metod <xref:System.Text.StringBuilder>. V následujícím příkladu Předpokládejme, že je nutné upravit původní řetězec určitým způsobem a následně uložit výsledky pro budoucí použití:  
  
 [!code-csharp[csProgGuideStrings#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#27)]  
  
## <a name="null-strings-and-empty-strings"></a>Řetězce s hodnotou null a prázdné řetězce  
 Prázdný řetězec je instancí objektu <xref:System.String?displayProperty=nameWithType>, který obsahuje nula znaků. Prázdné řetězce jsou často používány v různých programovacích scénářích, které představují prázdné textové pole. Můžete volat metody pro prázdné řetězce, protože jsou platné <xref:System.String?displayProperty=nameWithType> objekty. Prázdné řetězce jsou inicializovány následujícím způsobem:  
  
```csharp  
string s = String.Empty;  
```  
  
 Naproti tomu řetězec s hodnotou null neodkazuje na instanci objektu <xref:System.String?displayProperty=nameWithType> a žádný pokus o volání metody na řetězec s hodnotou null způsobí <xref:System.NullReferenceException>. V zřetězení a porovnávání operací s jinými řetězci však můžete použít řetězce s hodnotou null. Následující příklady ilustrují některé případy, ve kterých je odkaz na řetězec s hodnotou null, a nezpůsobí vyvolání výjimky:  
  
 [!code-csharp[csProgGuideStrings#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#20)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Použití StringBuilder pro rychlé vytváření řetězců  
 Operace s řetězci v rozhraní .NET jsou vysoce optimalizované a ve většině případů významně neovlivňují výkon. V některých scénářích, jako jsou například těsné smyčky, které spouštějí mnoho stovek nebo tisíců, můžou operace s řetězci ovlivnit výkon. Třída <xref:System.Text.StringBuilder> vytvoří vyrovnávací paměť řetězců, která nabízí lepší výkon, pokud program provádí mnoho manipulace s řetězci. Řetězec <xref:System.Text.StringBuilder> také umožňuje změnit přiřazení jednotlivých znaků, a to něco, co vestavěný datový typ String nepodporuje. Tento kód například změní obsah řetězce bez vytvoření nového řetězce:  
  
 [!code-csharp[csProgGuideStrings#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#15)]  
  
 V tomto příkladu se k vytvoření řetězce ze sady číselných typů používá <xref:System.Text.StringBuilder> objekt:  
  
 [!code-csharp[TestStringBuilder#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/TestStringBuilder.cs)]
  
## <a name="strings-extension-methods-and-linq"></a>Řetězce, rozšiřující metody a LINQ  
 Vzhledem k tomu, že typ <xref:System.String> implementuje <xref:System.Collections.Generic.IEnumerable%601>, můžete použít metody rozšíření definované ve třídě <xref:System.Linq.Enumerable> v řetězcích. Aby se zabránilo vizuálnímu zbytečným, jsou tyto metody vyloučeny z technologie IntelliSense pro <xref:System.String> typ, ale jsou však k dispozici. Výrazy dotazů LINQ můžete použít také pro řetězce. Další informace naleznete v tématu [LINQ and Strings](../concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Jak změnit obsah řetězce](../../how-to/modify-string-contents.md)|Ukazuje techniky pro transformaci řetězců a úpravu obsahu řetězců.|  
|[Jak porovnat řetězce](../../how-to/compare-strings.md)|Ukazuje, jak provádět porovnání s ordinálními a konkrétní jazykovou verzí řetězců.|  
|[Jak zřetězit více řetězců](../../how-to/concatenate-multiple-strings.md)|Ukazuje různé způsoby, jak připojit více řetězců k jednomu.|
|[Jak analyzovat řetězce pomocí String. Split](../../how-to/parse-strings-using-split.md)|Obsahuje příklady kódu, které ilustrují použití metody `String.Split` k analýze řetězců.|  
|[Jak hledat řetězce](../../how-to/search-strings.md)|Vysvětluje, jak používat hledání určitého textu nebo vzorů v řetězcích.|  
|[Jak zjistit, zda řetězec představuje číselnou hodnotu](./how-to-determine-whether-a-string-represents-a-numeric-value.md)|Ukazuje, jak bezpečně analyzovat řetězec, abyste viděli, zda má platnou číselnou hodnotu.|  
|[Interpolace řetězců](../../language-reference/tokens/interpolated.md)|Popisuje funkci interpolace řetězce, která poskytuje pohodlný Syntax pro formátování řetězců.|
|[Základní operace s řetězci](../../../standard/base-types/basic-string-operations.md)|Obsahuje odkazy na témata, která používají <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> metody k provádění základních operací s řetězci.|  
|[Analýza řetězců](../../../standard/base-types/parsing-strings.md)|Popisuje, jak převést řetězcové reprezentace základních typů .NET na instance odpovídajících typů.|  
|[Analýza řetězců data a času v .NET](../../../standard/base-types/parsing-datetime.md)|Ukazuje, jak převést řetězec, například "01/24/2008" na objekt <xref:System.DateTime?displayProperty=nameWithType>.|  
|[Porovnávání řetězců](../../../standard/base-types/comparing.md)|Obsahuje informace o tom, jak porovnat řetězce a poskytuje příklady C# v a Visual Basic.|  
|[Používání třídy StringBuilder](../../../standard/base-types/stringbuilder.md)|Popisuje, jak vytvořit a upravit dynamické objekty řetězce pomocí třídy <xref:System.Text.StringBuilder>.|  
|[LINQ a řetězce](../concepts/linq/linq-and-strings.md)|Poskytuje informace o tom, jak provádět různé řetězcové operace pomocí dotazů LINQ.|  
|[Průvodce programováním v jazyce C#](../index.md)|Obsahuje odkazy na témata, která vysvětlují programovací C#konstrukce v.|  
