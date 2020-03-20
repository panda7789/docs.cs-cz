---
title: Opožděná inicializace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
ms.openlocfilehash: 4f2b585dded6e20bb604f623217c6d1f1505c097
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180568"
---
# <a name="lazy-initialization"></a>Opožděná inicializace
*Opožděná inicializace* objektu znamená, že jeho vytvoření je odloženo, dokud není poprvé použit. (Pro toto téma jsou synonyma termíny *opožděná inicializace* a *opožděná instance.)* Opožděná inicializace se používá především ke zlepšení výkonu, vyhnout se nehospodárným výpočtům a snížit požadavky na paměť programu. Toto jsou nejběžnější scénáře:  
  
- Pokud máte objekt, který je nákladné vytvořit a program nemusí použít. Předpokládejme například, že máte `Customer` v paměti `Orders` objekt, který má `Order` vlastnost, která obsahuje velké pole objektů, které, které mají být inicializovány, vyžaduje připojení k databázi. Pokud uživatel nikdy nepožádá o zobrazení objednávky nebo použití dat ve výpočtu, pak není důvod k jeho vytvoření použít systémovou paměť nebo výpočetní cykly. Pomocí `Lazy<Orders>` deklarovat `Orders` objekt pro opožděné inicializace, můžete se vyhnout plýtvání systémové prostředky, pokud objekt není použit.  
  
- Pokud máte objekt, který je nákladné vytvořit a chcete odložit jeho vytvoření až po dokončení jiných nákladných operací. Předpokládejme například, že program načte několik instancí objektu při spuštění, ale pouze některé z nich jsou vyžadovány okamžitě. Výkon spuštění programu můžete zlepšit odložením inicializace objektů, které nejsou požadovány, dokud nebudou vytvořeny požadované objekty.  
  
 I když můžete napsat vlastní kód k provedení opožděné <xref:System.Lazy%601> inicializace, doporučujeme použít místo. <xref:System.Lazy%601>a jeho související typy také podporují bezpečnost vláken a poskytují konzistentní zásady šíření výjimek.  
  
 V následující tabulce jsou uvedeny typy, které poskytuje rozhraní .NET Framework verze 4 pro povolení opožděné inicializace v různých scénářích.  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Obálka třída, která poskytuje opožděné inicializace sémantiku pro všechny třídy knihovny nebo uživatelem definovaný typ.|  
|<xref:System.Threading.ThreadLocal%601>|Podobá <xref:System.Lazy%601> se s tím rozdílem, že poskytuje opožděné inicializace sémantiku na místní bázi vlákna. Každé vlákno má přístup ke své vlastní jedinečné hodnotě.|  
|<xref:System.Threading.LazyInitializer>|Poskytuje rozšířené `static` `Shared` (v jazyce Visual Basic) metody pro opožděné inicializace objektů bez režie třídy.|  
  
