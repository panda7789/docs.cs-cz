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
ms.openlocfilehash: dd38b59e39f938d6347457100243f09935444d88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="best-practices-for-exceptions"></a>Doporučené postupy pro výjimky

Za účelem zamezení pádu aplikace zpracovává dobře navržená aplikace výjimky a chyby. Tato část popisuje doporučené postupy pro zpracování a vytváření výjimek.

## <a name="use-trycatchfinally-blocks"></a>Použít try/catch/finally – bloky

Použití `try` / `catch` / `finally` bloky kolem kód, který může potenciálně generovat výjimku. 

V `catch` blokuje vždy pořadí výjimky z nejvíce konkrétní nejméně specifická.

Použití `finally` blok k vyčištění prostředků, zda lze obnovit nebo ne.

## <a name="handle-common-conditions-without-throwing-exceptions"></a>Zpracování běžné podmínky bez způsobení výjimky

Podmínky, které by mohly nastat, ale může aktivovat výjimku, zvažte jejich zpracování způsobem, který zabrání výjimku. Například pokud se pokusíte uzavřít připojení, který již byl uzavřen, získáte `InvalidOperationException`. Můžete vyhnout použitím `if` příkaz Zkontrolovat stav připojení před pokusem o zavřete ho.

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

Pokud nemáte zkontrolovat stav připojení před zavřením, můžete zachytit `InvalidOperationException` výjimky.

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

Metoda zvolit závisí na tom, jak často předpokládáte dojde k události.

- Použijte zpracování výjimek, pokud k události nedochází velmi často, tzn. pokud k události dochází výjimečně a značí chybu (jako například neočekávaný konec souboru). Při používání zpracování výjimek je za běžných podmínek provedena menší část kódu.

- Pokud události se stane, pravidelně a může být považovány za součást normální spuštění Zkontrolujte chybové stavy v kódu. Při kontrole běžné chybové stavy, méně kódu je provést, protože se vyhnout výjimky.

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Navrhování třídy tak, aby se vyhnout výjimky

Třída může poskytnout metody nebo vlastnosti, které vám umožní vyhnout, že zavoláte vyvolalo výjimku. Například <xref:System.IO.FileStream> třída poskytuje metody, které pomáhají určit, zda byl dosažen konec souboru. Tyto umožňuje vyhnout se výjimka, která je vyvolána, pokud čtete za konec souboru. Následující příklad ukazuje, jak číst na konec souboru bez vyvolání k výjimce.

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

Jiný způsob, jak zabránit výjimky je vrátit hodnotu null pro velmi běžné případy chyba místo došlo k výjimce. Za nejběžnější případ chyby lze považovat běžný tok řízení. Vrácením hodnoty null v těchto případech minimalizujete dopad výkonu pro aplikaci.

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Generování výjimek místo vrací kód chyby

Výjimky Ujistěte se, že selhání nedojde protože volání, že kód nebyl zkontrolovat návratový kód. 

## <a name="use-the-predefined-net-exception-types"></a>Pomocí předdefinovaných typů výjimek rozhraní .NET

Zavést nové třídy výjimky jenom v případě, že se netýká předdefinované jeden. Příklad:

- Throw – <xref:System.InvalidOperationException> výjimka, není-li vlastnost sadu nebo metoda volání odpovídající zadané aktuální stav objektu.

- Throw – <xref:System.ArgumentException> výjimky nebo jeden z předdefinovaných tříd, které jsou odvozeny od <xref:System.ArgumentException> Pokud jsou předány neplatné parametry.

## <a name="end-exception-class-names-with-the-word-exception"></a>Ukončete názvy tříd výjimek slovem `Exception`

Při vlastní výjimky je nutné, pojmenujte ji odpovídajícím způsobem a odvodí z <xref:System.Exception> třídy. Příklad:

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a>Zahrnout tři konstruktory třídy vlastní výjimek

Použijte alespoň tři společné konstruktory při vytváření vlastní třídy výjimek: výchozí konstruktor, konstruktor, který přebírá zprávu řetězec a konstruktor, který přebírá zprávu řetězec a vnitřní výjimku.

* <xref:System.Exception.%23ctor>, který používá výchozí hodnoty.
  
