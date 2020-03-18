---
title: Strings - Programovací příručka Jazyka C#
ms.date: 06/27/2019
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: dd76450c2a6a1726d630285f652d252c5f66183f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711906"
---
# <a name="strings-c-programming-guide"></a>Řetězce (Průvodce programováním v C#)
Řetězec je objekt typu, <xref:System.String> jehož hodnota je text. Interně je text uložen jako sekvenční <xref:System.Char> kolekce objektů jen pro čtení. Na konci řetězce Jazyka C# není žádný znak null ukončující; Řetězec jazyka C# proto může obsahovat libovolný počet vložených prázdných znaků (\0). Vlastnost <xref:System.String.Length%2A> řetězce představuje počet `Char` objektů, které obsahuje, nikoli počet znaků Unicode. Chcete-li získat přístup k jednotlivým bodům <xref:System.Globalization.StringInfo> kódu Unicode v řetězci, použijte objekt.  
  
## <a name="string-vs-systemstring"></a>řetězec vs. System.String  
 V c# `string` klíčové slovo je <xref:System.String>alias pro . Proto `String` a `string` jsou ekvivalentní a můžete použít podle toho, co konvence pojmenování dáváte přednost. Třída `String` poskytuje mnoho metod pro bezpečné vytváření, manipulaci a porovnávání řetězců. Kromě toho jazyk C# přetíží některé operátory zjednodušit běžné operace řetězce. Další informace o klíčovém slově naleznete v [tématu string](../../language-reference/builtin-types/reference-types.md). Další informace o typu a jeho <xref:System.String>metodách naleznete v tématu .  
  
## <a name="declaring-and-initializing-strings"></a>Deklarování a inicializace řetězců  
 Řetězce můžete deklarovat a inicializovat různými způsoby, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#1)]  
  
 Všimněte si, že nepoužíváte [nový](../../language-reference/operators/new-operator.md) operátor k vytvoření objektu řetězce s výjimkou při inicializaci řetězce s polem znaků.  
  
 Inicializovat řetězec <xref:System.String.Empty> s konstantní hodnotou <xref:System.String> vytvořit nový objekt, jehož řetězec je nulové délky. Řetězcová literálová reprezentace řetězce nulové délky je "". Inicializací <xref:System.String.Empty> řetězců s hodnotou namísto [null](../../language-reference/keywords/null.md)můžete <xref:System.NullReferenceException> snížit pravděpodobnost výskytu. Statickou <xref:System.String.IsNullOrEmpty%28System.String%29> metodu použijte k ověření hodnoty řetězce před pokusem o přístup k němu.  
  
