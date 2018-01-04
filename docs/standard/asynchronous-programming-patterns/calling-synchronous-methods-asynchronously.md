---
title: "Asynchronní volání synchronních metod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e7e6f402d9423a8ae1ee464499f1b794785c2b06
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="calling-synchronous-methods-asynchronously"></a>Asynchronní volání synchronních metod
Rozhraní .NET Framework umožňuje libovolné metody asynchronní volání. K tomu můžete definovat delegáta se stejným podpisem jako metodu, kterou chcete volat; modul common language runtime automaticky definuje `BeginInvoke` a `EndInvoke` metody pro tento delegát s odpovídajícími podpisy.  
  
> [!NOTE]
>  Volá asynchronní delegáta, konkrétně `BeginInvoke` a `EndInvoke` metody, nejsou podporovány v rozhraní .NET Compact Framework.  
  
 `BeginInvoke` Metoda iniciuje asynchronní volání. Má stejné parametry jako metodu, kterou chcete provést asynchronně plus dva další volitelné parametry. První parametr je <xref:System.AsyncCallback> delegáta, který odkazuje na metodu, která se má volat po dokončení asynchronního volání. Druhý parametr je objekt definovaný uživatelem, který předává informace do metoda zpětného volání. `BeginInvoke`Vrátí okamžitě a nečeká na dokončení asynchronního volání. `BeginInvoke`Vrátí <xref:System.IAsyncResult>, které lze použít pro monitorování průběhu asynchronního volání.  
  
 `EndInvoke` Metoda načítá výsledek asynchronního volání. Může být volána kdykoli po `BeginInvoke`. Pokud asynchronního volání nebyla dokončena, `EndInvoke` blokuje volající vlákno, dokud nebude dokončena. Parametry `EndInvoke` zahrnují `out` a `ref` parametry (`<Out>` `ByRef` a `ByRef` v jazyce Visual Basic) metody, která se má provést asynchronně, a <xref:System.IAsyncResult> vrácený `BeginInvoke`.  
  
> [!NOTE]
>  Funkci IntelliSense v [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] zobrazí parametry `BeginInvoke` a `EndInvoke`. Pokud nepoužíváte Visual Studio nebo podobného nástroje, nebo pokud používáte C# s použitím [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], najdete v části [asynchronní programování modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) popis parametrů definovaných pro tyto metody.  
  
 Příklady kódu v tomto tématu ukazují čtyři běžné způsoby použití `BeginInvoke` a `EndInvoke` asynchronní volání. Po volání `BeginInvoke` můžete provést následující:  
  
-   Provést některé fungovat a pak zavolají `EndInvoke` blok, dokud se nedokončí volání.  
  
-   Získat <xref:System.Threading.WaitHandle> pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> vlastnosti, použijte jeho <xref:System.Threading.WaitHandle.WaitOne%2A> metoda spouštění bloku až <xref:System.Threading.WaitHandle> signalizace a pak zavolají `EndInvoke`.  
  
-   Dotazování <xref:System.IAsyncResult> vrácený `BeginInvoke` určete po dokončení asynchronního volání a pak zavolají `EndInvoke`.  
  
-   Předání delegáta pro metody zpětného volání k `BeginInvoke`. Tuto metodu je spustit na <xref:System.Threading.ThreadPool> vláken po dokončení asynchronního volání. Volání metody zpětného volání `EndInvoke`.  
  
> [!IMPORTANT]
>  Bez ohledu na to, jaké metody můžete použít, vždy volat `EndInvoke` na dokončení asynchronního volání.  
  
## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Definování testovací metoda a asynchronní delegáta  
 Příklady kódu ukazují různých způsobů volání stejnou metodu dlouho běžící `TestMethod`, asynchronně. `TestMethod` Metoda zobrazí zprávu konzoly pro zobrazení, zahájení zpracování, v režimu spánku několik sekund a pak ukončí. `TestMethod`má `out` parametr k předvedení způsobu, jakým tyto parametry jsou přidány do signatur `BeginInvoke` a `EndInvoke`. Dokáže zpracovat `ref` parametry podobně.  
  
 Následující příklad kódu ukazuje definici `TestMethod` a delegáta s názvem `AsyncMethodCaller` který lze použít k volání `TestMethod` asynchronně. Kompilace ukázky kódu, musí obsahovat definice pro `TestMethod` a `AsyncMethodCaller` delegovat.  
  
 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]  
  
## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>Čekání na asynchronní volání s EndInvoke –  
 Nejjednodušší způsob, jak provedení metody asynchronně je spustit provedení metody voláním delegáta `BeginInvoke` metoda, některé pracovat na hlavní vlákno a pak zavolají delegáta `EndInvoke` metoda. `EndInvoke`volající vlákno mohou blokovat, protože nevrací až po dokončení asynchronního volání. To je dobrý technika pro použití s soubor nebo síťové operace.  
  
> [!IMPORTANT]
>  Protože `EndInvoke` mohou blokovat, můžete by měly nikdy volat z vlákna, které služeb uživatelské rozhraní.  
  
 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]  
  
## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>Čekání na asynchronní volání s WaitHandle  
 Můžete získat <xref:System.Threading.WaitHandle> pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost <xref:System.IAsyncResult> vrácený `BeginInvoke`. <xref:System.Threading.WaitHandle> Signalizace při dokončení asynchronní volání a počkejte, až ho voláním <xref:System.Threading.WaitHandle.WaitOne%2A> metoda.  
  
 Pokud používáte <xref:System.Threading.WaitHandle>, můžete provést další zpracování před nebo po dokončení asynchronního volání, ale před voláním `EndInvoke` načíst výsledky.  
  
> [!NOTE]
>  Popisovač čekání není uzavřený automaticky při volání `EndInvoke`. Pokud je uvolnit všechny odkazy na popisovač čekání, systémové prostředky jsou uvolněny při uvolňování paměti získá popisovač čekání. Uvolnit systémové prostředky, jakmile budete hotovi, pomocí popisovač čekání, dispose to voláním <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> metoda. Uvolňování paměti funguje efektivněji, když na jedno použití objekty jsou explicitně zlikvidován.  
  
 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]  
  
## <a name="polling-for-asynchronous-call-completion"></a>Dotazování na dokončení asynchronního volání  
 Můžete použít <xref:System.IAsyncResult.IsCompleted%2A> vlastnost <xref:System.IAsyncResult> vrácený `BeginInvoke` pro zjišťování po dokončení asynchronního volání. Můžete to třeba udělat při provádění asynchronní volání z vlákna, které služby uživatelské rozhraní. Dotazování pro dokončení umožňuje volající vlákno chcete pokračovat v provádění během asynchronního volání provede na <xref:System.Threading.ThreadPool> přístup z více vláken.  
  
 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]  
  
## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Provádění metody zpětného volání při dokončení asynchronní volání  
 Pokud podproces, který iniciuje asynchronní volání nemusí být podproces, který zpracuje výsledky, je možné spustit metody zpětného volání při dokončení volání. Metoda zpětného volání, které se spouští na <xref:System.Threading.ThreadPool> přístup z více vláken.  
  
 Chcete-li použít metody zpětného volání, musíte zadat `BeginInvoke` <xref:System.AsyncCallback> delegáta, který představuje metoda zpětného volání. Také můžete předat objekt, který obsahuje informace, které použije metoda zpětného volání. Metoda zpětného volání, můžete převést <xref:System.IAsyncResult>, na které je jediný parametr metody zpětného volání <xref:System.Runtime.Remoting.Messaging.AsyncResult> objektu. Pak můžete použít <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> vlastnost k získání delegáta, který byl použit k iniciujte hovor, takže můžete volat `EndInvoke`.  
  
 Poznámky na příkladu:  
  
-   `threadId` Parametr `TestMethod` je `out` parametr ([`<Out>` `ByRef` v jazyce Visual Basic), takže jeho vstupní hodnota je používán nikdy `TestMethod`. Předaný fiktivní proměnné `BeginInvoke` volání. Pokud `threadId` měla parametr `ref` parametr (`ByRef` v jazyce Visual Basic), proměnná by mohl být na úrovni pole tak, aby ho může být předat do obou `BeginInvoke` a `EndInvoke`.  
  
-   Informace o stavu, který je předán `BeginInvoke` je formátovací řetězec, který používá metoda zpětného volání k formátování zprávu výstup. Protože je předána jako typ <xref:System.Object>, informace o stavu musí před použitím přetypovat na typ správné.  
  
-   Zpětné volání se provádí na <xref:System.Threading.ThreadPool> přístup z více vláken. <xref:System.Threading.ThreadPool>vlákna jsou vlákna na pozadí, které by neměly být aplikace spuštěna pokud hlavní vlákno skončí, takže hlavní vlákno v příkladu má do režimu spánku dostatečně dlouhou dobu na dokončení zpětného volání.  
  
 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Delegate>  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
