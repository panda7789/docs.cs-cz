---
title: Try... Catch... Příkaz finally - jazyka Visual Basic
description: Zjistěte, jak použít zpracování výjimek s příkazy jazyka Visual Basic Try/Catch/Finally.
ms.date: 12/07/2018
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
ms.custom: seodec18
ms.openlocfilehash: 126f20c86bb47e8002382e069ce6236600394aba
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638774"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch....Finally – příkaz (Visual Basic)

Poskytuje způsob, jak zpracovat některé nebo všechny možné chyby, které mohou nastat v daném bloku kódu, za stálého běhu programu.

## <a name="syntax"></a>Syntaxe

```vb
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
|`tryStatements`|Volitelné. Příkazů, kde může dojít k chybě. Může být složený příkaz.|
|`Catch`|Volitelné. Více `Catch` bloky povolené. Pokud dojde k výjimce při zpracování `Try` blokovat, každý `Catch` je příkaz zkoumán, v textové pořadí. určíte, zda zpracovává výjimku, s `exception` reprezentující výjimku, která byla vyvolána.|
|`exception`|Volitelné. Libovolný název proměnné. Počáteční hodnota `exception` je hodnota vyvolané chyby. Použít s `Catch` k určení chybou byla zachycena. Pokud tento parametr vynechán, `Catch` příkaz zachytí jakoukoli výjimku.|
|`type`|Volitelné. Určuje typ filtru třídy. Pokud hodnota `exception` je typu určeného `type` nebo odvozeného typu, identifikátor vázán na objekt výjimky.|
|`When`|Volitelné. A `Catch` příkazem `When` klauzule zachytává výjimky pouze tehdy, když `expression` vyhodnotí jako `True`. A `When` až po kontrole typ výjimky, je použita klauzule a `expression` mohou odkazovat na identifikátor reprezentující výjimku.|
|`expression`|Volitelné. Musí být implicitně převeditelný na `Boolean`. Libovolný výraz, který popisuje obecný filtru. Obvykle se používá k filtrování podle čísla chyby. Použít s `When` – klíčové slovo k určení podmínek, za kterých je zachycena chybu.|
|`catchStatements`|Volitelné. Příkazů pro zpracování chyb, ke kterým dochází v přidruženém `Try` bloku. Může být složený příkaz.|
|`Exit Try`|Volitelné. Klíčové slovo, které se přeruší z celkového počtu `Try...Catch...Finally` struktury. Provádění pokračuje s kódem, hned za `End Try` příkazu. `Finally` Příkazu bude stále spuštěn. Není povoleno v `Finally` bloky.|
|`Finally`|Volitelné. A `Finally` bloku je vždy spuštěn při provádění opustí libovolné části `Try...Catch` příkazu.|
|`finallyStatements`|Volitelné. Příkazů, který se spustí po další zpracování chyby došlo k chybě.|
|`End Try`|Ukončuje `Try...Catch...Finally` struktury.|

## <a name="remarks"></a>Poznámky

Pokud očekáváte, že konkrétní výjimka muže vzniknout během určité části kódu, vložte kód `Try` blokovat a použít `Catch` blok se zachovat kontrolu a zpracovala výjimku. Pokud k němu dojde.

A `Try…Catch` příkaz se skládá z `Try` bloku, za nímž následuje jedna nebo více `Catch` klauzule, které určují obslužné rutiny pro různé výjimky. Když je výjimka vyvolána `Try` blokovat, Visual Basic vyhledá `Catch` příkaz, který zpracovává výjimku. Pokud odpovídající `Catch` příkaz nebyl nalezen, Visual Basic zjišťuje metody, která volá metodu aktuální výše v zásobníku volání a tak dále. Pokud ne `Catch` nalezen blok, Visual Basic zobrazí zprávu neošetřená výjimka na uživatele a zastaví provádění programu.

Můžete použít více než jednu `Catch` výroky `Try…Catch` příkazu. Pokud to provedete, pořadí `Catch` klauzulí je důležité, protože jsou zkoumány podle pořadí. Zachycení více specifické výjimky než těch, které jsou specifické pro less.

Následující `Catch` příkaz podmínky jsou po nejméně konkrétní a zachytí všechny výjimky, které jsou odvozeny z <xref:System.Exception> třídy. Jednu z těchto variant má obvykle použít jako poslední `Catch` blokovat `Try...Catch...Finally` struktury po zachycení specifické výjimky očekáváte. Tok řízení můžete nikdy nedorazí `Catch` blok, který následuje některý z těchto variant.

- `type` Je `Exception`, například: `Catch ex As Exception`

- Příkaz nemá žádné `exception` proměnných, například: `Catch`

Když `Try…Catch…Finally` příkaz je vnořená v jiném `Try` bloku, Visual Basic nejprve zkontroluje každý `Catch` příkaz v nejvnitřnější `Try` bloku. Pokud neexistuje odpovídající `Catch` příkaz nenajde, vyhledávání pokračuje do `Catch` ve vnějším `Try…Catch…Finally` bloku.

Lokální proměnné z `Try` nejsou k dispozici v bloku `Catch` blokovat, protože jde o samostatné bloky. Pokud chcete použít proměnnou ve více než jeden blok, deklarace proměnné mimo `Try...Catch...Finally` struktury.

> [!TIP]
> `Try…Catch…Finally` Příkaz je dostupný jako fragment kódu technologie IntelliSense. Ve Správci fragmentů kódu, rozbalte **vzorky kódu – If, For Each, Try Catch, vlastnost atd**a potom **zpracování chyb (výjimek)**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Blok finally

Pokud máte jeden nebo více příkazů, které musí spustit před ukončením `Try` strukturu, použijte `Finally` bloku. Řízení se předá `Finally` blokovat těsně před plánovaným začátkem předá z celkového počtu `Try…Catch` struktury. To platí i v případě, že dojde k výjimce kdekoli uvnitř `Try` struktury.

A `Finally` bloku je užitečné pro spuštění jakéhokoli kódu, které musí spustit i v případě, že dojde k výjimce. Řízení je předáno `Finally` blokovat bez ohledu na to, jak `Try...Catch` blokovat ukončí.

Kód v `Finally` blok i v případě, že váš kód zjistí `Return` příkaz v `Try` nebo `Catch` bloku. Ovládací prvek z nepředává `Try` nebo `Catch` blokovat na odpovídající `Finally` blokovat v následujících případech:

- [End – příkaz](end-statement.md) dochází v `Try` nebo `Catch` bloku.

- A <xref:System.StackOverflowException> je vyvolána `Try` nebo `Catch` bloku.

Není platné. explicitně přenést do spuštění `Finally` bloku. Přenos z celkového počtu spuštění `Finally` blok není platný, s výjimkou prostřednictvím výjimku.

Pokud `Try` alespoň jeden příkaz neobsahuje `Catch` bloku, musí obsahovat `Finally` bloku.

> [!TIP]
> Pokud nemáte zachytit specifické výjimky `Using` se chová stejně jako `Try…Finally` bloku a záruky zacházení s prostředky, bez ohledu na to, jak ukončení bloku. To platí dokonce i s neošetřenou výjimkou. Další informace najdete v tématu [příkazu Using](using-statement.md).

## <a name="exception-argument"></a>Výjimky argumentu

`Catch` Bloku `exception` je argument instancí <xref:System.Exception> třídu nebo třídu odvozenou od `Exception` třídy. `Exception` Odpovídá chyby, ke které došlo k chybě v instanci třídy `Try` bloku.

Vlastnosti `Exception` objektu zobrazíte nápovědu, jak určit příčinu a umístění výjimky. Například <xref:System.Exception.StackTrace%2A> seznamů vlastností volané metody, která vedla k výjimce, pomáhá najít, kde došlo k chybě v kódu. <xref:System.Exception.Message%2A> vrátí zprávu, která popisuje výjimku. <xref:System.Exception.HelpLink%2A> Vrátí odkaz na související soubor nápovědy. <xref:System.Exception.InnerException%2A> Vrátí `Exception` objektu, která způsobila aktuální výjimku nebo vrátí `Nothing` Pokud neexistuje žádná původní `Exception`.

## <a name="considerations-when-using-a-trycatch-statement"></a>Informace týkající se použití Try... Catch – příkaz

Použití `Try…Catch` příkaz pouze k signalizaci výskytu neobvyklých nebo neočekávané události. Důvody patří:

- Zachycování výjimek za běhu vytvoří další režii a by mohla být pomalejší než předběžné kontroly, aby výjimky.

- Pokud `Catch` bloku nezpracovává správně, výjimka nemusí být uveden správně pro uživatele.

- Zpracování výjimek je program složitější.

Není vždy nutné `Try…Catch` příkaz podmínku, která by mohla nastat. Následující příklad zkontroluje, zda soubor existuje. před pokusem o otevření. To snižuje nutnost zachycení výjimky vyvolané <xref:System.IO.File.OpenText%2A> metody.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

Ujistěte se, že kód v `Catch` bloky může hlásit výjimky na uživatele, správně prostřednictvím bezpečné pro vlákna protokolování nebo příslušné zprávy. V opačném případě může zůstat výjimky neznámý.

## <a name="async-methods"></a>Asynchronní metody

Pokud určíte metodu s [asynchronní](../modifiers/async.md) modifikátor, můžete použít [Await](../operators/await-operator.md) operátor v metodě. Příkaz s `Await` operátor pozastaví provádění metody až do dokončení očekávané úlohy. Úloha představuje probíhající práci. Když úloha, která je přidružena `Await` operátor dokončí, obnoví spuštění ve stejnou metodu. Další informace najdete v tématu [tok řízení v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).

Úkol vrácený asynchronní metody ukončit v chybovém stavu, která je dokončena z důvodu neošetřené výjimky. Úkol může také skončit ve zrušeném stavu, což vede `OperationCanceledException` vyvolané z výrazu await. K zachycení buď typ výjimky, umístěte `Await` výraz, který je spojen s úlohou v `Try` blokovat a zachytit výjimku v `Catch` bloku. Příklad je k dispozici dále v tomto tématu.

Úloha může být v chybovém stavu, protože více výjimek tým byl zodpovědný za jeho přerušením. Úloha může být například výsledek volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Když budete očekávat takový úkol, zachycené výjimky je pouze jednu z výjimek a nelze předpovědět, které k výjimce. Příklad je k dispozici dále v tomto tématu.

`Await` Výraz nemůže být uvnitř `Catch` bloku nebo `Finally` bloku.

## <a name="iterators"></a>Iterátory

Funkce iterátoru nebo `Get` přistupující objekt provádí vlastní iterace nad kolekcí. Iterátor používá [Yield](yield-statement.md) příkaz k vrácení každého prvku kolekce jeden po druhém. Volání funkce iterátoru pomocí [For Each... Další příkaz](for-each-next-statement.md).

A `Yield` příkaz může být v rámci `Try` bloku. A `Try` blok, který obsahuje `Yield` může mít příkaz `Catch` a ostatní porty blokuje může mít `Finally` bloku. Najdete v části "zkuste bloky v jazyce Visual Basic" [iterátory](../../programming-guide/concepts/iterators.md) příklad.

A `Yield` příkaz nejde provést uvnitř `Catch` bloku nebo `Finally` bloku.

Pokud `For Each` text (mimo funkce iterátoru) vyvolá výjimku, `Catch` bloku funkce iterátoru není spuštěn, ale `Finally` je proveden blok v funkce iterátoru. A `Catch` bloku funkce iterátoru zachytává pouze výjimky, ke kterým dochází uvnitř funkce iterátoru.

## <a name="partial-trust-situations"></a>Situacích částečné důvěryhodnosti

V situacích částečné důvěryhodnosti, jako je například aplikace hostované ve sdílené síťové složce `Try...Catch...Finally` nezachytí výjimky zabezpečení, ke kterým dochází před vyvoláním metody, která obsahuje volání. Následující příklad, když vložit ho do sdílené složky serveru a spusťte z něj, vytvoří chybu "System.Security.SecurityException: Požadavek se nezdařil." Další informace o bezpečnostním výjimkám, najdete v článku <xref:System.Security.SecurityException> třídy.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

V takové částečným vztahem důvěryhodnosti situace, je nutné umístit `Process.Start` příkaz v samostatném `Sub`. Počáteční volání `Sub` se nezdaří. Díky tomu `Try...Catch` má zachytit před `Sub` obsahující `Process.Start` je spuštěná a vytváří výjimku zabezpečení.

## <a name="examples"></a>Příklady

### <a name="the-structure-of-trycatchfinally"></a>Struktury Try... Catch... Nakonec

Následující příklad ukazuje strukturu `Try...Catch...Finally` příkazu.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Výjimka v metodě volat z bloku Try

V následujícím příkladu `CreateException` vyvolá metoda výjimku `NullReferenceException`. Není v kódu, který generuje výjimku `Try` bloku. Proto `CreateException` metodu ke zpracování výjimky. `RunSample` Metoda zpracování výjimky, protože volání `CreateException` metoda je `Try` bloku.

Příklad obsahuje `Catch` příkazy pro několik typů výjimek, seřazené od nejkonkrétnější většinu obecných.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Příkaz Catch, když

Následující příklad ukazuje způsob použití `Catch When` příkaz k filtrování podmíněný výraz. Pokud podmíněný výraz je vyhodnocen jako `True`, kód `Catch` blok.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>Vnořené příkazy Try

Následující příklad obsahuje `Try…Catch` příkaz, který je součástí `Try` bloku. Vnitřní `Catch` bloku vyvolá výjimku, která má jeho `InnerException` nastavenou na původní výjimku. Vnější `Catch` bloku hlásí svůj vlastní výjimku a vnitřní výjimku.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Zpracování výjimek pro asynchronní metody

Následující příklad ukazuje zpracování výjimek pro asynchronní metody. Zachytit výjimku, která se vztahuje na asynchronní úlohy, `Await` výraz `Try` bloku volajícího a výjimky je zachycena v `Catch` bloku.

Zrušením komentáře u `Throw New Exception` řádek v příkladu předvést zpracování výjimek. Výjimka je zachycena v `Catch` blokovat, úkolu `IsFaulted` je nastavena na `True`a úkolu `Exception.InnerException` je nastavena na výjimku.

Zrušením komentáře u `Throw New OperationCancelledException` řádku předvést, co se stane, když zrušíte asynchronní proces. Výjimka je zachycena v `Catch` bloku a tato úloha `IsCanceled` je nastavena na `True`. Ale za určitých podmínek, které se nevztahují na tomto příkladu `IsFaulted` je nastavena na `True` a `IsCanceled` je nastavena na `False`.

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Zpracování více výjimky v asynchronních metodách

Následující příklad ukazuje zpracování výjimek, kde více úkolů může vést k více výjimek. `Try` Má bloku `Await` výraz pro úlohu, která <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> vrátila. Když tři úkolů, ke kterému je úkol dokončený <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> se použije se dokončí.

Všechny tři úkoly dojde k výjimce. `Catch` Bloku prochází výjimky, které jsou součástí `Exception.InnerExceptions` vlastnosti úkolu, který `Task.WhenAll` vrátila.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Příkaz Exit](exit-statement.md)
- [Příkaz On Error](on-error-statement.md)
- [Doporučené postupy pro používání fragmentů kódu](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Zpracování výjimek](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Příkaz Throw](throw-statement.md)