## <a name="immutability-of-string-objects"></a>Neměnnost řetězcových objektů  
 Objekty řetězce jsou *neměnné*: po jejich vytvoření je nelze změnit. Všechny <xref:System.String> metody a C# operátory, které se zobrazí upravit řetězec ve skutečnosti vrátit výsledky v nový objekt řetězce. V následujícím příkladu při `s1` obsah `s2` a jsou zřetězené tvořit jeden řetězec, dva původní řetězce jsou nezměněny. Operátor `+=` vytvoří nový řetězec, který obsahuje kombinovaný obsah. Tento nový objekt je `s1`přiřazen proměnné a původní objekt, který byl přiřazen k `s1` je uvolněna pro uvolňování paměti, protože žádná jiná proměnná obsahuje odkaz na něj.  
  
 [!code-csharp[csProgGuideStrings#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#2)]  
  
 Vzhledem k tomu, že řetězec "modifikace" je ve skutečnosti vytvoření nového řetězce, je nutné při vytváření odkazů na řetězce opatrnosti. Pokud vytvoříte odkaz na řetězec a potom "upravíte" původní řetězec, odkaz bude nadále odkazovat na původní objekt namísto nového objektu, který byl vytvořen při změně řetězce. Následující kód ilustruje toto chování:  
  
 [!code-csharp[csProgGuideStrings#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#25)]  
  
 Další informace o vytváření nových řetězců, které jsou založeny na změnách, jako je například hledání a nahrazení operací v původním řetězci, naleznete v [tématu Jak upravit obsah řetězce](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Pravidelné a verbatim řetězcové literály  
 Normální řetězcové literály použijte, pokud je nutné vložit řídicí znaky poskytované c#, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#3)]  
  
 Použijte doslovné řetězce pro pohodlí a lepší čitelnost, když text řetězce obsahuje znaky zpětného lomítka, například v cestách souborů. Vzhledem k tomu, že doslovné řetězce zachovávají nové znaky řádku jako součást textu řetězce, lze je použít k inicializaci víceřádkových řetězců. Dvojité uvozovky slouží k vložení uvozovky do doslovného řetězce. Následující příklad ukazuje některé běžné použití pro doslovné řetězce:  
  
 [!code-csharp[csProgGuideStrings#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#4)]  
  
## <a name="string-escape-sequences"></a>Sekvence úniku řetězců  
  
|Úniková sekvence|Název znaku|Kódování Unicode|  
|---------------------|--------------------|----------------------|  
|\\'|Jedna nabídka|0x0027|  
|\\"|Dvojitá nabídka|0x0022|  
|\\\\ |Zpětné lomítko|0x005C|  
|\0|Null|0x0000|  
|\a|Výstrahy|0x0007|  
|\b|Backspace|0x0008|  
|\f|Informační kanál formuláře|0x000C|  
|\n|Nový řádek|0x000A|  
|\r|Návrat na začátek řádku|0x000D|  
|\t|Horizontální tabulátor|0x0009|  
|\v|Vertikální tabulátor|0x000B|  
|\u|Úniková sekvence Unicode (UTF-16)|`\uHHHH`(rozsah: 0000 - FFFF; příklad: `\u00E7` = "ç")|  
|\U|Úniková sekvence Unicode (UTF-32)|`\U00HHHHHH`(rozsah: 000000 - 10FFFF; příklad: `\U0001F47D` = "&#x1F47D;")|  
|\x|Řídicí sekvence Unicode podobná "\u" s výjimkou s proměnnou délkou|`\xH[H][H][H]`(rozsah: 0 - FFFF; `\x0E7` `\xE7` příklad: `\x00E7` nebo = "ç")|  
  
> [!WARNING]
> Při použití `\x` sekvence escape a zadání méně než 4 šestnáctilonové číslice, pokud znaky, které bezprostředně následují sekvence escape jsou platné šestnáctkové číslice (tj. 0-9, A-F a a-f), budou interpretovány jako součást sekvence escape. Například `\xA1` vytváří "&#161;", což je bod kódu U + 00A1. Pokud je však další znak "A" nebo "a", bude sekvence `\xA1A` escape místo toho interpretována jako bytí a vytvoří "&#x0A1A;", což je bod kódu U + 0A1A. V takových případech zabrání zadání všech 4 šestnáctkových `\x00A1` číslic (např. ) případné muzika nesprávnéinterpretace.  
  
> [!NOTE]
> V době kompilace doslovné řetězce jsou převedeny na běžné řetězce se všemi stejnými sekvencemi escape. Proto pokud zobrazíte doslovný řetězec v okně sledování ladicího programu, uvidíte řídicí znaky, které byly přidány kompilátorem, nikoli doslovnou verzi ze zdrojového kódu. Například doslovný řetězec `@"C:\files.txt"` se zobrazí v okně kukátka jako "C:\\\files.txt".  
  
## <a name="format-strings"></a>Řetězce formátů  
 Formátovací řetězec je řetězec, jehož obsah je určen dynamicky za běhu. Formátovací řetězce se vytvářejí vložením *interpolovaných výrazů* nebo zástupných symbolů do závorek do řetězce. Vše uvnitř závorek (`{...}`) bude vyřešeno na hodnotu a výstup jako formátovaný řetězec za běhu. Existují dvě metody pro vytvoření formátovacích řetězců: interpolace řetězců a složené formátování.

### <a name="string-interpolation"></a>Interpolace řetězců
K dispozici v C# 6.0 a novější, [*interpolované řetězce*](../../language-reference/tokens/interpolated.md) jsou identifikovány `$` speciální znak a obsahují interpolované výrazy ve složených závorkách. Pokud jste novým řetězce interpolace, naleznete [řetězec interpolace - C# interaktivní kurz](../../tutorials/exploration/interpolated-strings.yml) pro rychlý přehled.

Pomocí interpolace řetězce zlepšit čitelnost a udržovatelnost kódu. Řetězcová interpolace dosahuje stejných výsledků jako `String.Format` metoda, ale zlepšuje snadnost použití a vložkou jasnost.

[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringInterpolation)]

### <a name="composite-formatting"></a>Složené formátování
Použije <xref:System.String.Format%2A?displayProperty=nameWithType> zástupné symboly ve složených závorkách k vytvoření formátovacího řetězce. Tento příklad má za následek podobný výstup jako metoda interpolace řetězce použitá výše.
  
[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringFormat)]

Další informace o formátování typů rozhraní .NET naleznete [v tématu Typy formátování v rozhraní .NET](../../../standard/base-types/formatting-types.md).
  
## <a name="substrings"></a>Podřetězců  
 Podřetězec je libovolná posloupnost znaků, která je obsažena v řetězci. Pomocí <xref:System.String.Substring%2A> metody vytvořte nový řetězec z části původního řetězce. Pomocí <xref:System.String.IndexOf%2A> metody můžete vyhledat jeden nebo více výskytů podřetězce. Pomocí <xref:System.String.Replace%2A> metody můžete nahradit všechny výskyty zadaného podřetězce novým řetězcem. Stejně <xref:System.String.Substring%2A> jako <xref:System.String.Replace%2A> metoda ve skutečnosti vrátí nový řetězec a nezmění původní řetězec. Další informace naleznete v [tématech Jak vyhledávat řetězce](../../how-to/search-strings.md) a [Jak upravit obsah řetězce](../../how-to/modify-string-contents.md).
  
 [!code-csharp[csProgGuideStrings#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#9)]  
  
## <a name="accessing-individual-characters"></a>Přístup k jednotlivým znakům  
 Zápis pole s hodnotou indexu můžete použít k získání přístupu jen pro čtení k jednotlivým znakům, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#8)]  
  
 Pokud <xref:System.String> metody neposkytují funkce, které je nutné upravit jednotlivé znaky v řetězci, můžete použít <xref:System.Text.StringBuilder> objekt upravit jednotlivé znaky "na místě" a potom vytvořit <xref:System.Text.StringBuilder> nový řetězec pro uložení výsledků pomocí metod. V následujícím příkladu předpokládejme, že je nutné upravit původní řetězec určitým způsobem a potom uložit výsledky pro budoucí použití:  
  
 [!code-csharp[csProgGuideStrings#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#27)]  
  
## <a name="null-strings-and-empty-strings"></a>Nulové řetězce a prázdné řetězce  
 Prázdný řetězec je instancí objektu, který obsahuje nula <xref:System.String?displayProperty=nameWithType> znaků. Prázdné řetězce se často používají v různých scénářích programování k reprezentaci prázdného textového pole. Metody můžete volat na prázdné řetězce, <xref:System.String?displayProperty=nameWithType> protože se jedná o platné objekty. Prázdné řetězce jsou inicializovány následujícím způsobem:  
  
```csharp  
string s = String.Empty;  
```  
  
 Naproti tomu nulový řetězec neodkazuje na <xref:System.String?displayProperty=nameWithType> instanci objektu a jakýkoli pokus o <xref:System.NullReferenceException>volání metody na nulovém řetězci způsobí. Však můžete použít nulové řetězce v zřetězení a porovnání operací s jinými řetězci. Následující příklady ilustrují některé případy, ve kterých odkaz na nulový řetězec nezpůsobuje a nezpůsobuje výjimku:  
  
 [!code-csharp[csProgGuideStrings#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#20)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Použití StringBuilder pro rychlé vytváření řetězců  
 Řetězcové operace v rozhraní .NET jsou vysoce optimalizované a ve většině případů nemají významný vliv na výkon. V některých scénářích, jako jsou například těsné smyčky, které jsou provádění mnoho stovek nebo tisíckrát, operace řetězce může ovlivnit výkon. Třída <xref:System.Text.StringBuilder> vytvoří vyrovnávací paměť řetězce, která nabízí lepší výkon, pokud program provádí mnoho manipulace s řetězci. Řetězec <xref:System.Text.StringBuilder> také umožňuje znovu přiřadit jednotlivé znaky, něco, co vestavěný řetězec datový typ nepodporuje. Tento kód například změní obsah řetězce bez vytvoření nového řetězce:  
  
 [!code-csharp[csProgGuideStrings#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#15)]  
  
 V tomto příkladu <xref:System.Text.StringBuilder> se objekt používá k vytvoření řetězce ze sady číselných typů:  
  
 [!code-csharp[TestStringBuilder#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/TestStringBuilder.cs)]
  
## <a name="strings-extension-methods-and-linq"></a>Řetězce, rozšiřující metody a LINQ  
 Vzhledem <xref:System.String> k <xref:System.Collections.Generic.IEnumerable%601>tomu, že typ implementuje <xref:System.Linq.Enumerable> , můžete použít metody rozšíření definované ve třídě na řetězce. Aby se zabránilo vizuální nepořádek, tyto metody jsou <xref:System.String> vyloučeny z IntelliSense pro typ, ale jsou k dispozici přesto. Výrazy dotazu LINQ můžete také použít na řetězcích. Další informace naleznete v tématu [LINQ a Strings](../concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Jak změnit obsah řetězce](../../how-to/modify-string-contents.md)|Ilustruje techniky transformace řetězců a upravit obsah řetězců.|  
|[Jak porovnat řetězce](../../how-to/compare-strings.md)|Ukazuje, jak provádět řadové a jazykové verze specifické porovnání řetězců.|  
|[Jak zřetězit více řetězců](../../how-to/concatenate-multiple-strings.md)|Ukazuje různé způsoby, jak spojit více řetězců do jednoho.|
|[Jak analyzovat řetězce pomocí String.Split](../../how-to/parse-strings-using-split.md)|Obsahuje příklady kódu, které `String.Split` ilustrují, jak použít metodu k analýzě řetězců.|  
|[Jak hledat řetězce](../../how-to/search-strings.md)|Vysvětluje, jak používat hledání konkrétního textu nebo vzorků v řetězcích.|  
|[Jak určit, jestli řetězec představuje číselnou hodnotu](./how-to-determine-whether-a-string-represents-a-numeric-value.md)|Ukazuje, jak bezpečně analyzovat řetězec a zjistit, zda má platnou číselnou hodnotu.|  
|[Interpolace řetězců](../../language-reference/tokens/interpolated.md)|Popisuje funkci interpolace řetězců, která poskytuje pohodlnou syntaxi pro formátování řetězců.|
|[Základní operace s řetězci](../../../standard/base-types/basic-string-operations.md)|Obsahuje odkazy na <xref:System.String?displayProperty=nameWithType> témata, která používají a <xref:System.Text.StringBuilder?displayProperty=nameWithType> metody k provádění základních operací řetězce.|  
|[Analýza řetězců](../../../standard/base-types/parsing-strings.md)|Popisuje, jak převést řetězcové reprezentace základních typů .NET na instance odpovídajících typů.|  
|[Analýza řetězců data a času v rozhraní .NET](../../../standard/base-types/parsing-datetime.md)|Ukazuje, jak převést řetězec, například "01/24/2008" na <xref:System.DateTime?displayProperty=nameWithType> objekt.|  
|[Porovnávání řetězců](../../../standard/base-types/comparing.md)|Obsahuje informace o tom, jak porovnat řetězce a poskytuje příklady v jazyce C# a Visual Basic.|  
|[Používání třídy StringBuilder](../../../standard/base-types/stringbuilder.md)|Popisuje, jak vytvořit a upravit dynamické <xref:System.Text.StringBuilder> objekty řetězce pomocí třídy.|  
|[LINQ a řetězce](../concepts/linq/linq-and-strings.md)|Obsahuje informace o tom, jak provádět různé operace řetězce pomocí dotazů LINQ.|  
|[Programovací příručka jazyka C#](../index.md)|Obsahuje odkazy na témata, která vysvětlují konstrukce programování v jazyce C#.|  
