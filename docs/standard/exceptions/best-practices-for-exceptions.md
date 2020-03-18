---
title: Doporučené postupy pro výjimky - .NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 1de231b01e3fa97e78a87ae6b0595a9b5536374e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160167"
---
# <a name="best-practices-for-exceptions"></a>Doporučené postupy pro výjimky

Za účelem zamezení pádu aplikace zpracovává dobře navržená aplikace výjimky a chyby. Tato část popisuje osvědčené postupy pro zpracování a vytváření výjimek.

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a>Pomocí bloků try/catch/finally se zotavit z chyb nebo uvolnit prostředky

`try` / Použijte `catch` bloky kolem kódu, který může potenciálně generovat výjimku ***a*** váš kód můžete obnovit z této výjimky. V `catch` blocích vždy seřizovat výjimky z nejvíce odvozené nejméně odvozené. Všechny výjimky <xref:System.Exception>jsou odvozeny z . Více odvozené výjimky nejsou zpracovány catch klauzule, která předchází catch klauzule pro základní třídy výjimek. Pokud váš kód nelze obnovit z výjimky, nezachytávejte tuto výjimku. Povolit metody dále nahoru zásobníku volání obnovit, pokud je to možné.

Vyčištění prostředků přidělených `using` buď příkazy nebo `finally` bloky. Preferovat `using` příkazy automaticky vyčistit prostředky při vyvolání výjimky. Pomocí `finally` bloků vyčistěte prostředky, které <xref:System.IDisposable>se neimplementují . Kód v `finally` klauzuli je téměř vždy spuštěn, i když jsou vyvolány výjimky.

## <a name="handle-common-conditions-without-throwing-exceptions"></a>Zpracování běžných podmínek bez vyvolání výjimek

Pro podmínky, které mohou nastat, ale může vyvolat výjimku, zvažte jejich zpracování způsobem, který zabrání výjimce. Pokud se například pokusíte ukončit připojení, které je `InvalidOperationException`již uzavřeno, získáte . Můžete se tomu vyhnout `if` pomocí příkazu ke kontrole stavu připojení před pokusem o jeho zavření.

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

Pokud před zavřením nezkontrolujete stav připojení, můžete výjimku `InvalidOperationException` zachytit.

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

Metoda, kterou zvolit, závisí na tom, jak často očekáváte, že k události dojde.

- Použijte zpracování výjimek, pokud k události nedochází velmi často, tzn. pokud k události dochází výjimečně a značí chybu (jako například neočekávaný konec souboru). Při používání zpracování výjimek je za běžných podmínek provedena menší část kódu.

- Zkontrolujte chybové stavy v kódu, pokud k události dochází rutinně a může být považována za součást normálního spuštění. Při kontrole běžných chybových stavů je spuštěno méně kódu, protože se vyhnete výjimkám.

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Navrhujte třídy tak, aby se zabránilo výjimkám

Třída může poskytnout metody nebo vlastnosti, které umožňují vyhnout se volání, které by spustilo výjimku. Například <xref:System.IO.FileStream> třída poskytuje metody, které pomáhají určit, zda bylo dosaženo konce souboru. Ty lze použít, aby se zabránilo výjimku, která je vyvolána, pokud čtete za koncem souboru. Následující příklad ukazuje, jak číst až do konce souboru bez spuštění výjimky.

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

Dalším způsobem, jak se vyhnout výjimkám, je vrátit hodnotu null (nebo výchozí) pro extrémně běžné chybové případy namísto vyvolání výjimky. Za nejběžnější případ chyby lze považovat běžný tok řízení. Vrácením null (nebo výchozí) v těchto případech minimalizovat dopad na výkon aplikace.

