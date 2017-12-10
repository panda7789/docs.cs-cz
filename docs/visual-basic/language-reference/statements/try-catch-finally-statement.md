---
title: "Try...Catch....Finally – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement [Visual Basic]
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement [Visual Basic], Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement [Visual Basic]
- When keyword [Visual Basic]
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
caps.latest.revision: "69"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56dd7fc339c452d64eb18211337b9a7674a83e1c
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch....Finally – příkaz (Visual Basic)
Poskytuje způsob, jak zpracovávat některé nebo všechny možné chyby, které mohou nastat v každém bloku kódu, při stále běhu kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Try  
    [ tryStatements ]  
    [ Exit Try ]  
[ Catch [ exception [ As type ] ] [ When expression ]  
    [ catchStatements ]  
    [ Exit Try ] ]  
[ Catch ... ]  
[ Finally  
    [ finallyStatements ] ]  
End Try  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`tryStatements`|Volitelné. Příkazy, kde může dojít k chybě. Může být složený příkaz.|  
|`Catch`|Volitelné. Více `Catch` bloky povolené. Pokud dojde k výjimce při zpracování `Try` blokovat, každý `Catch` v textové pořadí k určení, zda ji s ošetří výjimku, je zkontrolován příkaz `exception` představující výjimku, která byla vyvolána.|  
|`exception`|Volitelné. Libovolný název proměnné. Počáteční hodnota `exception` je hodnota této výjimce dojde chyby. Použít s `Catch` k určení chyba zachycena. Pokud tento parametr vynechán, `Catch` příkaz zachytí všechny výjimky.|  
|`type`|Volitelné. Určuje typ třídy filtru. Pokud hodnota `exception` je v typu zadaném pomocí `type` nebo odvozený typ se změní na identifikátor vázaná na objekt výjimky.|  
|`When`|Volitelné. A `Catch` příkaz s `When` klauzule zachytí výjimky pouze tehdy, když `expression` vyhodnocuje `True`. A `When` klauzule se použije pouze po zkontrolování typ výjimky, a `expression` mohou odkazovat na identifikátor reprezentující výjimku.|  
|`expression`|Volitelné. Musí být implicitně převést na `Boolean`. Všechny výraz, který popisuje obecný filtru. Obvykle se používá k filtrování podle číslo chyby. Použít s `When` – klíčové slovo k určení podmínek, za kterých je chyba zachycena.|  
|`catchStatements`|Volitelné. Příkazy se budou zpracovávat chyby, ke kterým došlo v přidruženém `Try` bloku. Může být složený příkaz.|  
|`Exit Try`|Volitelné. Klíčové slovo, které dělí mimo `Try...Catch...Finally` struktura. Provádění pokračuje hned za kódem `End Try` příkaz. `Finally` Stále bude třeba spustit příkaz. Není povoleno v `Finally` bloky.|  
|`Finally`|Volitelné. A `Finally` bloku je vždy provést při spuštění opustí libovolná součást `Try...Catch` příkaz.|  
|`finallyStatements`|Volitelné. Příkazy, které jsou spouštěny po další zpracování chyby došlo k chybě.|  
|`End Try`|Ukončí `Try...Catch...Finally` struktura.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud očekáváte, že konkrétní výjimka mohou nastat během určité části kódu, vložte kód `Try` blokovat a použít `Catch` blok k uchování kontroly a zpracovat výjimku, pokud k němu dojde.  
  
 A `Try…Catch` příkaz se skládá z `Try` bloku, za nímž následuje jeden nebo více `Catch` klauzule, které určují obslužné rutiny pro různé výjimky. Pokud je vyvolána výjimka `Try` bloku [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hledá `Catch` příkaz, který zpracovává výjimku. Pokud odpovídající `Catch` příkaz nebyl nalezen, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] prozkoumá metodu, která volá metodu aktuální, a tak dále zásobníkem volání. Pokud žádné `Catch` bloku nenajde, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zobrazí uživateli zprávu neošetřené výjimky a zastaví provádění tohoto programu.  
  
 Můžete použít více než jednu `Catch` příkaz v `Try…Catch` příkaz. Pokud použijete tento pořadí `Catch` klauzule je důležité, protože se zkontrolují v pořadí. Před méně konkrétní ty catch konkrétnější výjimky.  
  
 Následující `Catch` příkaz podmínky jsou nejméně specifická a zachytí všechny výjimky, které jsou odvozeny od <xref:System.Exception> třídy. Jeden z těchto variant má obvykle použít jako poslední `Catch` blokovat `Try...Catch...Finally` struktura po zachycování specifických výjimek očekáváte. Tok řízení nikdy dosáhnout `Catch` blok, který odpovídá některé z těchto variant.  
  
