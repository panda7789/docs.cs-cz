---
title: Zkusit... Zachytit... Finally – příkaz
description: Naučte se používat zpracování výjimek s příkazy Visual Basic try/catch/finally.
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
ms.openlocfilehash: eb04b6cff0847009407e38a3696e9be7c700356c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337336"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch....Finally – příkaz (Visual Basic)

Poskytuje způsob, jak zpracovat některé nebo všechny možné chyby, které mohou nastat v daném bloku kódu, a přitom stále spouštět kód.

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
|`tryStatements`|Volitelné. Příkazy, kde může dojít k chybě. Může být složený příkaz.|
|`Catch`|Volitelné. Je povoleno více bloků `Catch`. Pokud dojde k výjimce při zpracování `Try` bloku, každý příkaz `Catch` je zkontrolován v textovém pořadí, aby určil, zda zpracovává výjimku, `exception` představují výjimku, která byla vyvolána.|
|`exception`|Volitelné. Libovolný název proměnné. Počáteční hodnota `exception` je hodnota vyvolané chyby. Používá se s `Catch` k určení zjištěné chyby. Je-li tento parametr vynechán, příkaz `Catch` zachytí jakoukoli výjimku.|
|`type`|Volitelné. Určuje typ filtru třídy. Pokud je hodnota `exception` typu určeném `type` nebo odvozeného typu, bude identifikátor svázán s objektem výjimky.|
|`When`|Volitelné. Příkaz `Catch` s klauzulí `When` zachytává výjimky pouze v případě, že je `expression` vyhodnocena jako `True`. Klauzule `When` je použita pouze po kontrole typu výjimky a `expression` mohou odkazovat na identifikátor představující výjimku.|
|`expression`|Volitelné. Musí být implicitně převoditelné na `Boolean`. Libovolný výraz, který popisuje obecný filtr. Obvykle se používá k filtrování podle čísla chyby. Používá se s klíčovým slovem `When` k určení podmínek, za kterých se zachytí chyba.|
|`catchStatements`|Volitelné. Příkazy pro zpracování chyb, ke kterým došlo v přidruženém bloku `Try`. Může být složený příkaz.|
|`Exit Try`|Volitelné. Klíčové slovo, které se rozdělí z `Try...Catch...Finally` struktury. Provádění pokračuje pomocí kódu hned za příkazem `End Try`. Příkaz `Finally` bude stále proveden. Není povolené v blocích `Finally`.|
|`Finally`|Volitelné. `Finally` blok je vždy spuštěn, když provádění opustí jakoukoli část příkazu `Try...Catch`.|
|`finallyStatements`|Volitelné. Příkazy, které se spustí po všech ostatních zpracováních chyb.|
|`End Try`|Ukončí strukturu `Try...Catch...Finally`.|

## <a name="remarks"></a>Poznámky

Pokud očekáváte, že určitá výjimka může nastat během konkrétní části kódu, vložte kód do `Try`ového bloku a pomocí `Catch` bloku zachovejte kontrolu a zpracujte výjimku, pokud k ní dojde.

Příkaz `Try…Catch` se skládá z bloku `Try` následovaného jednou nebo více `Catch` klauzulími, které určují obslužné rutiny pro různé výjimky. Pokud je vyvolána výjimka ve `Try` bloku, Visual Basic vyhledá příkaz `Catch`, který zpracovává výjimku. Pokud nebyl nalezen odpovídající příkaz `Catch`, Visual Basic prověřuje metodu, která volala aktuální metodu, a tak dále v zásobníku volání. Pokud není nalezen žádný blok `Catch`, Visual Basic zobrazí uživateli neošetřenou zprávu o výjimce a zastaví provádění programu.

V příkazu `Try…Catch` můžete použít více než jeden `Catch` příkaz. Pokud to uděláte, pořadí klauzulí `Catch` je významné, protože jsou prověřeny v daném pořadí. Zachyťte konkrétnější výjimky před méně specifickými výjimkami.

