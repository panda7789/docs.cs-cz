---
title: Opožděná inicializace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce217e2ed8e542ad0f7122970655aa32a353f51a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949939"
---
# <a name="lazy-initialization"></a>Opožděná inicializace
*Opožděná inicializace* objektu znamená, že jeho vytvoření je odloženo, dokud je poprvé použita. (Pro toto téma podmínky *opožděné inicializace* a *opožděné instance* jsou shodné.) Opožděná inicializace slouží především ke zvýšení výkonu, zabránit plýtvání výpočtu a snížit požadavky na paměť pro program. Jedná se o nejběžnějších scénářů:  
  
- Pokud máte objekt, který je nákladné a nemusí použít program. Předpokládejme například, že máte v paměti `Customer` objekt, který má `Orders` vlastnost, která obsahuje velké pole `Order` objekty, které mají být inicializovány, vyžaduje připojení k databázi. Pokud uživatel požádá nikdy zobrazujících objednávky nebo použít data ve výpočtu, neexistuje žádný důvod k jeho vytvoření použít systémové paměti nebo výpočetních cyklů. S použitím `Lazy<Orders>` pro deklaraci `Orders` objektu pro opožděnou inicializaci, pokud není používán objekt se můžete vyhnout plýtvání systémových prostředků.  
  
- Pokud máte objekt, který je nákladné a chcete odložit jeho vytvoření až po dokončili další nákladný provoz. Předpokládejme například, že váš program načte několik instancí objektů při spuštění, ale jenom některé z nich je nutné okamžitě. Odložené inicializace objektů, které nejsou povinné, dokud vytvořili požadované objekty, lze vylepšit výkon při spuštění programu.  
  
 I když můžete napsat vlastní kód pro provádění opožděné inicializace, doporučujeme použít <xref:System.Lazy%601> místo. <xref:System.Lazy%601> a jeho souvisejících typů také podporuje bezpečnost vláken a poskytnout zásady šíření výjimky konzistentní vzhledem k aplikacím.  
  
 Následující tabulka uvádí typy opožděná inicializace v různých scénářích povolit poskytuje rozhraní .NET Framework verze 4.  
  
|Type|Popis|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Obálkovou třídu, která poskytuje sémantiku opožděné inicializace pro všechny knihovny tříd nebo typ definovaný uživatelem.|  
|<xref:System.Threading.ThreadLocal%601>|Se podobá <xref:System.Lazy%601> s tím rozdílem, že poskytuje sémantiku opožděné inicializace na základě místního vlákna. Každé vlákno má přístup k vlastní jedinečnou hodnotu.|  
|<xref:System.Threading.LazyInitializer>|Poskytuje pokročilé `static` (`Shared` v jazyce Visual Basic) metody pro opožděné inicializace objektů bez režie třídy.|  
  
