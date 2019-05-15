---
title: Zrušení ve spravovaných vláknech
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation in .NET, overview
ms.assetid: eea11fe5-d8b0-4314-bb5d-8a58166fb1c3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0776db4d045a8e52521859b9126583558bc5b51
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586354"
---
# <a name="cancellation-in-managed-threads"></a>Zrušení ve spravovaných vláknech
Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], rozhraní .NET Framework používá jednotný model pro kooperativní zrušení asynchronní nebo dlouhotrvající synchronní operace. Tento model je založen na zjednodušené objekt volána token zrušení. Objekt, který vyvolá jednu nebo více operací zrušitelný, třeba tak, že vytvoříte nová vlákna nebo úlohy, předá token pro každou operaci. Jednotlivé operace můžete zase předat další operace kopie token. Později objekt, který vytvoří token, který slouží k požadavku, že operace zastavit, co dělají. Pouze žádost o objekt může vydat žádost o zrušení a každý naslouchací proces je zodpovědný za řadí žádosti a reagovat na ni vhodné a včasné způsobem.  
  
 Je obecný vzor implementace vzoru kooperativní zrušení:  
  
- Vytvořit instanci <xref:System.Threading.CancellationTokenSource> objektu, který spravuje a odešle oznámení o zrušení tokenů jednotlivé zrušení.  
  
- Předat token vrácený <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> vlastnost pro každý úkol nebo vláknem, které čeká na zrušení.  
  
- Poskytuje mechanismus pro každý úkol nebo vlákno reagovat na zrušení.  
  
- Volání <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodu k dispozici oznámení o zrušení.  
  
