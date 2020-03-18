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
ms.openlocfilehash: d4bbf30923d65ad7aeced80efa626136ae27491b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138143"
---
# <a name="cancellation-in-managed-threads"></a>Zrušení ve spravovaných vláknech
Počínaje rozhraním .NET Framework 4 používá rozhraní .NET Framework jednotný model pro kooperativní zrušení asynchronních nebo dlouhotrvajících synchronních operací. Tento model je založen na zjednodušeném objektu nazývaném token zrušení. Objekt, který vyvolá jednu nebo více zrušitelných operací, například vytvořením nových vláken nebo úkolů, předá token každé operaci. Jednotlivé operace mohou zase předat kopie tokenu do jiných operací. Někdy později objekt, který vytvořil token můžete použít k požadavku, aby operace zastavit, co dělají. Pouze žádající objekt může vydat žádost o zrušení a každý naslouchací proces je zodpovědný za všímat požadavek a reagovat na něj vhodným a včasným způsobem.  
  
 Obecný vzor pro implementaci modelu zrušení spolupráce je:  
  
- Vytvořte správu <xref:System.Threading.CancellationTokenSource> objektu, který spravuje a odesílá oznámení o zrušení jednotlivým tokenům zrušení.  
  
- Předajte token <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> vrácený vlastností každému úkolu nebo vláknu, které naslouchá zrušení.  
  
- Poskytněte mechanismus pro každý úkol nebo vlákno reagovat na zrušení.  
  
- Volání <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metody poskytnout oznámení o zrušení.  
  
