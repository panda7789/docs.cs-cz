---
title: Tok dat (Task Parallel Library)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library
ms.assetid: 643575d0-d26d-4c35-8de7-a9c403e97dd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d89b26016213872250bcb4dbee96d7376afd3fcb
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666401"
---
# <a name="dataflow-task-parallel-library"></a>Tok dat (Task Parallel Library)
<a name="top"></a>Task Parallel Library (TPL) poskytuje součásti toku dat, které vám pomůžou zvýšit odolnost aplikací s podporou souběžného zpracování. Tyto komponenty toku dat jsou souhrnně označovány jako *Knihovna rozhraní TPL Dataflow*. Tento model toku dat propaguje programování založené na objektu actor tím, že zajišťuje předávání zpráv v procesu pro hrubý úlohy toku dat a zřetězení. Komponenty toku dat se vytvářejí na typech a plánování infrastruktury aplikace TPL a integrují se s podporou C#, Visual Basic a F# jazykovou podporou pro asynchronní programování. Tyto součásti toku dat jsou užitečné v případě, že máte více operací, které musí komunikovat s jiným asynchronním nebo pokud chcete data zpracovat, jakmile budou k dispozici. Zvažte například aplikaci, která zpracovává obrazová data z webové kamery. Pomocí modelu toku dat aplikace může zpracovat snímky imagí, jakmile budou k dispozici. Pokud aplikace vylepšuje snímky obrázků, například provedením světlé nápravy nebo snížení červeného oka, můžete vytvořit *kanál* komponent toku dat. Každá fáze kanálu může použít více hrubých paralelních funkcí, jako jsou funkce, které poskytuje TPL, k transformaci image.  
  
 Tento dokument poskytuje přehled knihovny toku dat TPL. Popisuje programovací model, předdefinované typy bloků toku dat a způsob konfigurace bloků toku dat pro splnění konkrétních požadavků vašich aplikací.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
 Tento dokument obsahuje následující části:  
  