> [!IMPORTANT]
>  <xref:System.Threading.CancellationTokenSource> Implementuje třída <xref:System.IDisposable> rozhraní. By měl nezapomeňte volat <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> metoda po dokončení používání zdroje tokenu zrušení uvolnit žádné nespravované prostředky, které obsahuje.  
  
 Následující ilustrace znázorňuje vztah mezi zdrojem tokenu a všechny kopie svůj token.  
  
 ![CancellationTokenSource – a zrušení tokenů](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Nový model zrušení usnadňuje vytváření aplikací pracujících s zrušení a knihoven a podporuje následující funkce:  
  
- Zrušení je spolupráce a nebude se vynucovat na naslouchací proces. Naslouchací proces určuje, jak v reakci na žádost o zrušení řádně ukončit.  
  
- Požaduje se liší od naslouchání. Objekt, který vyvolá zrušitelnou operaci můžete řídit, kdy (Pokud) je požadováno zrušení.  
  
- Žádost o objekt vydá požadavek na zrušení u všech kopií token s použitím pouze jedné metody volání.  
  
- Naslouchací proces mohl naslouchat více tokenů současně jejich sloučením do jedné *propojené token*.  
  
- Uživatelský kód můžete zaznamenat a odpovědět na požadavky zrušení z knihovny kódu a kód knihovny můžete zaznamenat a odpovědět na požadavky zrušení z uživatelského kódu.  
  
- Naslouchací procesy můžete dostávat oznámení žádostí o zrušení dotazování, registrace zpětného volání a čekání na obslužné rutiny čekání.  
  
## <a name="cancellation-types"></a>Typy zrušení  
 Zrušení framework je implementované jako sada souvisejících typů, které jsou uvedeny v následující tabulce.  
  
|Název typu|Popis|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|Objekt, který vytvoří token zrušení a také vystaví žádost o zrušení pro všechny kopie tohoto tokenu.|  
|<xref:System.Threading.CancellationToken>|Zjednodušené hodnotu předán typ na jeden nebo více naslouchacích procesů, obvykle jako parametr metody. Naslouchací procesy monitorování hodnoty `IsCancellationRequested` vlastnost tokenu dotazování, zpětné volání nebo popisovač čekání.|  
|<xref:System.OperationCanceledException>|Přetížení konstruktoru tuto výjimku přijmout <xref:System.Threading.CancellationToken> jako parametr. Naslouchacích procesů může volitelně vyvolat tuto výjimku ověřit zdroj zrušení a informovat ostatní, které odpověděl na požadavek na zrušení.|  
  
 Nový model zrušení je integrovaná v rozhraní .NET Framework v několika typech. Nejdůležitější ty jsou <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> a <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>. Doporučujeme použít tento nový model zrušení pro všechny nové kód knihovny a aplikace.  
  
## <a name="code-example"></a>Příklad kódu  
 V následujícím příkladu se vytvoří žádost o objekt <xref:System.Threading.CancellationTokenSource> objektu a předává jeho <xref:System.Threading.CancellationTokenSource.Token%2A> vlastnost zrušitelnou operaci. Operace, která obdrží požadavek monitoruje hodnotu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost tokenu cyklického dotazování. Pokud tato hodnota začne `true`, můžete ve svých ukončí naslouchací proces. V tomto příkladu metoda právě ukončí, což je vše, co je nutné v mnoha případech.  
  
> [!NOTE]
>  V příkladu se používá <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda prokázat, že je kompatibilní s starší verze rozhraní API rozhraní nové zrušení. Příklad, který používá nový, upřednostňované <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zadejte naleznete v tématu [jak: Zrušení úlohy a jejích potomků](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>Operace zrušení a zrušení objektu  
 V rámci nové zrušení zrušení odkazuje na operace, ne objekty. Žádost o zrušení znamená, že by se měla operaci zastavit co nejdříve po provedení všechny potřebné vyčištění. Jeden token zrušení by měla odkazovat na jeden "zrušitelnou operaci,", ale tuto operaci mohou být implementovány v aplikaci. Po <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost tokenu je nastavená na `true`, nelze jej obnovit do `false`. Proto tokeny zrušení nemůže být znovu použité po byla zrušena.  
  
 Pokud budete potřebovat mechanismus zrušení objektu, můžete založit ho na mechanismu zrušení operace voláním <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> způsob, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Pokud objekt podporuje víc souběžných zrušitelnou operaci, předejte samostatný token jako vstup pro každý jedinečných zrušitelnou operaci. Tímto způsobem, aniž by to ovlivnilo ostatní lze zrušit jednu operaci.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Naslouchání a reagovat na požadavky zrušení  
 Implementátor zrušitelnou operaci v uživatelském delegátu, určuje, jak ukončit operaci v reakci na žádost o zrušení. V mnoha případech můžete uživatelský delegát provést všechny potřebné vyčištění a vrátíte se okamžitě.  
  
 Nicméně v složitějších případech bude pravděpodobně nutné pro uživatelský delegát oznámit kód knihovny, který má došlo ke zrušení. V takovém případě je správný způsob ukončení operace pro delegáta pro volání <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, metodu, která způsobí, že <xref:System.OperationCanceledException> vyvolání. Kód knihovny můžete tuto výjimku zachytit na vlákně uživatelského delegáta a zkontrolujte token této výjimky k určení, zda výjimku označuje kooperativní zrušení nebo některé jiné výjimečné situace.  
  
 <xref:System.Threading.Tasks.Task> Třídy obslužné rutiny <xref:System.OperationCanceledException> tímto způsobem. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Naslouchání cyklického dotazování  
 Pro dlouhodobé výpočtů tuto smyčku nebo recurse, může naslouchat pro žádost o zrušení pomocí pravidelně cyklického dotazování hodnotu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> vlastnost. Pokud je jeho hodnota `true`, metoda by měla vyčistit a ukončit tak rychle. Optimální frekvence cyklického dotazování závisí na typu aplikace. Je pro vývojáře k určení nejlepší četnost pro libovolný daný program dotazování. Dotazování samotný není výrazně ovlivnit výkon. Následující příklad ukazuje jeden možný způsob, jak dotazovat.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Podrobnější příklad naleznete v tématu [jak: Naslouchání požadavkům zrušení dotazováním](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md).  
  
### <a name="listening-by-registering-a-callback"></a>Naslouchání tak, že zaregistrujete zpětné volání  
 Některé operace můžou tak, že se nelze vrátit hodnota tokenu zrušení se změnami tak včas nereflektují zablokování. Pro tyto případy můžete zaregistrovat metodu zpětného volání, která se odblokuje metodu, když je obdržena žádost o zrušení.  
  
 <xref:System.Threading.CancellationToken.Register%2A> Metoda vrátí hodnotu <xref:System.Threading.CancellationTokenRegistration> objekt, který je speciálně pro tento účel použít. Následující příklad ukazuje způsob použití <xref:System.Threading.CancellationToken.Register%2A> metodu zrušení asynchronní webový požadavek.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 <xref:System.Threading.CancellationTokenRegistration> Objekt spravuje synchronizaci vláken a zajistí, že zpětné volání se zastaví provádění na konkrétním místě v čase.  
  
 Aby bylo možné zajistit rychlost odezvy systému a aby se zabránilo zablokování podle následujících pokynů musí následovat při registraci zpětná volání:  
  
- Metoda zpětného volání by mělo být rychle, protože je volána synchronně a proto volání <xref:System.Threading.CancellationTokenSource.Cancel%2A> nevrací až do zpětného volání vrátí.  
  
- Při volání <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> zpětného volání je spuštěn a uchování, která zpětné volání čeká na zámek, váš program může zablokování. Po `Dispose` vrátí, můžete uvolnit všechny prostředky vyžadované zpětného volání.  
  
- Zpětná volání neměli provádět jakékoli ruční vlákno nebo <xref:System.Threading.SynchronizationContext> využití ve zpětném volání. Pokud zpětné volání, musíte spustit na konkrétní vlákno, použijte <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> konstruktor, který vám umožňuje určit, že cíl syncContext je aktivní <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>. Provádění ruční práce s vlákny ve zpětném volání může způsobit zablokování.  
  
 Podrobnější příklad naleznete v tématu [jak: Registrace zpětných volání pro požadavky zrušení](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Naslouchání pomocí popisovač čekání  
 Pokud můžete zablokovat zrušitelnou operaci během čekání v rámci synchronizačního primitiva, jako <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> nebo <xref:System.Threading.Semaphore?displayProperty=nameWithType>, můžete použít <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> vlastností pro povolení operace čekání na události a žádost o zrušení. Popisovač čekání token zrušení bude stát signalizovanými v reakci na žádost o zrušení a metodu můžete použít na návratový typ <xref:System.Threading.WaitHandle.WaitAny%2A> metodou ke zjištění, zda byla zrušení token, který signál. Operace následně právě ukončete, nebo vyvolat <xref:System.OperationCanceledException>podle potřeby.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 V novém kódu, který se zaměřuje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> podporovaly nový rámec zrušení v jejich `Wait` metody. Můžete předat <xref:System.Threading.CancellationToken> metody, a pokud se požaduje zrušení, události probudí a vyvolá výjimku <xref:System.OperationCanceledException>.  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Podrobnější příklad naleznete v tématu [jak: Naslouchání požadavkům zrušení, které mají obslužné rutiny čekání](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md).  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Naslouchání současně více tokenů  
 V některých případech může mít naslouchací proces nenaslouchá na více tokenů zrušení současně. Například může mít zrušitelnou operaci monitorování token zrušení interní kromě token předaný externě jako argument pro parametr metody. K tomu vytvořte zdroj propojené token, který se můžete zapojit do dvou nebo více tokenů do jednoho tokenu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Všimněte si, že je nutné volat `Dispose` na propojený zdroj tokenu, až budete hotovi s ním. Podrobnější příklad naleznete v tématu [jak: Naslouchání více požadavkům zrušení](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md).  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Spolupráce mezi kód knihovny a kód uživatele  
 Rozhraní unified zrušení umožňuje kód knihovny zrušit uživatelský kód a kód uživatele zrušit kód knihovny na způsob spolupráce za. Smooth spolupráce, závisí na každé straně držet těchto pokynů:  
  
- Pokud kód knihovny poskytuje operace zaslána, měl by také poskytovat veřejné metody, které přijímají token zrušení externí tak, aby uživatelský kód, můžete požádat o zrušení.  
  
- Volá-li kód knihovny do uživatelského kódu, kód knihovny by měl interpretovat OperationCanceledException(externalToken) jako *kooperativní zrušení*a nikoli jako výjimky na chyby.  
  
- Uživatelské delegáty mají pokusit odpovědět na požadavky zrušení z kódu knihovny včas.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> jsou příklady tříd, které postupujte podle následujících pokynů. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md) a [jak: Zrušení dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="see-also"></a>Viz také:

- [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)