## <a name="basic-lazy-initialization"></a>Základní opožděná inicializace  
 Chcete-li definovat typ opožděné inicializované, `MyType`například , use `Lazy<MyType>` (`Lazy(Of MyType)` v jazyce Visual Basic), jak je znázorněno v následujícím příkladu. Pokud žádný delegát je <xref:System.Lazy%601> předán v konstruktoru, zalomený typ je vytvořen pomocí <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> při prvním přístupu k vlastnosti value. Pokud typ nemá konstruktor bez parametrů, je vyvolána výjimka za běhu.  
  
 V následujícím příkladu `Orders` předpokládejme, že se `Order` jedná o třídu, která obsahuje pole objektů načtených z databáze. Objekt `Customer` obsahuje instanci `Orders`aplikace , ale v závislosti `Orders` na akcích uživatele nemusí být data z objektu vyžadována.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Můžete také předat delegáta <xref:System.Lazy%601> v konstruktoru, který vyvolá přetížení konkrétníkonstruktor u zabaleného typu v době vytvoření a provést všechny další kroky inicializace, které jsou požadovány, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Po vytvoření Lazy objekt je `Orders` vytvořen žádná <xref:System.Lazy%601.Value%2A> instance, dokud je poprvé přístupná vlastnost Lazy proměnné. Při prvním přístupu je zabalený typ vytvořen a vrácen a uložen pro jakýkoli budoucí přístup.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 Objekt <xref:System.Lazy%601> vždy vrátí stejný objekt nebo hodnotu, se kterou byl inicializován. Proto je <xref:System.Lazy%601.Value%2A> vlastnost jen pro čtení. Pokud <xref:System.Lazy%601.Value%2A> ukládá typ odkazu, nelze mu přiřadit nový objekt. (Můžete však změnit hodnotu jeho měnitelných veřejných polí a vlastností.) Pokud <xref:System.Lazy%601.Value%2A> ukládá typ hodnoty, nelze změnit jeho hodnotu. Nicméně můžete vytvořit novou proměnnou znovu vyvoláním konstruktoru proměnné pomocí nových argumentů.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Nová líná instance, stejně jako předchozí, `Orders` není <xref:System.Lazy%601.Value%2A> vytvořena instance, dokud není nejprve přístupná k její vlastnosti.  
  
### <a name="thread-safe-initialization"></a>Inicializace bezpečná pro přístup z více vláken  
 Ve výchozím <xref:System.Lazy%601> nastavení jsou objekty bezpečné pro přístup z více vláken. To znamená, že pokud konstruktor neurčuje druh <xref:System.Lazy%601> bezpečnosti podprocesu, objekty, které vytvoří, jsou bezpečné pro přístup z více vláken. Ve scénářích s více vlákny první <xref:System.Lazy%601.Value%2A> vlákno pro přístup <xref:System.Lazy%601> k vlastnosti objektu bezpečného pro přístup k vláknům inicializuje pro všechny následné přístupy ve všech vláknech a všechna vlákna sdílejí stejná data. Proto nezáleží na tom, které vlákno inicializuje objekt a podmínky časovky jsou neškodné.  
  
