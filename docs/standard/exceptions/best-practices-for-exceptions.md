---
title: Osvědčené postupy pro výjimky – .NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: e12a83d3932d11baa086310ab0be23fb431459fc
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107194"
---
# <a name="best-practices-for-exceptions"></a>Osvědčené postupy pro výjimky

Za účelem zamezení pádu aplikace zpracovává dobře navržená aplikace výjimky a chyby. Tato část popisuje osvědčené postupy pro zpracování a vytváření výjimek.

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a>Pro zotavení z chyb nebo uvolnění prostředků použijte bloky try/catch/finally.

Používejte `try` bloky/kolem kódu, který může potenciálně generovat výjimku ***a*** váš kód může z této výjimky obnovit. `catch` V `catch` blocích vždy seřazení výjimek z největší odvozené na nejméně odvozené. Všechny výjimky jsou odvozeny z <xref:System.Exception>. Další odvozené výjimky nejsou zpracovány klauzulí catch, která předchází klauzuli catch pro základní třídu výjimky. Když se váš kód nemůže zotavit z výjimky, nezachyťte tuto výjimku. Pokud je to možné, povolte metody další v zásobníku volání pro obnovení.

Vyčistěte prostředky přidělené `using` buď pomocí příkazů `finally` , nebo bloků. Preferovat `using` příkazy k automatickému vyčištění prostředků, když jsou vyvolány výjimky. Pomocí `finally` bloků vyčistěte prostředky, které neimplementují <xref:System.IDisposable>. Kód v `finally` klauzuli je téměř vždy spouštěn i v případě, že jsou výjimky vyvolány.

## <a name="handle-common-conditions-without-throwing-exceptions"></a>Zpracování běžných podmínek bez vyvolání výjimek

Pro podmínky, které se pravděpodobně vyskytují, ale mohou aktivovat výjimku, zvažte jejich zpracování způsobem, který se vyhne výjimce. Například pokud se pokusíte zavřít připojení, které je již uzavřeno, získáte `InvalidOperationException`. Je možné vyhnout se tomu pomocí `if` příkazu ke kontrole stavu připojení před pokusem o jeho zavření.

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

Pokud před zavřením nezkontrolujete stav připojení, můžete `InvalidOperationException` výjimku zachytit.

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

Metoda, kterou zvolíte, závisí na tom, jak často očekáváte, že k události dojde.

- Použijte zpracování výjimek, pokud k události nedochází velmi často, tzn. pokud k události dochází výjimečně a značí chybu (jako například neočekávaný konec souboru). Při používání zpracování výjimek je za běžných podmínek provedena menší část kódu.

- Zkontroluje chybové podmínky v kódu, pokud k události dochází rutinně a mohla by být považována za součást normálního spuštění. Při kontrole běžných chybových stavů se spustí méně kódu, protože se vyhnete výjimkám.

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Třídy návrhu tak, aby bylo možné vyhnout se výjimkám

Třída může poskytovat metody nebo vlastnosti, které umožňují vyhnout se volání, které by aktivovalo výjimku. Například <xref:System.IO.FileStream> Třída poskytuje metody, které vám pomůžou určit, zda bylo dosaženo konce souboru. Ty lze použít k zamezení výjimky, která je vyvolána, pokud přečtení za koncem souboru. Následující příklad ukazuje, jak číst na konec souboru bez vyvolání výjimky.

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

Dalším způsobem, jak se vyhnout výjimkám, je vrátit hodnotu null (nebo výchozí) pro extrémně běžné chybové případy namísto vyvolání výjimky. Za nejběžnější případ chyby lze považovat běžný tok řízení. Vrácením hodnoty null (nebo výchozí) v těchto případech minimalizujete dopad na výkon aplikace.

Pro typy hodnot, zda se má `Nullable<T>` použít nebo jako výchozí používat jako indikátor chyb, je třeba zvážit konkrétní aplikaci. Pomocí `Nullable<Guid>`, `default` se místo`null` . `Guid.Empty` V některých případech se `Nullable<T>` dá přidat, takže pokud je hodnota přítomná nebo chybí, může to být jasné. Jinak přidávání `Nullable<T>` může vytvořit další případy, které kontrolují, že nepotřebujete, a sloužit jenom k vytváření potenciálních zdrojů chyb. 

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Vyvolat výjimky místo vrácení kódu chyby

Výjimky zajišťují, že chyby nejdou nekontrolují, protože volání kódu nevrátilo návratový kód.

## <a name="use-the-predefined-net-exception-types"></a>Použít předdefinované typy výjimek .NET

Zaveďte novou třídu výjimky pouze v případě, že není použita předdefinovaná. Příklad:

- Vyvolejte <xref:System.InvalidOperationException> výjimku, pokud sada vlastností nebo volání metody není vhodné vzhledem k aktuálnímu stavu objektu.

- Vyvolejte <xref:System.ArgumentException> výjimku nebo jednu z předdefinovaných tříd, které jsou odvozeny z, pokud jsou předány neplatné parametry. <xref:System.ArgumentException>

## <a name="end-exception-class-names-with-the-word-exception"></a>Ukončení názvů tříd výjimek pomocí slova`Exception`

Pokud je nezbytná vlastní výjimka, pojmenujte ji odpovídajícím způsobem a odvodit ji od <xref:System.Exception> třídy. Příklad:

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a>Zahrnout tři konstruktory do vlastních tříd výjimek

Při vytváření vlastních tříd výjimek použijte alespoň tři společné konstruktory: konstruktor bez parametrů, konstruktor, který přijímá zprávu řetězce, a konstruktor, který přijímá zprávu řetězce a vnitřní výjimku.

