---
title: Asynchronní volání synchronních metod
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
ms.openlocfilehash: 06df584f0120fbd4978e18647854a3ee844a2095
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105130"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Asynchronní volání synchronních metod

Rozhraní .NET Framework umožňuje volat libovolnou metodu asynchronně. Chcete-li to provést, definujte delegáta se stejným podpisem jako metoda, kterou chcete volat; společný jazyk runtime automaticky `BeginInvoke` `EndInvoke` definuje a metody pro tohoto delegáta, s příslušnými podpisy.

> [!NOTE]
> Asynchronní delegátská volání, `BeginInvoke` `EndInvoke` konkrétně a metody, nejsou v rozhraní .NET Compact Framework podporována.

Metoda `BeginInvoke` iniciuje asynchronní volání. Má stejné parametry jako metoda, kterou chcete spustit asynchronně, plus dva další volitelné parametry. První parametr je <xref:System.AsyncCallback> delegát, který odkazuje na metodu, která má být volána po dokončení asynchronního volání. Druhý parametr je uživatelem definovaný objekt, který předává informace do metody zpětného volání. `BeginInvoke`vrátí okamžitě a nečeká na dokončení asynchronního volání. `BeginInvoke`vrátí <xref:System.IAsyncResult>, který lze použít ke sledování průběhu asynchronního volání.

Metoda `EndInvoke` načte výsledky asynchronní volání. To může být volána kdykoliv po `BeginInvoke`. Pokud asynchronní volání nebylo dokončeno, `EndInvoke` blokuje volající vlákno, dokud nebude dokončeno. `EndInvoke` Parametry zahrnují `out` parametry `ref` a`<Out>` `ByRef` ( `ByRef` a v jazyce Visual Basic) metody, kterou chcete <xref:System.IAsyncResult> provést `BeginInvoke`asynchronně, plus vrácené .

> [!NOTE]
> Funkce IntelliSense v sadě Visual Studio `BeginInvoke` `EndInvoke`zobrazuje parametry aplikace a . Pokud nepoužíváte Visual Studio nebo podobný nástroj, nebo pokud používáte C# s Visual Studio, naleznete v tématu [asynchronní programovací model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) popis parametrů definovaných pro tyto metody.

Příklady kódu v tomto tématu ukazují `BeginInvoke` `EndInvoke` čtyři běžné způsoby použití a provádět asynchronní volání. Po `BeginInvoke` zavolání můžete provést následující kroky:

- Proveďte nějakou práci `EndInvoke` a pak volejte blokovat, dokud hovor neskončí.

- Získat <xref:System.Threading.WaitHandle> pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> vlastnosti, <xref:System.Threading.WaitHandle.WaitOne%2A> použijte jeho metodu <xref:System.Threading.WaitHandle> blokovat provádění, dokud `EndInvoke`je signalizována a pak volání .

- Dotazování <xref:System.IAsyncResult> vrácené podle `BeginInvoke` určit, kdy bylo dokončeno asynchronní volání a potom volání `EndInvoke`.

- Předejte delegáta pro metodu zpětného volání společnosti `BeginInvoke`. Metoda je spuštěna <xref:System.Threading.ThreadPool> ve vlákně po dokončení asynchronního volání. Volání metody zpětného volání `EndInvoke`.

> [!IMPORTANT]
> Bez ohledu na to, `EndInvoke` jakou techniku používáte, vždy volání k dokončení asynchronní volání.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Definování testovací metody a asynchronního delegáta
 Příklady kódu, které následují ukazují různé způsoby volání `TestMethod`stejné metody dlouhotrvající, asynchronně. Metoda `TestMethod` zobrazí zprávu konzoly, která ukazuje, že byla zahájena zpracování, přepne několik sekund do režimu spánku a poté skončí. `TestMethod`má `out` parametr, který ukazuje způsob, jakým jsou tyto `BeginInvoke` `EndInvoke`parametry přidány k podpisům a . Parametry `ref` můžete zpracovat podobně.

 Následující příklad kódu ukazuje `TestMethod` definici a `AsyncMethodCaller` delegáta s `TestMethod` názvem, který lze použít k volání asynchronně. Chcete-li zkompilovat příklady kódu, `TestMethod` musíte `AsyncMethodCaller` zahrnout definice pro a delegáta.

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>Čekání na asynchronní volání s EndInvoke
 Nejjednodušší způsob, jak spustit metodu asynchronně je spustit provádění metody voláním `BeginInvoke` metody delegáta, provést nějakou práci v hlavním `EndInvoke` vlákně a potom volat metodu delegáta. `EndInvoke`může blokovat volající vlákno, protože se nevrátí, dokud nedokončí asynchronní volání. To je dobrá technika pro použití se souborem nebo síťovými operacemi.

