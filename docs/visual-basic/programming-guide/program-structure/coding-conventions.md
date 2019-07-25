---
title: Visual Basic – konvence kódování
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: 580a6e1caa78ea981b6d2be68a6e7c61e2ad55d7
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433814"
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic – konvence kódování
Společnost Microsoft vyvíjí ukázky a dokumentaci, které se řídí pokyny v tomto tématu. Pokud se řídíte stejnými konvencemi kódování, můžete získat následující výhody:  
  
- Váš kód bude mít konzistentní vzhled, aby se čtenáři mohli lépe soustředit na obsah, nikoli na rozložení.  
  
- Čtenáři porozuměli kódu rychleji, protože mohou vytvářet předpoklady na základě předchozích zkušeností.  
  
- Kód můžete snadněji kopírovat, měnit a udržovat.  
  
- Pomůžete zajistit, aby váš kód předvádí "osvědčené postupy" pro Visual Basic.  
  
## <a name="naming-conventions"></a>Konvence vytváření názvů  
  
- Informace o pokynech pro pojmenování najdete v tématu [pokyny](../../../standard/design-guidelines/naming-guidelines.md) pro pojmenování.  
  
- Nepoužívejte "my" nebo "my" jako součást názvu proměnné. Tento postup vytváří nejasnost s `My` objekty.  
  
- Nemusíte měnit názvy objektů v automaticky generovaném kódu, aby se vešly podle pokynů.  
  
## <a name="layout-conventions"></a>Konvence rozložení  
  
- Vložte tabulátory jako mezery a používejte inteligentní odsazení se čtyřmi mezerami.  
  
- Použijte k přeformátování kódu v editoru kódu formátování (přeformátování **)** . Další informace najdete v tématu [Možnosti, textový editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
- Použijte pouze jeden příkaz na řádek. Nepoužívejte znak oddělovače Visual Basic čáry (:).  
  
- Vyhněte se použití znaku explicitního pokračování řádku "_" místo implicitního pokračování řádku, kdykoli to jazyk umožňuje.  
  
- Použijte pouze jednu deklaraci na řádek.  
  
- Pokud je **v podstatě výpis (přeformátování) kódu** neformátované řádky pokračování automaticky, odsadí řádky pokračování jednu zarážku tabulátoru. V seznamu ale vždycky zarovnáváme položky vlevo.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
- Mezi definice metod a vlastností přidejte alespoň jeden prázdný řádek.  
  
## <a name="commenting-conventions"></a>Konvence při psaní komentářů  
  
- Komentáře umístěte na samostatný řádek místo na konci řádku kódu.  
  
- Začněte text komentáře velkým písmenem a ukončete text komentáře s tečkou.  
  
- Vložte jednu mezeru mezi oddělovač komentáře (') a text komentáře.  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- Nezadávejte komentáře pomocí formátovaných bloků hvězdiček.  
  
## <a name="program-structure"></a>Struktura programu  
  
- Při použití `Main` metody použijte výchozí konstrukci pro nové konzolové aplikace a použijte `My` pro argumenty příkazového řádku.  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a>Pokyny pro jazyk  
  
### <a name="string-data-type"></a>Datový typ String  
  
- Použijte [interpolaci řetězce](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings) k zřetězení krátkých řetězců, jak je znázorněno v následujícím kódu.
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- Chcete-li připojit řetězce ve smyčce, použijte <xref:System.Text.StringBuilder> objekt.  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Odlehčení Delegáti v obslužných rutinách událostí  
 Explicitně nekvalifikovat argumenty (Object a EventArgs) pro obslužné rutiny událostí. Pokud nepoužíváte argumenty události, které jsou předány události (například odesilatel jako objekt, e jako EventArgs), použijte odlehčené delegáty a vynechte argumenty události v kódu:  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a>Nepodepsaný datový typ  
  
- Použijte `Integer` spíše než typy bez znaménka, s výjimkou případů, kdy jsou nezbytné.  
  
### <a name="arrays"></a>Pole  
  
- Použijte krátkou syntaxi při inicializaci polí na řádku deklarace. Použijte například následující syntaxi.  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     Nepoužívejte následující syntaxi.  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- Uveďte označení pole pro typ, nikoli proměnnou. Použijte například následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     Nepoužívejte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- Použijte syntaxi {} při deklaraci a inicializaci polí základních datových typů. Použijte například následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     Nepoužívejte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a>Použití klíčového slova with  
 Při vytváření řady volání jednoho objektu zvažte použití `With` klíčového slova:  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Použijte try... Zachytit a použít příkazy při zpracování výjimek  
 Nepoužívejte `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Použití klíčového slova IsNot  
 Místo použijte `IsNot` klíčové slovo `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>New – klíčové slovo  
  
- Používejte krátkodobé vytváření instancí. Použijte například následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     Předchozí řádek je podobný tomuto:  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- Použít inicializátory objektů pro nové objekty místo konstruktoru bez parametrů:  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a>Zpracování událostí  
  
- `Handles` Použijte`AddHandler`místo:  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- Použijte `AddressOf`, a nevytvářejte instanci delegáta explicitně:  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- Při definování události použijte krátkou syntaxi a nechejte kompilátor definovat delegáta:  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- Neověřuje, zda je `Nothing` událost (null) před `RaiseEvent` voláním metody. `RaiseEvent`zkontroluje, `Nothing` než se událost vyvolá.  
  
### <a name="using-shared-members"></a>Použití sdílených členů  
 Volejte `Shared` členy pomocí názvu třídy, nikoli z proměnné instance.  
  
### <a name="use-xml-literals"></a>Použití literálů XML  
 Literály XML zjednodušují nejběžnější úlohy, které se vyskytnou při práci s XML (například načtení, dotazování a transformace). Při vývoji s jazykem XML postupujte podle těchto pokynů:  
  
- Použijte literály XML k vytvoření dokumentů a fragmentů XML namísto přímého volání rozhraní API XML.  
  
- Importujte obory názvů XML na úrovni souboru nebo projektu, abyste mohli využívat optimalizace výkonu pro literály XML.  
  
- Použijte Vlastnosti osy XML pro přístup k prvkům a atributům v dokumentu XML.  
  
- Vložené výrazy použijte k zahrnutí hodnot a k vytvoření XML z existujících hodnot namísto použití volání rozhraní API, jako je `Add` například metoda:  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a>Dotazy LINQ  
  
- Pro proměnné dotazů použijte smysluplné názvy:  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- Zadejte názvy prvků v dotazu, abyste se ujistili, že názvy vlastností anonymních typů jsou správně velkými písmeny v jazyce Pascal:  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- Přejmenujte vlastnosti, pokud by názvy vlastností ve výsledku byly dvojznačné. Například pokud váš dotaz vrátí název zákazníka a ID objednávky, přejmenujte ho místo toho `Name` , aby a `ID` ve výsledku:  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- Použijte odvození typu v deklaraci proměnných dotazu a proměnných rozsahu:  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- Zarovnat klauzule dotazu pod `From` příkazem:  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- Klauzule `Where` použijte před ostatními klauzulemi dotazu tak, aby pozdější klauzule dotazu pracovaly na filtrované sadě dat:  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- Použijte klauzuli k explicitnímu definování operace spojení namísto `Where` použití klauzule k implicitnímu definování operace spojení: `Join`  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../standard/security/secure-coding-guidelines.md)
