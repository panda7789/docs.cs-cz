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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 371e958aca87c922c902d8efd945d94d611672d9
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478250"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Asynchronní volání synchronních metod

Rozhraní .NET Framework umožňuje volat jakékoli metody asynchronně. Provedete to tak můžete definovat delegáta se stejným podpisem jako metodu, kterou chcete volat; modul common language runtime automaticky definuje `BeginInvoke` a `EndInvoke` metody pro tento delegát s odpovídajícími podpisy.

> [!NOTE]
> Volání asynchronních delegátů, konkrétně `BeginInvoke` a `EndInvoke` metody, nejsou podporovány v rozhraní .NET Compact Framework.

`BeginInvoke` Zahájí asynchronní volání metody. Má stejné parametry jako metodu, která je zapotřebí spustit asynchronně, a navíc další dva volitelné parametry. První parametr je <xref:System.AsyncCallback> delegáta, který odkazuje na metodu, která se má volat po dokončení asynchronního volání. Druhý parametr je objekt definovaný uživatelem, který předává informace do metody zpětného volání. `BeginInvoke` Vrátí hodnotu okamžitě a nečeká na dokončení asynchronního volání. `BeginInvoke` Vrátí <xref:System.IAsyncResult>, které lze použít ke sledování průběhu asynchronní volání.

`EndInvoke` Načítá výsledek z asynchronního volání metody. Může být volán kdykoli po `BeginInvoke`. Pokud asynchronní volání nebyla dokončena, `EndInvoke` blokuje volající vlákno, dokud se nedokončí. Parametry `EndInvoke` zahrnout `out` a `ref` parametry (`<Out>` `ByRef` a `ByRef` v jazyce Visual Basic) metody, která je zapotřebí spustit asynchronně, plus <xref:System.IAsyncResult> vrácený `BeginInvoke`.

> [!NOTE]
> Funkce IntelliSense v sadě Visual Studio zobrazuje parametry `BeginInvoke` a `EndInvoke`. Pokud nepoužíváte Visual Studio nebo něco podobného, nebo pokud používáte C# pomocí sady Visual Studio, naleznete v tématu [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) popis o parametrech definovaných pro tyto metody.

Příklady kódu v tomto tématu ukazují čtyři běžné způsoby použití `BeginInvoke` a `EndInvoke` pro asynchronní volání. Po volání `BeginInvoke` můžete dělat tyto věci:

-   Provést některé práci a následně zavolat `EndInvoke` do bloku, dokud se nedokončí volání.

-   Získat <xref:System.Threading.WaitHandle> pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> vlastnosti, použijte jeho <xref:System.Threading.WaitHandle.WaitOne%2A> metodu pro provádění bloku, dokud <xref:System.Threading.WaitHandle> signalizován a pak vyvolejte `EndInvoke`.

-   Dotazování <xref:System.IAsyncResult> vrácený `BeginInvoke` k určení po dokončení asynchronního volání a následně zavolat `EndInvoke`.

-   Předání delegáta pro metodu zpětného volání pro `BeginInvoke`. Metoda se spouští podle <xref:System.Threading.ThreadPool> vlákna po dokončení asynchronního volání. Volání metody zpětného volání `EndInvoke`.

> [!IMPORTANT]
> Bez ohledu na to, které techniku použít, vždy volejte `EndInvoke` na dokončení asynchronního volání.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Definování testovací metody a asynchronních delegátů
 Následující příklady kódu ukazují různé způsoby volání stejné metody dlouhotrvající `TestMethod`, asynchronně. `TestMethod` Metoda zobrazí zprávu konzoly, chcete-li zobrazit, že byl zahájen zpracování, po prodlevě pár sekund a končí. `TestMethod` má `out` parametr předvést způsob, jak tyto parametry jsou přidány do signatur `BeginInvoke` a `EndInvoke`. Dokáže zpracovat `ref` parametry podobně.

 Následující příklad kódu ukazuje definici `TestMethod` a delegáta s názvem `AsyncMethodCaller` , který je možné volat `TestMethod` asynchronně. Chcete-li zkompilovat příklady kódu, musí obsahovat definice pro `TestMethod` a `AsyncMethodCaller` delegovat.

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>Čekání na asynchronní volání s EndInvoke
 Nejjednodušší způsob, jak provést asynchronní metody je spustit provedení metody při volání delegáta `BeginInvoke` metody, některé pracovat na hlavním vlákně a následně zavolat delegáta `EndInvoke` metody. `EndInvoke` může blokovat volající vlákno, protože nevrací až po dokončení asynchronního volání. Toto je dobrý postup pomocí souboru nebo síťové operace.

