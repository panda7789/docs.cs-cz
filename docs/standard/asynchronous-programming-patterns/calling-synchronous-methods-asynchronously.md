---
title: Asynchronní volání synchronních metod
description: Naučte se asynchronní volání synchronních metod v rozhraní .NET pomocí metod BeginInvoke a EndInvoke u delegujících.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- asynchronous programming, delegates
- asynchronous delegates
- AsyncWaitHandle property
- callback methods
- calling synchronous methods in asynchronous manner
- WaitHandle class, code examples
- asynchronous programming, status polling
- polling asynchronous operation status
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
- waiting for asynchronous calls
- status information [.NET Framework], asynchronous operations
ms.assetid: 41972034-92ed-450a-9664-ab93fcc6f1fb
ms.openlocfilehash: ff2d30c00e7b6becb0c3ff910d825c2e9d6f78e3
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662638"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Asynchronní volání synchronních metod

.NET Framework slouží k asynchronnímu volání jakékoli metody. Uděláte to tak, že definujete delegáta se stejnou signaturou jako metoda, kterou chcete volat; modul CLR (Common Language Runtime) automaticky definuje `BeginInvoke` a `EndInvoke` metody pro tohoto delegáta s příslušnými signaturami.

> [!NOTE]
> Asynchronní volání delegáta, konkrétně `BeginInvoke` `EndInvoke` metody a, nejsou v prostředí .NET Compact Framework podporována.

`BeginInvoke`Metoda iniciuje asynchronní volání. Má stejné parametry jako metoda, kterou chcete spustit asynchronně, a další dva volitelné parametry. První parametr je <xref:System.AsyncCallback> delegát, který odkazuje na metodu, která má být volána po dokončení asynchronního volání. Druhý parametr je uživatelem definovaný objekt, který předává informace do metody zpětného volání. `BeginInvoke`Vrátí hodnotu okamžitě a nečeká na dokončení asynchronního volání. `BeginInvoke`Vrátí <xref:System.IAsyncResult> , který lze použít k monitorování průběhu asynchronního volání.

`EndInvoke`Metoda načte výsledky asynchronního volání. Může být volána kdykoli po `BeginInvoke` . Pokud asynchronní volání nebylo dokončeno, `EndInvoke` blokuje volající vlákno, dokud se nedokončí. Parametry `EndInvoke` zahrnují `out` `ref` parametry a ( `<Out>` `ByRef` a `ByRef` v Visual Basic) metody, kterou chcete spustit asynchronně, a navíc <xref:System.IAsyncResult> vrátí `BeginInvoke` .

> [!NOTE]
> Funkce technologie IntelliSense v aplikaci Visual Studio zobrazuje parametry `BeginInvoke` a `EndInvoke` . Pokud nepoužíváte sadu Visual Studio nebo podobný nástroj nebo pokud používáte jazyk C# se sadou Visual Studio, přečtěte si téma [asynchronní programovací model (APM)](asynchronous-programming-model-apm.md) pro popis parametrů definovaných pro tyto metody.

Příklady kódu v tomto tématu ukazují čtyři běžné způsoby použití `BeginInvoke` a `EndInvoke` k provádění asynchronních volání. Po volání `BeginInvoke` můžete provést následující akce:

- Udělejte nějakou práci a potom zavolejte `EndInvoke` k blokování, dokud se volání nedokončí.

- Získejte <xref:System.Threading.WaitHandle> pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> vlastnosti, použijte její <xref:System.Threading.WaitHandle.WaitOne%2A> metodu k zablokování provádění, dokud <xref:System.Threading.WaitHandle> není signál, a potom zavolejte `EndInvoke` .

- Proveďte dotazování <xref:System.IAsyncResult> vráceného pomocí a `BeginInvoke` Určete, kdy se asynchronní volání dokončilo, a potom zavolejte `EndInvoke` .

- Předání delegáta pro metodu zpětného volání `BeginInvoke` . Metoda je provedena ve <xref:System.Threading.ThreadPool> vlákně po dokončení asynchronního volání. Metoda zpětného volání volá `EndInvoke` .

> [!IMPORTANT]
> Bez ohledu na to, kterou metodu použijete, se vždy zavolá `EndInvoke` k dokončení asynchronního volání.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Definování testovací metody a asynchronního delegáta
 Příklady kódu, které následují, ukazují různé způsoby volání stejné dlouhotrvající metody, `TestMethod` asynchronně. `TestMethod`Metoda zobrazí zprávu konzoly, která ukazuje, že začala zpracovávat, v režimu spánku po dobu několika sekund a potom končí. `TestMethod`obsahuje `out` parametr, který předvádí způsob přidání těchto parametrů k podpisům `BeginInvoke` a `EndInvoke` . Můžete zpracovat `ref` parametry podobně.

 Následující příklad kódu ukazuje definici `TestMethod` a delegáta s názvem `AsyncMethodCaller` , který lze použít k `TestMethod` asynchronnímu volání. Chcete-li kompilovat příklady kódu, musíte zahrnout definice pro `TestMethod` a `AsyncMethodCaller` delegáta.

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>Čekání na asynchronní volání pomocí EndInvoke u delegujících
 Nejjednodušší způsob, jak spustit metodu asynchronně, je spuštění metody voláním metody delegáta `BeginInvoke` , provedení některé práce v hlavním vlákně a volání metody delegáta `EndInvoke` . `EndInvoke`může zablokovat volající vlákno, protože se nevrátí, dokud se nedokončí asynchronní volání. To je dobrý postup pro použití se soubory nebo síťovými operacemi.

