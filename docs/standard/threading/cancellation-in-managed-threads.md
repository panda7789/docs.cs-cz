---
title: "Zrušení ve spravovaných vláknech"
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
helpviewer_keywords: cancellation in .NET, overview
ms.assetid: eea11fe5-d8b0-4314-bb5d-8a58166fb1c3
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5407beba999ede6131adbc17f56d139396429597
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="cancellation-in-managed-threads"></a>Zrušení ve spravovaných vláknech
Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], rozhraní .NET Framework používá jednotný model pro spolupráci zrušení asynchronní nebo dlouhotrvající synchronní operace. Tento model je založen na prostý objekt názvem token zrušení. Objekt, který vyvolá jednu nebo více operací možné zrušit, třeba tak, že vytvoříte novou vláken nebo úlohy, předá tento token na každou operaci. Jednotlivé operace můžete zase předat jiné operace kopie tokenu. Později objekt, který vytvořili token slouží k vyžádání, že operace zastavit, co dělají. Pouze objekt požadavku můžete vydat žádost o zrušení a každý listener je odpovědná za vašeho povšimnutí žádosti a reagovat na ni příslušná a včas způsobem.  
  
 Obecné vzor pro implementaci spolupráci zrušení modelu je:  
  
-   Vytváření instancí <xref:System.Threading.CancellationTokenSource> objekt, který spravuje a odesílá oznámení zrušení jednotlivé zrušení tokenů.  
  
-   Předejte token vrácený <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> vlastnosti tak, aby každý úkol nebo vlákno, které čeká na zrušení.  
  
-   Poskytují mechanismus pro každou úlohu nebo vlákno reagovat na zrušení.  
  
-   Volání <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda poskytnout oznámení o zrušení.  
  
> [!IMPORTANT]
>  <xref:System.Threading.CancellationTokenSource> Třída implementuje <xref:System.IDisposable> rozhraní. Musí být volejte <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> metoda po dokončení pomocí tokenu zdroje zrušení uvolnit všechny nespravovaných prostředků, které drží.  
  
 Následující obrázek znázorňuje vztah mezi zdrojem tokenu a všechny kopie jeho tokenu.  
  
 ![CancellationTokenSource a zrušení tokenů](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Nový model zrušení usnadňuje vytvoření aplikace využívající zrušení a knihovny, a podporuje následující funkce:  
  
-   Zrušení je spolupráci a není vynucena, naslouchací proces. Naslouchací proces určuje, jak řádně ukončena v reakci na žádost o zrušení.  
  
-   Požaduje se liší od naslouchá. Objekt, který vyvolá možné zrušit operaci můžete řídit, kdy (Pokud někdy) zrušení je požadováno.  
  
-   Objekt požadavku vydá pomocí volání metody pouze jednu žádost o zrušení všechny kopie tokenu.  
  
-   Naslouchací proces můžete naslouchání na několika tokeny současně spojením do jednoho *propojené token*.  
  
-   Uživatelský kód můžete Všimněte si, reagovat na požadavky zrušení z knihovny kódu a kód knihovny můžete Všimněte si a reagovat na požadavky zrušení z uživatelského kódu.  
  
-   Naslouchací procesy můžete informováni o zrušení žádosti o dotazování, registrace zpětného volání nebo čekání na obslužné rutiny čekání.  
  
## <a name="cancellation-types"></a>Zrušení typy  
 Rozhraní framework zrušení je implementovaná jako sada souvisejících typů, které jsou uvedeny v následující tabulce.  
  
|Název typu|Popis|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|Objekt, který vytvoří token zrušení a také vydává žádost o zrušení pro všechny kopie tohoto tokenu.|  
|<xref:System.Threading.CancellationToken>|Typ hodnoty Lightweight předaný jeden nebo více naslouchací procesy, obvykle jako parametr metody. Naslouchací procesy monitorování hodnotu `IsCancellationRequested` vlastnost tokenu dotazování, zpětného volání nebo popisovač čekání.|  
|<xref:System.OperationCanceledException>|Přetěžování tato výjimka konstruktor přijímá <xref:System.Threading.CancellationToken> jako parametr. Naslouchací procesy můžete volitelně vyvolat výjimku ověřte zdroj zrušení a informovat ostatní, které má odpověděl na žádost o zrušení.|  
  
 Nový model zrušení je integrována do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] v několika typů. Nejdůležitější ty, které jsou <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> a <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>. Doporučujeme, abyste používali tohoto nového modelu zrušení pro všechny nové knihovny a aplikace kódu.  
  
