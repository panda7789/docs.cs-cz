---
title: Řetězce – Průvodce programováním v C#
description: Seznamte se s řetězci v programování v jazyce C#. Podívejte se na informace o deklarování a inicializaci řetězců, neměnnosti objektů řetězců a řetězcových řídicích sekvencích.
ms.date: 06/27/2019
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: 8e833bdeefcce2f12c839738b43778df8e54fa5b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381603"
---
# <a name="strings-c-programming-guide"></a>Řetězce (Průvodce programováním v C#)
Řetězec je objekt typu, <xref:System.String> jehož hodnota je text. Interně je text uložen jako sekvenční kolekce objektů jen pro čtení <xref:System.Char> . Na konci řetězce jazyka C# není ukončovací znak null; řetězec jazyka C# proto může obsahovat libovolný počet vložených znaků null (' \ 0 '). <xref:System.String.Length%2A>Vlastnost řetězce představuje počet `Char` objektů, které obsahuje, nikoli počet znaků Unicode. Pro přístup k jednotlivým bodům kódu Unicode v řetězci použijte <xref:System.Globalization.StringInfo> objekt.  
  
## <a name="string-vs-systemstring"></a>řetězec vs. System. String  
 V jazyce C# `string` je klíčové slovo alias pro <xref:System.String> . `String`A jsou proto `string` ekvivalentní a můžete použít libovolné konvence pojmenování, které dáváte přednost. `String`Třída poskytuje mnoho metod pro bezpečné vytváření, manipulaci a porovnávání řetězců. Kromě toho jazyk C# přetěžuje některé operátory pro zjednodušení běžných operací s řetězci. Další informace o klíčovém slově naleznete v tématu [String](../../language-reference/builtin-types/reference-types.md). Další informace o typu a jeho metodách naleznete v tématu <xref:System.String> .  
  
## <a name="declaring-and-initializing-strings"></a>Deklarace a inicializace řetězců  
 Můžete deklarovat a inicializovat řetězce různými způsoby, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#1)]  
  
 Všimněte si, že nepoužíváte operátor [New](../../language-reference/operators/new-operator.md) k vytvoření objektu String s výjimkou toho, že inicializujete řetězec s polem znaků.  
  
 Inicializujte řetězec s <xref:System.String.Empty> konstantní hodnotou pro vytvoření nového objektu, <xref:System.String> jehož řetězec má nulovou délku. Řetězcové vyjádření řetězce s nulovou délkou je "". Inicializací řetězců s <xref:System.String.Empty> hodnotou namísto [hodnoty null](../../language-reference/keywords/null.md)můžete snížit pravděpodobnost výskytu <xref:System.NullReferenceException> . Použijte statickou <xref:System.String.IsNullOrEmpty%28System.String%29> metodu k ověření hodnoty řetězce před tím, než se pokusíte o přístup k němu.  
  