> [!IMPORTANT]
> Protože `EndInvoke` může blokovat, nikdy byste měli volat z podprocesů, které služby uživatelské rozhraní.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>Čekání na asynchronní volání s WaitHandle
 Můžete získat <xref:System.Threading.WaitHandle> pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnostvrácena <xref:System.IAsyncResult> . `BeginInvoke` Je <xref:System.Threading.WaitHandle> signalizována po dokončení asynchronního volání a můžete na <xref:System.Threading.WaitHandle.WaitOne%2A> něj počkat voláním metody.

 Pokud používáte <xref:System.Threading.WaitHandle>, můžete provést další zpracování před nebo po dokončení asynchronního volání, ale před voláním `EndInvoke` k načtení výsledků.

> [!NOTE]
> Popisovač čekání není automaticky uzavřen `EndInvoke`při volání . Pokud uvolníte všechny odkazy na popisovač čekání, systémové prostředky jsou uvolněny při uvolnění uvolňování paměti uvolní popisovač čekání. Chcete-li uvolnit systémové prostředky, jakmile dokončíte pomocí popisovač čekání, <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> vyřazujte jej voláním metody. Uvolňování paměti funguje efektivněji při jednorázové objekty jsou explicitně uvolněny.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Dotazování pro dokončení asynchronního volání
 Můžete použít <xref:System.IAsyncResult.IsCompleted%2A> vlastnost <xref:System.IAsyncResult> vrácené `BeginInvoke` podle zjistit, kdy asynchronní volání dokončí. Můžete to provést při provádění asynchronní volání z vlákna, které služby uživatelské rozhraní. Dotazování pro dokončení umožňuje volající vlákno pokračovat v provádění, zatímco <xref:System.Threading.ThreadPool> asynchronní volání provede ve vlákně.

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Spuštění metody zpětného volání při dokončení asynchronního volání
 Pokud vlákno, které iniciuje asynchronní volání nemusí být podproces, který zpracovává výsledky, můžete spustit metodu zpětného volání po dokončení volání. Metoda zpětného volání je <xref:System.Threading.ThreadPool> spuštěna ve vlákně.

 Chcete-li použít metodu zpětného volání, musíte předat `BeginInvoke` delegáta, <xref:System.AsyncCallback> který představuje metodu zpětného volání. Můžete také předat objekt, který obsahuje informace, které mají být použity metodou zpětného volání. V metodě zpětného volání <xref:System.IAsyncResult>můžete přetypovat , což je jediný <xref:System.Runtime.Remoting.Messaging.AsyncResult> parametr metody zpětného volání, na objekt. Vlastnost potom můžete <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> použít k získání delegáta, který byl použit `EndInvoke`k zahájení volání, takže můžete volat .

 Poznámky k příkladu:

- Parametr `threadId` `TestMethod` je `out` parametr ([`<Out>` `ByRef` v jazyce Visual Basic), takže `TestMethod`jeho vstupní hodnota není nikdy použita . Fiktivní proměnná je předána `BeginInvoke` volání. Pokud `threadId` by parametr `ref` emitoval parametr (`ByRef` v jazyce Visual Basic), musela by proměnná `BeginInvoke` `EndInvoke`být pole na úrovni třídy, aby mohla být předána oběma a .

- Informace o stavu, `BeginInvoke` který je předán, je formátovací řetězec, který metoda zpětného volání používá k formátování výstupní zprávy. Vzhledem k tomu, že je předán jako typ <xref:System.Object>, informace o stavu musí být přetypován na jeho správný typ před jeho použití.

- Zpětné volání se provádí <xref:System.Threading.ThreadPool> ve vlákně. <xref:System.Threading.ThreadPool>vlákna jsou vlákna na pozadí, které neudržují aplikaci spuštěnou, pokud hlavní vlákno končí, takže hlavní vlákno příkladu musí spát dostatečně dlouho, aby bylo zpětné volání dokončeno.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Viz také

- <xref:System.Delegate>
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