Pro typy hodnot, `Nullable<T>` zda použít nebo výchozí jako indikátor chyby je něco, co je třeba zvážit pro konkrétní aplikaci. Pomocí `Nullable<Guid>`aplikace `default` `null` se `Guid.Empty`místo aplikace stane . Někdy, přidání `Nullable<T>` může být jasnější, když je hodnota přítomna nebo chybí. Jindy přidání `Nullable<T>` můžete vytvořit další případy pro kontrolu, které nejsou nutné a slouží pouze k vytvoření potenciální zdroje chyb.

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Vyvolat výjimky namísto vrácení kódu chyby

Výjimky zajišťují, že chyby nezůstávají bez povšimnutí, protože volající kód nezkontroloval návratový kód.

## <a name="use-the-predefined-net-exception-types"></a>Použití předdefinovaných typů výjimek .NET

Zavést novou třídu výjimek pouze v případě, že se nepoužije předdefinovaná třída. Například:

- Vyvolat <xref:System.InvalidOperationException> výjimku, pokud sada vlastností nebo volání metody není vhodné vzhledem k aktuálnímu stavu objektu.

- Vyvolat <xref:System.ArgumentException> výjimku nebo jednu z předdefinovaných tříd, které jsou odvozeny z <xref:System.ArgumentException> pokud jsou předány neplatné parametry.

## <a name="end-exception-class-names-with-the-word-exception"></a>Ukončení názvů tříd výjimek se slovem`Exception`

Pokud je nutná vlastní výjimka, pojmenujte <xref:System.Exception> ji odpovídajícím způsobem a odvodte ji z třídy. Například:

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a>Zahrnout tři konstruktory do vlastních tříd výjimek

Při vytváření vlastních tříd výjimek použijte alespoň tři běžné konstruktory: konstruktor bez parametrů, konstruktor, který přebírá zprávu řetězce, a konstruktor, který přebírá zprávu řetězce a vnitřní výjimku.

- <xref:System.Exception.%23ctor>, který používá výchozí hodnoty.

- <xref:System.Exception.%23ctor%28System.String%29>, který přijímá zprávu řetězce.

- <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, který přijímá zprávu řetězce a vnitřní výjimku.

