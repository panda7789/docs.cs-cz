---
title: Opožděná inicializace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
ms.openlocfilehash: 54776304e484fc7f1db2c56b102034ed0e8650c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130321"
---
# <a name="lazy-initialization"></a>Opožděná inicializace
*Opožděná inicializace* objektu znamená, že jeho vytvoření je odloženo až do prvního použití. (Pro toto téma jsou výrazy *opožděné inicializace* a *opožděné vytváření instancí* synonymní.) Opožděná inicializace se primárně používá ke zvýšení výkonu, vyhněte se výpočtu wasteful a snížení požadavků na paměť programu. Jedná se o nejběžnější scénáře:  
  
- Pokud máte objekt, který je nákladný k vytvoření, a program ho možná nepoužije. Například Předpokládejme, že máte v paměti objekt `Customer`, který má vlastnost `Orders`, která obsahuje velké pole `Order` objektů, které mají být inicializovány, vyžaduje připojení k databázi. Pokud uživatel nikdy nežádá o zobrazení objednávek nebo použití dat v rámci výpočtu, neexistuje žádný důvod k jeho vytvoření pomocí systémové paměti nebo výpočetních cyklů. Použitím `Lazy<Orders>` k deklaraci objektu `Orders` pro opožděnou inicializaci, se můžete vyhnout plýtvání systémových prostředků, když se objekt nepoužívá.  
  
- Pokud máte objekt, který je nákladný k vytvoření, a chcete odložit jeho vytvoření až po dokončení dalších nákladných operací. Předpokládejme například, že program při spuštění načte několik instancí objektů, ale pouze některé z nich jsou požadovány okamžitě. Můžete zlepšit výkon při spuštění programu odložením inicializace objektů, které nejsou požadovány, dokud nebudou vytvořeny požadované objekty.  
  
 I když můžete napsat vlastní kód pro provedení opožděné inicializace, doporučujeme místo toho použít <xref:System.Lazy%601>. <xref:System.Lazy%601> a jeho související typy také podporují bezpečnost pro přístup z více vláken a poskytují konzistentní zásady šíření výjimek.  
  
 Následující tabulka obsahuje seznam typů, které .NET Framework verze 4 poskytují pro povolení opožděné inicializace v různých scénářích.  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Obálková třída, která poskytuje sémantiku opožděné inicializace pro libovolnou knihovnu tříd nebo uživatelsky definovaný typ.|  
|<xref:System.Threading.ThreadLocal%601>|Se podobá <xref:System.Lazy%601> s tím rozdílem, že poskytuje sémantiku opožděné inicializace na místním vlákně. Každé vlákno má přístup k vlastní jedinečné hodnotě.|  
|<xref:System.Threading.LazyInitializer>|Poskytuje pokročilé `static` (`Shared` v Visual Basic) metody pro opožděnou inicializaci objektů bez režie třídy.|  
  
