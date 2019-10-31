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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138143"
---
# <a name="cancellation-in-managed-threads"></a>Zrušení ve spravovaných vláknech
Počínaje .NET Framework 4 používá .NET Framework jednotný model pro spolupráci se zrušením asynchronních nebo dlouhodobě spuštěných synchronních operací. Tento model je založen na odlehčeném objektu nazývaném token zrušení. Objekt, který vyvolá jednu nebo více operací, které lze zrušit, například vytvořením nových vláken nebo úkolů, předá token každé operaci. Jednotlivé operace mohou v nástroji předat kopie tokenu jiným operacím. V některých případech může objekt, který vytvořil token, použít ho k vyžádání, že operace přestanou dělat, co dělají. Pouze žádající objekt může vystavit žádost o zrušení a každý naslouchací proces zodpovídá za všímáteí žádosti a na ni včas reagovat.  
  
 Obecný vzor pro implementaci modelu zrušení spolupráce je:  
  
- Vytvořte instanci objektu <xref:System.Threading.CancellationTokenSource>, který spravuje a odesílá oznámení o zrušení na jednotlivé tokeny zrušení.  
  
- Předání tokenu vráceného vlastností <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> každému úkolu nebo vláknu, které naslouchá ke zrušení.  
  
- Poskytněte mechanismus pro každý úkol nebo vlákno, které budou reagovat na zrušení.  
  
- Chcete-li poskytnout oznámení o zrušení, zavolejte metodu <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> Třída <xref:System.Threading.CancellationTokenSource> implementuje rozhraní <xref:System.IDisposable>. Je nutné volat metodu <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> po dokončení použití zdroje tokenu zrušení k uvolnění jakýchkoli nespravovaných prostředků, které obsahuje.  
  
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
|<xref:System.Threading.CancellationToken>|Nenáročný typ hodnoty předaný jednomu nebo více posluchačům, obvykle jako parametr metody. Naslouchací procesy monitorují hodnotu vlastnosti `IsCancellationRequested` tokenu pomocí cyklického dotazování, zpětného volání nebo popisovače čekání.|  
|<xref:System.OperationCanceledException>|Přetížení konstruktoru této výjimky přijímají <xref:System.Threading.CancellationToken> jako parametr. Naslouchací procesy mohou volitelně vyvolat tuto výjimku za účelem ověření zdroje zrušení a informování dalších uživatelů, že odpověděli na žádost o zrušení.|  
  
 Nový model zrušení je integrován do .NET Framework v několika typech. Nejdůležitějšími těmi jsou <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> a <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>. Pro všechny nové knihovny a kód aplikace doporučujeme použít tento nový model zrušení.  
  
## <a name="code-example"></a>Příklad kódu  
 V následujícím příkladu objekt žádající objekt vytvoří objekt <xref:System.Threading.CancellationTokenSource> a poté předá jeho vlastnost <xref:System.Threading.CancellationTokenSource.Token%2A> k operaci, kterou lze zrušit. Operace, která přijme požadavek, monitoruje hodnotu vlastnosti <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> tokenu pomocí cyklického dotazování. Když se hodnota `true`, naslouchací proces může skončit jakýmkoli způsobem. V tomto příkladu metoda pouze ukončí, což je vše vyžadované v mnoha případech.  
  
