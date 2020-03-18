---
title: C# Kódovací konvence – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 77b173a420f26834855e0bdca3c8d04406ac65d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399733"
---
# <a name="c-coding-conventions-c-programming-guide"></a>Převody kódování C# (Průvodce programováním v C#)

Kódovací konvence slouží následujícím účelům:  
  
- Vytvářejí konzistentní vzhled kódu, takže čtenáři se mohou soustředit na obsah, nikoli na rozložení.  
  
- Umožňují čtenářům pochopit kód rychleji tím, že předpoklady na základě předchozích zkušeností.  
  
- Usnadňují kopírování, změnu a údržbu kódu.  
  
- Předváděte osvědčené postupy jazyka C#.  

Pokyny v tomto článku používají společnost Microsoft k vývoji ukázek a dokumentace.  
  
## <a name="naming-conventions"></a>Konvence vytváření názvů  
  
- V krátkých příkladech, které nezahrnují [použití direktiv](../../language-reference/keywords/using-directive.md), použijte kvalifikace oboru názvů. Pokud víte, že obor názvů je importován ve výchozím nastavení v projektu, není třeba plně kvalifikovat názvy z tohoto oboru názvů. Kvalifikované názvy mohou být přerušeny po tečka (.), pokud jsou příliš dlouhé pro jeden řádek, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- Není třeba měnit názvy objektů, které byly vytvořeny pomocí nástrojů aplikace Visual Studio návrháře, aby byly vhodné pro jiné pokyny.  
  
## <a name="layout-conventions"></a>Konvence rozložení  

Dobré rozložení používá formátování ke zdůraznění struktury kódu a k usnadnění čtení kódu. Příklady a ukázky společnosti Microsoft odpovídají následujícím konvencím:  
  