## <a name="immutability-of-string-objects"></a>Neměnnosti objektů řetězců  
 Objekty řetězce jsou *neměnné*: po vytvoření již nelze změnit. Všechny <xref:System.String> metody a operátory jazyka C#, které se zobrazí pro úpravu řetězce, ve skutečnosti vrátí výsledek v novém objektu String. V následujícím příkladu, když je obsah `s1` a `s2` zřetězeni tak, aby tvořily jeden řetězec, jsou tyto dva původní řetězce nezměněny. `+=`Operátor vytvoří nový řetězec, který obsahuje kombinovaný obsah. Tento nový objekt je přiřazen proměnné `s1` a původní objekt, který byl přiřazen, `s1` je uvolněn pro uvolňování paměti, protože žádná jiná proměnná neuchovává odkaz na ni.  
  
 [!code-csharp[csProgGuideStrings#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#2)]  
  
 Vzhledem k tomu, že je řetězec "úpravy" ve skutečnosti vytvoření nového řetězce, je nutné při vytváření odkazů na řetězce použít upozornění. Vytvoříte-li odkaz na řetězec a pak "" Upravit "původní řetězec, odkaz bude nadále ukazovat na původní objekt namísto nového objektu, který byl vytvořen při úpravě řetězce. Toto chování je znázorněno v následujícím kódu:  
  
 [!code-csharp[csProgGuideStrings#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#25)]  
  
 Další informace o tom, jak vytvořit nové řetězce, které jsou založeny na úpravách, jako je například operace hledání a nahrazení v původním řetězci, naleznete v tématu [How to Modify String String](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Regulární a doslovné řetězcové literály  
 Použijte regulární řetězcové literály, pokud je nutné vložit řídicí znaky poskytované jazykem C#, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#3)]  
  
 Používejte doslovné řetězce pro usnadnění a lepší čitelnost, pokud text řetězce obsahuje znaky zpětného lomítka, například v cestách k souboru. Vzhledem k tomu, že doslovné řetězce uchovávají znaky nového řádku jako součást textu řetězce, lze je použít k inicializaci víceřádkových řetězců. Pomocí dvojitých uvozovek vložte uvozovky do doslovného řetězce. Následující příklad ukazuje některé běžné použití pro doslovné řetězce:  
  
 [!code-csharp[csProgGuideStrings#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#4)]  
  
## <a name="string-escape-sequences"></a>Řetězcové řídicí sekvence  
  
|Řídicí sekvence|Název znaku|Kódování Unicode|  
|---------------------|--------------------|----------------------|  
|\\'|Jednoduchá uvozovka|0x0027|  
|\\"|Dvojité uvozovky|0x0022|  
|\\\\ |Zpětné lomítko|0x005C|  
|\ 0|Null|0x0000|  
|\a|Výstrahy|0x0007|  
|\b|Backspace|0x0008|  
|\f|Informační kanál formuláře|0x000C|  
|\n|Nový řádek|0x000A|  
|\r|Návrat na začátek řádku|0x000D|  
|\t|Horizontální tabulátor|0x0009|  
|\v|Vertikální tabulátor|0x000B|  
|\u|Řídicí sekvence Unicode (UTF-16)|`\uHHHH`(rozsah: 0000-FFFF; příklad: `\u00E7` = "ç")|  
|\U|Řídicí sekvence Unicode (UTF-32)|`\U00HHHHHH`(Range: 000000-10FFFF; příklad: `\U0001F47D` = "& # x1F47D;")|  
|Uprav|Řídicí sekvence Unicode podobně jako "\u" s výjimkou proměnné délky|`\xH[H][H][H]`(rozsah: 0-FFFF; příklad: `\x00E7` nebo `\x0E7` OR `\xE7` = "ç")|  
  
> [!WARNING]
> Při použití `\x` řídicí sekvence a zadání méně než 4 šestnáctkových číslic, pokud jsou znaky, které bezprostředně následují řídicí sekvence, platné šestnáctkové číslice (tj. 0-9, a-f a a-F), budou interpretovány jako součást řídicí sekvence. Například `\xA1` vytvoří "&#161;", což je kód Point U + 00A1. Nicméně, pokud je další znak "A" nebo "a", pak bude řídicí sekvence místo interpretovat jako `\xA1A` a vytvoří "&#x0A1A;", což je kódový bod U + 0A1A. V takových případech zadáním všech 4 hex číslic (např. `\x00A1` ) zabráníte případnému případnému mylnému výkladu.  
  
> [!NOTE]
> V době kompilace jsou doslovné řetězce převedeny na běžné řetězce se všemi stejnými řídicími sekvencemi. Proto pokud si v okně kukátka ladicího programu zobrazíte doslovné řetězce, zobrazí se řídicí znaky, které byly přidány kompilátorem, nikoli doslovné verze ze zdrojového kódu. Například doslovné řetězec se `@"C:\files.txt"` zobrazí v okně kukátko jako "C: \\\files.txt".  
  
## <a name="format-strings"></a>Řetězce formátů  
 Formátovací řetězec je řetězec, jehož obsah je za běhu určen dynamicky. Řetězce formátu jsou vytvářeny vložením *interpolované výrazy* nebo zástupných symbolů do složených závorek v rámci řetězce. Vše, co uvnitř složených závorek ( `{...}` ), bude za běhu přeloženo na hodnotu a výstup jako formátovaný řetězec. Existují dvě metody vytváření řetězců formátu: interpolace řetězce a složené formátování.

### <a name="string-interpolation"></a>Interpolace řetězců
K dispozici v C# 6,0 a novějších jsou [*interpolované řetězce*](../../language-reference/tokens/interpolated.md) označeny `$` speciálním znakem a obsahují interpolované výrazy v závorkách. Pokud s interpolací řetězce začínáte, přečtěte si rychlý přehled o tom, jak se v řetězci [interpoluje Interaktivní kurz jazyka C#](../../tutorials/exploration/interpolated-strings.yml) .

Použijte interpolaci řetězců pro zlepšení čitelnosti a udržovatelnosti kódu. Interpolace řetězců dosahuje stejných výsledků jako `String.Format` metoda, ale zlepšuje snadné použití a vkládání na základě průhlednosti.

[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringInterpolation)]

### <a name="composite-formatting"></a>Složené formátování
<xref:System.String.Format%2A?displayProperty=nameWithType>Používá zástupné symboly v závorkách k vytvoření formátovacího řetězce. Tento příklad vede k podobným výstupům výše použitým způsobem interpolace řetězce.
  
[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringFormat)]

Další informace o formátování typů .NET naleznete [v tématu formátování typů v rozhraní .NET](../../../standard/base-types/formatting-types.md).
  
## <a name="substrings"></a>Podřetězců  
 Podřetězec je libovolná sekvence znaků, která je obsažena v řetězci. Použijte <xref:System.String.Substring%2A> metodu k vytvoření nového řetězce z části původního řetězce. Jeden nebo více výskytů podřetězce můžete vyhledat pomocí <xref:System.String.IndexOf%2A> metody. Pomocí <xref:System.String.Replace%2A> metody nahraďte všechny výskyty zadaného podřetězce novým řetězcem. Podobně jako <xref:System.String.Substring%2A> metoda, <xref:System.String.Replace%2A> ve skutečnosti vrátí nový řetězec a neupravuje původní řetězec. Další informace naleznete v tématu [jak hledat řetězce](../../how-to/search-strings.md) a [jak upravit obsah řetězce](../../how-to/modify-string-contents.md).
  
 [!code-csharp[csProgGuideStrings#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#7)]  
  
## <a name="accessing-individual-characters"></a>Přístup k jednotlivým znakům  
 Pomocí notace Array s hodnotou indexu můžete získat přístup k jednotlivým znakům jen pro čtení, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#8)]  
  
 Pokud <xref:System.String> metody neposkytují funkce, které je nutné pro úpravu jednotlivých znaků v řetězci, lze použít <xref:System.Text.StringBuilder> objekt pro úpravu jednotlivých znaků "na místě" a pak vytvořit nový řetězec pro uložení výsledků pomocí <xref:System.Text.StringBuilder> metod. V následujícím příkladu Předpokládejme, že je nutné upravit původní řetězec určitým způsobem a následně uložit výsledky pro budoucí použití:  
  
 [!code-csharp[csProgGuideStrings#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#27)]  
  
## <a name="null-strings-and-empty-strings"></a>Řetězce s hodnotou null a prázdné řetězce  
 Prázdný řetězec je instancí <xref:System.String?displayProperty=nameWithType> objektu, který obsahuje nula znaků. Prázdné řetězce jsou často používány v různých programovacích scénářích, které představují prázdné textové pole. Můžete volat metody v prázdných řetězcích, protože jsou platné <xref:System.String?displayProperty=nameWithType> objekty. Prázdné řetězce jsou inicializovány následujícím způsobem:  
  
```csharp  
string s = String.Empty;  
```  
  
 Naproti tomu řetězec s hodnotou null neodkazuje na instanci <xref:System.String?displayProperty=nameWithType> objektu a žádný pokus o volání metody na řetězec s hodnotou null způsobí <xref:System.NullReferenceException> . V zřetězení a porovnávání operací s jinými řetězci však můžete použít řetězce s hodnotou null. Následující příklady ilustrují některé případy, ve kterých je odkaz na řetězec s hodnotou null, a nezpůsobí vyvolání výjimky:  
  
 [!code-csharp[csProgGuideStrings#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#20)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Použití StringBuilder pro rychlé vytváření řetězců  
 Operace s řetězci v rozhraní .NET jsou vysoce optimalizované a ve většině případů významně neovlivňují výkon. V některých scénářích, jako jsou například těsné smyčky, které spouštějí mnoho stovek nebo tisíců, můžou operace s řetězci ovlivnit výkon. <xref:System.Text.StringBuilder>Třída vytvoří vyrovnávací paměť řetězců, která nabízí lepší výkon, pokud program provádí mnoho manipulace s řetězci. <xref:System.Text.StringBuilder>Řetězec také umožňuje změnit přiřazení jednotlivých znaků, a to něco, co vestavěný datový typ String nepodporuje. Tento kód například změní obsah řetězce bez vytvoření nového řetězce:  
  
 [!code-csharp[csProgGuideStrings#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#15)]  
  
 V tomto příkladu <xref:System.Text.StringBuilder> se k vytvoření řetězce ze sady číselných typů používá objekt:  
  
 [!code-csharp[TestStringBuilder#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/TestStringBuilder.cs)]
  
## <a name="strings-extension-methods-and-linq"></a>Řetězce, rozšiřující metody a LINQ  
 Vzhledem k tomu <xref:System.String> , že typ implementuje <xref:System.Collections.Generic.IEnumerable%601> , můžete použít metody rozšíření definované ve <xref:System.Linq.Enumerable> třídě na řetězcích. Aby se zabránilo vizuálnímu zbytečným, jsou tyto metody z technologie IntelliSense pro daný typ vyloučeny <xref:System.String> , ale jsou však k dispozici. Výrazy dotazů LINQ můžete použít také pro řetězce. Další informace naleznete v tématu [LINQ and Strings](../concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Jak změnit obsah řetězce](../../how-to/modify-string-contents.md)|Ukazuje techniky pro transformaci řetězců a úpravu obsahu řetězců.|  
|[Jak porovnat řetězce](../../how-to/compare-strings.md)|Ukazuje, jak provádět porovnání s ordinálními a konkrétní jazykovou verzí řetězců.|  
|[Jak zřetězit více řetězců](../../how-to/concatenate-multiple-strings.md)|Ukazuje různé způsoby, jak připojit více řetězců k jednomu.|
|[Jak analyzovat řetězce pomocí String. Split](../../how-to/parse-strings-using-split.md)|Obsahuje příklady kódu, které ilustrují, jak použít `String.Split` metodu k analýze řetězců.|  
|[Jak hledat řetězce](../../how-to/search-strings.md)|Vysvětluje, jak používat hledání určitého textu nebo vzorů v řetězcích.|  
|[Jak určit, jestli řetězec představuje číselnou hodnotu](./how-to-determine-whether-a-string-represents-a-numeric-value.md)|Ukazuje, jak bezpečně analyzovat řetězec, abyste viděli, zda má platnou číselnou hodnotu.|  
|[Interpolace řetězců](../../language-reference/tokens/interpolated.md)|Popisuje funkci interpolace řetězce, která poskytuje pohodlný Syntax pro formátování řetězců.|
|[Základní operace s řetězci](../../../standard/base-types/basic-string-operations.md)|Obsahuje odkazy na témata, která <xref:System.String?displayProperty=nameWithType> používají <xref:System.Text.StringBuilder?displayProperty=nameWithType> metody a k provádění základních operací s řetězci.|  
|[Analýza řetězců](../../../standard/base-types/parsing-strings.md)|Popisuje, jak převést řetězcové reprezentace základních typů .NET na instance odpovídajících typů.|  
|[Analýza řetězců data a času v .NET](../../../standard/base-types/parsing-datetime.md)|Ukazuje, jak převést řetězec, například "01/24/2008" na <xref:System.DateTime?displayProperty=nameWithType> objekt.|  
|[Porovnávání řetězců](../../../standard/base-types/comparing.md)|Obsahuje informace o tom, jak porovnat řetězce a poskytuje příklady v jazyce C# a Visual Basic.|  
|[Používání třídy StringBuilder](../../../standard/base-types/stringbuilder.md)|Popisuje, jak vytvořit a upravit dynamické objekty řetězce pomocí <xref:System.Text.StringBuilder> třídy.|  
|[LINQ a řetězce](../concepts/linq/linq-and-strings.md)|Poskytuje informace o tom, jak provádět různé řetězcové operace pomocí dotazů LINQ.|  
|[Průvodce programováním v C#](../index.md)|Obsahuje odkazy na témata, která vysvětlují programovací konstrukce v jazyce C#.|  