> [!NOTE]
> V příkladu se používá metoda <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> k předvedení, že nové rozhraní zrušení je kompatibilní se staršími rozhraními API. Příklad, který používá nový preferovaný typ <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, naleznete v tématu [How to: Cancel a a jejích potomků](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>Zrušení operace versus zrušení objektu  
 V novém rozhraní zrušení odkazuje zrušení na operace, nikoli na objekty. Žádost o zrušení znamená, že operace by se měla zastavit co nejdříve po provedení veškerého potřebného vyčištění. Jeden token zrušení by měl odkazovat na jednu operaci, kterou lze zrušit, tato operace však může být implementována v programu. Po nastavení vlastnosti <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> tokenu na hodnotu `true`nelze obnovit `false`. Proto se tokeny zrušení po zrušení nedají znovu použít.  
  
 Pokud vyžadujete mechanismus zrušení objektu, můžete ho založit na mechanismu zrušení operace voláním metody <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType>, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Pokud objekt podporuje více než jednu souběžnou operaci, která může být zrušena, předejte samostatný token jako vstup do každé samostatné operace zrušení. Tímto způsobem je možné zrušit jednu operaci, aniž by to ovlivnilo ostatní.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Naslouchat a reagovat na žádosti o zrušení  
 V uživatelském delegátu může implementátor operace s zrušením určit, jak ukončit operaci v reakci na žádost o zrušení. V mnoha případech může delegát uživatele provést pouze požadované vyčištění a pak hned vrátit.  
  
 Ve složitějších případech ale může být nutné, aby uživatel s delegátem upozornil na kód knihovny, ke kterému došlo ke zrušení. V takových případech je správný způsob, jak operaci ukončit, je, aby delegát volal <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, metodu, která způsobí, že <xref:System.OperationCanceledException> vyvolána. Kód knihovny může zachytit tuto výjimku ve vlákně delegáta uživatele a ověřit token výjimky a zjistit, zda výjimka označuje kooperativní zrušení nebo jinou výjimečnou situaci.  
  
 <xref:System.Threading.Tasks.Task> třída zpracovává <xref:System.OperationCanceledException> tímto způsobem. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Naslouchání pomocí cyklického dotazování  
 U dlouhotrvajících výpočtů, které smyčka nebo rekurzuje, můžete naslouchat žádosti o zrušení pravidelným dotazování hodnoty vlastnosti <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType>. Pokud je jeho hodnota `true`, měla by metoda co nejrychleji vyčistit a ukončit. Optimální frekvence cyklického dotazování závisí na typu aplikace. Aby bylo možné určit nejlepší četnost dotazování pro libovolný daný program, je to pro vývojáře. Cyklické dotazování sama o sobě nijak neovlivňuje výkon. Následující příklad ukazuje jeden možný způsob dotazování.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Úplnější příklad naleznete v tématu [How to: Listening for requests on a cyklické dotazování](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md).  
  
### <a name="listening-by-registering-a-callback"></a>Naslouchání registrací zpětného volání  
 Některé operace se mohou zablokovat takovým způsobem, že nemohou včas kontrolovat hodnotu tokenu zrušení. V těchto případech můžete zaregistrovat metodu zpětného volání, která odblokuje metodu při přijetí žádosti o zrušení.  
  
 Metoda <xref:System.Threading.CancellationToken.Register%2A> vrátí objekt <xref:System.Threading.CancellationTokenRegistration>, který se používá specificky pro tento účel. Následující příklad ukazuje, jak použít metodu <xref:System.Threading.CancellationToken.Register%2A> pro zrušení asynchronního webového požadavku.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 Objekt <xref:System.Threading.CancellationTokenRegistration> spravuje synchronizaci vláken a zajišťuje, že zpětné volání přestane být spuštěno v přesném bodě v čase.  
  
 Aby se zajistila odezva systému a aby se zabránilo zablokování, při registraci zpětných volání musí být dodrženy následující pokyny:  
  
- Metoda zpětného volání by měla být rychlá, protože je volána synchronně, proto volání <xref:System.Threading.CancellationTokenSource.Cancel%2A> nevrátí, dokud zpětné volání nevrátí.  
  
- Pokud zavoláte <xref:System.Threading.CancellationTokenRegistration.Dispose%2A>, když je spuštěno zpětné volání, a držíte zámek, na kterém zpětné volání čeká, váš program může zablokovat. Až `Dispose` vrátí, můžete uvolnit všechny prostředky, které zpětné volání vyžaduje.  
  
- Zpětná volání by neměla provádět žádné ruční vlákno nebo <xref:System.Threading.SynchronizationContext> použití ve zpětném volání. Pokud zpětné volání musí být spuštěno v konkrétním vlákně, použijte konstruktor <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType>, který umožňuje určit, že cílový syncContext je aktivní <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>. Ruční provádění vláken ve zpětném volání může způsobit zablokování.  
  
 Úplnější příklad naleznete v tématu [How to: Register Callbacks for requests](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Poslech pomocí popisovače čekání  
 Když je možné zrušit operaci, která může být blokována při čekání na primitiva synchronizace, jako je <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> nebo <xref:System.Threading.Semaphore?displayProperty=nameWithType>, můžete pomocí vlastnosti <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> povolit operaci počkat na událost i na žádost o zrušení. Obslužná rutina čekání na token zrušení se bude signalizovat jako odpověď na žádost o zrušení a metoda může použít návratovou hodnotu metody <xref:System.Threading.WaitHandle.WaitAny%2A> k určení, zda se jednalo o token zrušení, který se signalizace. Operace pak může pouze skončit nebo vyvolávat <xref:System.OperationCanceledException>podle potřeby.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 V novém kódu, který cílí na .NET Framework 4, <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> podporuje nové rozhraní zrušení v jejich `Wait`ch metodách. Můžete předat <xref:System.Threading.CancellationToken> do metody a když je požadováno zrušení, událost se probudí a vyvolá <xref:System.OperationCanceledException>.  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Úplnější příklad naleznete v tématu [How to: Listen for zrušení žádosti, které mají obslužné rutiny čekání](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md).  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Souběžné naslouchat více tokenům  
 V některých případech může naslouchací proces naslouchat více tokenům zrušení současně. Například operace s zrušením může být nutné monitorovat interní token zrušení kromě tokenu předaného externě jako argument parametru metody. Chcete-li to provést, vytvořte propojený zdroj tokenu, který může spojit dva nebo více tokenů do jednoho tokenu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Všimněte si, že když s ním budete hotovi, musíte volat `Dispose` ve zdroji propojeného tokenu. Úplnější příklad naleznete v tématu [How to: Listen for Multiple requests](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md).  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Spolupráce mezi kódem knihovny a uživatelským kódem  
 Jednotná architektura zrušení umožňuje kódu knihovny zrušit kód uživatele a kód pro zrušení kódu knihovny. Bezproblémová spolupráce závisí na každé ze strany těchto pokynů:  
  
- Pokud kód knihovny poskytuje operace, které lze zrušit, měla by také poskytovat veřejné metody, které přijímají externí token zrušení, aby mohl kód uživatele požádat o zrušení.  
  
- Pokud kód knihovny volá do uživatelského kódu, kód knihovny by měl interpretovat OperationCanceledException (externalToken) jako *kooperativní zrušení*a nemusí nutně znamenat výjimku selhání.  
  
- Delegáti uživatele by se měli snažit včas odpovědět na žádosti o zrušení z kódu knihovny.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> jsou příklady tříd, které následují podle těchto pokynů. Další informace naleznete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md) a [Postup: zrušení dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="see-also"></a>Viz také:

- [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)