- Použijte výchozí nastavení Editoru kódu (inteligentní odsazení, čtyřmístné odsazení, karty uložené jako mezery). Další informace naleznete v [tématu Možnosti, Textový editor, C#, Formátování](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
- Napište pouze jeden příkaz na řádek.  
  
- Napište pouze jednu deklaraci na řádek.  
  
- Pokud řádky pokračování nejsou odsazeny automaticky, odsaďte je o jednu zarážku tabulátoru (čtyři mezery).  
  
- Přidejte alespoň jeden prázdný řádek mezi definice metody a definice vlastností.  
  
- Pomocí závorek můžete klauzule ve výrazu zdánlivě zjevit, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Konvence při psaní komentářů  
  
- Umístěte komentář na samostatný řádek, nikoli na konec řádku kódu.  
  
- Začněte text komentáře s velkými písmeny.  
  
- Ukončit text komentáře tečkou  
  
- Vložte jednu mezeru mezi oddělovač poznámek (//) a text komentáře, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- Nevytvářejte formátované bloky hvězdiček kolem komentářů.  
  
## <a name="language-guidelines"></a>Pokyny pro jazyk  

Následující části popisují postupy, které tým C# následuje připravit příklady kódu a ukázky.  
  
### <a name="string-data-type"></a>Datový typ String  
  
- Pomocí [interpolace řetězců](../../language-reference/tokens/interpolated.md) zřetězete krátké řetězce, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- Chcete-li připojit řetězce ve smyčkách, zejména při práci <xref:System.Text.StringBuilder> s velkým množstvím textu, použijte objekt.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Implicitně typované lokální proměnné  
  
- [Implicitní psaní](../classes-and-structs/implicitly-typed-local-variables.md) pro místní proměnné, pokud je typ proměnné zřejmý z pravé strany přiřazení nebo pokud přesný typ není důležitý.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- Nepoužívejte [var,](../../language-reference/keywords/var.md) pokud typ není zřejmý z pravé strany přiřazení.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- Nespoléhejte na název proměnné k určení typu proměnné. Možná to není správné.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- Vyhněte `var` se použití místo [dynamického](../../language-reference/builtin-types/reference-types.md).  
  
- Implicitní psaní slouží k určení typu proměnné smyčky v [pro](../../language-reference/keywords/for.md) smyčky.  
  
     Následující příklad používá implicitní `for` psaní v příkazu.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- Nepoužívejte implicitní psaní k určení typu proměnné smyčky v [foreach](../../language-reference/keywords/foreach-in.md) smyčky.

     Následující příklad používá explicitní psaní `foreach` v příkazu.

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > Dávejte pozor, abyste omylem nezměnili typ prvku iterable kolekce. Například je snadné přepnout <xref:System.Linq.IQueryable?displayProperty=nameWithType> <xref:System.Collections.IEnumerable?displayProperty=nameWithType> z `foreach` v příkazu, který změní provádění dotazu.

### <a name="unsigned-data-type"></a>Nepodepsaný datový typ  
  
Obecně používejte `int` spíše než nepodepsané typy. Použití `int` je běžné v celém c#, a je snazší komunikovat `int`s jinými knihovnami při použití .  
  
### <a name="arrays"></a>Pole  
  
Při inicializaci polí na řádku deklarace použijte stručnou syntaxi.  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Delegáty  
  
Pomocí stručné syntaxe můžete vytvářet instance typu delegáta.  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>Zpracování výjimek s použitím příkazů try-catch a using  
  
- Pro většinu zpracování výjimek použijte příkaz [try-catch.](../../language-reference/keywords/try-catch.md)  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- Zjednodušte kód pomocí [příkazu](../../language-reference/keywords/using-statement.md)C# using . Pokud máte [příkaz try-finally,](../../language-reference/keywords/try-finally.md) ve kterém `finally` je jediným kódem <xref:System.IDisposable.Dispose%2A> v bloku `using` volání metody, použijte příkaz.  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>&& a &#124;&#124; operátory  
  
Chcete-li se vyhnout výjimkám a zvýšit [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) výkon [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) přeskočením zbytečných porovnání, použijte místo a [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) místo [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) při provádění porovnání, jak je znázorněno v následujícím příkladu.  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>Operátor new  
  
- Použijte stručnou formu instance objektu s implicitním psaním, jak je znázorněno v následujícím prohlášení.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     Předchozí řádek je ekvivalentní následující prohlášení.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- Ke zjednodušení vytváření objektů použijte inicializátory objektů.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Zpracování událostí  
  
Pokud definujete obslužnou rutinu události, kterou není nutné později odebrat, použijte výraz lambda.  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Statické členy  
  
Volání [statických](../../language-reference/keywords/static.md) členů pomocí názvu třídy: *ClassName.StaticMember*. Tento postup umožňuje kód čitelnější tím, že statický přístup jasné.  Nekvalifikujte statický člen definovaný v základní třídě s názvem odvozené třídy.  Zatímco tento kód zkompiluje, čitelnost kódu je zavádějící a kód může přerušit v budoucnu, pokud přidáte statický člen se stejným názvem do odvozené třídy.  
  
### <a name="linq-queries"></a>Dotazy LINQ  
  
- Pro proměnné dotazu použijte smysluplné názvy. Následující příklad `seattleCustomers` používá pro zákazníky, kteří se nacházejí v Seattlu.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Pomocí aliasů se ujistěte, že názvy vlastností anonymních typů jsou správně velkými písmeny pomocí pascalu.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- Přejmenujte vlastnosti, pokud by názvy vlastností ve výsledku byly nejednoznačné. Například pokud dotaz vrátí jméno zákazníka a ID distributora, `ID` namísto jejich ponechání jako `Name` `Name` a ve výsledku, `ID` přejmenujte je, aby bylo jasné, že je jméno zákazníka a je ID distributora.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- Použijte implicitní psaní v deklaraci proměnných dotazu a proměnných rozsahu.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Zarovnejte klauzule dotazu pod klauzulí [from,](../../language-reference/keywords/from-clause.md) jak je znázorněno v předchozích příkladech.  
  
- Použijte [kde](../../language-reference/keywords/where-clause.md) klauzule před jiné klauzule dotazu k zajištění, že novější klauzule dotazu pracovat na redukované, filtrované sadu dat.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- Použijte `from` více klauzulí namísto [join](../../language-reference/keywords/join-clause.md) klauzule pro přístup k vnitřní kolekce. Například kolekce `Student` objektů může obsahovat kolekci výsledků testu. Při spuštění následujícího dotazu vrátí každé skóre, které je starší 90, spolu s příjmením studenta, který obdržel skóre.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Zabezpečení  

Postupujte podle pokynů v [pokynech pro bezpečné kódování](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Viz také

- [Visual Basic – konvence kódování](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [Pokyny pro zabezpečené kódování](../../../standard/security/secure-coding-guidelines.md)
