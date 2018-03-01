---
title: "Opožděná inicializace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f4998cc0c836cf46d79d854ad9a85e7eacf70d7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lazy-initialization"></a>Opožděná inicializace
*Opožděná inicializace* objektu znamená, že je její vytvoření odložení dokud nejprve se používá. (Pro toto téma podmínky *opožděné inicializace* a *opožděné konkretizaci* jsou shodné.) Opožděná inicializace slouží především zvyšování výkonu, vyhněte se plýtvání výpočtů a snížit požadavky na paměť programu. Jedná se o nejběžnějších scénářů:  
  
-   Pokud máte objekt, který je nákladné a program se nemusí použít. Předpokládejme například, že máte v paměti `Customer` objekt, který má `Orders` vlastnost, která obsahuje velké pole `Order` objekty, které, chcete-li inicializovat, vyžaduje připojení k databázi. Pokud uživatel požádá nikdy zobrazit objednávky nebo používat data při výpočet, neexistuje žádný důvod k jeho vytvoření použít systémové paměti nebo computing cykly. Pomocí `Lazy<Orders>` deklarovat `Orders` objekt pro opožděné inicializace, když objekt se nepoužije se můžete vyhnout plýtvání systémové prostředky.  
  
-   Pokud máte objekt, který je nákladné, a chcete odložení svého vytvoření až po další náročná operace. Předpokládejme například, že váš program načte několik instancí objektů, když jeho spuštění, ale jenom některé z nich jsou vyžadovány okamžitě. Může zvýšit výkon při spuštění programu rozlišením inicializace objektů, které nejsou povinné, dokud požadované objekty byly vytvořeny.  
  
 I když můžete napsat vlastní kód pro provádění opožděné inicializace, doporučujeme použít <xref:System.Lazy%601> místo. <xref:System.Lazy%601>a jeho souvisejících typů také podporují vláken a zadejte zásadu šíření konzistentní výjimka.  
  
 Následující tabulka uvádí typy, které poskytuje rozhraní .NET Framework verze 4 povolit opožděná inicializace v různých scénářích.  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Obálka třídu, která poskytuje sémantiku opožděné inicializace pro všechny knihovny tříd a uživatelsky definovaný typ.|  
|<xref:System.Threading.ThreadLocal%601>|Podobá <xref:System.Lazy%601> s tím rozdílem, že poskytuje sémantiku opožděné inicializace na základě specifická pro přístup z více vláken. Každé vlákno má přístup k vlastní jedinečnou hodnotu.|  
|<xref:System.Threading.LazyInitializer>|Poskytuje pokročilé `static` (`Shared` v jazyce Visual Basic) metody pro opožděné inicializace objektů bez režie třídy.|  
  
## <a name="basic-lazy-initialization"></a>Základní opožděné inicializace  
 Chcete-li definovat opožděně inicializované typu, například `MyType`, použijte `Lazy<MyType>` (`Lazy(Of MyType)` v jazyce Visual Basic), jak je znázorněno v následujícím příkladu. Pokud je předaná žádné delegáta <xref:System.Lazy%601> konstruktoru, zabalené typ je vytvořená pomocí <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> při prvním přístupu vlastnosti value. Pokud typ nemá výchozí konstruktor, je vyvolána výjimka běhu.  
  
 V následujícím příkladu předpokládáme, že `Orders` je třída, která obsahuje pole `Order` objekty načíst z databáze. A `Customer` objekt obsahuje instanci `Orders`, ale v závislosti na akce uživatele, data z `Orders` objekt nemusí být požadována.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Můžete také předání delegáta v <xref:System.Lazy%601> konstruktor, který volá konstruktor konkrétní přetížení na typ zabalené v okamžiku vytvoření a provedení dalších kroků inicializace, které jsou požadovány, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Po vytvoření objektu opožděné není žádná instance `Orders` se vytvoří až <xref:System.Lazy%601.Value%2A> poprvé získat přístup k vlastnosti opožděné proměnné. Na první přístup je typ zabalené vytvořit a vrátí a uložené pro jakýkoli budoucí přístup.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 A <xref:System.Lazy%601> objekt vždy vrátí stejné objekt nebo hodnotu, která byla inicializována s. Proto <xref:System.Lazy%601.Value%2A> vlastnost je jen pro čtení. Pokud <xref:System.Lazy%601.Value%2A> uloží odkaz na typ, nelze přiřadit nový objekt k němu. (Můžete však změnit hodnotu jeho nastavit veřejná pole a vlastnosti.) Pokud <xref:System.Lazy%601.Value%2A> uloží hodnotu typu, nelze změnit jeho hodnotu. Nicméně můžete vytvořit nové proměnné vyvoláním proměnné konstruktor znovu pomocí nového argumenty.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Nová instance opožděné, stejný, jako je dřívější nevytvoří instanci `Orders` dokud jeho <xref:System.Lazy%601.Value%2A> je nejdřív získat přístup k vlastnosti.  
  
