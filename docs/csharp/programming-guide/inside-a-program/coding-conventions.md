---
title: C#Konvence – kódování C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 598f0e75a96a43162d0c626d00320effb418c7fd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241428"
---
# <a name="c-coding-conventions-c-programming-guide"></a>Převody kódování C# (Průvodce programováním v C#)
 Konvence kódování slouží k následujícím účelům:  
  
-   Vytváření konzistentního vzhledu na kód, tak, aby se čtenáři mohli soustředit na obsah ne na rozložení.  
  
-   Umožňují uživatelům pochopit kód rychleji odhad na základě předchozích zkušeností.  
  
-   Usnadňují kopírování, změna a údržba kódu.  
  
-   Vysvětlují, C# osvědčené postupy.  

 Pokyny v tomto tématu se používá společnost Microsoft pro vývoj ukázky a dokumentaci.  
  
## <a name="naming-conventions"></a>Zásady vytváření názvů  
  
-   V krátké příklady, které neobsahují [direktiv using](../../../csharp/language-reference/keywords/using-directive.md), použijte kvalifikaci oboru názvů. Pokud víte, že je ve výchozím nastavení v projektu importován oboru názvů, není nutné k plnému určení názvů z daného oboru názvů. Kvalifikované názvy může být přerušeno za tečku (.) Pokud jsou příliš dlouhé pro jeden řádek, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   Nemusíte změnit názvy objektů, které byly vytvořeny pomocí návrhářské nástroje Visual Studio, aby se daly přizpůsobit další pokyny.  
  
## <a name="layout-conventions"></a>Konvence rozložení  
 Dobré rozložení používá formátování zvýraznit struktury kódu a aby byl kód lépe čitelný. Microsoft příkladů a ukázek splňovat následující konvence:  
  
-   Použijte výchozí nastavení editoru kódu (inteligentní odsazení, čtyřmístný odsazení, uložení jako mezery tabulátory). Další informace najdete v tématu [možnosti, textový Editor, C#, formátování vzorků](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
-   Zapište pouze jeden příkaz na každém řádku.  
  
-   Zapisovat pouze jednu deklaraci na každém řádku.  
  
-   Pokud nejsou pokračovací řádky automaticky odsazený, odsazení, je o jednu zarážku tabulátoru (čtyři mezery).  
  
-   Přidejte alespoň jeden prázdný řádek mezi definice metod a definicích vlastností.  
  
-   Chcete-li klauzule ve výrazu je zřejmé, jak je znázorněno v následujícím kódu pomocí závorek.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Konvence při psaní komentářů  
  
-   Místo komentář na samostatném řádku, není na konci řádku kódu.  
  
-   Zahájit text komentáře velkým písmenem.  
  
-   Ukončit komentář tečkou.  
  
-   Vložte jednu mezeru mezi oddělovač komentáře (/ /) a text komentáře, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   Nevytvářejte hvězdičky z obou stran kolem komentářů formátované bloky.  
  
## <a name="language-guidelines"></a>Pokyny pro jazyk  
 Následující části popisují postupy, které tým C# následujících pokynů můžete připravit příklady kódu a ukázky.  
  
### <a name="string-data-type"></a>Datový typ String  
  
-   Použití [interpolace](../../language-reference/tokens/interpolated.md) ke zřetězení krátké řetězce, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   Pro přidání řetězce ve smyčkách, zejména v případě, že pracujete s velkého množství textu, použijte <xref:System.Text.StringBuilder> objektu.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Implicitně typované lokální proměnné  
  
-   Použití [implicitního zápisu](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) pro místní proměnné, když je typ proměnné zřejmý z pravé strany přiřazení, nebo pokud přesný typ není důležité.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   Nepoužívejte [var](../../../csharp/language-reference/keywords/var.md) když typ není zřejmé z pravé strany přiřazení.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   Nespoléhejte na název proměnné k určení typu proměnné. Nemusí být správné.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   Nepoužívejte `var` místo [dynamické](../../../csharp/language-reference/keywords/dynamic.md).  
  
-   K určení typu proměnné smyčky v použití implicitního zápisu [pro](../../../csharp/language-reference/keywords/for.md) a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) smyčky.  
  
     Následující příklad používá implicitní psát `for` příkazu.  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     Následující příklad používá implicitní psát `foreach` příkazu.  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a>Nepodepsaný datový typ  
  