## <a name="basic-lazy-initialization"></a>Základní opožděná inicializace  
 Chcete-li definovat opožděně inicializované typu, například `MyType`, použijte `Lazy<MyType>` (`Lazy(Of MyType)` v jazyce Visual Basic), jak je znázorněno v následujícím příkladu. Pokud není předán žádný delegáta v <xref:System.Lazy%601> konstruktoru, zabalený typ, který je vytvořen pomocí <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> při prvním přístupu vlastnost value. Pokud typ nemá výchozí konstruktor, je vyvolána výjimka za běhu.  
  
 V následujícím příkladu se předpokládá, že `Orders` je třída, která obsahuje pole `Order` objekty načteny z databáze. A `Customer` objekt obsahuje instanci `Orders`, ale v závislosti na akce uživatelů, dat z `Orders` objektu nemusí být nutná.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Můžete také předat delegáta v <xref:System.Lazy%601> konstruktor, který vyvolá konkrétního konstruktoru přetížení na zabalený typ, který v okamžiku vytvoření a provedení dalších kroků inicializace, které jsou požadovány, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Po vytvoření objektu opožděné žádná instance `Orders` se vytvoří až <xref:System.Lazy%601.Value%2A> poprvé získat přístup k vlastnosti opožděné proměnné. Na první přístup je zabalený typ, který vytvoří a vrátí a uložené pro jakýkoli budoucí přístup.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 A <xref:System.Lazy%601> objekt vždy vrátí na stejný objekt nebo hodnotu, která nebyla inicializována. Proto <xref:System.Lazy%601.Value%2A> vlastnost je jen pro čtení. Pokud <xref:System.Lazy%601.Value%2A> zadejte úložiště odkaz nelze přiřadit nový objekt k němu. (Můžete ale změnit hodnotu nastavitelné veřejné polí a vlastností.) Pokud <xref:System.Lazy%601.Value%2A> ukládá hodnotu typu, nelze změnit jeho hodnotu. Můžete však vytvořit novou proměnnou vyvoláním konstruktoru proměnné znovu pomocí nové argumenty.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Novou instanci opožděné, jako je ta starší nevytvoří instanci `Orders` až do jeho <xref:System.Lazy%601.Value%2A> vlastnost je nejprve otevřen.  
  
### <a name="thread-safe-initialization"></a>Inicializace bezpečná pro vlákno  
 Ve výchozím nastavení <xref:System.Lazy%601> objekty jsou vláknově bezpečné. To znamená, pokud konstruktor neurčuje druh bezpečný přístup z více vláken <xref:System.Lazy%601> vytvoří objekty jsou vláknově bezpečné. Ve scénářích s více procesy, první vlákno pro přístup k <xref:System.Lazy%601.Value%2A> vlastnost vláknově bezpečné <xref:System.Lazy%601> objektu inicializuje ji pro všechny další přístupy na všech vláknech a všechna vlákna sdílet stejná data. Proto není důležité, které vlákno inicializuje objekt a konflikty časování je neškodný.  
  