### <a name="thread-safe-initialization"></a>Inicializace bezpečné pro přístup z více vláken  
 Ve výchozím nastavení <xref:System.Lazy%601> objekty jsou bezpečné pro přístup z více vláken. To znamená, pokud konstruktoru neurčuje druh zabezpečení vlákna <xref:System.Lazy%601> vytvoří objekty jsou bezpečné pro přístup z více vláken. Ve scénářích s více procesy, první vlákno pro přístup k <xref:System.Lazy%601.Value%2A> vlastnost bezpečného přístupu <xref:System.Lazy%601> objekt inicializuje ho pro všechny následných přístupech na všechna vlákna, a všechna vlákna sdílet stejná data. Proto není důležité, které vlákno inicializuje objekt a konflikty časování jsou neškodné.  
  
> [!NOTE]
>  Tato konzistence na chybové stavy můžete rozšířit pomocí ukládání do mezipaměti výjimka. Další informace najdete v části Další [výjimky v opožděné objekty](../../../docs/framework/performance/lazy-initialization.md#ExceptionsInLazyObjects).  
  
 Následující příklad ukazuje, že stejný `Lazy<int>` instance má stejnou hodnotu pro tři samostatné vlákna.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Pokud budete potřebovat samostatný data na každé vlákno, použijte <xref:System.Threading.ThreadLocal%601> zadejte, jak je popsáno dále v tomto tématu.  
  
 Některé <xref:System.Lazy%601> konstruktory mít parametr typu Boolean s názvem `isThreadSafe` používané k určení zda <xref:System.Lazy%601.Value%2A> vlastnost budou mít přístup z více vláken. Pokud chcete získat přístup k vlastnosti z právě jedno vlákno, předejte `false` získat výhody nenáročné na výkon. Pokud chcete získat přístup k vlastnosti z více vláken, předejte `true` dáte pokyn, aby <xref:System.Lazy%601> instance správně zpracovat časování, ve kterých jedno vlákno vyvolá výjimku během inicializace.  
  
 Některé <xref:System.Lazy%601> být konstruktory <xref:System.Threading.LazyThreadSafetyMode> parametr s názvem `mode`. Tyto konstruktory zadejte také další vlákno režim zabezpečení. Následující tabulka ukazuje, jak bezpečný přístup z <xref:System.Lazy%601> objektu je ovlivňován konstruktor parametrů, které určují bezpečný přístup z více vláken. Každý konstruktor má maximálně jeden takový parametr.  
  
|Zabezpečení vlákna objektu|`LazyThreadSafetyMode``mode` parametr|Logická hodnota `isThreadSafe` parametru|Žádné parametry bezpečný přístup z více vláken|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|Plně bezpečný přístup z více vláken; pouze jedno vlákno současně pokusí k inicializaci hodnoty.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Ano.|  
|Není bezpečný přístup z více vláken.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Nelze použít.|  
|Plně bezpečný přístup z více vláken; soupeření vláken k inicializaci hodnoty.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Nelze použít.|Nelze použít.|  
  
 Jako v tabulce jsou uvedeny, zadání <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> pro `mode` parametr je stejné jako zadání `true` pro `isThreadSafe` parametr a zadání <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> je stejné jako zadání `false`.  
  
 Určení <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> umožňuje více vláken na pokus o inicializaci <xref:System.Lazy%601> instance. Pouze jedno vlákno můžete win tento soupeření a všechna vlákna zobrazí hodnotu, která byla inicializována úspěšné vlákno. Pokud na vlákno během inicializace je vyvolána výjimka, daném vláknu neobdrží hodnotu nastavenou úspěšné vlákno. Výjimky se neukládají do mezipaměti, takže dalšímu pokusu o přístup <xref:System.Lazy%601.Value%2A> vlastnost může mít za následek úspěšné inicializace. To se liší od způsob, jakým výjimky jsou zpracovány v jiných režimů, který je popsaný v následující části. Další informace najdete v tématu <xref:System.Threading.LazyThreadSafetyMode> výčtu.  
  
<a name="ExceptionsInLazyObjects"></a>   
## <a name="exceptions-in-lazy-objects"></a>Výjimky v opožděné objekty  
 Jak jsme uvedli dříve, <xref:System.Lazy%601> objekt vždy vrátí stejné objekt nebo hodnotu, která byla inicializována, a proto <xref:System.Lazy%601.Value%2A> vlastnost je jen pro čtení. Pokud povolíte ukládání do mezipaměti výjimky, tento neměnitelnosti taky ji rozšiřuje na chování výjimka. Pokud je objekt opožděně inicializované výjimka povoleno ukládání do mezipaměti a vyvolá výjimku z jeho inicializační metoda při <xref:System.Lazy%601.Value%2A> je nejdřív získat přístup k vlastnosti, že stejná výjimka je vyvolána na všechny následné pokusy o přístup <xref:System.Lazy%601.Value%2A> vlastnost . Jinými slovy konstruktor typu zabalené nikdy znovu vyvolání ve scénářích s více vlákny. Proto <xref:System.Lazy%601> objekt nelze vyvolat výjimku na jedno přístupu a vrátit hodnotu na následné přístup.  
  
 Výjimka povoleno ukládání do mezipaměti je při použití žádné <xref:System.Lazy%601?displayProperty=nameWithType> konstruktor, který přebírá metodu inicializace (`valueFactory` parametr), například je povolena při použití `Lazy(T)(Func(T))`konstruktor. Pokud také trvá konstruktoru <xref:System.Threading.LazyThreadSafetyMode> hodnotu (`mode` parametr), zadejte <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> nebo <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>. Určení inicializační metoda umožňuje ukládání do mezipaměti výjimky pro tyto dva režimy. Inicializační metoda může být velmi jednoduché. Například může volat výchozí konstruktor pro `T`: `new Lazy<Contents>(() => new Contents(), mode)` v jazyce C# nebo `New Lazy(Of Contents)(Function() New Contents())` v jazyce Visual Basic. Pokud používáte <xref:System.Lazy%601?displayProperty=nameWithType> konstruktor, který není uveden inicializační metoda, výjimky, které jsou vyvolány pro výchozí konstruktor `T` se neukládají do mezipaměti. Další informace najdete v tématu <xref:System.Threading.LazyThreadSafetyMode> výčtu.  
  
> [!NOTE]
>  Pokud vytvoříte <xref:System.Lazy%601> objektu s `isThreadSafe` parametr konstruktoru nastavena na `false` nebo `mode` parametr konstruktoru nastavena na <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>, je nutné získat přístup <xref:System.Lazy%601> objektu z jednoho vlákna nebo zadejte vlastní synchronizace. To platí pro všechny aspekty objektu, včetně výjimek ukládání do mezipaměti.  
  
 Jak jsme uvedli v předchozí části, <xref:System.Lazy%601> objekty vytvořené tak, že zadáte <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> jinak považovat výjimky. S <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>, můžete k chybě při inicializaci pokouší více vláken <xref:System.Lazy%601> instance. V takovém případě výjimky se neukládají do mezipaměti a pokusí o přístup <xref:System.Lazy%601.Value%2A> vlastnost může pokračovat, dokud nebude úspěšná inicializace.  
  
 Následující tabulka shrnuje způsob, jakým <xref:System.Lazy%601> řízení konstruktory výjimky ukládání do mezipaměti.  
  
|Konstruktor|Režim bezpečný přístup z více vláken|Používá inicializační metoda|Výjimky jsou uložené v mezipaměti|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Lazy(T)()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Ne|Ne|  
|Lazy(T)(Func(T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Ano|Ano|  
|Lazy(T)(Boolean)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) nebo `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Ne|Ne|  
|Lazy(T)(Func(T), logická hodnota)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) nebo `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Ano|Ano|  
|Lazy(T)(LazyThreadSafetyMode)|Definované uživatelem|Ne|Ne|  
|Lazy(T)(Func(T), LazyThreadSafetyMode)|Definované uživatelem|Ano|Ne, pokud uživatel zadá <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>, jinak hodnota Ano.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Implementace opožděně inicializované vlastnost  
 Chcete-li implementovat veřejné vlastnosti pomocí opožděné inicializace, definovat pole základní vlastnosti jako <xref:System.Lazy%601>a vrátit <xref:System.Lazy%601.Value%2A> vlastnost z `get` přistupujícího objektu vlastnosti.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 <xref:System.Lazy%601.Value%2A> Vlastnost je jen pro čtení; proto nemá vlastnost, která ji vystavuje `set` přistupujícího objektu. Pokud požadujete, aby zajišťoval vlastnost pro čtení a zápis <xref:System.Lazy%601> objekt, `set` přistupujícího objektu, musíte vytvořit nový <xref:System.Lazy%601> objektu a přiřaďte ho k záložnímu úložišti. `set` Přistupujícího objektu musí vytvoření výrazu lambda, který vrátí novou hodnotu vlastnosti, která byla předána `set` přistupujícího objektu a že výrazu lambda předat konstruktoru pro nové <xref:System.Lazy%601> objektu. Další přístup <xref:System.Lazy%601.Value%2A> vlastnost způsobí, že nová inicializace <xref:System.Lazy%601>a jeho <xref:System.Lazy%601.Value%2A> vlastnost po tomto datu vrátí nové hodnoty, které bylo přiřazeno k vlastnosti. Příčinu tohoto convoluted uspořádání je zachování multithreading ochrany součástí <xref:System.Lazy%601>. Jinak, by přístupové objekty vlastnosti mít pro ukládání do mezipaměti první hodnoty vrácené <xref:System.Lazy%601.Value%2A> vlastnost a měnit pouze hodnotu uloženou v mezipaměti, a budete muset napsat vlastní kód bezpečné pro přístup z více vláken na to. Kvůli další inicializacích vyžadovanou pro čtení a zápis vlastnost zajišťoval <xref:System.Lazy%601> objektu, nemusí být přijatelný výkon. Kromě toho, v závislosti na konkrétní scénář, další koordinaci bude pravděpodobně nutné předejdete časování mezi setter a metod getter.  
  
## <a name="thread-local-lazy-initialization"></a>Opožděná inicializace Thread Local  
 V některých scénářích s více vlákny můžete poskytnout každé vlákno jeho vlastní privátní data. Taková data se nazývá *místní data*. V rozhraní .NET Framework verze 3.5 a starší, je možné aplikovat `ThreadStatic` atribut statické proměnné, chcete-li místní. Ale při použití `ThreadStatic` atribut může vést k jemně chyby. Například i základní inicializace příkazy způsobí proměnnou inicializovat pouze na první vláken, který přistupuje k, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 Na všechny ostatní vláken, budou inicializována proměnná pomocí jeho výchozí hodnota (nula). Jako alternativu v rozhraní .NET Framework verze 4, můžete použít <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> typ k vytvoření na základě instance, místní proměnné, která je inicializován na všechna vlákna pomocí <xref:System.Action%601> delegáta, který zadáte. V následujícím příkladu, všechna vlákna, který přístup `counter` jako 1 zobrazí jeho výchozí hodnotu.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601>zabalí jeho objekt stejným způsobem jako <xref:System.Lazy%601>, se tyto základní rozdíly:  
  
-   Každé vlákno inicializuje místní proměnné pomocí jeho vlastní privátní data, která nejsou přístupné z jiných vláken.  
  
-   <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> Vlastnost pro čtení a zápis a je možné upravit všechny stanovený počet. To může mít vliv šíření výjimek, například jeden `get` operace může vyvolat výjimku, ale dalšímu můžete úspěšně inicializován hodnota.  
  
-   Pokud je k dispozici žádné inicializace delegáta, <xref:System.Threading.ThreadLocal%601> bude inicializace typ zabalené pomocí výchozí hodnota typu. V tomto ohledu <xref:System.Threading.ThreadLocal%601> je v souladu s <xref:System.ThreadStaticAttribute> atribut.  
  
 Následující příklad ukazuje, že každé vlákno, který přistupuje `ThreadLocal<int>` instance získá svůj vlastní jedinečný kopii dat.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Lokální proměnné vláken v Parallel.For a ForEach  
 Při použití <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metoda nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metoda Iterujte přes zdroje dat současně, můžete použít přetížení, které mají integrovanou podporu pro místní data. V těchto metod vlákno polohu dosaženo pomocí místní delegáty pro vytvoření, přístup a vyčistit data. Další informace najdete v tématu [postupy: zápis smyčky Parallel.For pomocí proměnných Thread-Local](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) a [postupy: zápis smyčky Parallel.ForEach pomocí proměnných Thread-Local](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Pomocí opožděné inicializace pro nízkou režii scénáře  
 V případech, kdy máte opožděné inicializace velký počet objektů, můžete rozhodnout, že zabalení každý objekt v <xref:System.Lazy%601> vyžaduje příliš mnoho paměti nebo příliš mnoho výpočetních prostředků. Nebo můžete mít přísné požadavky je vystaven o tom, jak opožděné inicializace. V takových případech můžete použít `static` (`Shared` v jazyce Visual Basic) metody <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> opožděné inicializace každého objektu bez zabalení v instanci třídy <xref:System.Lazy%601>.  
  
 V následujícím příkladu předpokládáme, že, místo zabalení celou `Orders` objektu v jedné <xref:System.Lazy%601> objektu mít opožděně inicializované individuální `Order` pouze objekty, pokud jsou povinné.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 V tomto příkladu Všimněte si, že proces inicializace je vyvolán v každé iteraci smyčky. Ve scénářích s více procesy první vlákno k vyvolání procedury inicializace je ten, jehož hodnota je vidět všechna vlákna. Novější vláken také vyvolat proceduru inicializace, ale nepoužívají se jejich výsledky. Pokud tento druh možný spor není přijatelné, použijte přetížení <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> , která má logická hodnota argumentu a objekt synchronizace.  
  
## <a name="see-also"></a>Viz také  
 [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)  
 [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Postupy: Provádění opožděné inicializace objektů](../../../docs/framework/performance/how-to-perform-lazy-initialization-of-objects.md)