> [!IMPORTANT]
> Protože `EndInvoke` může blokovat, které by nikdy neměl volat z vlákna uživatelského rozhraní služby.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>Čekání na asynchronní volání s WaitHandle
 Můžete získat <xref:System.Threading.WaitHandle> pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost <xref:System.IAsyncResult> vrácený `BeginInvoke`. <xref:System.Threading.WaitHandle> Signalizován po dokončení asynchronního volání a může čekat na jeho voláním <xref:System.Threading.WaitHandle.WaitOne%2A> metody.

 Pokud používáte <xref:System.Threading.WaitHandle>, můžete provést další zpracování před nebo po dokončení asynchronního volání, ale před voláním `EndInvoke` k načtení výsledků.

> [!NOTE]
> Popisovač čekání není uzavřená automaticky při volání `EndInvoke`. Pokud můžete uvolnit všechny odkazy na popisovač čekání, jsou uvolněny systémové prostředky při uvolňování paměti získá popisovač čekání. Uvolnit systémové prostředky, jakmile budete hotovi, pomocí popisovač čekání, vyřadit voláním <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> metody. Uvolňování paměti funguje efektivněji, když se objekt explicitně uvolněn uvolnitelné objekty.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Dotazování na dokončení asynchronního volání
 Můžete použít <xref:System.IAsyncResult.IsCompleted%2A> vlastnost <xref:System.IAsyncResult> vrácený `BeginInvoke` ke zjišťování po dokončení asynchronního volání. Můžete tak učinit při provádění asynchronní volání z vlákna, které uživatelské rozhraní služby. Dotazování pro dokončení umožňuje volajícího vlákna má pokračovat provedením během asynchronního volání se spustí na <xref:System.Threading.ThreadPool> vlákna.

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Provádění metody zpětného volání při dokončení asynchronní volání
 Pokud podproces, který iniciuje asynchronní volání nemusí být vlákna, která zpracovává výsledky, je možné spustit metodu zpětného volání při dokončení volání. Metoda zpětného volání, které se spouští podle <xref:System.Threading.ThreadPool> vlákna.

 Pokud chcete použít metodu zpětného volání, musíte předat `BeginInvoke` <xref:System.AsyncCallback> delegáta, který představuje metodu zpětného volání. Můžete také předat objekt, který obsahuje informace, které použije metoda zpětného volání. V metodě zpětného volání, můžete přetypovat <xref:System.IAsyncResult>, na který je jediným parametrem metody zpětného volání <xref:System.Runtime.Remoting.Messaging.AsyncResult> objektu. Pak můžete použít <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> vlastnost k získání delegáta, který byl použit k iniciujte hovor, takže můžete volat `EndInvoke`.

 Poznámky v tomto příkladu:

-   `threadId` Parametr `TestMethod` je `out` parametr ([`<Out>` `ByRef` v jazyce Visual Basic), takže jeho vstupní hodnotu nikdy používají `TestMethod`. Fiktivní proměnná je předána `BeginInvoke` volání. Pokud `threadId` byly parametr `ref` parametr (`ByRef` v jazyce Visual Basic), proměnné by mohl být pole třídu úrovně tak, aby ho mohli předat i `BeginInvoke` a `EndInvoke`.

-   Informace o stavu, který je předán `BeginInvoke` je formátovací řetězec, který používá metodu zpětného volání k formátování výstupní zprávu. Protože je předán jako typ <xref:System.Object>, informace o stavu musí být přetypovat na typ správné předtím, než je možné.

-   Je provedeno zpětné volání <xref:System.Threading.ThreadPool> vlákna. <xref:System.Threading.ThreadPool> vlákna jsou vlákna na pozadí, které není byla aplikace spuštěná, pokud hlavní podproces skončí, takže do režimu spánku dostatečně dlouhou dobu na dokončení zpětného volání obsahuje hlavní vlákno v příkladu.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Viz také:

- <xref:System.Delegate>
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