> [!NOTE]
>  Taková konzistence pro chybové podmínky můžete rozšířit pomocí ukládání do mezipaměti výjimky. Další informace naleznete v části Další [výjimky v opožděné objekty](../../../docs/framework/performance/lazy-initialization.md#ExceptionsInLazyObjects).  
  
 Následující příklad ukazuje, že stejné `Lazy<int>` instance má stejnou hodnotu pro tři samostatné vlákna.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Pokud budete potřebovat samostatné dat v každém vláknu, použijte <xref:System.Threading.ThreadLocal%601> zadejte, jak je popsáno dále v tomto tématu.  
  
 Některé <xref:System.Lazy%601> konstruktory nemají logickým parametrem s názvem `isThreadSafe` , který se používá k určení, zda <xref:System.Lazy%601.Value%2A> vlastnost budou mít přístup z více vláken. Pokud chcete získat přístup k vlastnosti z právě jedno vlákno, předejte `false` získat mírné zvýšení výkonu. Pokud chcete získat přístup k vlastnosti z více vláken, předejte `true` dáte pokyn, aby <xref:System.Lazy%601> instance správně zpracovat časování, ve kterých jedno vlákno vyvolá výjimku během inicializace.  
  
 Některé <xref:System.Lazy%601> mají konstruktory <xref:System.Threading.LazyThreadSafetyMode> parametr s názvem `mode`. Tyto konstruktory zadat režim zabezpečení další vlákna. Následující tabulka ukazuje, jak bezpečnost vlákna <xref:System.Lazy%601> je objekt ovlivněn parametry konstruktoru, které určují bezpečný přístup z více vláken. Každý konstruktor má nejvýše jeden takový parametr.  
  
|Zabezpečení vlákna objektu|`LazyThreadSafetyMode` `mode` Parametr|Logická `isThreadSafe` parametr|Žádné parametry bezpečný přístup z více vláken|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|Plně bezpečné pro vlákna; pouze jedno vlákno současně pokusí o inicializaci hodnoty.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Ano.|  
|Není bezpečné pro vlákna.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Není k dispozici.|  
|Plně bezpečné pro vlákna; závod vláken k inicializaci hodnoty.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Není k dispozici.|Není k dispozici.|  
  
 Jak je zobrazeno v tabulce, určení <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> pro `mode` parametr je stejné jako zadání `true` pro `isThreadSafe` parametru a zadáním <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> je stejné jako zadání `false`.  
  
 Určení <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> umožňuje více vláken, k pokusu o inicializaci <xref:System.Lazy%601> instance. Pouze jedno vlákno může tento závod vyhrát a všechny ostatní vlákna zobrazí hodnotu, která byla inicializována úspěšné vláknem. Pokud během inicializace je vyvolána výjimka ve vlákně, bylo vlákno nezíská hodnoty nastavené v úspěšné vlákna. Výjimky nejsou uložené v mezipaměti, takže další pokus o přístup <xref:System.Lazy%601.Value%2A> vlastnost může mít za následek úspěšné inicializace. Tím se liší od způsob, jakým výjimky jsou považovány v ostatních režimech, která je popsána v následující části. Další informace najdete v tématu <xref:System.Threading.LazyThreadSafetyMode> výčtu.  
  
<a name="ExceptionsInLazyObjects"></a>   
## <a name="exceptions-in-lazy-objects"></a>Výjimky v opožděné objekty  
 Jak bylo uvedeno dříve, <xref:System.Lazy%601> objekt vždy vrátí na stejný objekt nebo hodnotu, která byla inicializována, a proto <xref:System.Lazy%601.Value%2A> vlastnost je jen pro čtení. Pokud povolíte ukládání do mezipaměti výjimku, tato neměnnosti také rozšiřuje výjimky chování. Pokud je objekt opožděně inicializované výjimka povoleno ukládání do mezipaměti a vyvolá výjimku z jeho inicializační metoda při <xref:System.Lazy%601.Value%2A> vlastnost je nejprve otevřen, že stejná výjimka je vyvolána na všechny následné pokusy o přístup k <xref:System.Lazy%601.Value%2A> vlastnost . Jinými slovy konstruktor zabalený typ, který se nikdy znovu vyvolána, dokonce i ve scénářích s více vlákny. Proto <xref:System.Lazy%601> objekt nelze vyvolat výjimku na jeden přístup a všechny další přístupy nevrací hodnotu.  
  
 Ukládání do mezipaměti výjimka je povolená, když použijete některou <xref:System.Lazy%601?displayProperty=nameWithType> konstruktor, který přijímá metodu inicializace (`valueFactory` parametr); například je povolená, když použijete `Lazy(T)(Func(T))`konstruktoru. Pokud konstruktor také přijímá <xref:System.Threading.LazyThreadSafetyMode> hodnotu (`mode` parametr), zadejte <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> nebo <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>. Určení inicializační metoda umožňuje ukládání do mezipaměti výjimky pro tyto dva režimy. Inicializační metoda může být velmi jednoduché. Například může volat výchozí konstruktor pro `T`: `new Lazy<Contents>(() => new Contents(), mode)` v jazyce C#, nebo `New Lazy(Of Contents)(Function() New Contents())` v jazyce Visual Basic. Pokud používáte <xref:System.Lazy%601?displayProperty=nameWithType> konstruktor, který neurčuje metodu inicializace, výjimky, které jsou vyvolány výchozí konstruktor pro `T` nejsou uložené v mezipaměti. Další informace najdete v tématu <xref:System.Threading.LazyThreadSafetyMode> výčtu.  
  
> [!NOTE]
>  Pokud vytvoříte <xref:System.Lazy%601> objekt s `isThreadSafe` konstruktor parametrem nastaveným na `false` nebo `mode` konstruktor parametrem nastaveným na <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>, musí přejít <xref:System.Lazy%601> objektu z jednoho vlákna nebo zadat vlastní synchronizace. To platí pro všechny aspekty objektu, včetně výjimek, ukládání do mezipaměti.  
  
 Jak je uvedeno v předchozí části, <xref:System.Lazy%601> objekty vytvořené tak, že zadáte <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> zpracovávat výjimky odlišně. S <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>, více vláken se mohou utkat inicializovat <xref:System.Lazy%601> instance. V takovém případě výjimky nejsou uložené v mezipaměti a pokusí o přístup k <xref:System.Lazy%601.Value%2A> vlastnost může pokračovat, dokud nebude úspěšné inicializace.  
  
 Následující tabulka shrnuje způsob, jakým <xref:System.Lazy%601> řízení konstruktorů výjimek ukládání do mezipaměti.  
  
|Konstruktor|Režim zabezpečení vlákna|Používá metodu inicializace|Výjimky jsou uložené v mezipaměti|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Lazy(T)()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Ne|Ne|  
|Lazy(T)(Func(T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Ano|Ano|  
|Lazy(T)(Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) nebo `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Ne|Ne|  
|Lazy(T)(Func(T), logická hodnota)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) nebo `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Ano|Ano|  
|Lazy(T)(LazyThreadSafetyMode)|Zadané uživatelem|Ne|Ne|  
|Lazy(T)(Func(T), LazyThreadSafetyMode)|Zadané uživatelem|Ano|Ne, pokud uživatel zadá <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>; jinak vrátí hodnotu, Ano.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Implementace opožděně inicializované vlastnosti  
 Chcete-li implementovat veřejné vlastnosti pomocí opožděné inicializace, definujte pomocným polem vlastnosti jako datový typ <xref:System.Lazy%601>a vraťte se <xref:System.Lazy%601.Value%2A> vlastnost z `get` přistupujícího objektu vlastnosti.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 <xref:System.Lazy%601.Value%2A> Vlastnost je jen pro čtení; proto vlastnost, která zpřístupní ho nemá žádné `set` přistupujícího objektu. Pokud vyžadujete, aby se opírá o vlastnost pro čtení a zápis <xref:System.Lazy%601> objektu, `set` přístupového objektu musíte vytvořit nový <xref:System.Lazy%601> objekt a přiřaďte ho ke záložního úložiště. `set` Přístupového objektu musíte vytvořit výraz lambda, který vrátí hodnotu, která byla předána hodnota nové vlastnosti `set` přístupový objekt a předat tento výraz lambda konstruktoru pro novou <xref:System.Lazy%601> objektu. Další přístup <xref:System.Lazy%601.Value%2A> způsobí, že vlastnost inicializace nového <xref:System.Lazy%601>a jeho <xref:System.Lazy%601.Value%2A> vlastnost poté vrátí novou hodnotu, která byla přiřazena k vlastnosti. Důvod pro toto uspořádání složitými je zachovat multithreading ochrany, které jsou součástí <xref:System.Lazy%601>. V opačném případě by mít přistupující objekty vlastnosti pro ukládání do mezipaměti první hodnoty vrácené <xref:System.Lazy%601.Value%2A> vlastnost a měnit pouze hodnotu uloženou v mezipaměti a byste museli napsat vlastní kód bezpečným pro vlákno, které provedete. Kvůli další inicializace, vyžaduje se opírá o vlastnost pro čtení a zápis <xref:System.Lazy%601> objektu, nemusí být přijatelný výkon. V závislosti na konkrétním scénáři může být další koordinace navíc vyžadováno nedošlo ke konfliktům časování mezi setter a metody getter.  
  
## <a name="thread-local-lazy-initialization"></a>Thread-Local opožděná inicializace  
 V některých scénářích s více vlákny můžete chtít poskytnout vlastní privátní data každé vlákno. Tato data se nazývají *dat thread local*. V rozhraní .NET Framework verze 3.5 a starších, můžete použít `ThreadStatic` atribut statickou proměnnou, která usnadňují místního vlákna. Avšak použití `ThreadStatic` atribut může vést k drobným chybám. Například příkazy i základní inicializace způsobí, že proměnné mají být inicializovány pouze na první vlákno, k přístupu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 V jiných vláknech proměnná bude inicializován pomocí jeho výchozí hodnota (nula). Jako alternativu v rozhraní .NET Framework verze 4, můžete použít <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> vytvořit proměnnou založený na instancích, místního vlákna, který je inicializován na všech vláknech podle <xref:System.Action%601> delegáta, který zadáte. V následujícím příkladu, všechna vlákna, která přístup `counter` se zobrazí její výchozí hodnotu 1.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> zabalí jeho objekt stejným způsobem jako <xref:System.Lazy%601>, s následujícími základní rozdíly:  
  
- Každé vlákno inicializuje proměnná místního vlákna pomocí jeho vlastní privátní data, která nejsou přístupné z jiných vláken.  
  
- <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> Vlastnost pro čtení i zápis a je možné upravit libovolný počet. To může ovlivnit šíření výjimek, například jeden `get` operace může vyvolat výjimku, ale další možné úspěšně inicializovat hodnota.  
  
- Pokud je k dispozici žádná inicializace delegáta, <xref:System.Threading.ThreadLocal%601> inicializovat jeho zabalený typ, který bude použita výchozí hodnota typu. V tomto ohledu <xref:System.Threading.ThreadLocal%601> je konzistentní s <xref:System.ThreadStaticAttribute> atribut.  
  
 Následující příklad ukazuje, že každý podproces, který přistupuje k `ThreadLocal<int>` instance získá svou vlastní jedinečnou kopii data.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Místní proměnné vlákna smyčky Parallel.For a ForEach  
 Při použití <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metoda nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metoda k iteraci nad zdroji dat současně, můžete použít přetížení, které mají integrovanou podporu pro místní data. V těchto metodách umístění vlákna můžete dosáhnout použitím místní delegáti vytvořit, přístup a vyčistit data. Další informace najdete v tématu [jak: Zápis smyčky Parallel.for pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) a [jak: Zápis smyčky Parallel.ForEach pomocí proměnných v místním oddílu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Pomocí opožděné inicializace pro scénáře s nízkou režií  
 V situacích, kdy musíte opožděné inicializace velký počet objektů, můžete se rozhodnout obtékání jednotlivých objektů v <xref:System.Lazy%601> vyžaduje příliš mnoho paměti nebo příliš mnoho výpočetních prostředků. Nebo můžete mít přísné požadavky na informace o tom, jak opožděné inicializace je přístupný. V takovém případě můžete použít `static` (`Shared` v jazyce Visual Basic) metody <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> opožděné inicializace každý objekt nezabalili v instanci třídy <xref:System.Lazy%601>.  
  
 V následujícím příkladu se předpokládá, že, namísto obtékání celý `Orders` objekt v jednom <xref:System.Lazy%601> objektu, budete mít jednotlivé opožděně inicializované `Order` pouze objekty, pokud jsou povinné.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 V tomto příkladu Všimněte si, že je vyvolána inicializační proceduru v každé iteraci smyčky. Ve scénářích s více procesy první vlákno k vyvolání procedury inicializace je ten, jehož hodnota je vidět všechna vlákna. Novější vláken také vyvolat inicializační proceduru, ale nepoužívají se jejich výsledky. Pokud tento druh potenciální konflikt časování není přijatelná, použijte přetížení <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> , která přebírá argument typu Boolean a synchronizační objekt.  
  
## <a name="see-also"></a>Viz také:

- [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)
- [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)
- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Postupy: Provádění opožděné inicializace objektů](../../../docs/framework/performance/how-to-perform-lazy-initialization-of-objects.md)