-   `type` Je `Exception`, například:`Catch ex As Exception`  
  
-   Příkaz neobsahuje žádné `exception` proměnných, například:`Catch`  
  
 Když `Try…Catch…Finally` příkaz vnořen v jiném `Try` bloku [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nejprve zkontroluje každý `Catch` příkaz v nejvnitřnější `Try` bloku. Pokud neexistuje odpovídající `Catch` příkaz nenajde, vyhledávání pokračuje do `Catch` ve vnějším `Try…Catch…Finally` bloku.  
  
 Lokální proměnné z `Try` nejsou k dispozici v bloku `Catch` blokovat, protože jsou samostatné bloky. Pokud chcete použití proměnné v více než jeden blok, deklarovat proměnnou mimo `Try...Catch...Finally` struktura.  
  
> [!TIP]
>  `Try…Catch…Finally` Údajů je k dispozici jako fragment kódu technologie IntelliSense. Ve Správci fragmentů kódu, rozbalte položku **kód vzory – Pokud pro každou, zkuste Catch, vlastnost atd**a potom **chyba zpracování (výjimek)**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="finally-block"></a>Nakonec bloku  
 Pokud máte jeden nebo více příkazů, které musí spustit před ukončení `Try` struktury, použijte `Finally` bloku. Ovládací prvek předává do `Finally` blokovat těsně před předává mimo `Try…Catch` struktura. To platí i v případě, že dojde k výjimce uvnitř kdekoli `Try` struktura.  
  
 A `Finally` blok je užitečné pro spuštění jakékoli kódu, které musí spustit i v případě, že dojde k výjimce. Ovládací prvek je předána `Finally` bloku bez ohledu na to, jak `Try...Catch` blokovat ukončí.  
  
 Kód v `Finally` blokovat spustí i v případě, že váš kód zjistí `Return` příkaz v `Try` nebo `Catch` bloku. Ovládací prvek z nepředává `Try` nebo `Catch` blokovat do odpovídajících `Finally` blokovat v následujících případech:  
  
-   [End – příkaz](../../../visual-basic/language-reference/statements/end-statement.md) se vyskytuje v `Try` nebo `Catch` bloku.  
  
-   A <xref:System.StackOverflowException> je vyvolána `Try` nebo `Catch` bloku.  
  
 Není platný pro explicitně přenos provádění do `Finally` bloku. Přenos provádění mimo `Finally` blok není platný, s výjimkou prostřednictvím výjimku.  
  
 Pokud `Try` příkaz neobsahuje alespoň jeden `Catch` bloku musí obsahovat `Finally` bloku.  
  
> [!TIP]
>  Pokud nemáte zachytit specifické výjimky `Using` příkaz chová jako `Try…Finally` bloku a zaručuje uvolnění prostředků, bez ohledu na to, jak byl ukončen blok. To platí i s k neošetřené výjimce. Další informace najdete v tématu [pomocí příkazu](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="exception-argument"></a>Výjimky argumentu  
 `Catch` Bloku `exception` argument je instance <xref:System.Exception> nebo třída odvozená z `Exception` třídy. `Exception` Odpovídá chybu, která došlo k chybě v instanci třídy `Try` bloku.  
  
 Vlastnosti `Exception` objektu nápovědy k identifikaci příčina a umístění výjimku. Například <xref:System.Exception.StackTrace%2A> seznamů vlastností vyvolání metody, které vedly k výjimce a pomáhá vám zjistit, kde došlo k chybě v kódu. <xref:System.Exception.Message%2A>vrátí zprávu, která popisuje výjimku. <xref:System.Exception.HelpLink%2A>Vrátí odkaz na související soubor nápovědy. <xref:System.Exception.InnerException%2A>Vrátí `Exception` objektu, která způsobila, že aktuální výjimku nebo vrátí `Nothing` Pokud neexistuje žádné původní `Exception`.  
  
## <a name="considerations-when-using-a-trycatch-statement"></a>Informace týkající se použití bloku Try... Catch – příkaz  
 Použití `Try…Catch` příkaz pouze na signalizaci výskytem program neobvyklou nebo neočekávané události. Důvody zahrnují následující:  
  
-   Zachytávání výjimek v době běhu vytvoří další režii a může být pomalejší než předem kontrola předejdete výjimky.  
  
-   Pokud `Catch` blok není správně zpracovává, výjimka nemusí být správně hlášené uživatelům.  
  
-   Zpracovávání výjimek v jazyce díky program složitější.  
  
 Není vždy nutné `Try…Catch` příkaz zkontrolujte podmínku, která může dojít. Následující příklad zkontroluje, zda soubor existuje, než se pokusíte otevřít. Tím se snižuje potřebu zachytávání výjimka vyvolaná objektem <xref:System.IO.File.OpenText%2A> metoda.  
  
 [!code-vb[VbVbalrStatements#94](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 Ujistěte se, že kód v `Catch` bloky může hlásit výjimky pro uživatele, správně prostřednictvím bezpečné pro přístup z více vláken protokolování nebo odpovídající zprávy. Výjimky, jinak může zůstat neznámé.  
  
## <a name="async-methods"></a>Asynchronní metody  
 Pokud označíte metodu s [asynchronní](../../../visual-basic/language-reference/modifiers/async.md) modifikátor, můžete použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor v metodě. Příkaz s `Await` operátor pozastaví spuštění metody až do dokončení awaited úloh. Úloha reprezentuje probíhající práce. Když úloha, která je přidružená `Await` operátor dokončí, obnoví spuštění ve stejnou metodu. Další informace najdete v tématu [řízení toku v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
 Úlohu vrácený asynchronní metody může se stát v chybovém stavu, která udává, zda byla dokončena z důvodu neošetřené výjimky. Úloha může také končit zrušené stavu, což vede `OperationCanceledException` hlášeny mimo await výraz. K zachycení buď typ výjimky, umístit `Await` výraz, který je spojen s úloha v `Try` blokovat a zachycení výjimky v `Catch` bloku. Příklad je k dispozici dále v tomto tématu.  
  
 Úloha může být v chybovém stavu, protože byly zodpovědná za jeho chybující více výjimek. Úloha může být například výsledek volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Pokud jste await takových úloh, zachycená výjimka je pouze jeden z výjimky a nemůžete předpovědět, které k výjimce. Příklad je k dispozici dále v tomto tématu.  
  
 `Await` Výraz nesmí být uvnitř `Catch` bloku nebo `Finally` bloku.  
  
## <a name="iterators"></a>Iterátory  
 Iterator funkce nebo `Get` přistupujícího objektu provede vlastní iteraci přes kolekci. Používá iterovat [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz vrátit každý prvek kolekce, jeden v čase. Volání funkce iterator pomocí [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 A `Yield` příkaz může být uvnitř `Try` bloku. A `Try` blok, který obsahuje `Yield` příkaz může mít `Catch` blokuje a může mít `Finally` bloku. Najdete v části "zkuste bloky v jazyce Visual Basic" [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) příklad.  
  
 A `Yield` příkaz nemůže být uvnitř `Catch` bloku nebo `Finally` bloku.  
  
 Pokud `For Each` textu (mimo funkci iterator) vyvolá výjimku, `Catch` bloku ve funkci iterator není proveden, ale `Finally` bloku ve funkci iterator se spustí. A `Catch` bloku uvnitř funkce iterator zachytí pouze výjimky, které nastat uvnitř funkce iterator.  
  
## <a name="partial-trust-situations"></a>Situace částečné důvěryhodnosti  
 V situacích, částečným vztahem důvěryhodnosti, například aplikace hostované ve sdílené síťové složce `Try...Catch...Finally` nezachytí výjimky zabezpečení, které dojít před vyvoláním metody, která obsahuje volání. Následující příklad, pokud jste pro něj na sdílené složky serveru a spustit z ní, vytváří chyba "System.Security.SecurityException: žádosti se nezdařilo." Další informace o výjimkách zabezpečení najdete v tématu <xref:System.Security.SecurityException> třídy.  
  
 [!code-vb[VbVbalrStatements#85](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 V této částečným vztahem důvěryhodnosti situaci, budete muset uvést `Process.Start` příkaz v samostatném `Sub`. Počáteční volání `Sub` se nezdaří. To umožňuje `Try...Catch` k zachycení ho před `Sub` obsahující `Process.Start` spuštění a vytváří výjimka zabezpečení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje strukturu `Try...Catch...Finally` příkaz.  
  
 [!code-vb[VbVbalrStatements#86](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `CreateException` metoda vrátí `NullReferenceException`. Kód, který generuje výjimky se nepoužívá `Try` bloku. Proto `CreateException` metoda zpracovává výjimku. `RunSample` Metoda ošetření výjimky, protože volání `CreateException` metoda je `Try` bloku.  
  
 Příklad obsahuje `Catch` příkazy pro několik typů výjimek, seřazené od nejvíce konkrétních k nejvíce Obecné.  
  
 [!code-vb[VbVbalrStatements#91](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `Catch When` příkaz pro filtrování podmíněným výrazem. Pokud je výsledkem podmíněným výrazem `True`, kód `Catch` blokovat spuštění.  
  
 [!code-vb[VbVbalrStatements#92](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu má `Try…Catch` příkaz, který je součástí `Try` bloku. Vnitřní `Catch` bloku vyvolá výjimku, která má jeho `InnerException` vlastností nastavenou na původní výjimka. Vnější `Catch` bloku sestav svou vlastní výjimku a v popisu vnitřní výjimky.  
  
 [!code-vb[VbVbalrStatements#93](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje zpracování výjimek pro asynchronní metody. Zachytit výjimku, která platí pro asynchronní úlohy, `Await` výraz `Try` je bloku volající a výjimka zachycena v `Catch` bloku.  
  
 Zrušením komentáře u `Throw New Exception` řádku v příkladu za účelem ukázky zpracování výjimek. Výjimka je zachycena v `Catch` blok úkolu `IsFaulted` je nastavena na `True`a tato úloha `Exception.InnerException` je nastavena na výjimku.  
  
 Zrušením komentáře u `Throw New OperationCancelledException` řádku k předvedení toho, co se stane, když zrušíte asynchronní proces. Výjimka je zachycena v `Catch` bloku a úkolu `IsCanceled` je nastavena na `True`. Ale za určitých podmínek, které se nevztahují na tomto příkladu `IsFaulted` je nastaven na `True` a `IsCanceled` je nastaven na `False`.  
  
 [!code-vb[csAsyncExceptions#1](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje zpracování výjimek, kde více úloh může mít za následek více výjimek. `Try` Má bloku `Await` výraz pro úlohu, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> vrátila. Úloha je dokončená, když jsou tři úlohy, ke kterému <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> platí jsou dokončeny.  
  
 Jednotlivé tři úlohy dojde k výjimce. `Catch` Bloku iteruje výjimky, které jsou součástí `Exception.InnerExceptions` vlastnosti úlohy, `Task.WhenAll` vrátila.  
  
 [!code-vb[csAsyncExceptions#3](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:System.Exception>  
 [Exit – příkaz](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [On Error – příkaz](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Doporučené postupy pro používání fragmentů kódu](/visualstudio/ide/best-practices-for-using-code-snippets)  
 [Zpracování výjimek](../../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)  
 [Throw – příkaz](../../../visual-basic/language-reference/statements/throw-statement.md)