## <a name="basic-lazy-initialization"></a>Základní opožděná inicializace  
 Chcete-li definovat typ opožděně inicializovaného typu, například `MyType`, použijte `Lazy<MyType>` (`Lazy(Of MyType)` v Visual Basic), jak je znázorněno v následujícím příkladu. Pokud není předán žádný delegát v konstruktoru <xref:System.Lazy%601>, je zabalený typ vytvořen pomocí <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> při prvním použití vlastnosti Value. Pokud typ nemá konstruktor bez parametrů, je vyvolána výjimka za běhu.  
  
 V následujícím příkladu Předpokládejme, že `Orders` je třída, která obsahuje pole objektů `Order` načtených z databáze. Objekt `Customer` obsahuje instanci `Orders`, ale v závislosti na akcích uživatele nemusí být potřebná data z objektu `Orders`.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Delegáta můžete také předat v konstruktoru <xref:System.Lazy%601>, který vyvolá konkrétní přetížení konstruktoru pro zabalený typ při vytvoření a provede všechny další požadované kroky inicializace, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Po vytvoření opožděného objektu není vytvořena žádná instance `Orders`, dokud nebude poprvé k dispozici vlastnost <xref:System.Lazy%601.Value%2A> opožděné proměnné. Při prvním přístupu se vytvoří a vrátí zabalený typ, který se uloží pro jakýkoliv budoucí přístup.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 Objekt <xref:System.Lazy%601> vždy vrátí stejný objekt nebo hodnotu, se kterou bylo inicializováno. Proto vlastnost <xref:System.Lazy%601.Value%2A> je určena jen pro čtení. Pokud <xref:System.Lazy%601.Value%2A> ukládá odkazový typ, nemůžete k němu přiřadit nový objekt. (Můžete ale změnit hodnotu jeho nastavitelných veřejných polí a vlastností.) Pokud <xref:System.Lazy%601.Value%2A> ukládá hodnotový typ, nemůžete změnit jeho hodnotu. Můžete však vytvořit novou proměnnou vyvoláním konstruktoru proměnné znovu pomocí nových argumentů.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Nová opožděná instance, jako je ta dřív, nevytvoří instanci `Orders`, dokud nebude k jejímu <xref:System.Lazy%601.Value%2A> vlastnosti přistupujte poprvé.  
  
### <a name="thread-safe-initialization"></a>Inicializace bezpečná pro přístup z více vláken  
 Ve výchozím nastavení jsou objekty <xref:System.Lazy%601> bezpečné pro přístup z více vláken. To znamená, že pokud konstruktor neurčí druh zabezpečení vlákna, objekty <xref:System.Lazy%601>, které vytváří, jsou bezpečné pro přístup z více vláken. Ve scénářích s více vlákny má první vlákno přístup k vlastnosti <xref:System.Lazy%601.Value%2A> objektu <xref:System.Lazy%601> bezpečného pro přístup z více vláken, inicializuje ho pro všechny následné přístupy všech vláken a všechna vlákna sdílejí stejná data. Proto nezáleží na tom, které vlákno inicializuje objekt a konflikty časování jsou neškodné.  
  