Následující podmínky příkazu `Catch` jsou nejméně specifické a budou zachytit všechny výjimky, které jsou odvozeny z třídy <xref:System.Exception>. Tuto variantu byste měli obvykle používat jako poslední `Catch` blok ve struktuře `Try...Catch...Finally`, a to po zachycení všech konkrétních výjimek, které očekáváte. Tok řízení nemůže nikdy dosáhnout `Catch` blok, který následuje po jedné z těchto variant.

- `type` je `Exception`, například: `Catch ex As Exception`

- Příkaz nemá `exception` proměnnou, například: `Catch`

Pokud je příkaz `Try…Catch…Finally` vnořen v jiném bloku `Try`, Visual Basic nejprve prověřuje každý `Catch` příkaz v nejvnitřnějším `Try` bloku. Pokud se nenajde žádný vyhovující příkaz `Catch`, hledání pokračuje na `Catch` příkazů vnějšího `Try…Catch…Finally` bloku.

Místní proměnné z `Try` bloku nejsou k dispozici v bloku `Catch`, protože jsou to samostatné bloky. Pokud chcete použít proměnnou ve více než jednom bloku, deklarujte proměnnou mimo strukturu `Try...Catch...Finally`.

> [!TIP]
> Příkaz `Try…Catch…Finally` je k dispozici jako fragment kódu technologie IntelliSense. Ve Správci fragmentů kódu rozbalte položku **vzory kódu – Pokud pro každou, zkuste zachytit, vlastnost atd**. a pak **zpracování chyb (výjimky)** . Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Blok finally

Pokud máte jeden nebo více příkazů, které musí být spuštěny před ukončením `Try` struktury, použijte blok `Finally`. Řízení se předá do `Finally` bloku těsně před tím, než se předává ze struktury `Try…Catch`. To platí i v případě, že dojde k výjimce kdekoli uvnitř `Try` struktury.

Blok `Finally` je užitečný pro spuštění libovolného kódu, který musí být spuštěn, i když dojde k výjimce. Ovládací prvek se předává do bloku `Finally` bez ohledu na to, jak se `Try...Catch` blok ukončí.

Kód v `Finally`ovém bloku běží i v případě, že váš kód nalezne `Return` příkaz v `Try` nebo `Catch` bloku. Ovládací prvek nepřechází z `Try` nebo `Catch` bloku na odpovídající `Finally` blok v následujících případech:

- V bloku `Try` nebo `Catch` byl nalezen [příkaz end](end-statement.md) .

- V bloku `Try` nebo `Catch` je vyvolána <xref:System.StackOverflowException>.

Explicitní přenos spuštění do `Finally`ového bloku není platný. Přenos spuštění z `Finally`ho bloku není platný, s výjimkou výjimky.

Pokud `Try` příkaz neobsahuje alespoň jeden blok `Catch`, musí obsahovat blok `Finally`.

> [!TIP]
> Pokud nemusíte zachytit konkrétní výjimky, příkaz `Using` se chová jako `Try…Finally` blok a zaručuje odstranění prostředků bez ohledu na to, jakým způsobem ukončujete blok. To je pravdivé i s neošetřenou výjimkou. Další informace naleznete v tématu [using – příkaz](using-statement.md).

## <a name="exception-argument"></a>Argument výjimky

Argument `Catch` Block `exception` je instancí třídy <xref:System.Exception> nebo třídy, která je odvozena od třídy `Exception`. Instance třídy `Exception` odpovídá chybě, ke které došlo v bloku `Try`.

Vlastnosti objektu `Exception` pomůžou identifikovat příčinu a umístění výjimky. Například vlastnost <xref:System.Exception.StackTrace%2A> zobrazí seznam volaných metod, které vedly k výjimce, což vám pomůže najít, kde došlo k chybě v kódu. <xref:System.Exception.Message%2A> vrátí zprávu, která popisuje výjimku. <xref:System.Exception.HelpLink%2A> vrátí odkaz na související soubor Help. <xref:System.Exception.InnerException%2A> vrátí objekt `Exception`, který způsobil aktuální výjimku, nebo vrátí `Nothing`, pokud neexistuje původní `Exception`.

