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
ms.openlocfilehash: 3e39ee597f5142f2b3ccbd4ded49e59d6700ec8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960146"
---
# <a name="cancellation-in-managed-threads"></a>Zrušení ve spravovaných vláknech
Počínaje .NET Framework 4 používá .NET Framework jednotný model pro spolupráci se zrušením asynchronních nebo dlouhodobě spuštěných synchronních operací. Tento model je založen na odlehčeném objektu nazývaném token zrušení. Objekt, který vyvolá jednu nebo více operací, které lze zrušit, například vytvořením nových vláken nebo úkolů, předá token každé operaci. Jednotlivé operace mohou v nástroji předat kopie tokenu jiným operacím. V některých případech může objekt, který vytvořil token, použít ho k vyžádání, že operace přestanou dělat, co dělají. Pouze žádající objekt může vystavit žádost o zrušení a každý naslouchací proces zodpovídá za všímáteí žádosti a na ni včas reagovat.  
  
 Obecný vzor pro implementaci modelu zrušení spolupráce je:  
  
- Vytvořte instanci objektu, který spravuje a odesílá oznámení o zrušení na jednotlivé tokeny zrušení. <xref:System.Threading.CancellationTokenSource>  
  
- Předání tokenu vráceného <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> vlastností každému úkolu nebo vláknu, který naslouchá ke zrušení.  
  
- Poskytněte mechanismus pro každý úkol nebo vlákno, které budou reagovat na zrušení.  
  
- <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> Zavolejte metodu pro poskytnutí oznámení o zrušení.  
  