> [!NOTE]
> Tuto konzistenci můžete roztáhnout na chybové podmínky pomocí ukládání výjimek do mezipaměti. Další informace naleznete v další části [výjimky v opožděných objektech](lazy-initialization.md#ExceptionsInLazyObjects).  
  
 Následující příklad ukazuje, že stejná instance `Lazy<int>` má stejnou hodnotu pro tři samostatná vlákna.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Pokud potřebujete samostatná data v každém vlákně, použijte <xref:System.Threading.ThreadLocal%601> typ, jak je popsáno dále v tomto tématu.  
  
 Některé konstruktory <xref:System.Lazy%601> mají logický parametr nazvaný `isThreadSafe`, který se používá k určení, zda bude vlastnost <xref:System.Lazy%601.Value%2A> k dispozici z více vláken. Pokud máte v úmyslu získat přístup k vlastnosti jenom z jednoho vlákna, předejte `false`, abyste získali mírné výhody výkonu. Pokud máte v úmyslu získat přístup k vlastnosti z více vláken, předejte `true` k instruování instance <xref:System.Lazy%601>, aby správně zpracovávala konflikty časování, ve kterém jedno vlákno vyvolá výjimku v době inicializace.  
  
 Některé konstruktory <xref:System.Lazy%601> mají <xref:System.Threading.LazyThreadSafetyMode> parametr s názvem `mode`. Tyto konstruktory poskytují další režim zabezpečení vlákna. Následující tabulka ukazuje, jak je zabezpečení vlákna objektu <xref:System.Lazy%601> ovlivněno parametry konstruktoru, které určují bezpečnost vlákna. Každý konstruktor má maximálně jeden takový parametr.  
  
|Bezpečnost vlákna objektu|parametr `LazyThreadSafetyMode` `mode`|Logický `isThreadSafe` parametr|Žádné parametry zabezpečení vlákna|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|Plně bezpečné pro přístup z více vláken; pouze jedno vlákno v jednom okamžiku se pokusí inicializovat hodnotu.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Ano.|  
|Není bezpečné pro přístup z více vláken.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Nelze použít.|  
|Plně bezpečné pro přístup z více vláken; vlákna mají za to, že se má inicializovat hodnota.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Nelze použít.|Nelze použít.|  
  
 Jak je tabulka zobrazená, zadání <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> pro parametr `mode` je stejné jako zadání `true` pro parametr `isThreadSafe` a určení <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> je totéž jako určení `false`.  
  
 Určení <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> umožňuje více vláknům pokusit se o inicializaci instance <xref:System.Lazy%601>. Tuto rasy může získat pouze jeden podproces a všechna ostatní vlákna obdrží hodnotu, která byla inicializována úspěšným vláknem. Pokud je vyvolána výjimka ve vlákně během inicializace, vlákno neobdrží hodnotu nastavenou úspěšným vláknem. Výjimky nejsou ukládány do mezipaměti, takže následný pokus o přístup k vlastnosti <xref:System.Lazy%601.Value%2A> může mít za následek úspěšnou inicializaci. To se liší od způsobu, jakým jsou výjimky zpracovány v jiných režimech, které jsou popsány v následující části. Další informace najdete v <xref:System.Threading.LazyThreadSafetyMode> výčtu.  
  
<a name="ExceptionsInLazyObjects"></a>   
## <a name="exceptions-in-lazy-objects"></a>Výjimky v opožděných objektech  
 Jak bylo uvedeno dříve, objekt <xref:System.Lazy%601> vždy vrátí stejný objekt nebo hodnotu, se kterou bylo inicializováno, a proto je vlastnost <xref:System.Lazy%601.Value%2A> určena pouze pro čtení. Pokud povolíte ukládání výjimek do mezipaměti, tato neměnnosti také rozšiřuje chování při výjimkách. Pokud má opožděně inicializovaný objekt povolené ukládání výjimek do mezipaměti a vyvolá výjimku z své inicializační metody při prvním přístupu k vlastnosti <xref:System.Lazy%601.Value%2A>, je stejná výjimka vyvolána při každém dalším pokusu o přístup k vlastnosti <xref:System.Lazy%601.Value%2A>. Jinými slovy konstruktor zabaleného typu nikdy není znovu vyvolán ani ve scénářích s více vlákny. Objekt <xref:System.Lazy%601> proto nemůže vyvolat výjimku u jednoho přístupu a vracet hodnotu u následného přístupu.  
  
 Ukládání výjimek do mezipaměti je povoleno, je-li použit libovolný konstruktor <xref:System.Lazy%601?displayProperty=nameWithType>, který přebírá metodu inicializace (`valueFactory` parametr); Například je povoleno, pokud použijete konstruktor `Lazy(T)(Func(T))`. Pokud konstruktor také přebírá hodnotu <xref:System.Threading.LazyThreadSafetyMode> (parametr`mode`), zadejte <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> nebo <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>. Zadání inicializační metody povoluje ukládání výjimek do mezipaměti pro tyto dva režimy. Inicializační metoda může být velmi jednoduchá. Například může volat konstruktor bez parametrů pro `T`: `new Lazy<Contents>(() => new Contents(), mode)` v C#nebo `New Lazy(Of Contents)(Function() New Contents())` v Visual Basic. Pokud použijete konstruktor <xref:System.Lazy%601?displayProperty=nameWithType>, který neurčuje metodu inicializace, výjimky, které jsou vyvolány konstruktorem bez parametrů pro `T` nejsou ukládány do mezipaměti. Další informace najdete v <xref:System.Threading.LazyThreadSafetyMode> výčtu.  
  
> [!NOTE]
> Vytvoříte-li objekt <xref:System.Lazy%601> s parametrem `isThreadSafe` konstruktoru nastaveným na hodnotu `false` nebo parametr `mode` konstruktoru nastaven na hodnotu <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>, je nutné získat přístup k objektu <xref:System.Lazy%601> z jednoho vlákna nebo zadat vlastní synchronizaci. To platí pro všechny aspekty objektu, včetně ukládání výjimek do mezipaměti.  
  
 Jak je uvedeno v předchozí části, <xref:System.Lazy%601> objekty vytvořené zadáním <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> považovat výjimky za odlišné. V <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>může více vláken konkurovat inicializaci instance <xref:System.Lazy%601>. V takovém případě se výjimky neukládají do mezipaměti a pokusy o přístup k vlastnosti <xref:System.Lazy%601.Value%2A> mohou pokračovat, dokud nebude inicializace úspěšná.  
  
 Následující tabulka shrnuje způsob, jakým konstruktory <xref:System.Lazy%601> řídí ukládání výjimek do mezipaměti.  
  
|Konstruktor|Režim zabezpečení vlákna|Používá inicializační metodu|Výjimky jsou ukládány do mezipaměti.|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Opožděné (T) ()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Ne|Ne|  
|Opožděné (T) (Func (T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Ano|Ano|  
|Opožděné (T) (Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) nebo `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Ne|Ne|  
|Opožděné (T) (Func (T), Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) nebo `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Ano|Ano|  
|Opožděné (T) (LazyThreadSafetyMode)|Zadáno uživatelem|Ne|Ne|  
|Opožděné (T) (Func (T); LazyThreadSafetyMode)|Zadáno uživatelem|Ano|Ne, pokud uživatel určí <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>; v opačném případě ano.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Implementace opožděně inicializované vlastnosti  
 Chcete-li implementovat veřejnou vlastnost pomocí opožděné inicializace, definujte pole zálohování vlastnosti jako <xref:System.Lazy%601>a vraťte vlastnost <xref:System.Lazy%601.Value%2A> z přístupového objektu `get` vlastnosti.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 Vlastnost <xref:System.Lazy%601.Value%2A> je určena jen pro čtení; Proto vlastnost, která zpřístupňuje, nemá žádný přistupující objekt `set`. Pokud požadujete vlastnost pro čtení/zápis, kterou podporuje objekt <xref:System.Lazy%601>, musí přístupový objekt `set` vytvořit nový objekt <xref:System.Lazy%601> a přiřadit ho k záložnímu úložišti. Přistupující objekt `set` musí vytvořit výraz lambda, který vrací novou hodnotu vlastnosti, která byla předána přístupovému objektu `set` a předat tento výraz lambda konstruktoru pro nový objekt <xref:System.Lazy%601>. Další přístup vlastnosti <xref:System.Lazy%601.Value%2A> způsobí inicializaci nového <xref:System.Lazy%601>a jeho vlastnost <xref:System.Lazy%601.Value%2A> pak vrátí novou hodnotu, která byla přiřazena vlastnosti. Důvodem pro toto konvoluce je zachování ochrany s více vlákny, které jsou integrované v <xref:System.Lazy%601>. V opačném případě by přistupující objekty vlastnosti musely ukládat do mezipaměti první hodnotu vrácenou vlastností <xref:System.Lazy%601.Value%2A> a upravovat pouze hodnotu uloženou v mezipaměti. k tomu byste museli napsat vlastní kód bezpečný pro přístup z více vláken. Z důvodu dalších inicializací vyžadovaných vlastností pro čtení a zápis zálohovaných objektem <xref:System.Lazy%601> nemusí být výkon přijatelný. V závislosti na konkrétním scénáři se navíc může vyžadovat další koordinace, aby nedocházelo ke konfliktům mezi metodami setter a getter.  
  
## <a name="thread-local-lazy-initialization"></a>Opožděná inicializace místního vlákna  
 V některých scénářích s více vlákny můžete chtít každému vláknu poskytnout vlastní privátní data. Tato data se nazývají *místní data vlákna*. V .NET Framework verze 3,5 a starší můžete použít atribut `ThreadStatic` na statickou proměnnou a nastavit tak místní vlákno vlákna. Použití atributu `ThreadStatic` však může vést k drobným chybám. Například dokonce základní inicializační příkazy způsobí, že proměnná bude inicializována pouze v prvním vlákně, která k němu přistupuje, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 Ve všech ostatních vláknech bude proměnná inicializována pomocí výchozí hodnoty (nula). Jako alternativu ve verzi .NET Framework 4 můžete použít typ <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> k vytvoření místní proměnné vlákna, která je inicializována na všech vláknech pomocí delegáta <xref:System.Action%601>, který poskytnete. V následujícím příkladu se všechna vlákna, která přistupují k `counter`, zobrazí jako počáteční hodnota 1.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> zalomí svůj objekt podobným způsobem jako <xref:System.Lazy%601>, s těmito základními rozdíly:  
  
- Každé vlákno inicializuje místní proměnnou vlákna pomocí vlastních privátních dat, která nejsou přístupná z jiných vláken.  
  
- Vlastnost <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> je pro čtení i zápis a lze ji změnit libovolným počtem opakování. To může mít vliv na šíření výjimek, například jedna `get` operace může vyvolat výjimku, ale další může úspěšně inicializovat hodnotu.  
  
- Pokud není k dispozici žádný delegát inicializace, <xref:System.Threading.ThreadLocal%601> inicializuje zabalený typ pomocí výchozí hodnoty typu. V tomto ohledu <xref:System.Threading.ThreadLocal%601> je konzistentní s atributem <xref:System.ThreadStaticAttribute>.  
  
 Následující příklad ukazuje, že každé vlákno, které přistupuje k instanci `ThreadLocal<int>`, získá svou vlastní jedinečnou kopii dat.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Místní proměnné vlákna paralelně. for a ForEach  
 Při použití metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> nebo metody <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> k iterování zdrojů dat paralelně můžete použít přetížení, která mají integrovanou podporu pro místní data vlákna. V těchto metodách je možné dosáhnout lokálního vlákna pomocí místních delegátů k vytváření, přístupu a vyčištění dat. Další informace naleznete v tématu [How to: Write a Parallel. for smyčke s proměnnými místními vlákny](../../standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) a [How to: napište smyčku Parallel. ForEach s proměnnými místně na oddíl](../../standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Použití opožděné inicializace pro scénáře s nízkou režií  
 Ve scénářích, kdy je nutné provést opožděnou inicializaci velkého počtu objektů, se můžete rozhodnout, že balení každého objektu v <xref:System.Lazy%601> vyžaduje příliš mnoho paměti nebo příliš mnoho výpočetních prostředků. Nebo je možné, že máte přísné požadavky na to, jak je k dispozici opožděná inicializace. V takových případech můžete použít metody `static` (`Shared` v Visual Basic) třídy <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> k opožděné inicializaci každého objektu bez jeho zabalení do instance <xref:System.Lazy%601>.  
  
 V následujícím příkladu Předpokládejme, že místo zalamování celého objektu `Orders` v jednom objektu <xref:System.Lazy%601> máte opožděně inicializované objekty objektů `Order` pouze v případě, že jsou požadovány.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 V tomto příkladu si všimněte, že inicializační proceduru je vyvolána při každé iteraci smyčky. Ve scénářích s více vlákny je prvním vláknem vyvolání inicializační procedury ta, jejíž hodnota je zobrazena ve všech vláknech. Novější vlákna také vyvolávají inicializační proceduru, ale jejich výsledky se nepoužívají. Pokud tento druh potenciální časování není přijatelný, použijte přetížení <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType>, které přebírá logický argument a objekt synchronizace.  
  
## <a name="see-also"></a>Viz také:

- [Základy dělení na spravovaná vlákna](../../standard/threading/managed-threading-basics.md)
- [Vlákna a dělení na vlákna](../../standard/threading/threads-and-threading.md)
- [Task Parallel Library (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Postupy: Provádění opožděné inicializace objektů](how-to-perform-lazy-initialization-of-objects.md)