## <a name="considerations-when-using-a-trycatch-statement"></a>Doporučení při použití try... Catch – příkaz

Použijte příkaz `Try…Catch` jenom k signalizaci výskytu neobvyklých nebo neočekávaných událostí programu. K tomu patří následující důvody:

- Zachycování výjimek za běhu vytváří další režii a je pravděpodobně pomalejší než předběžná kontrola, aby nedocházelo k výjimkám.

- Pokud `Catch` blok není správně zpracován, výjimka nemusí být správně hlášena uživatelům.

- Zpracování výjimek způsobuje složitější program.

Nepotřebujete vždy příkaz `Try…Catch` ke kontrole podmínky, která by mohla nastat. Následující příklad zkontroluje, zda soubor existuje, než se pokusí ho otevřít. To snižuje nutnost zachycení výjimky vyvolané metodou <xref:System.IO.File.OpenText%2A>.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

Zajistěte, aby kód v blocích `Catch` mohl správně hlásit výjimky uživatelům, ať už prostřednictvím protokolování bezpečného pro přístup z více vláken, nebo vhodné zprávy. V opačném případě mohou výjimky zůstat neznámé.

## <a name="async-methods"></a>Asynchronní metody

Pokud označíte metodu pomocí modifikátoru [Async](../modifiers/async.md) , můžete použít operátor [await](../operators/await-operator.md) v metodě. Příkaz s operátorem `Await` pozastaví provádění metody až do dokončení očekávané úlohy. Úkol představuje probíhající práci. Po dokončení úlohy, která je spojena s operátorem `Await`, se provádění pokračuje ve stejné metodě. Další informace najdete v tématu [řízení toku v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).

Úloha vrácená asynchronní metodou může končit chybovým stavem, což značí, že byla dokončena z důvodu neošetřené výjimky. Úloha může také končit zrušeným stavem, což způsobí, že `OperationCanceledException` vyvolala z výrazu await. Chcete-li zachytit buď typ výjimky, umístěte výraz `Await`, který je spojen s úlohou v bloku `Try` a zachytí výjimku v bloku `Catch`. Příklad je uveden dále v tomto tématu.

Úloha může být v chybném stavu, protože za její chybu byla zodpovědná více výjimek. Například úloha může být výsledkem volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Při čekání na takovou úlohu je zachycená výjimka pouze jedna z výjimek a nelze předpovědět, která výjimka bude zachycena. Příklad je uveden dále v tomto tématu.

Výraz `Await` nemůže být uvnitř bloku `Catch` nebo bloku `Finally`.

## <a name="iterators"></a>Iterátory

Funkce iterátoru nebo přistupující objekt `Get` provádí vlastní iteraci v kolekci. Iterátor používá příkaz [yield](yield-statement.md) k vrácení každého prvku kolekce v jednom okamžiku. Vyvoláte funkci iterátoru pomocí metody [for each... Další příkaz](for-each-next-statement.md).

Příkaz `Yield` může být uvnitř bloku `Try`. `Try` blok, který obsahuje příkaz `Yield`, může mít `Catch` bloky a může mít `Finally` blok. Příklad naleznete v části "try Blocks in Visual Basic" v tématu [iterátory](../../programming-guide/concepts/iterators.md) .

Příkaz `Yield` nemůže být uvnitř bloku `Catch` nebo bloku `Finally`.

Pokud `For Each` tělo (mimo funkci iterátoru) vyvolá výjimku, není proveden blok `Catch` ve funkci iterátoru, ale je spuštěn blok `Finally` ve funkci iterátoru. `Catch` blok uvnitř funkce iterátoru zachytává pouze výjimky, ke kterým dojde uvnitř funkce iterátoru.

## <a name="partial-trust-situations"></a>Situace s částečnou důvěryhodností