> [!IMPORTANT]
> <xref:System.Threading.CancellationTokenSource> Třída<xref:System.IDisposable> implementuje rozhraní. Měli byste být schopni zavolat <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> metodu po dokončení použití zdroje tokenu zrušení pro uvolnění jakýchkoli nespravovaných prostředků, které obsahuje.  
  
 Následující ilustrace znázorňuje vztah mezi zdrojem tokenu a všemi kopiemi jeho tokenu.  
  
 ![CancellationTokenSource a zrušení tokenů](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Nový model zrušení usnadňuje vytváření aplikací a knihoven s podporou zrušení a podporuje následující funkce:  
  
- Zrušení je kooperativní a není vynuceno na naslouchací službě. Naslouchací proces určuje, jak se má řádně ukončit reakce na žádost o zrušení.  
  
- Požadavek se liší od naslouchání. Objekt, který vyvolá operaci s možnou metodou zrušení, může řídit, kdy se požaduje zrušení zrušení.  
  
- Žádající objekt vydá žádost o zrušení všem kopiím tokenu pomocí volání pouze jednoho volání metody.  
  
- Naslouchací proces může naslouchat více tokeny současně jejich připojením k jednomu *odkazovanému tokenu*.  
  
- Uživatelský kód může všimnout a reagovat na žádosti o zrušení z kódu knihovny a kód knihovny může všimnout a reagovat na žádosti o zrušení z uživatelského kódu.  
  
- Naslouchací procesy mohou být upozorňovány na žádosti o zrušení pomocí cyklického dotazování, registrace zpětného volání nebo čekání na obslužné rutiny čekání.  
  
## <a name="cancellation-types"></a>Typy zrušení  
 Rozhraní zrušení je implementováno jako sada souvisejících typů, které jsou uvedeny v následující tabulce.  
  
|Název typu|Popis|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|Objekt, který vytvoří token zrušení, a také vydá požadavek na zrušení pro všechny kopie tohoto tokenu.|  
|<xref:System.Threading.CancellationToken>|Nenáročný typ hodnoty předaný jednomu nebo více posluchačům, obvykle jako parametr metody. Naslouchací procesy monitorují hodnotu `IsCancellationRequested` vlastnosti tokenu pomocí cyklického dotazování, zpětného volání nebo popisovače čekání.|  
|<xref:System.OperationCanceledException>|Přetížení konstruktoru této výjimky přijímají <xref:System.Threading.CancellationToken> jako parametr. Naslouchací procesy mohou volitelně vyvolat tuto výjimku za účelem ověření zdroje zrušení a informování dalších uživatelů, že odpověděli na žádost o zrušení.|  
  
 Nový model zrušení je integrován do .NET Framework v několika typech. Nejdůležitějšími <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>těmi jsou <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> , a .<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> Pro všechny nové knihovny a kód aplikace doporučujeme použít tento nový model zrušení.  
  
## <a name="code-example"></a>Příklad kódu  
 V následujícím příkladu žádající objekt vytvoří <xref:System.Threading.CancellationTokenSource> objekt a poté předá jeho <xref:System.Threading.CancellationTokenSource.Token%2A> vlastnost operaci, kterou lze zrušit. Operace, která přijme požadavek, monitoruje hodnotu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnosti tokenu pomocí cyklického dotazování. Když se hodnota přestanou `true`, naslouchací proces může skončit jakýmkoli způsobem. V tomto příkladu metoda pouze ukončí, což je vše vyžadované v mnoha případech.  
  
> [!NOTE]
> V příkladu se používá <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda k předvedení, že nové rozhraní zrušení je kompatibilní se staršími rozhraními API. Příklad, který používá nový preferovaný <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typ, naleznete v tématu [How to: Zruší úlohu a její podřízené položky](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>Zrušení operace versus zrušení objektu  
 V novém rozhraní zrušení odkazuje zrušení na operace, nikoli na objekty. Žádost o zrušení znamená, že operace by se měla zastavit co nejdříve po provedení veškerého potřebného vyčištění. Jeden token zrušení by měl odkazovat na jednu operaci, kterou lze zrušit, tato operace však může být implementována v programu. Po nastavení `true` `false`vlastnosti tokenu na hodnotu nemůže být obnovena. <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> Proto se tokeny zrušení po zrušení nedají znovu použít.  
  
 Pokud vyžadujete mechanismus zrušení objektu, můžete ho založit na mechanismu zrušení operace voláním <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> metody, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Pokud objekt podporuje více než jednu souběžnou operaci, která může být zrušena, předejte samostatný token jako vstup do každé samostatné operace zrušení. Tímto způsobem je možné zrušit jednu operaci, aniž by to ovlivnilo ostatní.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Naslouchat a reagovat na žádosti o zrušení  
 V uživatelském delegátu může implementátor operace s zrušením určit, jak ukončit operaci v reakci na žádost o zrušení. V mnoha případech může delegát uživatele provést pouze požadované vyčištění a pak hned vrátit.  
  
 Ve složitějších případech ale může být nutné, aby uživatel s delegátem upozornil na kód knihovny, ke kterému došlo ke zrušení. V takových případech je správný způsob, jak operaci ukončit, je pro delegáta volat <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>metodu, která <xref:System.OperationCanceledException> způsobí vyvolání. Kód knihovny může zachytit tuto výjimku ve vlákně delegáta uživatele a ověřit token výjimky a zjistit, zda výjimka označuje kooperativní zrušení nebo jinou výjimečnou situaci.  
  
 <xref:System.Threading.Tasks.Task> Třída zpracovává<xref:System.OperationCanceledException> tímto způsobem. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Naslouchání pomocí cyklického dotazování  
 U dlouhotrvajících výpočtů, které cyklují nebo rekurzování můžete poslouchat žádost o zrušení pravidelným dotazování hodnoty <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> vlastnosti. Pokud je `true`jeho hodnota, metoda by měla co nejrychleji vyčistit a ukončit. Optimální frekvence cyklického dotazování závisí na typu aplikace. Aby bylo možné určit nejlepší četnost dotazování pro libovolný daný program, je to pro vývojáře. Cyklické dotazování sama o sobě nijak neovlivňuje výkon. Následující příklad ukazuje jeden možný způsob dotazování.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Úplnější příklad naleznete v tématu [How to: Naslouchat žádostem o zrušení pomocí](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md)cyklického dotazování.  
  
### <a name="listening-by-registering-a-callback"></a>Naslouchání registrací zpětného volání  
 Některé operace se mohou zablokovat takovým způsobem, že nemohou včas kontrolovat hodnotu tokenu zrušení. V těchto případech můžete zaregistrovat metodu zpětného volání, která odblokuje metodu při přijetí žádosti o zrušení.  
  
 <xref:System.Threading.CancellationToken.Register%2A> Metoda<xref:System.Threading.CancellationTokenRegistration> vrátí objekt, který se používá specificky pro tento účel. Následující příklad ukazuje, jak použít <xref:System.Threading.CancellationToken.Register%2A> metodu pro zrušení asynchronního webového požadavku.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 <xref:System.Threading.CancellationTokenRegistration> Objekt spravuje synchronizaci vláken a zajišťuje, že zpětné volání přestane být spuštěno v přesném bodě v čase.  
  
 Aby se zajistila odezva systému a aby se zabránilo zablokování, při registraci zpětných volání musí být dodrženy následující pokyny:  
  
- Metoda zpětného volání by měla být rychlá, protože je volána synchronně, proto volání <xref:System.Threading.CancellationTokenSource.Cancel%2A> nevrátí, dokud zpětné volání nevrátí.  
  
- Pokud zavoláte <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> na běhu zpětného volání a podržíte zámek, na kterém zpětné volání čeká, váš program může zablokovat. Po `Dispose` návratu můžete uvolnit všechny prostředky, které zpětné volání vyžaduje.  
  
- Zpětná volání by neměla provádět žádné ruční vlákno <xref:System.Threading.SynchronizationContext> nebo použití ve zpětném volání. Pokud zpětné volání musí být spuštěno v konkrétním vlákně, <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> použijte konstruktor, který umožňuje určit, že cílový syncContext je aktivní. <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> Ruční provádění vláken ve zpětném volání může způsobit zablokování.  
  
 Úplnější příklad naleznete v tématu [How to: Zaregistrujte zpětná volání](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md)pro žádosti o zrušení.  
  
### <a name="listening-by-using-a-wait-handle"></a>Poslech pomocí popisovače čekání  
 Když se může zrušit operace, která může být zablokovaná, zatímco čeká na primitivu <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> synchronizace <xref:System.Threading.Semaphore?displayProperty=nameWithType>, jako je nebo <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> , můžete vlastnost použít k povolení operace počkat na událost i na žádost o zrušení. Obslužná rutina čekání na token zrušení se bude signalizovat jako odpověď na žádost o zrušení a metoda může použít návratovou hodnotu <xref:System.Threading.WaitHandle.WaitAny%2A> metody k určení, zda se jednalo o token zrušení, který signalizace. Operace pak může pouze skončit nebo vyvolat <xref:System.OperationCanceledException>, podle potřeby.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 V novém kódu, který cílí na .NET Framework 4 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> , <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> a obě podporují nové rozhraní zrušení v jejich `Wait` metodách. Můžete předat <xref:System.Threading.CancellationToken> metodě a když je požadováno zrušení, událost se probudí a <xref:System.OperationCanceledException>vyvolá.  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Úplnější příklad naleznete v tématu [How to: Naslouchat žádostem o zrušení, které](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md)mají obslužné rutiny čekání.  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Souběžné naslouchat více tokenům  
 V některých případech může naslouchací proces naslouchat více tokenům zrušení současně. Například operace s zrušením může být nutné monitorovat interní token zrušení kromě tokenu předaného externě jako argument parametru metody. Chcete-li to provést, vytvořte propojený zdroj tokenu, který může spojit dva nebo více tokenů do jednoho tokenu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Všimněte si, že když `Dispose` s ním budete hotovi, musíte zavolat na propojený zdroj tokenu. Úplnější příklad naleznete v tématu [How to: Naslouchat více žádostem](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md)o zrušení.  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Spolupráce mezi kódem knihovny a uživatelským kódem  
 Jednotná architektura zrušení umožňuje kódu knihovny zrušit kód uživatele a kód pro zrušení kódu knihovny. Bezproblémová spolupráce závisí na každé ze strany těchto pokynů:  
  
- Pokud kód knihovny poskytuje operace, které lze zrušit, měla by také poskytovat veřejné metody, které přijímají externí token zrušení, aby mohl kód uživatele požádat o zrušení.  
  
- Pokud kód knihovny volá do uživatelského kódu, kód knihovny by měl interpretovat OperationCanceledException (externalToken) jako *kooperativní zrušení*a nemusí nutně znamenat výjimku selhání.  
  
- Delegáti uživatele by se měli snažit včas odpovědět na žádosti o zrušení z kódu knihovny.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>a <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> jsou příklady tříd, které následují podle těchto pokynů. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md) a [postup: Zruší dotaz](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)PLINQ.  
  
## <a name="see-also"></a>Viz také:

- [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)
