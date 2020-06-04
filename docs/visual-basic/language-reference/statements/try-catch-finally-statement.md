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
ms.openlocfilehash: 22f1611786a3da512632b5b547b7ef141c8f65c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391765"
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

|Pojem|Definice|
|---|---|
|`tryStatements`|Nepovinný parametr. Příkazy, kde může dojít k chybě. Může být složený příkaz.|
|`Catch`|Nepovinný parametr. Je `Catch` povoleno více bloků. Pokud při zpracování bloku dojde k výjimce `Try` , `Catch` je každý příkaz zkontrolován v textovém pořadí, aby bylo možné určit, zda zpracovává výjimku, a `exception` představuje výjimku, která byla vyvolána.|
|`exception`|Nepovinný parametr. Libovolný název proměnné. Počáteční hodnota `exception` je hodnota vyvolané chyby. Používá se s `Catch` k určení zjištěné chyby. Je-li tento parametr vynechán, `Catch` příkaz zachytí jakoukoli výjimku.|
|`type`|Nepovinný parametr. Určuje typ filtru třídy. Pokud hodnota `exception` je typu určeném `type` nebo odvozeným typem, bude identifikátor svázán s objektem výjimky.|
|`When`|Nepovinný parametr. `Catch`Příkaz s `When` klauzulí zachycuje výjimky pouze v případě `expression` , že je vyhodnocen jako `True` . `When`Klauzule je použita pouze po kontrole typu výjimky a `expression` může odkazovat na identifikátor představující výjimku.|
|`expression`|Nepovinný parametr. Musí být implicitně převoditelné na `Boolean` . Libovolný výraz, který popisuje obecný filtr. Obvykle se používá k filtrování podle čísla chyby. Používá se s `When` klíčovým slovem k určení podmínek, za kterých se zachytí chyba.|
|`catchStatements`|Nepovinný parametr. Příkazy pro zpracování chyb, ke kterým došlo v přidruženém `Try` bloku. Může být složený příkaz.|
|`Exit Try`|Nepovinný parametr. Klíčové slovo, které se rozdělí ze `Try...Catch...Finally` struktury. Spuštění pokračuje pomocí kódu hned po `End Try` příkazu. `Finally`Příkaz bude stále proveden. Nepovoluje se v `Finally` blocích.|
|`Finally`|Nepovinný parametr. `Finally`Blok je vždy proveden, pokud provádění opustí jakoukoli část `Try...Catch` příkazu.|
|`finallyStatements`|Nepovinný parametr. Příkazy, které se spustí po všech ostatních zpracováních chyb.|
|`End Try`|Ukončí `Try...Catch...Finally` strukturu.|

## <a name="remarks"></a>Poznámky

Pokud očekáváte, že konkrétní výjimka může nastat během konkrétní části kódu, vložte kód do `Try` bloku a pomocí `Catch` bloku zachovejte kontrolu a zpracujte výjimku, pokud k ní dojde.

`Try…Catch`Příkaz se skládá z `Try` bloku následovaného jednou nebo více `Catch` klauzulemi, které určují obslužné rutiny pro různé výjimky. Je-li v bloku vyvolána výjimka `Try` , Visual Basic vyhledá `Catch` příkaz, který zpracovává výjimku. Pokud nebyl `Catch` nalezen odpovídající příkaz, Visual Basic prověřuje metodu, která volala aktuální metodu, a tak dále v zásobníku volání. Pokud `Catch` není nalezen žádný blok, Visual Basic zobrazí uživateli neošetřenou zprávu o výjimce a zastaví provádění programu.

V příkazu lze použít více než jeden `Catch` příkaz `Try…Catch` . V takovém případě `Catch` je pořadí klauzulí významné, protože jsou zkontrolovány v pořadí. Zachyťte konkrétnější výjimky před méně specifickými výjimkami.

