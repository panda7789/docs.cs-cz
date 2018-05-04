---
title: Řetězce (Průvodce programováním v C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
caps.latest.revision: 41
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5a888440a76119eae7e4c525942878e0aa6ddafc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="strings-c-programming-guide"></a>Řetězce (Průvodce programováním v C#)
Řetězec se objekt typu <xref:System.String> jehož hodnota je text. Interně, je text uložený jako sekvenční jen pro čtení kolekce <xref:System.Char> objekty. Neexistuje žádné ukončení null znak na konci C# řetězec; řetězec jazyka C# proto může obsahovat libovolný počet vložené znaky null ('\0'). <xref:System.String.Length%2A> Vlastnost řetězce představuje počet `Char` objekty obsahuje, nikoli počet znaků Unicode. Chcete-li získat přístup k jednotlivé body kódu Unicode v řetězci, použijte <xref:System.Globalization.StringInfo> objektu.  
  
## <a name="string-vs-systemstring"></a>Řetězec vs. System.String  
 V jazyce C# `string` – klíčové slovo je alias <xref:System.String>. Proto `String` a `string` jsou ekvivalentní a můžete použít kteroukoli zásady vytváření názvů dáváte přednost. `String` Třída poskytuje mnoho způsobů pro bezpečně vytváření, manipulace a porovnávání řetězců. Kromě toho jazyka C# přetížení některé operátory zjednodušit běžné operace s řetězci. Další informace o klíčovém slově najdete v tématu [řetězec](../../../csharp/language-reference/keywords/string.md). Další informace o typu a její metody najdete v tématu <xref:System.String>.  
  
## <a name="declaring-and-initializing-strings"></a>Deklarace a inicializace řetězců  
 Můžete deklarace a inicializace řetězců různými způsoby, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#1](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_1.cs)]  
  
 Všimněte si, že použijete [nové](../../../csharp/language-reference/keywords/new-operator.md) operátoru pro vytvoření objektu řetězce s výjimkou při inicializaci řetězec s pole znaků.  
  
 Inicializuje řetězec s <xref:System.String.Empty> konstantní hodnota pro vytvoření nového <xref:System.String> objektu, na nichž je řetězec nulové délky. Řetězcová reprezentace literálu řetězec nulové délky je "". Podle inicializace řetězců s <xref:System.String.Empty> hodnotu místo [null](../../../csharp/language-reference/keywords/null.md), můžete snížit pravděpodobnost, <xref:System.NullReferenceException> ke kterým dochází. Použít statickou <xref:System.String.IsNullOrEmpty%28System.String%29> metoda ověření hodnoty řetězce, než se pokusí o přístup.  
  
## <a name="immutability-of-string-objects"></a>Neměnitelnosti řetězcových objektů  
 Řetězec objekty jsou *neměnné*: porty nelze změnit po jejich vytvoření. Všechny <xref:System.String> metody a operátory jazyka C#, které se zobrazují Upravit řetězec vracet výsledky v nový objekt řetězce. V následujícím příkladu když obsah `s1` a `s2` jsou zřetězeny k vytvoření jednoho řetězce, jsou dva původní řetězce beze změny. `+=` Operátor vytvoří nový řetězec, který obsahuje součet obsah. Tento nový objekt je přiřazen k proměnné `s1`a původní objekt, který byl přiřazen `s1` vydání pro uvolňování paměti, protože obsahuje odkaz na jeho žádné jiné proměnné.  
  
 [!code-csharp[csProgGuideStrings#2](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_2.cs)]  
  
 Protože je řetězec "modifikace" ve skutečnosti vytváření nového řetězec, musí se při vytvoření odkazů na řetězce buďte opatrní. Pokud vytvoříte odkaz na řetězec a potom "upravit" původního řetězce, odkaz bude tak, aby odkazoval na původní objekt místo nový objekt, který byl vytvořen při řetězec byla změněna. Následující kód ukazuje toto chování:  
  
 [!code-csharp[csProgGuideStrings#25](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_3.cs)]  
  
 Další informace o tom, jak vytváření nových řetězců, které jsou založené na změny, jako je hledání a nahrazovat operace u původního řetězce najdete v tématu [postupy: Změna obsahu řetězce](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Pravidelné a typu Verbatim textové literály  
 Používejte regulární řetězcové literály, když je nutné vložit řídicí znaky poskytované C#, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#3](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_4.cs)]  
  
 Používá typu verbatim řetězce pro usnadnění práce a lepší čitelnost textový řetězec musí obsahovat znaky zpětné lomítko, například v cestách k souborům. Protože typu verbatim řetězce zachovat znaky nového řádku jako součást textový řetězec, můžete použít k chybě při inicializaci Víceřádkový řetězce. Použijte uvozovky k vložení uvozovky uvnitř typu verbatim řetězec. Následující příklad ukazuje některé běžné používá pro typu verbatim řetězce:  
  
 [!code-csharp[csProgGuideStrings#4](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_5.cs)]  
  
## <a name="string-escape-sequences"></a>Řetězec řídicí sekvence  
  
|Řídicí sekvence|Název znaku|Kódování Unicode|  
|---------------------|--------------------|----------------------|  
|\\'|jednoduché uvozovky|0x0027|  
|\\"|dvojité uvozovky|0x0022|  
|\\\\ |Zpětné lomítko|0x005C|  
|\0|Null|0x0000|  
|\a|Výstrahy|0x0007|  
|\b|Backspace|0x0008|  
|\f|řídicí znak|0x000C|  
|\n|Nový řádek|0x000A|  
|\r|Návrat na začátek řádku|0x000D|  
|\t|Horizontální tabulátor|0x0009|  
|\U|Řídicí sekvence Unicode pro náhradní dvojice.|\Unnnnnnnn|  
|\u|Unicode – řídicí sekvence|\u0041 = "A"|  
|\v|Vertikální tabulátor|0x000B|  
|\x|Unicode – řídicí sekvence podobná "\u" kromě s proměnlivou délkou.|\x0041 = "A"|  
  
> [!NOTE]
>  Při kompilaci typu verbatim řetězce jsou převedeny na běžné řetězce s stejné řídicí sekvence. Proto pokud řetězec typu verbatim zobrazí v okně Sledování ladicí program, zobrazí se řídicí znaky, které byly přidány kompilátorem není typu verbatim verzi z vašeho zdrojového kódu. Například typu verbatim řetězec @"C:\files.txt" se zobrazí v okně sledovat jako "C:\\\files.txt".  
  
## <a name="format-strings"></a>Řetězce formátu  
 Formátovací řetězec je řetězec, jehož obsah můžete určit dynamicky za běhu. Vytvořit řetězec formátu pomocí statické <xref:System.String.Format%2A> metoda a vložení zástupné symboly v složené závorky, které budou nahrazeny další hodnoty za běhu. Následující příklad používá k vypsání výsledek každé iteraci smyčky řetězec formátu:  
  
 [!code-csharp[csProgGuideStrings#26](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_6.cs)]  
  
 Jedním přetížením <xref:System.Console.WriteLine%2A> metoda přebírá řetězec formátu jako parametr. Proto můžete vložit pouze formát řetězcový literál bez explicitní volání metody. Ale pokud používáte <xref:System.Diagnostics.Trace.WriteLine%2A> metodu pro zobrazení výstupu ladění v sadě Visual Studio **výstup** okna, je nutné explicitně volání <xref:System.String.Format%2A> – metoda protože <xref:System.Diagnostics.Trace.WriteLine%2A> přijímá pouze řetězec, řetězec formátu. Další informace o řetězce formátu najdete v tématu [typy formátování](../../../standard/base-types/formatting-types.md).  
  
## <a name="substrings"></a>Dílčích řetězců  
 Dílčí řetězec je posloupnost znaků, který je obsažen v řetězci. Použití <xref:System.String.Substring%2A> metodu pro vytvoření nového řetězce z části původního řetězce. Jeden nebo více výskytů dílčí řetězec můžete vyhledat pomocí <xref:System.String.IndexOf%2A> metoda. Použití <xref:System.String.Replace%2A> metodu pro nový řetězec nahraďte všechny výskyty je určený dílčí řetězec. Podobně jako <xref:System.String.Substring%2A> metody <xref:System.String.Replace%2A> ve skutečnosti vrátí nového řetězce a nedojde ke změně původního řetězce. Další informace najdete v tématu [postupy: vyhledávání řetězců](../../how-to/search-strings.md) a [postupy: Změna obsahu řetězce](../../how-to/modify-string-contents.md).  
  
 [!code-csharp[csProgGuideStrings#7](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_7.cs)]  
  
## <a name="accessing-individual-characters"></a>Přístup k jednotlivých znaků  
 Zápis pole s hodnotou indexu můžete použít se získat přístup jen pro čtení k jednotlivé znaky, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStrings#9](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_8.cs)]  
  
 Pokud <xref:System.String> metody neposkytují funkce, která je nutné upravit jednotlivé znaky v řetězci, můžete použít <xref:System.Text.StringBuilder> objektu upravit jednotlivé znaků "místní" a pak vytvořte nový řetězec můžete ukládat výsledky pomocí <xref:System.Text.StringBuilder> metody. V následujícím příkladu předpokládají, že musíte upravit původní řetězec určitým způsobem a potom uložte výsledky pro budoucí použití:  
  
 [!code-csharp[csProgGuideStrings#8](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_9.cs)]  
  
## <a name="null-strings-and-empty-strings"></a>Řetězce Null a prázdné řetězce  
 Prázdný řetězec je instance <xref:System.String?displayProperty=nameWithType> objekt, který obsahuje nulový počet znaků. Prázdné řetězce se často používají v různých situacích programovací představují prázdné textové pole. Můžete volat metody pro prázdné řetězce, protože jsou platné <xref:System.String?displayProperty=nameWithType> objekty. Prázdné řetězce jsou inicializovány následujícím způsobem:  
  
```  
string s = String.Empty;  
```  
  
 Naopak řetězec null není odkaz na instanci <xref:System.String?displayProperty=nameWithType> objekt a pokusy o volání metody na řetězec null příčiny <xref:System.NullReferenceException>. Můžete však použít řetězce null v zřetězení a operace porovnání s jiných řetězců. Následující příklady ilustrují některých případech, ve kterých odkaz na řetězec null nemá a nedojde k vyvolání výjimky:  
  
 [!code-csharp[csProgGuideStrings#27](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_10.cs)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Pro vytvoření rychlé řetězců pomocí StringBuilder  
 Operace s řetězci v .NET jsou vysoce optimalizovaný a ve většině případů není mít výrazný vliv na výkon. V některých případech, například úzkou cykly, které jsou prováděny mnoho stovkami nebo tisíci časy, ale operace s řetězci může ovlivnit výkon. <xref:System.Text.StringBuilder> Třída vytvoří řetězec vyrovnávací paměť, která nabízí lepší výkon, pokud váš program provádí mnoho manipulace s řetězci. <xref:System.Text.StringBuilder> Řetězec také umožňuje přiřadit jednotlivé znaky, něco předdefinované řetězec – datový typ není podporován. Tento kód, například změní obsah řetězec bez vytvoření nového řetězce:  
  
 [!code-csharp[csProgGuideStrings#20](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_11.cs)]  
  
 V tomto příkladu <xref:System.Text.StringBuilder> objekt se používá k vytvoření řetězce z sadu číselnými typy:  
  
 [!code-csharp[csProgGuideStrings#15](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_12.cs)]  
  
## <a name="strings-extension-methods-and-linq"></a>Řetězce, metod rozšíření a LINQ  
 Protože <xref:System.String> zadejte implementuje <xref:System.Collections.Generic.IEnumerable%601>, můžete použít rozšíření metody definované v <xref:System.Linq.Enumerable> třída řetězce. Abyste se vyhnuli visual zbytečné soubory, tyto metody jsou vyloučeny z IntelliSense pro <xref:System.String> typu, ale jsou nicméně k dispozici. Můžete také použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazy řetězce dotazu. Další informace najdete v tématu [LINQ a řetězce](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Postupy: Změna obsahu řetězce](../../how-to/modify-string-contents.md)|Ukázky postupů k transformaci řetězce a upravovat obsah řetězce.|  
|[Postupy: Porovnávání řetězců](../../how-to/compare-strings.md)|Ukazuje, jak provést pořadí a jazykovou verzi konkrétní porovnání hodnot řetězců.|  
|[Postupy: Zřetězení více řetězců](../../how-to/concatenate-multiple-strings.md)|Ukazuje různé způsoby, jak připojit více řetězce do jednoho.|
|[Postupy: Analýza řetězců využívajících String.Split ](../../how-to/parse-strings-using-split.md)|Obsahuje příklady kódu, které ukazují, jak používat `String.Split` metoda analyzovat řetězce.|  
|[Postupy: vyhledávání řetězců](../../how-to/search-strings.md)|Vysvětluje, jak používat v řetězcích vyhledávání pro určitý text nebo vzory.|  
|[Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|Ukazuje, jak bezpečně analyzovat řetězec a zjistěte, zda má platnou číselnou hodnotu.|  
|[Interpolace řetězců](../../language-reference/tokens/interpolated.md)|Popisuje funkci interpolace řetězec, který poskytuje pohodlné syntaxe do řetězce formátu.|
|[Základní operace s řetězci](../../../../docs/standard/base-types/basic-string-operations.md)|Obsahuje odkazy na témata, které používají <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> metody k provedení základní operace s řetězci.|  
|[Analýza řetězců](../../../standard/base-types/parsing-strings.md)|Popisuje, jak převést řetězcové vyjádření základních typů .NET instancí odpovídající typy.|  
|[Analýza řetězců data a času v rozhraní .NET](../../../standard/base-types/parsing-datetime.md)|Ukazuje, jak převést řetězec jako je například "01/24/2008" k <xref:System.DateTime?displayProperty=nameWithType> objektu.|  
|[Porovnávání řetězců](../../../../docs/standard/base-types/comparing.md)|Obsahuje informace o tom, jak porovnat řetězce a příklady v C# a Visual Basic.|  
|[Používání třídy StringBuilder](../../../standard/base-types/stringbuilder.md)|Popisuje, jak vytvořit a upravit objekty dynamického řetězce pomocí <xref:System.Text.StringBuilder> třídy.|  
|[LINQ a řetězce](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)|Poskytuje informace o tom, jak provádět různé operace s řetězci pomocí dotazů LINQ.|  
|[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)|Obsahuje odkazy na témata, která popisují programovací konstrukce v jazyce C#.|  
