---
title: C#Konvence kódování C# – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 77b173a420f26834855e0bdca3c8d04406ac65d4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452003"
---
# <a name="c-coding-conventions-c-programming-guide"></a>Převody kódování C# (Průvodce programováním v C#)

Konvence kódování slouží k následujícím účelům:  
  
- Vytvářejí konzistentní vzhled kódu, aby se čtenáři mohli soustředit na obsah, nikoli na rozložení.  
  
- Umožňují čtenářům lépe pochopit kód tím, že se na základě předchozích zkušeností vydávají předpoklady.  
  
- Usnadňují kopírování, změny a údržbu kódu.  
  
- Ukazují C# osvědčené postupy.  

Pokyny v tomto článku používá společnost Microsoft k vývoji ukázek a dokumentace.  
  
## <a name="naming-conventions"></a>Konvence vytváření názvů  
  
- V krátkých příkladech, které neobsahují [direktivy using](../../language-reference/keywords/using-directive.md), použijte kvalifikaci oboru názvů. Pokud víte, že je ve výchozím nastavení v projektu importován obor názvů, nemusíte plně kvalifikovat názvy z tohoto oboru názvů. Kvalifikované názvy mohou být porušeny za tečku (.), pokud jsou příliš dlouhé pro jeden řádek, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- Nemusíte měnit názvy objektů, které byly vytvořeny pomocí nástrojů návrháře sady Visual Studio, aby vyhovovaly jiným pokynům.  
  
## <a name="layout-conventions"></a>Konvence rozložení  

Dobrá rozložení používá formátování k zdůraznění struktury kódu a k usnadnění čtení kódu. Příklady a ukázky společnosti Microsoft splňují následující konvence:  
  