Příklad najdete v [tématu How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Ujistěte se, že data výjimky jsou k dispozici při vzdáleném spuštění kódu

Při vytváření uživatelem definovaných výjimek se ujistěte, že metadata pro výjimky jsou k dispozici pro kód, který je spuštěn vzdáleně.

Například na implementacích rozhraní .NET, které podporují domény aplikací, mohou v doménách aplikací nastat výjimky. Předpokládejme, že doména aplikace A vytvoří doménu aplikace B, která spustí kód, který vyvolá výjimku. Pro doménu aplikace A správně zachytit a zpracovat výjimku, musí být schopen najít sestavení, které obsahuje výjimku vyváděnou doménou aplikace B. Pokud doména aplikace B vyvolá výjimku, která je obsažena v sestavení v rámci jeho aplikační základny, ale ne v rámci aplikační základny domény <xref:System.IO.FileNotFoundException> aplikace, doména aplikace A nebude moci najít výjimku a za běhu společného jazyka vyvolá výjimku. Této situaci zamezíte tak, že nasadíte sestavení obsahující informace o výjimce dvěma způsoby:

- Sestavení umístěte do společného základu cesty aplikace sdíleného oběma doménami aplikace.

    \-nebo -

- Pokud domény nesdílejí společný základ cesty aplikace, podepište sestavení obsahující informace o výjimce silným názvem a nasaďte sestavení do globální mezipaměti sestavení (GAC).

## <a name="use-grammatically-correct-error-messages"></a>Použití gramaticky správných chybových zpráv

Napište jasné věty a zahrňte koncovou interpunkci. Každá věta v řetězci přiřazené vlastnosti <xref:System.Exception.Message?displayProperty=nameWithType> by měla končit tečkou. Například "Tabulka protokolu přetekl." by byl vhodný řetězec zprávy.

## <a name="include-a-localized-string-message-in-every-exception"></a>Zahrnout lokalizovanou zprávu řetězce do každé výjimky

Chybová zpráva, která se zobrazí uživatel <xref:System.Exception.Message?displayProperty=nameWithType> je odvozen z vlastnosti výjimky, která byla vyvolána a nikoli z názvu třídy výjimky. Obvykle přiřadíte hodnotu <xref:System.Exception.Message?displayProperty=nameWithType> vlastnosti předáním řetězce `message` zprávy argumentu [konstruktoru Exception](xref:System.Exception.%23ctor%2A).

Pro lokalizované aplikace byste měli zadat řetězec lokalizované zprávy pro každou výjimku, kterou může aplikace vyvolat. Soubory prostředků se používají k poskytování lokalizovaných chybových zpráv. Informace o lokalizaci aplikací a načítání lokalizovaných řetězců naleznete v následujících článcích:

- [Postupy: Vytváření uživatelsky definovaných výjimek s lokalizovanými zprávami výjimek](how-to-create-localized-exception-messages.md)
- [Prostředky v aplikacích klasické pracovní plochy](../../framework/resources/index.md)
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>Ve vlastních výjimkách poskytněte podle potřeby další vlastnosti.

Zadejte další vlastnosti pro výjimku (kromě řetězce vlastní zprávy) pouze v případě, že existuje programový scénář, kde jsou užitečné další informace. Například poskytuje <xref:System.IO.FileNotFoundException> <xref:System.IO.FileNotFoundException.FileName> vlastnost.

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Umístit příkazy throw tak, aby trasování zásobníku bylo užitečné

Trasování zásobníku začíná na příkaz, kde je vyvolána výjimka a končí na `catch` příkaz, který zachytí výjimku.

## <a name="use-exception-builder-methods"></a>Použití metod tvůrce výjimek

Pro třídu je běžné vyvolat stejnou výjimku z různých míst v rámci příslušné implementace. Abyste zabránili nadbytečnému kódu, použijte pomocné metody k vytvoření výjimky a vrácení výjimky. Například:

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

V některých případech je vhodnější použít konstruktor výjimky k vytvoření výjimky. Příkladem je globální třída výjimek, například <xref:System.ArgumentException>.

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a>Obnovit stav, když metody nejsou dokončeny z důvodu výjimek

Volající by měl předpokládat, že při vyvolání výjimky z metody nedojde k žádným vedlejším účinkům. Máte-li například kód, který převádí peníze výběrem z jednoho účtu a uložením na jiný účet, a při provádění vkladu je vyvolána výjimka, nechcete, aby výběr zůstal v platnosti.

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect.
    to.Deposit(amount);
}
```

```vb
Public Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    from.Withdrawal(amount)
    ' If the deposit fails, the withdrawal shouldn't remain in effect.
    [to].Deposit(amount)
End Sub
```

Výše uvedená metoda nevyvolá žádné výjimky, ale musí být napsána defenzivně, takže pokud operace vkladu selže, výběr je obrácen.

Jedním ze způsobů, jak tuto situaci zvládnout, je zachytit všechny výjimky vyvržené vkladovou transakcí a vrátit zpět výběr.

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

```vb
Private Shared Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    Dim withdrawalTrxID As String = from.Withdrawal(amount)
    Try
        [to].Deposit(amount)
    Catch
        from.RollbackTransaction(withdrawalTrxID)
        Throw
    End Try
End Sub
```

Tento příklad ilustruje použití `throw` znovu vyvolat původní výjimku, která může usnadnit volajícím zobrazit skutečnou příčinu <xref:System.Exception.InnerException> problému bez nutnosti zkoumat vlastnost. Alternativou je vyvolat novou výjimku a zahrnout původní výjimku jako vnitřní výjimku:

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed.", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

```vb
Catch ex As Exception
    from.RollbackTransaction(withdrawalTrxID)
    Throw New TransferFundsException("Withdrawal failed.", innerException:=ex) With
    {
        .From = from,
        .[To] = [to],
        .Amount = amount
    }
End Try
```

## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