Následující `Catch` podmínky příkazu jsou nejméně specifické a budou zachytit všechny výjimky, které jsou odvozeny z <xref:System.Exception> třídy. Jednu z těchto variant byste měli obvykle používat jako poslední `Catch` blok ve `Try...Catch...Finally` struktuře, a to po zachycení všech konkrétních výjimek, které očekáváte. Tok řízení nemůže nikdy dosáhnout `Catch` bloku, který následuje po jedné z těchto variant.

- `type`Je `Exception` například:`Catch ex As Exception`

- Příkaz nemá žádnou `exception` proměnnou, například:`Catch`

Když `Try…Catch…Finally` je příkaz vnořený do jiného `Try` bloku, Visual Basic nejprve prověřuje každý `Catch` příkaz v nejvnitřnějším `Try` bloku. Pokud `Catch` není nalezen žádný vyhovující příkaz, hledání pokračuje na `Catch` příkazy vnějšího `Try…Catch…Finally` bloku.

Lokální proměnné z `Try` bloku nejsou v bloku k dispozici, `Catch` protože se jedná o samostatné bloky. Pokud chcete použít proměnnou ve více než jednom bloku, deklarujte proměnnou mimo `Try...Catch...Finally` strukturu.

> [!TIP]
> `Try…Catch…Finally`Příkaz je k dispozici jako fragment kódu technologie IntelliSense. Ve Správci fragmentů kódu rozbalte položku **vzory kódu – Pokud pro každou, zkuste zachytit, vlastnost atd**. a pak **zpracování chyb (výjimky)**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Blok finally

Pokud máte jeden nebo více příkazů, které musí být spuštěny před ukončením `Try` struktury, použijte `Finally` blok. Řízení se předá do `Finally` bloku těsně před tím, než se předává ze `Try…Catch` struktury. To platí i v případě, že dojde k výjimce kdekoli uvnitř `Try` struktury.

`Finally`Blok je vhodný pro spuštění libovolného kódu, který musí být proveden, i v případě, že dojde k výjimce. Ovládací prvek se předává do `Finally` bloku bez ohledu na to, jak se `Try...Catch` blok ukončí.

Kód v `Finally` bloku běží i v případě, že váš kód nalezne `Return` příkaz v `Try` bloku nebo `Catch` . Ovládací prvek neprojde z `Try` bloku nebo `Catch` do odpovídajícího `Finally` bloku v následujících případech:

- V bloku nebo byl nalezen [příkaz end](end-statement.md) `Try` `Catch` .

- <xref:System.StackOverflowException>V bloku nebo je vyvolána `Try` výjimka `Catch` .

Explicitní přenos spuštění do bloku není platný `Finally` . Přenos provádění z `Finally` bloku není platný, s výjimkou výjimky.

Pokud `Try` příkaz neobsahuje alespoň jeden `Catch` blok, musí obsahovat `Finally` blok.

> [!TIP]
> Pokud nemusíte zachytit konkrétní výjimky, `Using` příkaz se chová jako `Try…Finally` blok a zaručuje odstranění prostředků bez ohledu na to, jak tento blok ukončujete. To je pravdivé i s neošetřenou výjimkou. Další informace naleznete v tématu [using – příkaz](using-statement.md).

## <a name="exception-argument"></a>Argument výjimky

`Catch`Argument Block `exception` je instance <xref:System.Exception> třídy nebo třídy, která je odvozena od `Exception` třídy. `Exception`Instance třídy odpovídá chybě, ke které došlo v `Try` bloku.

Vlastnosti `Exception` objektu usnadňují identifikaci příčiny a umístění výjimky. Například <xref:System.Exception.StackTrace%2A> vlastnost zobrazuje seznam volaných metod, které vedly k výjimce, což pomáhá najít, kde došlo k chybě v kódu. <xref:System.Exception.Message%2A>Vrátí zprávu popisující výjimku. <xref:System.Exception.HelpLink%2A>Vrátí odkaz na související soubor Help. <xref:System.Exception.InnerException%2A>Vrátí `Exception` objekt, který způsobil aktuální výjimku, nebo vrátí, `Nothing` Pokud není k dispozici žádný originál `Exception` .