- [Programovací model](#model)  
  
- [Předdefinované typy bloků toku dat](#predefined_types)  
  
- [Konfigurace chování bloku toku dat](#behavior)  
  
- [Vlastní bloky toku dat](#custom)  
  
<a name="model"></a>   
## <a name="programming-model"></a>Programovací model  
 Knihovna TPL Dataflow poskytuje základ pro předávání zpráv a virtuálního aplikací náročných na výkon procesoru a vstupně-výstupní operace s vysokou propustností a nízkou latencí. Poskytuje vám také explicitní kontrolu nad tím, jak jsou data ukládána do vyrovnávací paměti a pohybují se systémem. Pro lepší pochopení programovacího modelu toku dat zvažte aplikaci, která asynchronně načte obrázky z disku a vytvoří složený z těchto imagí. Tradiční programovací modely obvykle vyžadují, abyste k koordinaci úloh a přístupu ke sdíleným datům použili zpětná volání a synchronizační objekty, jako jsou zámky. Pomocí modelu programování toku dat můžete vytvořit objekty Dataflow, které zpracovávají obrázky při jejich čtení z disku. V modelu toku dat deklarujete, jakým způsobem jsou data zpracována, jakmile budou k dispozici, a také všechny závislosti mezi daty. Vzhledem k tomu, že modul runtime spravuje závislosti mezi daty, můžete se často vyhnout nutnosti synchronizovat přístup ke sdíleným datům. Kromě toho, vzhledem k tomu, že modul runtime plánuje práci na základě asynchronního příjezdu dat, může tok dat zlepšit odezvu a propustnost tím, že efektivně spravuje podkladová vlákna. Příklad, který používá programovací model Dataflow k implementaci zpracování bitové kopie v aplikaci model Windows Forms, naleznete v tématu [Návod: Použití toku dat v aplikaci](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)model Windows Forms.  
  
### <a name="sources-and-targets"></a>Zdroje a cíle  
 Knihovna TPL Dataflow se skládá z *bloků toku*dat, což jsou datové struktury, které ukládají data do vyrovnávací paměti a zpracovávají data. TPL definuje tři druhy bloků toku: *zdrojové bloky*, *cílové bloky*a *bloky pro šíření*. Zdrojový blok funguje jako zdroj dat a lze ho číst z. Cílový blok funguje jako přijímač dat a lze do něj zapisovat. Blok šíření funguje jako zdrojový blok i cílový blok a lze ho číst z a zapisovat do. TPL definuje <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> rozhraní, které představuje zdroje, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> pro reprezentaci cílů a <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602?displayProperty=nameWithType> k reprezentaci rozšířících. <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>dědí z obou <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>a. <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>  
  
 Knihovna TPL Dataflow poskytuje několik předdefinovaných typů bloků toku dat, které <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>implementují <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>rozhraní, <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> a. Tyto typy bloků toku dat jsou popsány v tomto dokumentu v části [předdefinované typy bloků toku](#predefined_types)dat.  
  
### <a name="connecting-blocks"></a>Spojovací bloky  
 Bloky toku dat můžete propojit s *kanály*pro formuláře, které jsou lineární sekvence bloků toku dat nebo *sítě*, které jsou grafy bloků toku dat. Kanál je jedna forma sítě. V kanálu nebo v síti zdroje asynchronně šíří data do cílů, jakmile budou tato data k dispozici. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=nameWithType> Metoda propojuje zdrojový blok toku dat s cílovým blokem. Zdroj může být propojený s žádným nebo více cíli. cíle lze propojit z nula nebo více zdrojů. Bloky toku dat můžete do nebo z kanálu nebo sítě souběžně přidávat nebo odebírat. Předdefinované typy bloků toku dat zpracovávají všechny aspekty bezpečnosti pro přístup z více vláken při propojování a odpojování.  
  
 Příklad, který spojuje bloky toku dat s cílem vytvořit základní kanál, najdete v [tématu Názorný postup: Vytvoření kanálu](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)toku dat. Příklad propojení bloků toku dat za účelem vytvoření komplexnější sítě najdete v tématu [Názorný postup: Použití toku dat v aplikaci](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)model Windows Forms. Příklad, který odpojí cíl ze zdroje po tom, co zdroj nabízí cíl zprávy, naleznete v tématu [How to: Zrušení propojení bloků](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)toku dat  
  
#### <a name="filtering"></a>Filtrování  
 Při volání <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=nameWithType> metody pro propojení zdroje s cílem můžete zadat delegáta, který určuje, zda cílový blok přijme nebo odmítne zprávu na základě hodnoty této zprávy. Tento mechanismus filtrování je užitečný způsob, jak zajistit, aby blok toku dat přijímal jenom určité hodnoty. Pro většinu předdefinovaných typů bloku toku dat je-li zdrojový blok připojen k více cílovým blokům, poté, co cílový blok odmítne zprávu, zdroj nabídne tuto zprávu dalšímu cíli. Pořadí, ve kterém zdroj nabízí zprávy na cíle, je definováno zdrojem a může se lišit podle typu zdroje. Většina typů zdrojových bloků zastaví nabízenou zprávu po tom, co jeden cíl přijme tuto zprávu. Jedinou výjimkou z tohoto pravidla je <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> třída, která nabízí každou zprávu všem cílům, i když některé cíle odmítnou zprávu. Příklad, který používá filtrování pro zpracování pouze určitých zpráv, naleznete v [tématu Návod: Použití toku dat v aplikaci](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)model Windows Forms.  
  
> [!IMPORTANT]
>  Vzhledem k tomu, že každý předdefinovaný typ bloku toku dat zaručuje, že se zprávy šíří v pořadí, ve kterém byly přijaty, musí být každá zpráva načtena ze zdrojového bloku předtím, než může zdrojový blok zpracovat další zprávu. Proto když použijete filtrování k připojení více cílů ke zdroji, ujistěte se, že alespoň jeden cílový blok obdrží každou zprávu. V opačném případě se aplikace může zablokovat.  
  
### <a name="message-passing"></a>Předávání zpráv  
 Programovací model Dataflow se vztahuje na pojem *předávání zpráv*, kde nezávislé komponenty programu spolu komunikují prostřednictvím posílání zpráv. Jedním ze způsobů, jak šířit zprávy mezi součástmi aplikace, je <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> volat <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> metody a k odesílání zpráv do cílového bloku toku dat (<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> operace funguje synchronně; pracuje asynchronně) <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>a metody, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A> pro příjem zpráv ze zdrojových bloků. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> Tyto metody můžete kombinovat s kanály toku dat nebo sítěmi tím, že odesíláte vstupní data do hlavního uzlu (cílový blok) a přijímáte výstupní data z uzlu terminálu kanálu nebo uzlů terminálů sítě (jeden nebo více zdrojových bloků). Můžete také použít <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Choose%2A> metodu ke čtení z první z poskytnutých zdrojů, které mají data k dispozici a k provádění akcí u těchto dat.  
  
 Zdrojové bloky nabízejí data do cílových bloků voláním <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A?displayProperty=nameWithType> metody. Cílový blok odpoví na nabízenou zprávu jedním ze tří způsobů: může přijmout zprávu, odmítnout zprávu nebo odložit zprávu. Když cíl přijme zprávu, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Accepted>metoda. Když cíl zprávu odmítne, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Declined>metoda. Pokud cíl vyžaduje, aby již nepřijímal žádné zprávy ze zdroje, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> vrátí. <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.DecliningPermanently> Předdefinované typy zdrojových bloků nenabízejí zprávy do propojených cílů po přijetí takové návratové hodnoty a automaticky odpojí z těchto cílů.  
  
 Když cílový blok odloží zprávu pro pozdější použití, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Postponed>metoda. Cílový blok, který odloží zprávu, může později zavolat <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReserveMessage%2A?displayProperty=nameWithType> metodu pro pokus o rezervaci nabízené zprávy. V tomto okamžiku je zpráva buď stále k dispozici, a může ji použít cílovým blokem, nebo zpráva byla pořízena jiným cílem. Pokud cílový blok později vyžaduje zprávu nebo už zprávu nepotřebuje, volá <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=nameWithType> metodu nebo <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReleaseReservation%2A> v uvedeném pořadí. Rezervace zprávy obvykle používá typy bloků toku dat, které fungují v nehladovém režimu. Nehladový režim je vysvětlen dále v tomto dokumentu. Místo zachovávání odložené zprávy může cílový blok také použít <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=nameWithType> metodu k pokusu o přímé využití odložené zprávy.  
  
### <a name="dataflow-block-completion"></a>Dokončení bloku toku dat  
 Bloky toku dat také podporují koncept *dokončení*. Blok toku dat, který je v dokončeném stavu, neprovede žádnou další práci. Každý blok toku dat má přidružený <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekt, který je známý jako *úkol dokončení*, který představuje stav dokončení bloku. Vzhledem k tomu, že můžete <xref:System.Threading.Tasks.Task> počkat na dokončení objektu, můžete pomocí úloh dokončení počkat na dokončení jednoho nebo více uzlů terminálů sítě toku dat. Rozhraní definuje metodu, která informuje blok toku dat žádosti o dokončení a <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> vlastnost, která vrátí úlohu dokončení pro blok toku dat. <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> Obojí <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> dědí<xref:System.Threading.Tasks.Dataflow.IDataflowBlock> rozhraní.  
  
 Existují dva způsoby, jak určit, zda byl blok toku dat dokončen bez chyb, došlo k jedné nebo více chybám nebo byl zrušen. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> Prvním způsobem je zavolat metodu pro úkol dokončení `try` `catch` - v bloku (`Try` - vVisualBasic)`Catch` . Následující příklad vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který vyvolá <xref:System.ArgumentOutOfRangeException> v případě, že jeho vstupní hodnota je menší než nula. <xref:System.AggregateException>je vyvolána, když tento příklad <xref:System.Threading.Tasks.Task.Wait%2A> volá úlohu dokončení. Je k dispozici <xref:System.AggregateException.InnerExceptions%2A> prostřednictvím vlastnosti <xref:System.AggregateException> objektu. <xref:System.ArgumentOutOfRangeException>  
  
 [!code-csharp[TPLDataflow_Overview#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#10)]
 [!code-vb[TPLDataflow_Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#10)]  
  
 Tento příklad ukazuje případ, ve kterém výjimka Neošetřená v delegátu pro spuštění bloku toku dat. Doporučujeme zpracovávat výjimky v podvodních blocích. Nicméně pokud to nemůžete udělat, blok se chová, jako by byl zrušen a nezpracovává příchozí zprávy.  
  
 Když je blok toku dat explicitně zrušen, <xref:System.AggregateException> objekt obsahuje <xref:System.OperationCanceledException> <xref:System.AggregateException.InnerExceptions%2A> vlastnost. Další informace o zrušení toku dat najdete v části [Povolení zrušení](#enabling-cancellation) .  
  
 Druhým způsobem, jak určit stav dokončení bloku toku dat, je použití pokračování úlohy dokončení nebo použití asynchronních funkcí jazyka C# a Visual Basic k asynchronnímu čekání na úkol dokončení. Delegát, který zadáte do <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody, <xref:System.Threading.Tasks.Task> převezme objekt, který představuje předchozí úlohu. V případě <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> vlastnosti má delegát pro pokračování vlastní úlohu dokončení. Následující příklad je podobný předchozímu, s tím rozdílem, že používá <xref:System.Threading.Tasks.Task.ContinueWith%2A> také metodu k vytvoření pokračování úlohy, která vytiskne stav celkové operace toku dat.  
  
 [!code-csharp[TPLDataflow_Overview#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#11)]
 [!code-vb[TPLDataflow_Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#11)]  
  
 Můžete také použít vlastnosti <xref:System.Threading.Tasks.Task.IsCanceled%2A> , jako je například v těle úlohy pokračování, a určit tak další informace o stavu dokončení bloku toku dat. Další informace o pokračujících úkolech a jejich vztahu ke zrušení a zpracování chyb naleznete v tématu [zřetězení úloh pomocí úloh pokračování](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md), [zrušení úkolu](../../../docs/standard/parallel-programming/task-cancellation.md)a [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
 [[Přejít na začátek](#top)]  
  
<a name="predefined_types"></a>   
## <a name="predefined-dataflow-block-types"></a>Předdefinované typy bloků toku dat  
 Knihovna TPL Dataflow poskytuje několik předdefinovaných typů bloků toku dat. Tyto typy jsou rozděleny do tří kategorií: *bloky ukládání do vyrovnávací paměti*, *bloky spouštění*a *bloky seskupení*. Následující části popisují typy bloků, které tvoří tyto kategorie.  
  
### <a name="buffering-blocks"></a>Bloky ukládání do vyrovnávací paměti  
 Ukládání bloků do vyrovnávací paměti blokuje data, která používají příjemci dat. Knihovna TPL Dataflow poskytuje tři typy bloků vyrovnávací paměti: <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601?displayProperty=nameWithType>a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601?displayProperty=nameWithType>.  
  
#### <a name="bufferblockt"></a>BufferBlock (T)  
 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Třída reprezentuje strukturu asynchronního zasílání zpráv pro obecné účely. Tato třída ukládá do fronty první v, první ven (FIFO) zprávy, na které může zapisovat více zdrojů nebo číst z více cílů. Když cíl obdrží zprávu od <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu, tato zpráva se odebere z fronty zpráv. Proto i když <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objekt může mít více cílů, obdrží každou zprávu pouze jeden cíl. Třída <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> je užitečná v případě, že chcete předat více zpráv jiné komponentě a tato součást musí přijmout každou zprávu.  
  
 Následující základní příklad účtuje několik <xref:System.Int32> hodnot <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu a poté tyto hodnoty přečte z tohoto objektu.  
  
 [!code-csharp[TPLDataflow_Overview#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#1)]
 [!code-vb[TPLDataflow_Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#1)]  
  
 Úplný příklad, který ukazuje, jak napsat zprávy do a číst zprávy z <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu, naleznete v tématu [How to: Zápis zpráv do a čtení zpráv z bloku](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md)toku dat  
  
#### <a name="broadcastblockt"></a>BroadcastBlock (T)  
 Třída <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> je užitečná v případě, že je nutné předat více zpráv jiné komponentě, ale komponenta potřebuje pouze nejnovější hodnotu. Tato třída je užitečná také v případě, že chcete vysílat zprávu na více součástí.  
  
 Následující základní příklad účtuje <xref:System.Double> hodnotu <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> objektu a potom tuto hodnotu z tohoto objektu přečte několikrát. Vzhledem k tomu, že hodnoty <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> nejsou odebrány z objektů po jejich čtení, je stejná hodnota vždy k dispozici.  
  
 [!code-csharp[TPLDataflow_Overview#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#2)]
 [!code-vb[TPLDataflow_Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#2)]  
  
 Úplný příklad, který ukazuje, jak použít <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> pro vysílání zprávy do více cílových bloků, naleznete v tématu [How to: Zadejte Plánovač úloh v bloku](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)toku dat.  
  
#### <a name="writeonceblockt"></a>WriteOnceBlock (T)  
 Třída se <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> podobá<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> třídě, s tím rozdílem, že objekt může být zapsán pouze jednorázově. <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> Můžete si <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> představit jako podobné C# klíčové slovo [ReadOnly](../../csharp/language-reference/keywords/readonly.md) ([ReadOnly](../../visual-basic/language-reference/modifiers/readonly.md) <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> v Visual Basic), s tím rozdílem, že objekt se po přijetí hodnoty namísto konstrukce stal neměnné. Podobně jako <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> třída, když cíl obdrží zprávu z objektu, není tato zpráva z tohoto objektu odebrána. <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> Proto více cílů obdrží kopii zprávy. <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> Třída je užitečná, pokud chcete rozšířit pouze první z více zpráv.  
  
 Následující základní příklad odesílá více <xref:System.String> hodnot <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> do objektu a pak přečte hodnotu z tohoto objektu. Vzhledem k <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> tomu, že je možné objekt zapsat pouze jednou, <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> poté, co objekt obdrží zprávu, zahodí následné zprávy.  
  
 [!code-csharp[TPLDataflow_Overview#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#3)]
 [!code-vb[TPLDataflow_Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#3)]  
  
 Úplný příklad, který ukazuje, jak použít <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> k získání hodnoty první operace, která skončí, naleznete v tématu [How to: Zrušení propojení bloků](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)toku dat  
  
### <a name="execution-blocks"></a>Bloky spuštění  
 Bloky spouštění volají uživatelem poskytnutý delegát pro každou část přijatých dat. Knihovna TPL Dataflow poskytuje tři typy bloku spuštění: <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.  
  
#### <a name="actionblockt"></a>ActionBlock (T)  
 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Třída je cílovým blokem, který volá delegáta při přijímání dat. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objekt můžete představit jako delegát, který se spouští asynchronně, když budou data k dispozici. Delegát, který zadáte <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu, může být typu <xref:System.Action%601> nebo typu `System.Func<TInput, Task>`. Při použití <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu s <xref:System.Action%601>se zpracování každého elementu vstupu je považováno za dokončené, když se delegát vrátí. Při použití <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu se `System.Func<TInput, Task>`zpracování každého vstupního elementu je považováno za dokončené pouze v případě, že <xref:System.Threading.Tasks.Task> je vrácen objekt dokončen. Pomocí těchto dvou mechanismů lze použít <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> pro synchronní i asynchronní zpracování každého elementu Input.  
  
 Následující základní příklad odesílá více <xref:System.Int32> hodnot <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> do objektu. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objekt vytiskne tyto hodnoty do konzoly. Tento příklad nastaví blok na stav dokončeno a počká na dokončení všech úloh toku dat.  
  
 [!code-csharp[TPLDataflow_Overview#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#4)]
 [!code-vb[TPLDataflow_Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#4)]  
  
 Kompletní příklady, které ukazují, jak používat delegáty s <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> třídou, [naleznete v tématu How to: Provede akci, když blok toku dat přijme data](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md).  
  
#### <a name="transformblocktinput-toutput"></a>Operace TransformBlock (TInput, TOutput)  
 Třída se podobá <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> třídě, s tím rozdílem, že funguje jako zdroj i jako cíl. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Delegát, který předáte <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu, vrací hodnotu typu. `TOutput` Delegát, který zadáte <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu, může být typu `System.Func<TInput, TOutput>` nebo typu `System.Func<TInput, Task<TOutput>>`. Při použití <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu s `System.Func<TInput, TOutput>`se zpracování každého elementu vstupu je považováno za dokončené, když se delegát vrátí. Při použití <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu používaného s `System.Func<TInput, Task<TOutput>>`je zpracování každého vstupního elementu považováno za dokončeno pouze v případě, že <xref:System.Threading.Tasks.Task%601> je vrácen objekt dokončen. Stejně jako <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>u, pomocí těchto dvou mechanismů lze použít <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pro synchronní i asynchronní zpracování každého elementu Input.  
  
 Následující základní příklad vytvoří <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt, který vypočítá druhou odmocninu svého vstupu. Objekt přebírá <xref:System.Int32> hodnoty jako vstup a vytváří <xref:System.Double> hodnoty jako výstup. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>  
  
 [!code-csharp[TPLDataflow_Overview#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#5)]
 [!code-vb[TPLDataflow_Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#5)]  
  
 Kompletní příklady, které používá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> v síti bloků toku dat, který provádí zpracování imagí v model Windows Forms aplikaci, najdete v tématu [Názorný postup: Použití toku dat v aplikaci](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)model Windows Forms.  
  
#### <a name="transformmanyblocktinput-toutput"></a>TransformManyBlock(TInput, TOutput)  
 Třída se podobá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> třídě, s tím rozdílem, že <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> pro každou vstupní hodnotu vytvoří nula nebo více výstupních hodnot namísto jedné výstupní hodnoty pro každou vstupní hodnotu. <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> Delegát, který zadáte <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objektu, může být typu `System.Func<TInput, IEnumerable<TOutput>>` nebo typu `System.Func<TInput, Task<IEnumerable<TOutput>>>`. Při použití <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objektu s `System.Func<TInput, IEnumerable<TOutput>>`se zpracování každého elementu vstupu je považováno za dokončené, když se delegát vrátí. Při použití <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objektu se `System.Func<TInput, Task<IEnumerable<TOutput>>>`zpracování každého vstupního elementu je považováno za kompletní pouze v případě, že je `System.Threading.Tasks.Task<IEnumerable<TOutput>>` vrácen objekt dokončen.  
  
 Následující základní příklad vytvoří <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekt, který rozdělí řetězce do jejich jednotlivých znakových sekvencí. Objekt přebírá <xref:System.String> hodnoty jako vstup a vytváří <xref:System.Char> hodnoty jako výstup. <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>  
  
 [!code-csharp[TPLDataflow_Overview#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#6)]
 [!code-vb[TPLDataflow_Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#6)]  
  
 Kompletní příklady, které slouží <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> k vytvoření více nezávislých výstupů pro každý vstup v kanálu toku dat, naleznete [v tématu Návod: Vytvoření kanálu](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)toku dat.  
  
#### <a name="degree-of-parallelism"></a>Stupeň paralelismu  
 Každý <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>objekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, a<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> ukládá do vyrovnávací paměti vstupní zprávy, dokud je blok připravený na jejich zpracování. Ve výchozím nastavení tyto třídy zpracovávají zprávy v pořadí, ve kterém jsou přijímány, vždy jedna zpráva. Můžete také určit míru paralelismu, které mají být povoleny <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekty pro souběžné zpracování více zpráv. Další informace o souběžném spuštění najdete v části určení stupně paralelismu v níže v tomto dokumentu. Příklad, který nastaví míru paralelismus pro povolení bloku toku dat spouštění pro zpracování více než jedné zprávy najednou, naleznete v tématu [How to: Určuje stupeň paralelismu v bloku](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)toku dat.  
  
#### <a name="summary-of-delegate-types"></a>Souhrn typů delegátů  
 Následující tabulka shrnuje typy delegátů, které lze poskytnout <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>objektům, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> . Tato tabulka také určuje, zda typ delegáta funguje synchronně nebo asynchronně.  
  
|type|Typ synchronního delegáta|Typ asynchronního delegáta|  
|----------|-------------------------------|--------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|`System.Action`|`System.Func<TInput, Task>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|`System.Func<TInput, TOutput>`|`System.Func<TInput, Task<TOutput>>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|`System.Func<TInput, IEnumerable<TOutput>>`|`System.Func<TInput, Task<IEnumerable<TOutput>>>`|  
  
 Lambda výrazy můžete použít také při práci s typy bloku spuštění. Příklad, který ukazuje, jak použít výraz lambda s blokem spuštění, naleznete v tématu [How to: Provede akci, když blok toku dat přijme data](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md).  
  
### <a name="grouping-blocks"></a>Bloky seskupení  
 Bloky seskupení seskupují data z jednoho nebo více zdrojů a v různých omezeních. Knihovna TPL Dataflow poskytuje tři typy bloku spojení: <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>.  
  
#### <a name="batchblockt"></a>Tříd BatchBlock (T)  
 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> Třída kombinuje sady vstupních dat, která se označují jako dávky, do polí výstupních dat. Velikost každé dávky určíte při vytváření <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu. <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> Když objekt obdrží zadaný počet vstupních prvků, asynchronně rozšíří pole, které obsahuje tyto prvky. Pokud je <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt nastavený na stav dokončeno, ale neobsahuje dostatek prvků pro vytvoření dávky, rozšíří konečné pole, které obsahuje zbývající vstupní prvky.  
  
 Třída funguje buď v hladovém, nebo nehladovém režimu. <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> V režimu hladce, který je výchozí hodnota, <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt akceptuje každou zprávu, že je nabízena a šíří pole po přijetí zadaného počtu prvků. V nehladovém režimu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt odloží všechny příchozí zprávy, dokud dostatek zdrojů nenabídly do bloku zprávy, aby mohl vytvořit dávku. Hladový režim obvykle provádí lepší režim než hladec, protože vyžaduje méně režijních nákladů na zpracování. Nehladý režim však můžete použít v případě, že je nutné sjednotit spotřebu z více zdrojů atomicky. Určete Nehladový režim <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> nastavením na `False` <xref:System.Threading.Tasks.Dataflow.BatchBlock%601.%23ctor%2A> v `dataflowBlockOptions` parametru v konstruktoru.  
  
 Následující základní příklad účtuje několik <xref:System.Int32> hodnot <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> do objektu, který obsahuje deset prvků v dávce. Aby bylo zaručeno, že všechny hodnoty šíří mimo <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, tento příklad <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> volá metodu. Metoda nastaví objekt na stav dokončeno <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> , a proto objekt rozšíří všechny zbývající prvky jako finální dávku. <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>  
  
 [!code-csharp[TPLDataflow_Overview#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#7)]
 [!code-vb[TPLDataflow_Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#7)]  
  
 Úplný příklad, který nástroj používá <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> ke zlepšení efektivity operací vložení databáze, najdete v [tématu Názorný postup: Použití tříd BatchBlock a BatchedJoinBlock ke zvýšení efektivity](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md).  
  
#### <a name="joinblockt1-t2-"></a>JoinBlock (T1, T2,...)  
 Třídy <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> shromažďují vstupní <xref:System.Tuple%602?displayProperty=nameWithType> prvky<xref:System.Tuple%603?displayProperty=nameWithType> a šíří objekty, které obsahují tyto prvky. Třídy <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> nedědí z. Místo <xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target1%2A>toho poskytují vlastnosti, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target2%2A>, a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603.Target3%2A>, které implementují <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Podobně jako <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> a<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>funguje v hladovém nebo nehladovém režimu. <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> V režimu hladce, což je výchozí hodnota, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekt <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> nebo přijímá všechny zprávy, které jsou nabízeny, a šíří řazenou kolekci členů po každém z jeho cílů obdrží alespoň jednu zprávu. V nehladovém režimu <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekt nebo <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> odloží všechny příchozí zprávy, dokud nebudou všechny cíle nabídnuty na data potřebná k vytvoření řazené kolekce členů. V tomto okamžiku se zablokuje pomocí dvoufázového potvrzovacího protokolu, aby byly atomicky načteny všechny požadované položky ze zdrojů. Díky tomuto odložení je možné, že by jiná entita mohla data během této doby spotřebovat, aby celkový systém mohl předávat pokrok.  
  
 Následující základní příklad ukazuje případ, ve kterém <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objekt vyžaduje více dat pro výpočet hodnoty. Tento příklad vytvoří <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objekt, který vyžaduje dvě <xref:System.Int32> hodnoty a <xref:System.Char> hodnotu k provedení aritmetické operace.  
  
 [!code-csharp[TPLDataflow_Overview#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#8)]
 [!code-vb[TPLDataflow_Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#8)]  
  
 Úplný příklad, který používá <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekty v nehladovém režimu pro kooperativní sdílení prostředku, naleznete v tématu [How to: Pomocí JoinBlock můžete číst data z více zdrojů](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md).  
  
#### <a name="batchedjoinblockt1-t2-"></a>BatchedJoinBlock (T1, T2,...)  
 Třídy <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> `System.Tuple(IList(T1), IList(T2))` a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%603> shromažďují dávky vstupních prvků`System.Tuple(IList(T1), IList(T2), IList(T3))` a šíří objekty, které obsahují tyto prvky. Můžete si představit <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> jako kombinaci a. Určete velikost každé dávky při vytváření <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objektu. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>poskytuje také vlastnosti, <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A>, které implementují <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>. Při přijetí zadaného počtu vstupních prvků ze všech cílů <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objekt asynchronně šíří `System.Tuple(IList(T1), IList(T2))` objekt, který obsahuje tyto prvky.  
  
 Následující základní příklad vytvoří <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objekt, který obsahuje výsledky, <xref:System.Int32> hodnoty a chyby, které jsou <xref:System.Exception> objekty. Tento příklad provede více operací a zapisuje výsledky do <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A> vlastnosti a chyby <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A> <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objektu. Vzhledem k tomu, že počet úspěšných a neúspěšných operací je <xref:System.Collections.Generic.IList%601> předem neznámý, objekty umožňují, aby každý cíl přijímal nula nebo více hodnot.  
  
 [!code-csharp[TPLDataflow_Overview#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#9)]
 [!code-vb[TPLDataflow_Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#9)]  
  
 Úplný příklad, který používá <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> k zachycení výsledků a všech výjimek, ke kterým dojde, když program načítá z databáze, najdete v článku [Návod: Použití tříd BatchBlock a BatchedJoinBlock ke zvýšení efektivity](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md).  
  
 [[Přejít na začátek](#top)]  
  
<a name="behavior"></a>   
## <a name="configuring-dataflow--block-behavior"></a>Konfigurace chování bloku toku dat  
 Můžete povolit další možnosti poskytnutím <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=nameWithType> objektu konstruktoru typu bloku toku dat. Tyto možnosti řídí chování, jako je Plánovač, který spravuje základní úlohu a stupeň paralelismu. Má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions> také odvozené typy, které určují chování, které je specifické pro určité typy bloků toku dat. Následující tabulka shrnuje, které typy možností jsou spojené s každým typem bloku toku dat.  
  
|Typ bloku toku dat|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>textový|  
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
  
 Následující části poskytují další informace o důležitých typech možností bloku toku dat, které jsou k dispozici prostřednictvím <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=nameWithType>tříd, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions?displayProperty=nameWithType>a. <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions?displayProperty=nameWithType>  
  
### <a name="specifying-the-task-scheduler"></a>Určení Plánovač úloh  
 Každý předdefinovaný blok toku dat používá mechanizmus plánování úloh TPL k provádění aktivit, jako je například šíření dat do cíle, příjem dat ze zdroje a spuštění uživatelem definovaných delegátů, když budou data k dispozici. <xref:System.Threading.Tasks.TaskScheduler>je abstraktní třída, která představuje Plánovač úloh, který zařadí do fronty úlohy na vlákna. Výchozí Plánovač <xref:System.Threading.Tasks.TaskScheduler.Default%2A>úloh <xref:System.Threading.ThreadPool> používá třídu k zařazení do fronty a provedení práce. Výchozí Plánovač <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> úloh můžete přepsat nastavením vlastnosti při vytváření objektu bloku toku dat.  
  
 Když stejný Plánovač úloh spravuje více bloků toku dat, může v nich vyhovět zásadám. Například pokud jsou jednotlivé bloky toku dat nakonfigurovány tak, aby cílí na výhradní Plánovač stejného <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu, bude serializována veškerá práce, která běží v těchto blocích. Podobně platí, že pokud jsou tyto bloky nakonfigurovány tak, aby cílí na <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> souběžný Plánovač stejného objektu a že je tento Plánovač nakonfigurovaný tak, aby měl maximální úroveň souběžnosti, všechny práce z těchto bloků budou omezeny na tento počet souběžných operací. Příklad, který používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> třídu k umožnění operací čtení paralelně, ale operace zápisu mají být prováděny výhradně pro všechny ostatní operace, naleznete v tématu [How to: Zadejte Plánovač úloh v bloku](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)toku dat. Další informace o Plánovači úloh v TPL naleznete <xref:System.Threading.Tasks.TaskScheduler> v tématu třídy.  
  
### <a name="specifying-the-degree-of-parallelism"></a>Určení stupně paralelismu  
 Ve výchozím nastavení tři typy bloku spuštění, které poskytuje knihovna toku dat TPL, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>zpracovávají jednu zprávu v jednom okamžiku. Tyto typy bloků toku dat také zpracovávají zprávy v pořadí, ve kterém jsou přijaty. Chcete-li těmto blokům toku dat Povolit souběžné zpracování zpráv, nastavte <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> vlastnost při vytváření objektu bloku toku dat.  
  
 Výchozí hodnota <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> je 1, což zaručuje, že blok toku dat zpracuje jednu zprávu současně. Když nastavíte tuto vlastnost na hodnotu, která je větší než 1, povolí blok toku dat souběžně zpracovávat více zpráv. Nastavením této vlastnosti <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=nameWithType> umožníte základnímu Plánovači úloh spravovat maximální stupeň souběžnosti.  
  
> [!IMPORTANT]
>  Když zadáte maximální stupeň paralelismu, který je větší než 1, zpracovává se souběžně několik zpráv, takže zprávy nemusejí být zpracovány v pořadí, ve kterém byly přijaty. Pořadí, ve kterém jsou zprávy výstupem z bloku, je však stejné jako v tom, v jakém byly přijaty.  
  
 Vzhledem k tomu, že vlastnostpředstavujemaximálnístupeňparalelismu,můžebýtbloktokudatprovedensmenšímstupněmparalelismu,nežurčíte.<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> Blok toku dat může používat menší stupeň paralelismu k splnění jeho funkčních požadavků nebo nedostatku dostupných systémových prostředků. Blok toku dat nikdy nevolí více paralelismu, než zadáte.  
  
 Hodnota <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnosti je exkluzivní pro každý objekt bloku toku dat. Pokud například čtyři objekty bloku Dataflow každý určí 1 pro maximální stupeň paralelismu, mohou být všechny čtyři objekty bloku toku dat potenciálně spouštěny paralelně.  
  
 Příklad, který nastavuje maximální stupeň paralelismu, aby bylo možné paralelní operace provádět paralelně, naleznete v tématu [How to: Určuje stupeň paralelismu v bloku](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)toku dat.  
  
### <a name="specifying-the-number-of-messages-per-task"></a>Určení počtu zpráv na úlohu  
 Předdefinované typy bloků toku dat používají úlohy ke zpracování více elementů vstupu. To pomáhá minimalizovat počet objektů úloh, které jsou požadovány pro zpracování dat, což umožňuje aplikacím běžet efektivněji. Pokud ale úkoly z jedné sady bloků toku dat zpracovávají data, může se stát, že se úlohy z jiných bloků toku budou muset čekat na dobu zpracování v rámci řazení zpráv do fronty. Chcete-li umožnit lepší rovnost mezi úlohami toku dat <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> , nastavte vlastnost. Když <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> je nastavená <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=nameWithType>na, což je výchozí, úloha používaná blokem toku dat zpracovává všechny zprávy, které jsou k dispozici. Když <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> je nastavená na jinou hodnotu než <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded>, blok toku dat zpracovává maximálně tento počet zpráv na <xref:System.Threading.Tasks.Task> objekt. I když nastavení <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> vlastnosti může zvýšit spravedlivosti mezi úkoly, může způsobit, že systém vytvoří více úloh, než je nutné, což může snížit výkon.  
  
### <a name="enabling-cancellation"></a>Povolení zrušení  
 TPL poskytuje mechanismus, který umožňuje úlohám koordinovat zrušení v rámci spolupráce. Chcete-li povolit bloky toku dat pro účast v tomto mechanismu zrušení, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> nastavte vlastnost. Pokud je <xref:System.Threading.CancellationToken> tento objekt nastavený na stornovaný stav, všechny bloky toku dat, které sledují toto vykonání tohoto tokenu aktuální položky, ale nespouštějí následné zpracování položek. Tyto bloky toku dat také vymažou všechny zprávy ve vyrovnávací paměti, vydávají připojení k jakémukoli zdrojovému a cílovému bloku a přechod do stavu zrušeno. Přechodem na stornovaný stav <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> vlastnost <xref:System.Threading.Tasks.Task.Status%2A> má vlastnost nastavenou na <xref:System.Threading.Tasks.TaskStatus.Canceled>hodnotu, pokud během zpracování nedojde k výjimce. V takovém případě <xref:System.Threading.Tasks.Task.Status%2A> je nastavena na <xref:System.Threading.Tasks.TaskStatus.Faulted>.  
  
 Příklad, který ukazuje, jak použít zrušení v model Windows Forms aplikace, naleznete v tématu [How to: Zruší blok](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)toku dat. Další informace o zrušení v TPL naleznete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="specifying-greedy-versus-non-greedy-behavior"></a>Určení hladového versus nehladového chování  
 Několik typů bloků datového toku pro seskupení může pracovat buď v hladovém, nebo nehladovém režimu. Ve výchozím nastavení jsou předdefinované typy bloků toku dat provozovány v hladovém režimu.  
  
 Pro typy <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>bloku JOIN, jako je například hladový režim, znamená, že blok okamžitě přijímá data i v případě, že odpovídající data, ke kterým se připojíte, ještě nejsou k dispozici. Nehladový režim znamená, že blok odloží všechny příchozí zprávy, dokud není k dispozici na všech svých cílech pro dokončení spojení. Pokud již žádná z odložených zpráv není k dispozici, blok spojení uvolní všechny odložené zprávy a restartuje proces. Pro třídu, hladové a nehladové chování je podobné, s výjimkou případů, kdy v nehladovém režimu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt odloží všechny příchozí zprávy, dokud není dostatek dostupných z různých zdrojů k dokončení dávky. <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>  
  
 Chcete-li určit Nehladový režim pro blok toku dat, <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> nastavte `False`na. Příklad, který ukazuje, jak použít nehladý režim pro povolení více bloků spojení pro efektivnější sdílení zdroje dat, naleznete v tématu [How to: Pomocí JoinBlock můžete číst data z více zdrojů](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md).  
  
 [[Přejít na začátek](#top)]  
  
<a name="custom"></a>   
## <a name="custom-dataflow-blocks"></a>Vlastní bloky toku dat  
 I když knihovna TPL Dataflow poskytuje mnoho předdefinovaných typů bloku, můžete vytvořit další typy bloků, které provádějí vlastní chování. Implementujte <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> rozhraní nebo přímo nebo použijte metoduksestaveníkomplexníhobloku,kterýzapouzdřujechováníexistujícíchtypůbloků.<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> Příklady, které ukazují, jak implementovat vlastní funkci bloku toku dat, naleznete [v tématu Názorný postup: Vytváření vlastního typu](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)bloku toku dat  
  
 [[Přejít na začátek](#top)]  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Zápis zpráv do a čtení zpráv z bloku toku dat](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md)|Ukazuje, jak psát zprávy do a číst zprávy z <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu.|  
|[Postupy: Implementace vzoru toku dat producent – příjemce](../../../docs/standard/parallel-programming/how-to-implement-a-producer-consumer-dataflow-pattern.md)|Popisuje, jak použít model toku dat pro implementaci vzoru producent-příjemce, kde producent posílá zprávy do bloku toku dat a příjemce čte zprávy z tohoto bloku.|  
|[Postupy: Provést akci, když blok toku dat přijme data](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)|Popisuje, jak poskytnout delegáty pro spouštění typů <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>bloku toku dat,, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>.|  
|[Návod: Vytvoření kanálu toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)|V této části najdete popis postupu vytvoření kanálu toku dat, který stahuje text z webu a provádí operace s tímto textem.|  
|[Postupy: Zrušit propojení bloků toku dat](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)|Ukazuje, jak použít <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metodu k odpojení cílového bloku od zdroje poté, co zdroj nabídne zprávu cíli.|  
|[Návod: Použití toku dat v aplikaci model Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)|Ukazuje, jak vytvořit síť bloků toku dat, které provádějí zpracování bitové kopie v aplikaci model Windows Forms.|  
|[Postupy: Zrušení bloku toku dat](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)|Ukazuje, jak použít zrušení v aplikaci model Windows Forms.|  
|[Postupy: Použití JoinBlock ke čtení dat z více zdrojů](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)|Vysvětluje, jak použít <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> třídu k provedení operace, když jsou data k dispozici z více zdrojů, a jak použít Nehladový režim k povolení sdílení zdroje dat více spojovacími bloky.|  
|[Postupy: Určení stupně paralelismu v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)|Popisuje, jak nastavit <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnost tak, aby umožňovala zpracování bloku toku dat spouštění více zpráv najednou.|  
|[Postupy: Určení Plánovač úloh v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)|Ukazuje, jak přidružit konkrétní Plánovač úloh při použití toku dat ve vaší aplikaci.|  
|[Návod: Zvýšení efektivity pomocí tříd BatchBlock a BatchedJoinBlock](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)|Popisuje, jak použít <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídu ke zlepšení efektivity operací vložení databáze a způsobu <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> použití třídy k zachycení výsledků a všech výjimek, ke kterým dojde, když program načítá z databáze.|  
|[Návod: Vytvoření vlastního typu bloku toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)|Ukazuje dva způsoby vytvoření typu bloku toku dat, který implementuje vlastní chování.|  
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zavádí TPL, knihovnu, která zjednodušuje paralelní a souběžné programování v aplikacích .NET Framework.|