V situacích s částečným vztahem důvěryhodnosti, jako je například aplikace hostovaná v síťové sdílené složce, `Try...Catch...Finally` nezachytí výjimky zabezpečení, ke kterým dojde před vyvoláním metody, která obsahuje volání. Následující příklad: když ho umístíte na sdílenou složku na serveru a spustíte z něj, vytvoří se chyba "System. Security. SecurityException: požadavek se nezdařil." Další informace o výjimkách zabezpečení naleznete v tématu Třída <xref:System.Security.SecurityException>.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

V takové situaci s částečným vztahem důvěryhodnosti je nutné vložit příkaz `Process.Start` do samostatné `Sub`. Počáteční volání `Sub` se nezdaří. To umožňuje `Try...Catch` zachytit před `Sub`, který obsahuje `Process.Start`, a vytvořenou výjimkou zabezpečení.

## <a name="examples"></a>Příklady

### <a name="the-structure-of-trycatchfinally"></a>Struktura try... Zachytit... Uznan

Následující příklad ukazuje strukturu příkazu `Try...Catch...Finally`.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Výjimka v metodě volané z bloku try

V následujícím příkladu metoda `CreateException` vyvolá `NullReferenceException`. Kód, který generuje výjimku, není v bloku `Try`. Proto metoda `CreateException` nezpracovává výjimku. Metoda `RunSample` zpracovává výjimku, protože volání metody `CreateException` je v bloku `Try`.

Příklad obsahuje příkazy `Catch` pro několik typů výjimek, seřazené od nejvyšších po nejobecnější.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Příkaz catch when

Následující příklad ukazuje, jak použít příkaz `Catch When` pro filtrování podmíněného výrazu. Pokud se podmíněný výraz vyhodnotí jako `True`, kód v bloku `Catch` se spustí.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>Vnořené příkazy try

Následující příklad obsahuje příkaz `Try…Catch`, který je obsažen v bloku `Try`. Vnitřní `Catch` blok vyvolá výjimku, která má svou vlastnost `InnerException` nastavenou na původní výjimku. Vnější `Catch` blok hlásí svou vlastní výjimku a vnitřní výjimku.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Zpracování výjimek pro asynchronní metody

Následující příklad znázorňuje zpracování výjimek pro asynchronní metody. Chcete-li zachytit výjimku, která se vztahuje na asynchronní úlohu, je výraz `Await` v bloku `Try` volajícího a výjimka je zachycena v bloku `Catch`.

Odkomentujte `Throw New Exception` řádek v příkladu k demonstraci zpracování výjimek. Výjimka je zachycena v bloku `Catch`, vlastnost `IsFaulted` úlohy je nastavena na hodnotu `True`a vlastnost `Exception.InnerException` úkolu je nastavena na výjimku.

Odkomentujte `Throw New OperationCancelledException` řádek k předvedení toho, co se stane, když zrušíte asynchronní proces. Výjimka je zachycena v bloku `Catch` a vlastnost `IsCanceled` úlohy je nastavena na `True`. Nicméně za určitých podmínek, které se na tento příklad nevztahují, `IsFaulted` je nastavené na `True` a `IsCanceled` je nastavená na `False`.

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Zpracování více výjimek v asynchronních metodách

Následující příklad znázorňuje zpracování výjimek, kde více úloh může mít za následek vícenásobné výjimky. `Try` blok má výraz `Await` pro úkol, který <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> vrácen. Úkol je dokončen, když jsou dokončeny tři úkoly, na které <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> použito.

Každá ze tří úkolů způsobuje výjimku. Blok `Catch` prochází výjimkami, které se nacházejí ve vlastnosti `Exception.InnerExceptions` úlohy, kterou `Task.WhenAll` vrátil.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Příkaz Exit](exit-statement.md)
- [Příkaz On Error](on-error-statement.md)
- [Doporučené postupy pro používání fragmentů kódu](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Zpracování výjimek](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Příkaz Throw](throw-statement.md)