-   Obecně platí, `int` místo typů bez znaménka. Použití `int` je běžné v C#, a je jednodušší pracovat s dalšími knihovnami, při použití `int`.  
  
### <a name="arrays"></a>Pole  
  
-   Pomocí stručnější syntaxe, když inicializujete pole v řádku deklarace.  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Delegáty  
  
-   Pomocí stručnější syntaxe pro vytvoření instancí typu delegáta.  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>Zpracování výjimek s použitím příkazů try-catch a using  
  
-   Použití [bloku try-catch](../../../csharp/language-reference/keywords/try-catch.md) příkaz pro většinu zpracování výjimek.  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   Zjednodušení kódu pomocí jazyka C# [příkaz using](../../../csharp/language-reference/keywords/using-statement.md). Pokud máte [try-finally](../../../csharp/language-reference/keywords/try-finally.md) příkazu, ve kterém pouze kód v `finally` blok je volání <xref:System.IDisposable.Dispose%2A> metody, použijte `using` příkaz místo toho.  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>& & a &#124; &#124; operátory  
  
-   Pokud chcete zabránit výjimky a zvýšit výkon přeskočením zbytečné porovnání, použijte [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) místo [ & ](../../../csharp/language-reference/operators/and-operator.md) a [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)místo [ &#124; ](../../../csharp/language-reference/operators/or-operator.md) při provádění porovnání, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>Operátor new  
  
-   Pomocí Stručná forma vytváření instancí objektu implicitního zápisu, jak je znázorněno v následující deklaraci.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     Předchozí řádek odpovídá následující deklarace.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   Používejte inicializátory objektů pro zjednodušení vytváření objektů.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Zpracování událostí  
  
-   Pokud definujete obslužnou rutinu události, která není potřeba později odebrat, použijte výraz lambda.  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Statické členy  
  
-   Volání [statické](../../../csharp/language-reference/keywords/static.md) členy pomocí názvu třídy: *ClassName.StaticMember*. Tento postup vytvoří kód lépe čitelný tím, že statická přístup zrušte.  Nekvalifikujte statické člena definovaného v základní třídě s názvem odvozené třídy.  Tento kód se zkompiluje, je zavádějící čitelnost kódu a kód může v budoucnu přerušit, pokud chcete přidat statický člen se stejným názvem do odvozené třídy.  
  
### <a name="linq-queries"></a>Dotazy LINQ  
  
-   Použijte smysluplné názvy proměnných dotazu. Následující příklad používá `seattleCustomers` pro zákazníky, kteří se nacházejí v Seattlu.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Ujistěte se, že názvy vlastností anonymních typů mají správnou velikost písmen, pomocí Pascal pomocí aliasů velká a malá písmena.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   Přejmenujte vlastnosti, pokud by názvy vlastností ve výsledku nejednoznačné. Například, pokud dotaz vrátí zákazníka, název a ID distributora, nenechávejte jako `Name` a `ID` ve výsledku, je pro vysvětlení, že přejmenovat `Name` je název zákazníka, a `ID` je ID distributora.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   Použití implicitního zápisu v deklaraci proměnné dotazu a proměnných rozsahu.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Zarovnejte klauzule dotazu v [z](../../../csharp/language-reference/keywords/from-clause.md) klauzule, jak je znázorněno v předchozích příkladech.  
  
-   Použití [kde](../../../csharp/language-reference/keywords/where-clause.md) klauzule před další klauzule dotazu zajistit, aby pozdější klauzule dotazu pracovaly na snížení, filtrovat sadu data.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   Použití více `from` klauzule místo [spojení](../../../csharp/language-reference/keywords/join-clause.md) klauzuli pro přístup k vnitřních kolekcí. Například kolekce `Student` každý objekty mohou obsahovat kolekce skóre v testech. Při spuštění následující dotaz vrátí každý skóre, které je více než 90, spolu s příjmení studentů, kteří obdrželi skóre.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Zabezpečení  
 Postupujte podle pokynů v [zabezpečené kódování zásady](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Viz také

- [Visual Basic – konvence kódování](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
- [Pokyny pro zabezpečené kódování](../../../standard/security/secure-coding-guidelines.md)
