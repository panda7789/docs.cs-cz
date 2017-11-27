---
title: "Převody kódování C# (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84ddc2b3cebb6bad95f5076889de11f12624b4de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="c-coding-conventions-c-programming-guide"></a>Převody kódování C# (Průvodce programováním v C#)
[Specifikace jazyka C#](http://go.microsoft.com/fwlink/?LinkId=199552) nedefinuje kódování standard. Podle pokynů v tomto tématu jsou však použít společností Microsoft k vývoji ukázky a dokumentace.  
  
 Konvence psaní kódu slouží k následujícím účelům:  
  
-   Konzistentní vzhled kódu, vytvářejí tak, aby čtenáři můžou zaměřit na obsah, není rozložení.  
  
-   Umožňují uživatelům pochopit kód rychleji provede odhad založené na předchozí zkušenosti.  
  
-   Usnadnění jejich kopírování, změna a údržbě kód.  
  
-   Vysvětlují, C# osvědčené postupy.  
  
## <a name="naming-conventions"></a>Zásady vytváření názvů  
  
-   V krátké příklady, které neobsahují [pomocí direktiv](../../../csharp/language-reference/keywords/using-directive.md), použijte kvalifikaci oboru názvů. Pokud víte, že je ve výchozím nastavení v projektu naimportovat obor názvů, nemáte k plnému určení názvy z daného oboru názvů. Kvalifikované názvy může být poškozená po tečku (.) Pokud jsou moc dlouhý na jeden řádek, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   Chcete-li změnit názvy objektů, které byly vytvořeny pomocí návrháře nástroje sady Visual Studio, aby byly podle dalších pokynů nemáte.  
  
## <a name="layout-conventions"></a>Konvence rozložení  
 Dobrý rozložení používá formátování zdůraznil struktura kódu a snadněji kód. Příklady Microsoft a ukázky splňovat následující konvence:  
  
-   Použijte výchozí nastavení editoru kódu (inteligentní odsazení, čtyř znaků odsazení, karty, které jsou uloženy jako prostory). Další informace najdete v tématu [možnosti, textový Editor, C#, formátování vzorků](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
-   Zapište pouze jeden příkaz na každém řádku.  
  
-   Zapsat jenom jedna deklarace na každý řádek.  
  
-   Pokud pokračování řádků nejsou automaticky odsazeny, je odsadit jedné karty zastavení (čtyři prostory).  
  
-   Přidejte alespoň jeden prázdný řádek mezi definice metod a vlastností definice.  
  
-   Závorky lze použijte k provádění klauzule ve výrazu je zřejmé, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Konvence při psaní komentářů  
  
-   Komentář umístíte na samostatném řádku, nikoli na konci řádku kódu.  
  
-   Začněte text poznámky s velkým písmenem.  
  
-   Ukončení text poznámky s tečkou.  
  
-   Vložit jeden mezer mezi oddělovač komentář (/ /) a text poznámky, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   Nevytvářejte formátovaný bloky hvězdičky kolem komentáře.  
  
## <a name="language-guidelines"></a>Pokyny pro jazyk  
 Následující části popisují postupy, které týmem C# následujících pokynů můžete připravit příklady kódu a ukázky.  
  
### <a name="string-data-type"></a>Datový typ String  
  
-   Použití `+` operátor ke zřetězení krátké řetězce, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   Chcete-li připojit řetězců v smyčky, zejména v případě, že pracujete s velkým množstvím textu, použijte <xref:System.Text.StringBuilder> objektu.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Implicitně typované lokální proměnné  
  
-   Použití [implicitní zadáním](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) pro místní proměnné, když je typ proměnné zřejmé z pravé strany přiřazení nebo přesné typ není důležité.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   Nepoužívejte [var](../../../csharp/language-reference/keywords/var.md) při typ není zřejmá z pravé strany přiřazení.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   Nespoléhejte na název proměnné určit typ proměnné. Nemusí být správný.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   Nepoužívejte `var` místě [dynamické](../../../csharp/language-reference/keywords/dynamic.md).  
  
-   Použít implicitní zadáním určit typ proměnné smyčky v [pro](../../../csharp/language-reference/keywords/for.md) a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) smyčky.  
  
     Následující příklad používá implicitní zadáním v `for` příkaz.  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     Následující příklad používá implicitní zadáním v `foreach` příkaz.  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a>Nepodepsaný datový typ  
  
-   Obecně platí, použijte `int` místo typy bez znaménka. Použití `int` je běžné v C#, a je jednodušší interakci s další knihovny při použití `int`.  
  
### <a name="arrays"></a>Pole  
  
-   Při inicializaci pole na ose deklarace, použijte stručným syntaxi.  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Delegáty  
  
-   Použijte stručným syntaxi pro vytvoření instance typu delegáta.  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>Zpracování výjimek s použitím příkazů try-catch a using  
  
-   Použití [try-catch –](../../../csharp/language-reference/keywords/try-catch.md) příkaz pro většinu zpracování výjimek.  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   Zjednodušení kódu s použitím jazyka C# [pomocí příkazu](../../../csharp/language-reference/keywords/using-statement.md). Pokud máte [try-finally –](../../../csharp/language-reference/keywords/try-finally.md) příkaz, ve kterém kód pouze v `finally` blok je volání <xref:System.IDisposable.Dispose%2A> metoda, použití `using` příkaz místo.  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>& & a &#124; &#124; Operátory  
  
-   Pokud chcete zabránit výjimky a zvyšuje výkon přeskočení nepotřebné porovnání, použijte [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) místo [ & ](../../../csharp/language-reference/operators/and-operator.md) a [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) místo [&#124;](../../../csharp/language-reference/operators/or-operator.md) při provádění porovnávání, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>Operátor new  
  
-   Použijte stručným formu konkretizaci objektu s implicitní zadáte, jak je znázorněno v následující prohlášení.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     Předchozí řádek je ekvivalentní následující deklaraci.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   Inicializátory objektů slouží ke zjednodušení vytváření objektů.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Zpracování událostí  
  
-   Pokud definujete obslužnou rutinu události, které není potřeba odebrat později, použijte výraz lambda.  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Statické členy  
  
-   Volání [statické](../../../csharp/language-reference/keywords/static.md) členy pomocí názvu třídy: *ClassName.StaticMember*. Tento postup umožňuje kód srozumitelnější tím, že statické přístup vymazat.  Statický člen definované v základní třídě s názvem odvozené třídy nemohou být.  Během tento kód zkompiloval, je zavádějící čitelnost kód a kód mohou končit v budoucnu, pokud přidáte do odvozené třídy je statický člen se stejným názvem.  
  
### <a name="linq-queries"></a>Dotazů LINQ  
  
-   Používejte smysluplný názvy proměnných dotazu. Následující příklad používá `seattleCustomers` pro zákazníky, kteří jsou umístěné v Ostravě.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Pomocí aliasy se ujistěte, že jsou názvy vlastností anonymní typů správně písmeno, a to pomocí Pascal velká a malá písmena.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   Přejmenujte vlastnosti názvy vlastností, které ve výsledku by být nejednoznačný. Například pokud dotaz vrátí zákazníka, název a ID distributora, místo necháte jako `Name` a `ID` ve výsledku, přejmenujte je o vysvětlení, že `Name` je název zákazníka, a `ID` je ID distributora.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   Použití implicitní zadáním v deklarace proměnné dotazu a proměnné rozsahu.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   Zarovnat klauzule dotazu v části [z](../../../csharp/language-reference/keywords/from-clause.md) klauzule, jak je znázorněno v předchozích příkladech.  
  
-   Použití [kde](../../../csharp/language-reference/keywords/where-clause.md) klauzule před další klauzule dotazu zajistit, že novější klauzule dotazu fungovat na menší, filtrovat sadu dat.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   Použití více `from` klauzule místo [spojení](../../../csharp/language-reference/keywords/join-clause.md) klauzule pro přístup k vnitřní kolekce. Například kolekce `Student` jednotlivých objektů může obsahovat kolekce výsledků testu. Po provedení následující dotaz vrátí každý skóre, který je více než 90, společně s poslední název studenty, kteří obdrželi skóre.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Zabezpečení  
 Postupujte podle pokynů v [pokyny zabezpečení kódování](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – konvence kódování](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 [Pokyny pro zabezpečené kódování](../../../standard/security/secure-coding-guidelines.md)