- Použijte výchozí nastavení editoru kódu (inteligentní odrážky, odsazení čtyř znaků, tabulátory uložené jako mezery). Další informace naleznete v tématu [Možnosti, textový editor, C#formátování](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
- Zapsat pouze jeden příkaz na řádek.  
  
- Zapsat pouze jednu deklaraci na řádek.  
  
- Pokud nejsou řádky pro pokračování automaticky odsazeny, odsadíte je o jednu zarážku tabulátoru (čtyři mezery).  
  
- Přidejte alespoň jeden prázdný řádek mezi definice metody a definice vlastností.  
  
- Použijte závorky k vytvoření klauzulí ve výrazu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Konvence při psaní komentářů  
  
- Komentář umístěte na samostatný řádek, nikoli na konci řádku kódu.  
  
- Začněte text komentáře velkým písmenem.  
  
- Konec textu komentáře s tečkou  
  
- Vložte jednu mezeru mezi oddělovač komentáře (//) a text komentáře, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- Nevytvářejte formátované bloky hvězdiček kolem komentářů.  
  
## <a name="language-guidelines"></a>Pokyny pro jazyk  

Následující části popisují postupy, které C# tým sleduje pro přípravu příkladů kódu a ukázek.  
  
### <a name="string-data-type"></a>Datový typ String  
  
- Použijte [interpolaci řetězce](../../language-reference/tokens/interpolated.md) k zřetězení krátkých řetězců, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- Pro připojení řetězců ve smyčce, zejména při práci s velkým množstvím textu, použijte objekt <xref:System.Text.StringBuilder>.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Implicitně typované lokální proměnné  
  
- Použijte [implicitní psaní](../classes-and-structs/implicitly-typed-local-variables.md) pro lokální proměnné, pokud je typ proměnné zjevný z pravé strany přiřazení, nebo pokud přesný typ není důležitý.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- Nepoužívejte [var](../../language-reference/keywords/var.md) v případě, že typ není na pravé straně přiřazení zřejmý.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- Nespoléhá na název proměnné, abyste určili typ proměnné. Nemusí být správné.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- Vyhněte se použití `var` místo [dynamického](../../language-reference/builtin-types/reference-types.md).  
  
- Pomocí implicitního zápisu určete typ proměnné smyčky v [pro smyčky for](../../language-reference/keywords/for.md) .  
  
     Následující příklad používá implicitní zadání v příkazu `for`.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- Nepoužívejte implicitní typování k určení typu proměnné smyčky ve smyčce [foreach](../../language-reference/keywords/foreach-in.md) .

     Následující příklad používá explicitní psaní do příkazu `foreach`.

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > Buďte opatrní, aby nedošlo k náhodné změně typu prvku kolekce ITER. Například je snadné přepnout z <xref:System.Linq.IQueryable?displayProperty=nameWithType> na <xref:System.Collections.IEnumerable?displayProperty=nameWithType> v příkazu `foreach`, který změní spuštění dotazu.

### <a name="unsigned-data-type"></a>Nepodepsaný datový typ  
  
Obecně použijte `int` spíše než typy bez znaménka. Použití `int` je běžné v celém C#a při použití `int`je snazší pracovat s ostatními knihovnami.  
  
### <a name="arrays"></a>Pole  
  
Použijte stručnou syntaxi při inicializaci polí na řádku deklarace.  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Delegáty  
  
K vytvoření instancí typu delegáta použijte stručnou syntaxi.  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>Zpracování výjimek s použitím příkazů try-catch a using  
  
- Použijte příkaz [try-catch](../../language-reference/keywords/try-catch.md) pro většinu zpracování výjimek.  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- Zjednodušte svůj kód pomocí C# [příkazu Using](../../language-reference/keywords/using-statement.md). Pokud máte příkaz [try-finally](../../language-reference/keywords/try-finally.md) , ve kterém jediný kód v bloku `finally` je voláním metody <xref:System.IDisposable.Dispose%2A>, použijte místo toho příkaz `using`.  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>& & a &#124; &#124; operátory  
  
Aby nedocházelo k výjimkám a zvýšili výkon přeskočením zbytečných porovnání, použijte [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) namísto [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) a [ &#124; ](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) místo [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) při porovnávání, jak je znázorněno v následujícím příkladu.  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>Operátor new  
  
- Použijte stručnou formu instance objektu s implicitním zadáním, jak je znázorněno v následující deklaraci.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     Předchozí řádek je ekvivalentní následující deklaraci.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- K zjednodušení vytvoření objektu použijte Inicializátory objektů.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Zpracování událostí  
  
Pokud definujete obslužnou rutinu události, kterou nemusíte později odebrat, použijte výraz lambda.  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Statické členy  
  
Volejte [statické](../../language-reference/keywords/static.md) členy pomocí názvu třídy: *ClassName. StaticMember*. Tento postup usnadňuje čitelnost kódu tím, že provádí jasné zrušení statického přístupu.  Nekvalifikovat statický člen definovaný v základní třídě s názvem odvozené třídy.  Při kompilaci kódu je čitelnost kódu zavádějící a kód může být v budoucnu přerušen, pokud přidáte statický člen se stejným názvem do odvozené třídy.  
  
### <a name="linq-queries"></a>Dotazy LINQ  
  
- Pro proměnné dotazů použijte smysluplné názvy. Následující příklad používá `seattleCustomers` pro zákazníky nacházející se v Seattlu.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Použijte aliasy k zajištění správného kapitálu názvů vlastností anonymních typů pomocí malých a velkých písmen Pascal.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- Přejmenujte vlastnosti, pokud by názvy vlastností ve výsledku byly dvojznačné. Pokud například váš dotaz vrátí název zákazníka a ID distributora, nemusíte je opustit jako `Name` a `ID` ve výsledku, přejmenujte je, aby se vyjasnilo, že `Name` je název zákazníka, a `ID` je ID distributora.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- V deklaraci proměnných dotazu a proměnných rozsahu použijte implicitní zadání.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Zarovnat klauzule dotazu pod klauzulí [from](../../language-reference/keywords/from-clause.md) , jak je znázorněno v předchozích příkladech.  
  
- Pomocí klauzulí [WHERE](../../language-reference/keywords/where-clause.md) před jinými klauzulemi dotazu zajistěte, aby pozdější klauzule dotazu pracovaly na omezené a filtrované sadě dat.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- Pro přístup k vnitřním kolekcím použijte místo klauzule [Join](../../language-reference/keywords/join-clause.md) více klauzulí `from`. Například kolekce objektů `Student` může obsahovat kolekci hodnocení testů. Při spuštění následujícího dotazu vrátí všechny skóre, které je více než 90, spolu s posledním názvem studenta, který skóre přijal.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Zabezpečení  

Postupujte podle pokynů v části [zásady bezpečného kódování](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Viz také

- [Visual Basic konvence kódování](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [Pokyny pro zabezpečené kódování](../../../standard/security/secure-coding-guidelines.md)