* <xref:System.Exception.%23ctor%28System.String%29>, která přijímá zprávy řetězec.  
  
* <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, která přijímá zprávy řetězec a vnitřní výjimku.  
  
Příklad, naleznete v části [postup: výjimky Create User-Defined](how-to-create-user-defined-exceptions.md).

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Ujistěte se, že data výjimky je k dispozici, když kód provede vzdáleně

Při vytváření uživatelsky definovaných výjimek, zajistěte, aby metadata pro výjimky k dispozici pro kód, který je spustit vzdáleně. 

Například na implementace rozhraní .NET, které podporují doménami aplikací, může dojít výjimek mezi doménami aplikací. Předpokládejme, že doména aplikace A vytvoří aplikace domény B, který spustí kód, který vyvolá výjimku. Pro doménu aplikace A správně zachytit a zpracovat výjimku musí být schopna nalézt sestavení, které obsahuje výjimky vyvolané B. domény aplikace Pokud aplikace doména B vyvolá výjimku, která je součástí sestavení pod její základ cesty aplikace, ale není v rámci domény aplikací na základ cesty aplikace, doména aplikace A nebude možné najít výjimku a vyvolá výjimku modul common language runtime <xref:System.IO.FileNotFoundException> výjimka. Této situaci zamezíte tak, že nasadíte sestavení obsahující informace o výjimce dvěma způsoby:

- Sestavení umístěte do společného základu cesty aplikace sdíleného oběma doménami aplikace.

    \- nebo –

- Pokud domény nesdílejí společný základ cesty aplikace, podepište sestavení obsahující informace o výjimce silným názvem a nasaďte sestavení do globální mezipaměti sestavení (GAC).

## <a name="include-a-localized-description-string-in-every-exception"></a>Zahrnout lokalizované řetězce popisu každé výjimky

Chybová zpráva, která uživateli se zobrazí je odvozený z řetězce popis výjimky, která byla vydána a nikoli z název třídy výjimky.

## <a name="use-grammatically-correct-error-messages"></a>Použijte gramaticky správné chybové zprávy

Zápis zrušte věty a zahrnout koncové interpunkce. Jednotlivé věty v řetězci popisu výjimky by měly končit tečkou. Například "v tabulce protokolu došlo k přetečení." bude řetězec odpovídající popis.

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>Ve vlastní výjimky zadejte další vlastnosti podle potřeby

Zadejte další vlastnosti pro výjimku (kromě řetězec popisu) jenom v případě, že je programový scénář, kde Další informace jsou užitečné. Například <xref:System.IO.FileNotFoundException> poskytuje <xref:System.IO.FileNotFoundException.FileName> vlastnost.

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Tak, aby trasování zásobníku budou užitečné místní throw – příkazy

Trasování zásobníku začíná na příkaz, kde je vyvolána výjimka a končí `catch` příkaz, který zachytí výjimky.

## <a name="use-exception-builder-methods"></a>Pomocí metody tvůrce výjimky

Pro třídu je běžné vyvolat stejnou výjimku z různých míst v rámci příslušné implementace. Abyste zabránili nadbytečnému kódu, použijte pomocné metody k vytvoření výjimky a vrácení výjimky. Příklad:

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
V některých případech je vhodnější použít konstruktor v výjimky vytvořit výjimku. Příklad, jako je třída globální výjimka <xref:System.ArgumentException>.

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>Odstranit mezilehlých výsledků při vyvolání výjimky

Volající by měl předpokládat, že při vyvolání výjimky z metody nedojde k žádným vedlejším účinkům. Například pokud máte kód, který převádí peníze stažení z jednoho účtu a uloží v jiný účet, a při provádění uložení je vyvolána výjimka, nechcete odebrání zůstávají v platnosti.

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

Jedním ze způsobů ke zpracování této situace je catch jakékoli výjimky vyvolané uložení transakce a vrácení stažení.

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

Tento příklad ukazuje použití `throw` znovu vyvolat původní výjimka, která může usnadnit volající zobrazíte skutečná příčinu problému bez nutnosti zkontrolujte <xref:System.Exception.InnerException> vlastnost. Alternativou je throw novou výjimku a musí zahrnovat původní výjimka jako v popisu vnitřní výjimky:

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a>Viz také  
[Výjimky](index.md)