- <xref:System.Exception.%23ctor>, který používá výchozí hodnoty.

- <xref:System.Exception.%23ctor%28System.String%29>, který přijímá řetězcovou zprávu.

- <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, který přijímá řetězcovou zprávu a vnitřní výjimku.

Příklad naleznete v tématu [How to: Vytvořte uživatelsky definované výjimky](how-to-create-user-defined-exceptions.md).

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Ujistěte se, že data výjimky jsou k dispozici, když se kód spustí vzdáleně.

Při vytváření uživatelem definovaných výjimek se ujistěte, že metadata pro výjimky jsou k dispozici pro kód, který se spouští vzdáleně.

Například u implementací rozhraní .NET, které podporují aplikační domény, se může vyskytnout výjimka napříč doménami aplikace. Předpokládejme, že doména aplikace A vytvoří doménu aplikace B, která spustí kód, který vyvolá výjimku. Aby mohla doména aplikace A správně zachytit a zpracovat výjimku, musí být schopna najít sestavení, které obsahuje výjimku vyvolanou aplikační doménou B. Pokud doména aplikace B vyvolá výjimku, která je obsažena v sestavení v rámci jeho základu aplikace, ale ne v rámci databáze aplikace a, domény aplikace a nebude schopna najít výjimku a modul CLR vyvolá <xref:System.IO.FileNotFoundException> výjimku. Této situaci zamezíte tak, že nasadíte sestavení obsahující informace o výjimce dvěma způsoby:

- Sestavení umístěte do společného základu cesty aplikace sdíleného oběma doménami aplikace.

    \- nebo –

- Pokud domény nesdílejí společný základ cesty aplikace, podepište sestavení obsahující informace o výjimce silným názvem a nasaďte sestavení do globální mezipaměti sestavení (GAC).

## <a name="use-grammatically-correct-error-messages"></a>Použití gramaticky správných chybových zpráv

Pište jasné věty a zahrňte koncovou interpunkci. Každá věta v řetězci přiřazená <xref:System.Exception.Message?displayProperty=nameWithType> vlastnosti by měla končit tečkou. Například "došlo k přetečení tabulky protokolu". by byl vhodný řetězec zprávy.

## <a name="include-a-localized-string-message-in-every-exception"></a>Zahrnout do každé výjimky lokalizovanou zprávu řetězce

Chybová zpráva, kterou uživatel vidí, je odvozena z <xref:System.Exception.Message?displayProperty=nameWithType> vlastnosti výjimky, která byla vyvolána, a nikoli z názvu třídy Exception. Obvykle přiřadíte hodnotu k <xref:System.Exception.Message?displayProperty=nameWithType> vlastnosti předáním řetězce `message` zprávy argumentu [konstruktoru výjimky](xref:System.Exception.%23ctor%2A).

Pro lokalizované aplikace byste měli poskytnout lokalizovaný řetězec zprávy pro všechny výjimky, které může vaše aplikace vyvolat. Soubory prostředků můžete použít k poskytnutí lokalizovaných chybových zpráv. Informace o lokalizaci aplikací a načítání lokalizovaných řetězců naleznete v tématu [prostředky v aplikacích klasické pracovní plochy](../../framework/resources/index.md) a <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>V možnosti vlastní výjimky zadejte podle potřeby další vlastnosti.

Poskytněte další vlastnosti pro výjimku (kromě vlastního řetězce zprávy) pouze v případě, že existuje programový scénář, kde jsou další informace užitečné. <xref:System.IO.FileNotFoundException> Například<xref:System.IO.FileNotFoundException.FileName> poskytuje vlastnost.

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Umístěte příkazy throw tak, aby trasování zásobníku bylo užitečné.

Trasování zásobníku začíná příkazem, kde je vyvolána výjimka a končí v `catch` příkazu, který zachycuje výjimku.

## <a name="use-exception-builder-methods"></a>Použití metod Tvůrce výjimek

Pro třídu je běžné vyvolat stejnou výjimku z různých míst v rámci příslušné implementace. Abyste zabránili nadbytečnému kódu, použijte pomocné metody k vytvoření výjimky a vrácení výjimky. Příklad:

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

V některých případech je vhodnější použít konstruktor výjimky k sestavení výjimky. Příkladem je globální třída výjimek, jako je <xref:System.ArgumentException>.

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a>Obnovit stav, když se metody nedokončují kvůli výjimkám

Volající by měl předpokládat, že při vyvolání výjimky z metody nedojde k žádným vedlejším účinkům. Například pokud máte kód, který přenáší peníze odebráním z jednoho účtu a uložením do jiného účtu, a při provádění zálohy dojde k výjimce, nechcete, aby stažení zůstalo v platnosti.

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

Výše uvedená metoda přímo nevyvolává žádné výjimky, ale musí být zapsána defensively, aby v případě, že operace vkladu nebyla úspěšná, je zrušení vrácení zpět.

Jedním ze způsobů, jak tuto situaci zpracovat, je zachytit jakékoli výjimky vyvolané vkladovou transakcí a vrátit zpět odstoupení.

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

Tento příklad znázorňuje použití `throw` pro opětovné vyvolání původní výjimky, která může usnadnit volajícím zobrazit skutečnou příčinu problému bez nutnosti <xref:System.Exception.InnerException> prozkoumávat vlastnost. Alternativou je vyvolat novou výjimku a zahrnout původní výjimku jako vnitřní výjimku:

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

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