> [!IMPORTANT]
> Třída <xref:System.Threading.CancellationTokenSource> implementuje rozhraní <xref:System.IDisposable>. Měli byste se ujistit, že volání <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> metody po dokončení pomocí zdroje tokenu zrušení uvolnit všechny nespravované prostředky, které drží.  
  
 Následující obrázek znázorňuje vztah mezi zdrojem tokenu a všemi kopiemi jeho tokenu.  
  
 ![CancellationTokenSource a tokeny zrušení](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Nový model zrušení usnadňuje vytváření aplikací a knihoven podporujících zrušení a podporuje následující funkce:  
  
- Zrušení je spolupráce a není vynuceno na posluchače. Naslouchací proces určuje, jak řádně ukončit v reakci na požadavek na zrušení.  
  
- Žádost se liší od naslouchání. Objekt, který vyvolá zrušitelnou operaci, může řídit, kdy je požadováno (pokud vůbec).  
  
- Žádající objekt vydá požadavek na zrušení na všechny kopie tokenu pomocí pouze jedno volání metody.  
  
- Naslouchací proces může poslouchat více tokenů současně jejich připojením do jednoho *propojeného tokenu*.  
  
- Kód uživatele si může všimnout a reagovat na žádosti o zrušení z kódu knihovny a kód knihovny může zaznamenávat a reagovat na žádosti o zrušení z uživatelského kódu.  
  
- Naslouchací procesy mohou být upozorněni na požadavky na zrušení dotazování, registrace zpětného volání nebo čekání na popisovače čekání.  
  
## <a name="cancellation-types"></a>Typy zrušení  
 Rámec zrušení je implementována jako sada souvisejících typů, které jsou uvedeny v následující tabulce.  
  
|Název typu|Popis|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|Objekt, který vytvoří token zrušení a také vydá požadavek na zrušení pro všechny kopie tohoto tokenu.|  
|<xref:System.Threading.CancellationToken>|Zjednodušený typ hodnoty předán jeden nebo více posluchačů, obvykle jako parametr metody. Naslouchací `IsCancellationRequested` procesy sledovat hodnotu vlastnost tokenu dotazování, zpětné volání nebo popisovač čekání.|  
|<xref:System.OperationCanceledException>|Přetížení konstruktoru této výjimky <xref:System.Threading.CancellationToken> přijmout jako parametr. Naslouchací procesy mohou volitelně vyvolat tuto výjimku k ověření zdroje zrušení a upozornit ostatní, že odpověděl na žádost o zrušení.|  
  
 Nový model zrušení je integrován do rozhraní .NET Framework v několika typech. Nejdůležitější z nich <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>jsou <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> , <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>a . Doporučujeme použít tento nový model zrušení pro všechny nové knihovny a kódu aplikace.  
  
## <a name="code-example"></a>Příklad kódu  
 V následujícím příkladu žádající objekt <xref:System.Threading.CancellationTokenSource> vytvoří objekt a <xref:System.Threading.CancellationTokenSource.Token%2A> pak předá jeho vlastnost cancelable operace. Operace, která obdrží požadavek monitoruje <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> hodnotu vlastnosttokenu dotazování. Když se `true`hodnota stane , naslouchací proces může ukončit jakýmkoli způsobem je vhodné. V tomto příkladu metoda pouze ukončí, což je vše, co je požadováno v mnoha případech.  
  
> [!NOTE]
> Příklad používá <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metodu k prokázání, že nové rozhraní pro zrušení je kompatibilní se staršími rozhraními API. Příklad, který používá nový <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> upřednostňovaný typ, najdete v [tématu How to: Cancel a Task and its Children](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>Zrušení operace versus zrušení objektu  
 V novém rámci zrušení zrušení odkazuje na operace, nikoli objekty. Požadavek na zrušení znamená, že operace by měla zastavit co nejdříve po provedení požadované vyčištění. Jeden token zrušení by měl odkazovat na jednu "zrušitelnou operaci", ale tato operace může být implementována ve vašem programu. Po <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost tokenu byla nastavena na `true`, `false`nelze obnovit na . Proto tokeny zrušení nelze znovu použít po jejich zrušení.  
  
 Pokud požadujete mechanismus zrušení objektu, můžete jej založit <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> na mechanismu zrušení operace voláním metody, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Pokud objekt podporuje více než jednu souběžnou zrušitelnou operaci, předajte samostatný token jako vstup pro každou odlišnou zrušitelnou operaci. Tímto způsobem může být jedna operace zrušena, aniž by to ovlivnilo ostatní.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Naslouchání a odpovídání na žádosti o zrušení  
 V delegáta uživatele implementátor zrušitelné operace určuje, jak ukončit operaci v reakci na požadavek na zrušení. V mnoha případech může delegát uživatele provést všechny požadované vyčištění a okamžitě vrátit.  
  
 Ve složitějších případech však může být nutné, aby delegát uživatele upozornil kód knihovny, že došlo ke zrušení. V takových případech je správný způsob ukončení operace pro <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>delegáta volat , <xref:System.OperationCanceledException> metoda, která způsobí, že vyvolá. Kód knihovny můžete zachytit tuto výjimku ve vlákně delegáta uživatele a zkontrolujte token výjimky k určení, zda výjimka označuje kooperativní zrušení nebo jiné výjimečné situace.  
  
 Třída <xref:System.Threading.Tasks.Task> zpracovává <xref:System.OperationCanceledException> tímto způsobem. Další informace naleznete v [tématu Zrušení úkolu](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Naslouchání podle hlasování  
 Pro dlouhotrvající výpočty, které smyčky nebo recurse, můžete naslouchat žádosti o zrušení pravidelně <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> dotazování hodnotu vlastnosti. Pokud je `true`jeho hodnota , metoda by měla vyčistit a ukončit co nejrychleji. Optimální frekvence dotazování závisí na typu aplikace. Je na vývojáři, aby určil nejlepší frekvenci dotazování pro daný program. Samotné dotazování nemá významný vliv na výkon. Následující příklad ukazuje jeden možný způsob, jak dotazování.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Podrobnější příklad najdete v [tématu How to: Listen for Cancellation Requests by Polling](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md).  
  
### <a name="listening-by-registering-a-callback"></a>Naslouchání registrací zpětného volání  
 Některé operace mohou být blokovány takovým způsobem, že nemohou včas zkontrolovat hodnotu tokenu zrušení. V těchto případech můžete zaregistrovat metodu zpětného volání, která odblokuje metodu při přijetí požadavku na zrušení.  
  
 Metoda <xref:System.Threading.CancellationToken.Register%2A> vrátí <xref:System.Threading.CancellationTokenRegistration> objekt, který se používá speciálně pro tento účel. Následující příklad ukazuje, jak <xref:System.Threading.CancellationToken.Register%2A> použít metodu ke zrušení asynchronního webového požadavku.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 Objekt <xref:System.Threading.CancellationTokenRegistration> spravuje synchronizaci vláken a zajišťuje, že zpětné volání přestane provádět v přesném okamžiku.  
  
 Aby byla zajištěna odezva systému a aby se zabránilo zablokování, je třeba při registraci zpětná volání dodržovat následující pokyny:  
  
- Metoda zpětného volání by měla být rychlá, protože se <xref:System.Threading.CancellationTokenSource.Cancel%2A> nazývá synchronně a proto volání nevrací, dokud se nevrátí zpětné volání.  
  
- Pokud voláte, <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> když je zpětné volání spuštěno, a podržíte zámek, na který čeká zpětné volání, může váš program uváznout na mrtvém bodě. Po `Dispose` vrácení můžete uvolnit všechny prostředky vyžadované zpětné volání.  
  
- Zpětná volání by neměla <xref:System.Threading.SynchronizationContext> provádět žádné ruční vlákno nebo použití v zpětném volání. Pokud zpětné volání musí být spuštěno <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> v určitém vlákně, použijte konstruktor, který <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>umožňuje určit, že cíl syncContext je aktivní . Provádění ručního zřetězení v zpětném volání může způsobit zablokování.  
  
 Podrobnější příklad najdete v [tématu How to: Register Callbacks for Cancellation Requests](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Naslouchání pomocí popisovače čekání  
 Pokud zrušitelná operace může blokovat, zatímco čeká na synchronizaci <xref:System.Threading.Semaphore?displayProperty=nameWithType>primitivní, jako <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> je například <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> nebo , můžete použít vlastnost povolit operaci čekat na událost a požadavek na zrušení. Popisovač čekání token zrušení bude signalizovánv reakci na požadavek na zrušení a <xref:System.Threading.WaitHandle.WaitAny%2A> metoda můžete použít vrácenou hodnotu metody k určení, zda byl token zrušení, který signalizoval. Operace pak může pouze ukončit, nebo hodit <xref:System.OperationCanceledException>, podle potřeby.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 V novém kódu, který se <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> zaměřuje <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> na rozhraní .NET `Wait` Framework 4 a oba podporují nové rámce zrušení v jejich metody. Můžete předat <xref:System.Threading.CancellationToken> metodu a při zrušení je požadováno, událost probudí a <xref:System.OperationCanceledException>vyvolá .  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Úplnější příklad najdete v [tématu How to: Listen for cancellation requests that have Wait Handles](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md).  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Poslech více tokenů současně  
 V některých případech naslouchací proces může mít naslouchat více tokeny zrušení současně. Například zrušitelná operace může mít sledovat interní token zrušení kromě tokenu předaného externě jako argument parametru metody. Chcete-li to provést, vytvořte zdroj propojeného tokenu, který může spojit dva nebo více tokenů do jednoho tokenu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Všimněte si, `Dispose` že musíte volat na zdroj propojeného tokenu, když jste hotovi s ním. Podrobnější příklad najdete v [tématu How to: Listen for Multiple Cancellation Requests](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md).  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Spolupráce mezi knihovním kódem a uživatelským kódem  
 Sjednocená architektura zrušení umožňuje kód knihovny zrušit uživatelský kód a uživatelský kód zrušit kód knihovny kooperativním způsobem. Hladká spolupráce závisí na každé straně podle těchto pokynů:  
  
- Pokud kód knihovny poskytuje zrušitelné operace, měl by také poskytnout veřejné metody, které přijímají externí token zrušení, aby uživatelský kód mohl požádat o zrušení.  
  
- Pokud kód knihovny volá do uživatelského kódu, kód knihovny by měl interpretovat OperationCanceledException(externalToken) jako *kooperativní zrušení*a ne nutně jako výjimku selhání.  
  
- Uživatelští delegáti by se měli pokusit reagovat na žádosti o zrušení z kódu knihovny včas.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>a <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> jsou příklady tříd, které se řídí těmito pokyny. Další informace naleznete v [tématu Zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md) a [postup: Zrušení dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="see-also"></a>Viz také

- [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)