## <a name="code-example"></a>Příklad kódu  
 V následujícím příkladu se vytvoří objekt požadavku <xref:System.Threading.CancellationTokenSource> objektu a potom předává jeho <xref:System.Threading.CancellationTokenSource.Token%2A> vlastnost možné zrušit operaci. Hodnota monitoruje operace, které obdrží požadavek <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost tokenu pomocí cyklického dotazování. Když tato hodnota začne `true`, může být ukončen naslouchací proces jakýmkoli způsobem je vhodné. V tomto příkladu metoda právě ukončí, což je všechno, co je potřeba v mnoha případech.  
  
> [!NOTE]
>  V příkladu se používá <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda prokázat, že nové architektury zrušení je kompatibilní se starší verze rozhraní API. Pro příklad, který používá nový, upřednostňovaný <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zadejte najdete v tématu [postupy: zrušení úlohy a její podřízené položky](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>Zrušení operace porovnání zrušení objektu  
 V nové architektury zrušení označuje zrušení operace, ne objekty. Žádost o zrušení znamená, že by se měla po provedení všech požadovaných čištění co nejdříve zastavit operaci. Jeden token zrušení by měla odkazovat jednu "možné zrušit operaci,", ale této operace může být implementována v programu. Po <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost tokenu byla nastavena na `true`, nelze obnovit na `false`. Zrušení tokenů proto nemůže znovu, jakmile byla zrušena.  
  
 Pokud budete potřebovat mechanismus zrušení objekt, můžete založit ho na tento mechanismus pro zrušení operace voláním <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> metoda, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Pokud objekt podporuje víc souběžných možné zrušit operaci, předejte token samostatné jako vstup pro každou operaci distinct možné zrušit. Tímto způsobem jednu operaci můžete zrušit bez vlivu jiné.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Naslouchání a reagovat na požadavky zrušení  
 V delegát uživatele implementátor možné zrušit operace určuje postup ukončit operaci v reakci na žádost o zrušení. V mnoha případech můžete uživatelskému delegátovi provést všechny potřebné vyčištění a pak se vraťte okamžitě.  
  
 Však v případech, složitější, může být nezbytné pro delegáta uživatele upozornit kód knihovny zrušení došlo k chybě. V takových případech je správný způsob ukončení operace pro delegáta volání <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, metoda, která způsobí, že <xref:System.OperationCanceledException> vyvolání. Kód knihovny můžete catch tato výjimka ve vláknu delegáta uživatele a zkontrolujte token výjimky k určení, jestli výjimka označuje spolupráci zrušení nebo jiné výjimečné situace.  
  
 <xref:System.Threading.Tasks.Task> Třídu obslužné rutiny <xref:System.OperationCanceledException> tímto způsobem. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Naslouchání dotazováním  
 Pro výpočty dlouho běžící dané smyčky nebo recurse, můžete poslouchat na žádost o zrušení pomocí pravidelně cyklického dotazování hodnotu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> vlastnost. Pokud je jeho hodnota `true`, metoda by měla vyčištění a ukončit tak rychle. Optimální frekvenci dotazování závisí na typu aplikace. Je vývojář vybrat nejvhodnější dotazování četnost pro jakýkoli daný program. Dotazování samotné není výrazně ovlivnit výkon. Následující příklad ukazuje jeden možný způsob, jak dotazovat.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Více kompletní příklad najdete v tématu [postupy: Naslouchání požadavkům zrušení dotazováním](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md).  
  
### <a name="listening-by-registering-a-callback"></a>Naslouchání tak, že zaregistrujete zpětné volání  
 Některé operace, mohou stát blokovány tak, že se nemůže kontrolovat hodnota tokenu zrušení včas. Pro tyto případy můžete zaregistrovat metoda zpětného volání, která odblokuje metodu, když je obdržena žádost o zrušení.  
  
 <xref:System.Threading.CancellationToken.Register%2A> Metoda vrátí <xref:System.Threading.CancellationTokenRegistration> objekt, který se používá speciálně pro tento účel. Následující příklad ukazuje způsob použití <xref:System.Threading.CancellationToken.Register%2A> metoda zrušení asynchronní webový požadavek.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 <xref:System.Threading.CancellationTokenRegistration> Objekt spravuje synchronizace vláken a zajistí, že zpětné volání skončí u přesné bodu v čase.  
  
 K zajištění odezvy systému a aby se zabránilo zablokování je potřeba dodržovat následující pokyny při registraci zpětná volání:  
  
-   Metoda zpětného volání by mělo být rychlé, protože se označuje jako synchronně a proto volání <xref:System.Threading.CancellationTokenSource.Cancel%2A> nevrací až do vrátí zpětné volání.  
  
-   Když zavoláte <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> zpětné volání běží a uložení zpětné volání čekající na zámek, můžete zablokování vašeho programu. Po `Dispose` vrátí, můžete uvolnit všechny prostředky, které vyžadují zpětné volání.  
  
-   Zpětná volání nesmí provádět jakékoli ruční vlákno nebo <xref:System.Threading.SynchronizationContext> využití v zpětné volání. Pokud zpětné volání, musíte spustit na konkrétní vlákno, použijte <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> konstruktor, který umožňuje vám určit, že cíl syncContext je aktivní <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>. Provádění ruční vláken ve zpětné volání může způsobit zablokování.  
  
 Více kompletní příklad najdete v tématu [postupy: registrace zpětných volání pro požadavky zrušení](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Naslouchání pomocí popisovač čekání  
 Když možné zrušit operaci můžete blokovat během čekání na primitivní, jako synchronizaci <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> nebo <xref:System.Threading.Semaphore?displayProperty=nameWithType>, můžete použít <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> vlastnost Povolit operaci pro čekání na událost a žádost o zrušení. Popisovač čekání token zrušení se stane signalizovala v reakci na žádost o zrušení a metoda může používat vrácenou hodnotu <xref:System.Threading.WaitHandle.WaitAny%2A> metoda k určení, zda bylo zrušení token, který signál. Operaci následně právě ukončit, nebo throw <xref:System.OperationCanceledException>podle potřeby.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 V nový kód, který se zaměřuje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> obě podporovat nové architektury zrušení v jejich `Wait` metody. Můžete předat <xref:System.Threading.CancellationToken> metodu, a pokud se požaduje zrušení, události probudí a způsobí výjimku, <xref:System.OperationCanceledException>.  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Více kompletní příklad najdete v tématu [postupy: naslouchání zrušení žádosti, máte počkejte zpracovává](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md).  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Naslouchání více tokeny současně  
 V některých případech může mít naslouchací proces pro naslouchání na několika zrušení tokenů současně. Například může mít možné zrušit operaci monitorování token zrušení interní kromě token předaný v externě jako argument parametru metody. K tomu, vytvořte zdroj propojené token, který se můžete zapojit do dvou nebo více tokeny do jednoho tokenu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Všimněte si, že je třeba volat `Dispose` na propojené zdroj tokenu, když jste hotovi s ním. Více kompletní příklad najdete v tématu [postupy: naslouchání více požadavkům zrušení](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md).  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Spolupráce mezi knihovny kódu a uživatelského kódu  
 Rozhraní framework jednotná zrušení umožňuje pro kód knihovny zrušit uživatelského kódu a uživatelského kódu zrušit kód knihovny spolupráci způsobem. Bezproblémovou spolupráci, závisí na každé straně následujících pokynů:  
  
-   Pokud kód knihovny poskytuje možné zrušit operace, se musí zadat veřejné metody, které přijímají token zrušení externí tak, aby uživatelský kód může požádat o zrušení.  
  
-   Volá-li kód knihovny do uživatelského kódu, by měl kód knihovny interpretovat OperationCanceledException(externalToken) jako *spolupráci zrušení*a nikoli jako výjimky selhání.  
  
-   Delegáti uživatele mají pokusit odpovědět na požadavky zrušení z knihovny kódu v časovém limitu.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>a <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> jsou příklady třídy, které řídí tyto pokyny. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md)a [postupy: zrušení dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="see-also"></a>Viz také  
 [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)
