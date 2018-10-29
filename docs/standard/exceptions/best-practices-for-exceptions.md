---
title: Doporučené postupy pro výjimky
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6aa1049c531550687a2c6289ccd87e763ca2f58
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199627"
---
# <a name="best-practices-for-exceptions"></a>Doporučené postupy pro výjimky

Za účelem zamezení pádu aplikace zpracovává dobře navržená aplikace výjimky a chyby. Tato část popisuje osvědčené postupy pro zpracování a vytváření výjimek.

## <a name="use-trycatchfinally-blocks"></a>Pomocí konstrukce try/catch/finally bloky

Použití `try` / `catch` / `finally` okolo kódu, který může potenciálně generovat výjimku. 

V `catch` blokuje vždy nutné výjimky seřazovat od nejkonkrétnější po nejméně konkrétní.

Použití `finally` bloku pro vyčištění prostředků, zda lze obnovit nebo ne.

## <a name="handle-common-conditions-without-throwing-exceptions"></a>Zpracování běžných podmínek bez vyvolání výjimky

Podmínky, které by mohly nastat, ale může být spuštění výjimky, zvažte jejich zpracování tak, aby se vyhnete výjimku. Například pokud se pokusíte uzavřít připojení, který je už zavřený, získáte `InvalidOperationException`. Který můžete vyhnout použitím `if` příkaz a zkontrolujte stav připojení před dalším pokusem ho zavřít.

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

Pokud se nezaregistrují stav připojení před zavřením, můžete zachytit `InvalidOperationException` výjimky.

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

Metoda zvolit, závisí na očekáváte, jak často má k události docházet.

- Použijte zpracování výjimek, pokud k události nedochází velmi často, tzn. pokud k události dochází výjimečně a značí chybu (jako například neočekávaný konec souboru). Při používání zpracování výjimek je za běžných podmínek provedena menší část kódu.

- Pokud k události dochází rutinně a může být považována za součást běžného provedení Zkontrolujte chybové stavy v kódu. Při kontrole běžné chybové stavy, menší část kódu je provést, protože byste se vyhnout výjimky.

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Třídy Navrhujte tak, aby výjimky se můžete vyhnout.

Třída může poskytnout metody nebo vlastnosti, které vám umožní vyhnout volání, která se aktivuje výjimku. Například <xref:System.IO.FileStream> třída poskytuje metody, které pomáhají určit, zda bylo dosaženo konce souboru. Ty je možné, aby výjimka, která je vyvolána, pokud čtení za koncem souboru. Následující příklad znázorňuje způsob čtení do konce souboru bez vyvolání výjimky.

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

Jiný způsob, jak zabránit výjimky je k vrácení hodnoty null pro nejběžnější případy chyb namísto vyvolání výjimky. Za nejběžnější případ chyby lze považovat běžný tok řízení. Vrácením hodnoty null v těchto případech minimalizujete dopad výkonu pro aplikaci.

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Vyvolat výjimky místo vrácení chybový kód

Výjimky Ujistěte se, že selhání nedojde protože volání, že kód nezaškrtli návratový kód. 

## <a name="use-the-predefined-net-exception-types"></a>Použijte předdefinované typy výjimek .NET

Zavádí novou třídu výjimek pouze v případě, že neplatí předdefinované jeden. Příklad:

- Vyvolání <xref:System.InvalidOperationException> výjimku, pokud vlastnost set nebo metoda volání není vhodné aktuální stav objektu.

- Vyvolání <xref:System.ArgumentException> výjimky nebo jeden z předdefinovaných tříd, které jsou odvozeny z <xref:System.ArgumentException> Pokud jsou předány neplatné parametry.

## <a name="end-exception-class-names-with-the-word-exception"></a>Názvy tříd výjimek ukončujte slovem End `Exception`

Při vlastní výjimky je nezbytné, pojmenujte ji odpovídajícím způsobem a odvozovat z <xref:System.Exception> třídy. Příklad:

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a>Zahrnout tři konstruktory ve třídách vlastní výjimky

Použijte aspoň tři běžné konstruktory při vytváření vlastních tříd výjimek: výchozí konstruktor, konstruktor, který přijímá řetězcovou zprávu a konstruktor, který přijímá řetězcovou zprávu a vnitřní výjimku.

* <xref:System.Exception.%23ctor>, který používá výchozí hodnoty.
  
* <xref:System.Exception.%23ctor%28System.String%29>, která přijímá řetězcovou zprávu.  
  
* <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, která přijímá řetězcovou zprávu a vnitřní výjimku.  
  
Příklad najdete v tématu [jak: Create User-defined výjimky](how-to-create-user-defined-exceptions.md).

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Ujistěte se, že data výjimky je k dispozici, když je kód spuštěn vzdáleně