> [!IMPORTANT]
> Vzhledem `EndInvoke` k tomu, že by mohlo zablokovat, byste nikdy neměli volat z vláken, která obsluhují uživatelské rozhraní.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>Čekání na asynchronní volání pomocí WaitHandle
 Můžete získat <xref:System.Threading.WaitHandle> pomocí vlastnosti, kterou <xref:System.IAsyncResult.AsyncWaitHandle%2A> <xref:System.IAsyncResult> vrátí `BeginInvoke` . <xref:System.Threading.WaitHandle>Je signalizována signál po dokončení asynchronního volání a můžete ho počkat voláním <xref:System.Threading.WaitHandle.WaitOne%2A> metody.

 Použijete-li <xref:System.Threading.WaitHandle> , můžete provést další zpracování před nebo po dokončení asynchronního volání, ale před voláním `EndInvoke` načtení výsledků.

> [!NOTE]
> Obslužná rutina čekání není při volání automaticky uzavřena `EndInvoke` . Pokud uvolníte všechny odkazy na popisovač čekání, jsou systémové prostředky uvolněny, když uvolňování paměti znovu zpracuje popisovač čekání. Chcete-li uvolnit systémové prostředky ihned po dokončení používání obslužné rutiny čekání, vyřazení je zavoláním <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> metody. Uvolňování paměti funguje efektivněji, pokud jsou objekty na jedno použití explicitně uvolněny.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Cyklické dotazování na dokončení asynchronního volání
 Můžete použít <xref:System.IAsyncResult.IsCompleted%2A> vlastnost <xref:System.IAsyncResult> vrácenou funkcí `BeginInvoke` ke zjištění, kdy se asynchronní volání dokončí. To můžete provést při asynchronním volání z vlákna, které je službou uživatelského rozhraní. Cyklické dotazování na dokončení umožňuje volajícímu vláknu pokračovat v provádění, zatímco asynchronní volání se provádí ve <xref:System.Threading.ThreadPool> vlákně.

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Spuštění metody zpětného volání po dokončení asynchronního volání
 Pokud vlákno, které iniciuje asynchronní volání, nemusí být vláknem, které zpracovává výsledky, můžete po dokončení volání spustit metodu zpětného volání. Metoda zpětného volání je spuštěna ve <xref:System.Threading.ThreadPool> vlákně.

 Chcete-li použít metodu zpětného volání, je nutné předat `BeginInvoke` <xref:System.AsyncCallback> delegáta, který představuje metodu zpětného volání. Můžete také předat objekt, který obsahuje informace, které mají být použity metodou zpětného volání. V metodě zpětného volání můžete přetypovat <xref:System.IAsyncResult> , což je jediný parametr metody zpětného volání, na <xref:System.Runtime.Remoting.Messaging.AsyncResult> objekt. Pak můžete použít <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> vlastnost k získání delegáta, který byl použit k iniciování volání, aby bylo možné volat `EndInvoke` .

 Poznámky k příkladu:

- `threadId`Parametr parametru `TestMethod` je `out` parametr ([ `<Out>` `ByRef` in Visual Basic), takže jeho vstupní hodnota se nikdy nepoužívá v `TestMethod` . K volání je předána fiktivní proměnná `BeginInvoke` . Pokud `threadId` parametr byl `ref` parametrem ( `ByRef` v Visual Basic), proměnná by musel být pole na úrovni třídy, aby mohla být předána do obou `BeginInvoke` i `EndInvoke` .

- Stavové informace, které jsou předány `BeginInvoke` , je řetězec formátu, který metoda zpětného volání používá k naformátování výstupní zprávy. Vzhledem k tomu, že je předán jako typ <xref:System.Object> , informace o stavu musí být přetypování na svůj správný typ předtím, než bude možné ho použít.

- Zpětné volání je provedeno ve <xref:System.Threading.ThreadPool> vlákně. <xref:System.Threading.ThreadPool>vlákna jsou vlákna na pozadí, která neudržují aplikaci spuštěnou, pokud hlavní vlákno skončí, takže hlavní vlákno tohoto příkladu musí být dostatečně dlouhé, aby bylo zpětné volání dokončeno.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Viz také

- <xref:System.Delegate>
- [Asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md)