## <a name="considerations-when-using-a-trycatch-statement"></a>Doporučení při použití try... Catch – příkaz

Použijte `Try…Catch` příkaz pouze k signalizaci výskytu neobvyklých nebo neočekávaných událostí programu. K tomu patří následující důvody:

- Zachycování výjimek za běhu vytváří další režii a je pravděpodobně pomalejší než předběžná kontrola, aby nedocházelo k výjimkám.

- Pokud `Catch` blok není správně zpracován, výjimka nemusí být správně hlášena uživatelům.

- Zpracování výjimek způsobuje složitější program.

`Try…Catch`K kontrole podmínky, která může nastat, není vždy potřeba příkaz. Následující příklad zkontroluje, zda soubor existuje, než se pokusí ho otevřít. To snižuje nutnost zachycení výjimky vyvolané <xref:System.IO.File.OpenText%2A> metodou.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

Zajistěte, aby kód v `Catch` blocích mohl správně hlásit výjimky uživatelům, ať už prostřednictvím protokolování bezpečného pro přístup z více vláken, nebo odpovídajících zpráv. V opačném případě mohou výjimky zůstat neznámé.

## <a name="async-methods"></a>Asynchronní metody

Pokud označíte metodu pomocí modifikátoru [Async](../modifiers/async.md) , můžete použít operátor [await](../operators/await-operator.md) v metodě. Příkaz s `Await` operátorem pozastaví provádění metody až do dokončení očekávané úlohy. Úkol představuje probíhající práci. Po dokončení úlohy, která je přidružena k `Await` operátoru, provádění pokračuje ve stejné metodě. Další informace najdete v tématu [řízení toku v asynchronních programech](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Úloha vrácená asynchronní metodou může končit chybovým stavem, což značí, že byla dokončena z důvodu neošetřené výjimky. Úloha může také končit zrušeným stavem, což má za následek vystavení `OperationCanceledException` vyvolaného výrazu await. Chcete-li zachytit buď typ výjimky, umístěte `Await` výraz, který je přidružen k úloze v `Try` bloku, a zachyťte výjimku v `Catch` bloku. Příklad je uveden dále v tomto tématu.

Úloha může být v chybném stavu, protože za její chybu byla zodpovědná více výjimek. Například úloha může být výsledkem volání metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> . Při čekání na takovou úlohu je zachycená výjimka pouze jedna z výjimek a nelze předpovědět, která výjimka bude zachycena. Příklad je uveden dále v tomto tématu.

`Await`Výraz nemůže být uvnitř `Catch` bloku nebo `Finally` bloku.

## <a name="iterators"></a>Iterátory

Funkce iterátoru nebo `Get` přistupující objekt provádí vlastní iteraci v kolekci. Iterátor používá příkaz [yield](yield-statement.md) k vrácení každého prvku kolekce v jednom okamžiku. Vyvoláte funkci iterátoru pomocí metody [for each... Další příkaz](for-each-next-statement.md).

`Yield`Příkaz může být uvnitř `Try` bloku. `Try`Blok, který obsahuje `Yield` příkaz, může mít `Catch` bloky a může mít `Finally` blok. Příklad naleznete v části "try Blocks in Visual Basic" v tématu [iterátory](../../programming-guide/concepts/iterators.md) .

`Yield`Příkaz nemůže být uvnitř `Catch` bloku nebo `Finally` bloku.

Pokud `For Each` tělo (mimo funkci iterátoru) vyvolá výjimku, není `Catch` proveden blok ve funkci iterátoru, ale `Finally` je proveden blok ve funkci iterátoru. `Catch`Blok uvnitř funkce iterátoru zachytává pouze výjimky, ke kterým dojde uvnitř funkce iterátoru.

## <a name="partial-trust-situations"></a>Situace s částečnou důvěryhodností

V situacích s částečnou důvěryhodností, jako je například aplikace hostovaná v síťové sdílené složce, `Try...Catch...Finally` nezachytí výjimky zabezpečení, ke kterým dojde před vyvoláním metody, která obsahuje volání. Následující příklad: když ho umístíte na sdílenou složku na serveru a spustíte z něj, vytvoří se chyba "System. Security. SecurityException: požadavek se nezdařil." Další informace o výjimkách zabezpečení naleznete v tématu <xref:System.Security.SecurityException> Třída.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

V takové situaci s částečným vztahem důvěryhodnosti je nutné příkaz Vložit `Process.Start` do samostatného `Sub` . Prvotní volání metody se `Sub` nezdaří. To umožňuje `Try...Catch` jejich zachycení před spuštěním `Sub` , který obsahuje, `Process.Start` a vyprodukováním výjimky zabezpečení.

## <a name="examples"></a>Příklady

### <a name="the-structure-of-trycatchfinally"></a>Struktura try... Zachytit... Uznan

Následující příklad ukazuje strukturu `Try...Catch...Finally` příkazu.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Výjimka v metodě volané z bloku try

V následujícím příkladu `CreateException` metoda vyvolá výjimku `NullReferenceException` . Kód, který generuje výjimku, není v `Try` bloku. Proto `CreateException` Metoda nezpracovává výjimku. `RunSample`Metoda zpracovává výjimku, protože volání `CreateException` metody je v `Try` bloku.

Příklad obsahuje `Catch` příkazy pro několik typů výjimek, seřazené od nejobecnější po největší.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Příkaz catch when

Následující příklad ukazuje, jak použít `Catch When` příkaz pro filtrování podmíněného výrazu. Pokud se podmíněný výraz vyhodnotí jako `True` , kód v `Catch` bloku se spustí.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>Vnořené příkazy try

Následující příklad obsahuje `Try…Catch` příkaz, který je obsažen v `Try` bloku. Vnitřní `Catch` blok vyvolá výjimku, která má svou `InnerException` vlastnost nastavenou na původní výjimku. Vnější `Catch` blok hlásí svou vlastní výjimku a vnitřní výjimku.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Zpracování výjimek pro asynchronní metody

Následující příklad znázorňuje zpracování výjimek pro asynchronní metody. Chcete-li zachytit výjimku, která se vztahuje na asynchronní úlohu, `Await` je výraz v `Try` bloku volajícího a výjimka je zachycena v `Catch` bloku.

Odkomentujte `Throw New Exception` řádek v příkladu k demonstraci zpracování výjimek. Výjimka je zachycena v `Catch` bloku, `IsFaulted` vlastnost úlohy je nastavena na hodnotu `True` a `Exception.InnerException` vlastnost úkolu je nastavena na výjimku.

Odkomentujte `Throw New OperationCancelledException` řádek k předvedení toho, co se stane, když zrušíte asynchronní proces. Výjimka je zachycena v `Catch` bloku a `IsCanceled` vlastnost úlohy je nastavena na hodnotu `True` . Nicméně za určitých podmínek, které se nevztahují na tento příklad, `IsFaulted` je nastavena na `True` a `IsCanceled` je nastavena na `False` .

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Zpracování více výjimek v asynchronních metodách

Následující příklad znázorňuje zpracování výjimek, kde více úloh může mít za následek vícenásobné výjimky. `Try`Blok má `Await` výraz pro <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> vrácenou úlohu. Úkol je dokončen, když jsou dokončeny tři úkoly, na které <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> se vztahují.

Každá ze tří úkolů způsobuje výjimku. `Catch`Blok prochází výjimky, které jsou umístěny ve `Exception.InnerExceptions` vlastnosti `Task.WhenAll` vrácené úlohy.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit – příkaz](exit-statement.md)
- [On Error – příkaz](on-error-statement.md)
- [Doporučené postupy pro používání fragmentů kódu](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Zpracování výjimek](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw – příkaz](throw-statement.md)