Při vytváření uživatelsky definovaných výjimek, ujistěte se, že je k dispozici pro kód, který je prováděn vzdáleně metadata pro výjimky. 

Například na implementace .NET, které podporují domén aplikace, může dojít k výjimkám mezi doménami aplikace. Předpokládejme, že doména aplikace A vytvoří doménu aplikace B, která spustí kód, který vyvolá výjimku. Doména aplikace A k správně zachytila a zpracovala výjimku musí být schopna najít sestavení obsahující výjimku domény aplikace b Pokud doména aplikace B vyvolá výjimku, která je součástí sestavení v rámci její základ cesty aplikace, ale není pod základ cesty aplikace příslušné domény aplikace, doména aplikace A nebudete moci najít výjimku a modul common language runtime vyvolá výjimku <xref:System.IO.FileNotFoundException> výjimky. Této situaci zamezíte tak, že nasadíte sestavení obsahující informace o výjimce dvěma způsoby:

- Sestavení umístěte do společného základu cesty aplikace sdíleného oběma doménami aplikace.

    \- nebo –

- Pokud domény nesdílejí společný základ cesty aplikace, podepište sestavení obsahující informace o výjimce silným názvem a nasaďte sestavení do globální mezipaměti sestavení (GAC).

## <a name="use-grammatically-correct-error-messages"></a>Používejte gramaticky správné chybové zprávy

Zápis vymazat věty a zahrnout koncové interpunkce. Jednotlivé věty v řetězci přiřazené <xref:System.Exception.Message?displayProperty=nameWithType> vlastnost by měla končit tečkou. Například "The log table došlo k přetečení." by být řetězec odpovídající zprávu.

## <a name="include-a-localized-string-message-in-every-exception"></a>Přiložit zprávu lokalizované řetězce v každé výjimce

Chybová zpráva, která se uživateli je odvozen z <xref:System.Exception.Message?displayProperty=nameWithType> vlastnost, která byla vyvolána výjimka a nikoli z názvu třídy výjimek. Obvykle přiřadit hodnotu <xref:System.Exception.Message?displayProperty=nameWithType> vlastnost tím, že předáte řetězec zprávy `message` argument [výjimky konstruktoru](xref:System.Exception.%23ctor%2A). 

V případě lokalizovaných aplikací by měly poskytnout řetězce lokalizované zpráv pro každou výjimku, kterou vaše aplikace může vyvolat. Soubory prostředků vám poskytují lokalizované chybové zprávy. Informace o lokalizaci aplikací a načítání lokalizovaných řetězců naleznete v tématu [prostředky v desktopových aplikací](../../framework/resources/index.md) a <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>Vlastní výjimky zadejte další vlastnosti podle potřeby

Zadejte další vlastnosti pro výjimku (kromě řetězec vlastní zprávu) pouze v případě, že existuje programový scénář, kde Další informace jsou užitečné. Například <xref:System.IO.FileNotFoundException> poskytuje <xref:System.IO.FileNotFoundException.FileName> vlastnost.

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Příkaz throw místo tak, že bude užitečné trasování zásobníku

Trasování zásobníků začíná u příkazu, kde je vyvolána výjimka a končí `catch` příkaz, který zachytí výjimku.

## <a name="use-exception-builder-methods"></a>Použijte metody tvůrce výjimky

Pro třídu je běžné vyvolat stejnou výjimku z různých míst v rámci příslušné implementace. Abyste zabránili nadbytečnému kódu, použijte pomocné metody k vytvoření výjimky a vrácení výjimky. Příklad:

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
V některých případech je vhodnější použít konstruktor k vytvoření výjimky. Příkladem je třídy globálních výjimek, jako <xref:System.ArgumentException>.

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>Při vyvolání výjimky odstraňte dílčí výsledky

Volající by měl předpokládat, že při vyvolání výjimky z metody nedojde k žádným vedlejším účinkům. Například pokud máte kód, který převede peníze odebrání z jednoho účtu a uložení do jiného účtu, a je vyvolána výjimka při provádění uložení, nechcete stažení zůstávají v platnosti.

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

Jedním ze způsobů tuto situaci je zachytit žádné výjimky vyvolané uložení transakce a vrátit zpět stažení.

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

Tento příklad ukazuje použití metody `throw` pro opětovné vyvolání původní výjimku, která usnadní volajícím zobrazila skutečná příčinu problému bez nutnosti k prozkoumání <xref:System.Exception.InnerException> vlastnost. Alternativou je novou výjimku a zahrnují původní výjimku jako vnitřní výjimka:

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed", innerException: ex)
    {
        From = from,
    To = to,
    Amount = amount
    };
}
```

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