> [!NOTE]
> Tuto konzistenci můžete rozšířit na chybové stavy pomocí ukládání výjimek do mezipaměti. Další informace naleznete v další části [Výjimky v opožděné objekty](lazy-initialization.md#ExceptionsInLazyObjects).  
  
 Následující příklad ukazuje, `Lazy<int>` že stejná instance má stejnou hodnotu pro tři samostatné podprocesy.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Pokud požadujete samostatná data v <xref:System.Threading.ThreadLocal%601> každém vlákně, použijte typ, jak je popsáno dále v tomto tématu.  
  
 Někteří <xref:System.Lazy%601> konstruktory mají logický `isThreadSafe` parametr s názvem, <xref:System.Lazy%601.Value%2A> který se používá k určení, zda bude vlastnost přístupná z více vláken. Pokud máte v úmyslu získat přístup k `false` vlastnosti pouze z jednoho vlákna, předat získat výhodu skromný výkon. Pokud máte v úmyslu získat přístup k `true` vlastnosti <xref:System.Lazy%601> z více vláken, předat pokyn instance správně zpracovat spory, ve kterém jedno vlákno vyvolá výjimku v době inicializace.  
  
 Některé <xref:System.Lazy%601> konstruktory <xref:System.Threading.LazyThreadSafetyMode> mají `mode`parametr s názvem . Tyto konstruktory poskytují další režim bezpečnosti závitu. Následující tabulka ukazuje, jak je <xref:System.Lazy%601> bezpečnost podprocesu objektu ovlivněna parametry konstruktoru, které určují bezpečnost podprocesu. Každý konstruktor má maximálně jeden takový parametr.  
  
|Bezpečnost závitu objektu|`LazyThreadSafetyMode``mode` parametr|Logický `isThreadSafe` parametr|Žádné bezpečnostní parametry závitu|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|Plně bezpečné pro přístup z více vláken; pouze jedno vlákno najednou se pokusí inicializovat hodnotu.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Ano.|  
|Není bezpečné pro přístup z více vláken.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Neužívá se.|  
|Plně bezpečné pro přístup z více vláken; vlákna závod inicializovat hodnotu.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Neužívá se.|Neužívá se.|  
  
 Jak ukazuje tabulka, <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> určení `mode` parametru je stejné `true` jako `isThreadSafe` určení parametru <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> a určení je `false`stejné jako určení .  
  
 Zadání <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> umožňuje více vláken pokusit se inicializovat <xref:System.Lazy%601> instanci. Pouze jedno vlákno může vyhrát tento závod a všechny ostatní podprocesy obdrží hodnotu, která byla inicializována úspěšným vláknem. Pokud je vyvolána výjimka na vlákno během inicializace, toto vlákno neobdrží hodnotu nastavenou úspěšným vláknem. Výjimky nejsou ukládány do mezipaměti, <xref:System.Lazy%601.Value%2A> takže následný pokus o přístup k vlastnosti může mít za následek úspěšnou inicializaci. To se liší od způsobu, jakým jsou výjimky zpracovány v jiných režimech, což je popsáno v následující části. Další informace naleznete <xref:System.Threading.LazyThreadSafetyMode> ve výčtu.  
  
<a name="ExceptionsInLazyObjects"></a>
## <a name="exceptions-in-lazy-objects"></a>Výjimky v opožděných objektech  
 Jak již bylo <xref:System.Lazy%601> uvedeno dříve, objekt vždy vrátí stejný objekt nebo <xref:System.Lazy%601.Value%2A> hodnotu, která byla inicializována s, a proto je vlastnost jen pro čtení. Pokud povolíte ukládání výjimek do mezipaměti, tato neměnnost se vztahuje také na chování výjimek. Pokud opožděně inicializovaný objekt má povolen ukládání výjimek do mezipaměti <xref:System.Lazy%601.Value%2A> a vyvolá výjimku z jeho metody inicializace <xref:System.Lazy%601.Value%2A> při prvním přístupu k vlastnosti, je vyvolána stejná výjimka při každém následném pokusu o přístup k vlastnosti. Jinými slovy konstruktor zabalené typu je nikdy znovu vyvolána, a to i ve scénářích s více vlákny. Proto <xref:System.Lazy%601> objekt nemůže vyvolat výjimku na jeden přístup a vrátit hodnotu na následný přístup.  
  
 Ukládání výjimek do mezipaměti <xref:System.Lazy%601?displayProperty=nameWithType> je povoleno při použití libovolného konstruktoru, který přebírá metodu inicializace (parametr);`valueFactory` například je povolena při `Lazy(T)(Func(T))`použití konstruktoru. Pokud konstruktor také <xref:System.Threading.LazyThreadSafetyMode> přebírá`mode` hodnotu <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> ( <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>parametr), zadejte nebo . Zadání metody inicializace umožňuje ukládání výjimek do mezipaměti pro tyto dva režimy. Metoda inicializace může být velmi jednoduchá. Například může volat konstruktor bez `T`parametrů `new Lazy<Contents>(() => new Contents(), mode)` pro : `New Lazy(Of Contents)(Function() New Contents())` v jazyce C# nebo v jazyce Visual Basic. Pokud použijete <xref:System.Lazy%601?displayProperty=nameWithType> konstruktor, který neurčuje metodu inicializace, výjimky, které `T` jsou vyvolány konstruktorem bez parametrů, nejsou uloženy do mezipaměti. Další informace naleznete <xref:System.Threading.LazyThreadSafetyMode> ve výčtu.  
  
> [!NOTE]
> Pokud vytvoříte <xref:System.Lazy%601> objekt `isThreadSafe` s parametrem `false` konstruktoru nastaveným na nebo parametrem konstruktoru `mode` nastaveným na <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>, musíte k objektu <xref:System.Lazy%601> přistupovat z jednoho vlákna nebo zadat vlastní synchronizaci. To platí pro všechny aspekty objektu, včetně ukládání výjimek do mezipaměti.  
  
 Jak je uvedeno v <xref:System.Lazy%601> předchozí části, <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> objekty vytvořené zadáním výjimky jinak. S <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>, více vláken může soutěžit <xref:System.Lazy%601> o inicializaci instance. V tomto případě výjimky nejsou uloženy do mezipaměti a pokusy o přístup k <xref:System.Lazy%601.Value%2A> vlastnosti může pokračovat, dokud inicializace je úspěšná.  
  
 Následující tabulka shrnuje <xref:System.Lazy%601> způsob, jakým konstruktory řídí ukládání výjimek do mezipaměti.  
  
|Konstruktor|Režim bezpečnosti závitu|Používá metodu inicializace.|Výjimky jsou ukládány do mezipaměti|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Líný(T)()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Ne|Ne|  
|Líný(T)(Func(T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Ano|Ano|  
|Lazy(T)(logická hodnota)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) `false` <xref:System.Threading.LazyThreadSafetyMode.None>nebo (|Ne|Ne|  
|Lazy(T)(Func(T), logická)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) `false` <xref:System.Threading.LazyThreadSafetyMode.None>nebo (|Ano|Ano|  
|Lazy(T)(LazyThreadSafetyMode)|Zadané uživatelem|Ne|Ne|  
|Lazy(T)(Func(T), LazyThreadSafetyMode)|Zadané uživatelem|Ano|Ne, pokud <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>uživatel určuje ; jinak ano.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Implementace vlastnosti inicializované inicializovanou  
 Chcete-li implementovat veřejnou vlastnost pomocí opožděné inicializace, definujte záložní pole vlastnosti jako <xref:System.Lazy%601>a <xref:System.Lazy%601.Value%2A> vrátíte vlastnost z `get` přistupujícího objektu vlastnosti.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 Vlastnost <xref:System.Lazy%601.Value%2A> je jen pro čtení; proto vlastnost, která zveřejňuje nemá `set` žádný přistupující objekt. Pokud požadujete vlastnost pro čtení a <xref:System.Lazy%601> zápis `set` podporovanou objektem, <xref:System.Lazy%601> musí přistupující objekt vytvořit nový objekt a přiřadit jej k záložnímu úložišti. Přistupující `set` objekt musí vytvořit výraz lambda, který vrátí `set` novou hodnotu vlastnosti, která byla předána <xref:System.Lazy%601> přistupujícímu objektu, a předat tento výraz lambda konstruktoru pro nový objekt. Další přístup vlastnosti <xref:System.Lazy%601.Value%2A> způsobí inicializaci <xref:System.Lazy%601>nového <xref:System.Lazy%601.Value%2A> a jeho vlastnost poté vrátí novou hodnotu, která byla přiřazena vlastnosti. Důvodem pro toto spletité uspořádání je zachovat vícevláknové ochrany zabudované do <xref:System.Lazy%601>. V opačném případě by přístupové objekty vlastnosti <xref:System.Lazy%601.Value%2A> musely ukládat do mezipaměti první hodnotu vrácenou vlastností a upravovat pouze hodnotu uloženou v mezipaměti a k tomu by bylo nutné napsat vlastní kód bezpečný pro přístup pod proces. Z důvodu další inicializace vyžadované <xref:System.Lazy%601> vlastnosti pro čtení a zápis ukrytý objektem nemusí být výkon přijatelný. Kromě toho, v závislosti na konkrétním scénáři, může být nutná další koordinace, aby se zabránilo sporným podmínkám mezi settery a gettery.  
  
## <a name="thread-local-lazy-initialization"></a>Opožděná inicializace místního vlákna  
 V některých scénářích s více vlákny můžete chtít dát každému vláknu vlastní soukromá data. Tato data se nazývají *místní data podprocesu*. V rozhraní .NET Framework verze 3.5 a `ThreadStatic` starší, můžete použít atribut statickou proměnnou, aby bylo vlákno místní. Použití atributu `ThreadStatic` však může vést k jemným chybám. Například i základní inicializační příkazy způsobí, že proměnná bude inicializována pouze v prvním vlákně, které k ní přistupuje, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 Ve všech ostatních vláknech bude proměnná inicializována pomocí výchozí hodnoty (nula). Jako alternativu v rozhraní .NET Framework verze <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> 4 můžete použít typ k vytvoření proměnné založené na instancích, místní vlákno, která je inicializována na všech podvcích <xref:System.Action%601> delegátem, který zadáte. V následujícím příkladu se všem `counter` vláknům, ke kterým přistupuje, zobrazí počáteční hodnota jako 1.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601>zabalí svůj objekt v podstatě stejným způsobem jako <xref:System.Lazy%601>, s těmito základními rozdíly:  
  
- Každé vlákno inicializuje místní proměnnou podprocesu pomocí vlastních soukromých dat, která nejsou přístupná z jiných vláken.  
  
- Vlastnost <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> je čtení a zápis a lze upravit libovolný počet opakování. To může ovlivnit šíření výjimek, `get` například jedna operace může vyvolat výjimku, ale další může úspěšně inicializovat hodnotu.  
  
- Pokud není k dispozici žádný <xref:System.Threading.ThreadLocal%601> delegát inicializace, inicializuje jeho zalomený typ pomocí výchozí hodnoty typu. V tomto <xref:System.Threading.ThreadLocal%601> ohledu je <xref:System.ThreadStaticAttribute> v souladu s atributem.  
  
 Následující příklad ukazuje, že každé vlákno, které přistupuje k `ThreadLocal<int>` instanci získá vlastní jedinečnou kopii dat.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Místní proměnné podprocesu v Parallel.For a ForEach  
 Při použití <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> nebo metody iterát přes zdroje dat paralelně, můžete použít přetížení, které mají vestavěnou podporu pro místní data podprocesu. V těchto metodách je lokalita vlákna dosažena pomocí místních delegátů k vytvoření, přístupu a vyčištění dat. Další informace naleznete v [tématu How to: Write a Parallel.For Loop with Thread-Local Variables](../../standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) and [How to: Write a Parallel.ForEach Loop with Partition-Local Variables](../../standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Použití opožděné inicializace pro scénáře s nízkou režií  
 Ve scénářích, kde je třeba opožděně inicializovat velký počet objektů, <xref:System.Lazy%601> můžete se rozhodnout, že obtékání každého objektu v vyžaduje příliš mnoho paměti nebo příliš mnoho výpočetních prostředků. Nebo můžete mít přísné požadavky na jak opožděné inicializace je vystavena. V takových případech můžete `static` použít`Shared` ( v jazyce <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> Visual Basic) metody třídy opožděně inicializovat každý objekt bez obtékání v instanci <xref:System.Lazy%601>.  
  
 V následujícím příkladu předpokládejme, že `Orders` místo zabalení celého objektu v jednom <xref:System.Lazy%601> objektu máte opožděné inicializované jednotlivé `Order` objekty pouze v případě, že jsou požadovány.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 V tomto příkladu všimněte si, že postup inicializace je vyvolána na každé iteraci smyčky. Ve scénářích s více vlákny je první vlákno, které vyvolá inicializační proceduru, ten, jehož hodnotu vidí všechna vlákna. Pozdější vlákna také vyvolat postup inicializace, ale jejich výsledky nejsou použity. Pokud tento druh potenciální spor není přijatelné, použijte <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> přetížení, který trvá logický argument a objekt synchronizace.  
  
## <a name="see-also"></a>Viz také

- [Základy dělení na spravovaná vlákna](../../standard/threading/managed-threading-basics.md)
- [Vlákna a dělení na vlákna](../../standard/threading/threads-and-threading.md)
- [Task Parallel Library (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Postupy: Provádění opožděné inicializace objektů](how-to-perform-lazy-initialization-of-objects.md)
