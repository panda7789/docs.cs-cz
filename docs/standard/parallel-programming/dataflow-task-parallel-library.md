---
title: Tok dat (Task Parallel Library)
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library
ms.assetid: 643575d0-d26d-4c35-8de7-a9c403e97dd6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f91100303cb0970ed430eebe2a377a487017b47d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="dataflow-task-parallel-library"></a>Tok dat (Task Parallel Library)
<a name="top"></a>Task Parallel Library (TPL) poskytuje součásti toku dat a pomáhá tak zvýšit robustnost aplikací s povolenými souběžnosti. Tyto součásti toku dat se souhrnně označují jako *knihovna toku dat TPL*. Tento model toku dat podporuje programování založené na objektu actor pomocí poskytnete zprávy v procesu předávání pro hrubý toku dat a paralelní zpracování úlohy. Komponenty toku dat sestavení pro typy a plánování infrastruktury TPL a integrovat jazyka C#, [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]a F # jazyková podpora pro asynchronní programování. Tyto součásti toku dat jsou užitečné, pokud máte více operací, které musí vzájemnou komunikaci asynchronně, nebo pokud chcete zpracovat data, jakmile je k dispozici. Představte si třeba aplikaci, která zpracovává data bitové kopie z webové kamery. Pomocí modelu toku dat je aplikace dokáže zpracovat rámce bitové kopie, jakmile budou k dispozici. Pokud aplikace vylepšuje rámce bitové kopie, například provedením světla oprava nebo červených snížení, můžete vytvořit *kanálu* toku dat komponent. Každá fáze v kanálu může používat další funkce hrubý paralelismus, jako jsou funkce, která zajišťuje TPL k transformaci bitovou kopii.  
  
 Tento dokument obsahuje přehled knihovna toku dat TPL. Popisuje programovací model, typy bloku předdefinované toku dat a postup konfigurace bloků toku dat podle specifických požadavků vaší aplikace.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
 Tento dokument obsahuje následující části:  
  
-   [Model programování](#model)  
  
-   [Typy předdefinované bloku toku dat](#predefined_types)  
  
-   [Konfigurace chování bloku toku dat](#behavior)  
  
-   [Vlastních bloků toku dat](#custom)  
  
<a name="model"></a>   
## <a name="programming-model"></a>Programovací model  
 Knihovna toku dat TPL poskytuje základ pro zprávy předávání a paralelním prováděním náročná na prostředky procesoru a I náročnými aplikace, které mají vysoké prostupnosti a nízké latence. Také nabízí explicitní kontrolu nad dat do vyrovnávací paměti a přesune kolem systému. Abyste lépe pochopili programovací model toku dat, zvažte aplikaci, která asynchronně načte bitové kopie z disku a vytvoří složené tyto bitové kopie. Tradiční programovací modely obvykle vyžadují použití zpětná volání a synchronizace objekty, například zámků, koordinovat úloh a přístup ke sdíleným datům. Pomocí programovací model toku dat, můžete vytvořit objekty toku dat, které se načítají z disku zpracování obrázků. V rámci modelu toku dat je deklarovat, jak se zpracují data, až bude k dispozici a také všechny závislosti mezi daty. Vzhledem k tomu, že modul runtime spravuje závislosti mezi daty, často se můžete vyhnout požadavek na synchronizaci přístup ke sdíleným datům. Kromě toho protože modul runtime plánuje práci podle asynchronní doručení dat, toku dat lze vylepšit rychlost reakce a propustnost efektivně spravovat základní vláken. Příklad, který používá programovací model toku dat k implementaci zpracování obrázků v aplikaci Windows Forms, naleznete v části [návod: použití toku dat ve formulářové aplikaci Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
### <a name="sources-and-targets"></a>Zdroje a cíle  
 Knihovna toku dat TPL se skládá z *bloků toku dat*, které jsou data struktury dat vyrovnávací paměti a proces. Definuje tři druhy bloků toku dat TPL: *zdroje bloky*, *cíle bloky*, a *Šiřitel bloky*. Blok zdroj slouží jako zdroj dat a může číst z. Cílový blok fungují jako přijímač dat a je možné zapsat do. Blok Šiřitel funguje jako blok zdrojový i cílový blok a můžete být číst z a zapisovat do. Definuje TPL <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> rozhraní představují zdrojů, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> představují cíle, a <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602?displayProperty=nameWithType> představují propagators. <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>zdědí vlastnosti z obou <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Knihovna toku dat TPL poskytuje několik typů bloku předdefinované toku dat, které implementují <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, a <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> rozhraní. Tyto typy bloku toku dat jsou popsané v tomto dokumentu v části [předdefinované typy bloku toku dat](#predefined_types).  
  
### <a name="connecting-blocks"></a>Připojení bloky  
 Bloků toku dat můžete připojit k formuláři *kanály*, které jsou lineární pořadí bloků toku dat, nebo *sítě*, které jsou grafy bloků toku dat. Kanál je jednu formu sítě. V kanálu nebo sítě zdroje asynchronně rozšíří dat k cílům, jakmile tato data k dispozici. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=nameWithType> Metoda bloku toku dat zdroj odkazuje na cílový blok. Zdrojem může být propojený nula nebo více cílů; cíle může být propojený z nula nebo více zdrojů. Můžete přidat nebo odebrat bloků toku dat do nebo z kanálu nebo síti současně. Blok toku dat předdefinované typy zpracovávat všechny aspekty zabezpečení vlákna propojení a jejich oddělení.  
  
 Příklad, který se připojuje bloků toku dat k vytvoření základního kanálu, naleznete v části [návod: vytvoření kanálu toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Příklad, který se připojuje bloků toku dat, chcete-li vytvořit složitější síť, naleznete v části [návod: použití toku dat ve formulářové aplikaci Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md). Příklad, který zruší propojení cíl ze zdroje po zdroj nabízí cíl zprávy, naleznete v části [postupy: zrušení propojení bloků toku dat](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md).  
  
#### <a name="filtering"></a>Filtrování  
 Při volání <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=nameWithType> metoda propojení zdroj cíl, můžete zadat delegáta, který určuje, zda cílový blok přijme nebo odmítne zprávu na základě hodnoty této zprávy. Tento mechanismus filtrování je užitečný způsob, jak zajistit, že bloku toku dat přijímá jenom určité hodnoty. Pro většinu typů bloku předdefinované toku dat pokud blok zdroj je připojen k více bloků cíl, pokud cílový blok odmítne zprávy, zdroj nabízí zpráva Další cíl. Pořadí, ve kterém nabízí zdroj zprávy k cílům je definováno zdrojem a může lišit v závislosti na typu zdroje. Většina typů bloku zdroj zastavit nabídky zprávu po jeden cíl přijímá zprávy. Jedinou výjimkou tohoto pravidla se <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> třídy, která nabízí každou zprávu všechny cíle, i když některé cíle odmítnout zprávu. Příklad, který používá filtrování zpracovat jenom některé zprávy, naleznete v části [návod: použití toku dat ve formulářové aplikaci Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
> [!IMPORTANT]
>  Vzhledem k tomu, že každý typ bloku toku dat předdefinované zdroje zaručuje, že je v pořadí, ve kterém jsou přijaty zprávy rozšířeny, všechny zprávy musí čtení z bloku zdroje před zdrojového bloku dokáže zpracovat další zprávy. Proto při použití filtrování připojení ke zdroji více cílů se ujistěte, že každou zprávu přijme tomto bloku alespoň jeden cíl. Jinak může zablokování aplikace.  
  
### <a name="message-passing"></a>Předávání zpráv  
 Programovací model toku dat souvisí s koncept *předávání zpráv*, kde nezávislé komponenty programu vzájemnou komunikaci odesláním zprávy. Je možné rozšířit zpráv mezi součástmi aplikace k volání <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> metody k odeslání zprávy na hodnotu post bloků toku dat cílový (<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> funguje synchronně; <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> funguje asynchronně) a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>, a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A> metody pro příjem zpráv ze zdroje bloků. Tyto metody můžete kombinovat s kanály toku dat nebo sítě pomocí odesílání vstupní data k hlavnímu uzlu (cílový blok) a přijímání výstupní data z uzlu terminálu kanálu nebo terminálu uzlů sítě (jeden nebo více zdroj bloky). Můžete také <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Choose%2A> metoda číst z první zadané zdroje, které má data k dispozici a provádět akce na tato data.  
  
 Zdroj bloky nabízí data na cílové bloky voláním <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A?displayProperty=nameWithType> metoda. Cílový blok odpovídá na zprávu nabízený v jednom ze tří způsobů: dokáže přijímat zprávy, odmítnout zprávu nebo odložit zprávy. Pokud cílový přijme zprávu <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> metoda vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Accepted>. Pokud cílový odmítne zprávy, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> metoda vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Declined>. Pokud cílový vyžaduje, že už obdrží všechny zprávy ze zdroje, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.DecliningPermanently>. Typy bloku předdefinované zdrojů nenabízejí zprávy a pokuste se propojené cíle po přijetí návratovou hodnotu a budou automaticky zrušit propojení těchto cílů.  
  
 Pokud cílový blok odloží zprávu pro pozdější použití <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> metoda vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Postponed>. Cílový blok, který odloží zprávu můžete novější volání <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReserveMessage%2A?displayProperty=nameWithType> metoda můžete vyzkoušet tak, aby vyhradil nabízený zprávy. V tomto okamžiku zprávy je buď stále k dispozici a mohou být využívána cílový blok nebo zprávy byly převzaty jiný cíl. Pokud cílový blok novější vyžaduje zpráva nebo zpráva již nepotřebuje, zavolá <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReleaseReservation%2A> metoda, v uvedeném pořadí. Rezervace zpráva se obvykle používá typy bloku toku dat, které fungují v režimu typu non-greedy. Později v tomto dokumentu se vysvětluje typu non-greedy režimu. Namísto rezervování odložených zprávy, můžete také použít cílový blok <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=nameWithType> metoda se pokusit o přímo využívat odložených zprávy.  
  
### <a name="dataflow-block-completion"></a>Dokončení bloku toku dat  
 Bloky toku dat také podporují koncept *dokončení*. Blok toku dat, který je ve stavu dokončení nebude provádět žádné další práci. Každého bloku toku dat má přidruženou <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekt, označuje jako *dokončení úkolů*, která představuje stav dokončení bloku. Protože můžete počkat <xref:System.Threading.Tasks.Task> objektu ukončíte pomocí dokončení úloh, můžete počkat pro jednu nebo více uzlů Terminálové služby toku dat sítě ukončíte. <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> Definuje rozhraní <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metoda, která informuje o bloku toku dat požadavku na její dokončení, a <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> vlastnost, která vrací úloha dokončení bloku toku dat. Obě <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> dědění <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> rozhraní.  
  
 Existují dva způsoby, jak určit, zda bloku toku dat byla dokončena bez chyb, došlo k jedné nebo více chybám nebo byla zrušena. První způsob je volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metoda na dokončení úloh v `try` - `catch` blok (`Try` - `Catch` v jazyce Visual Basic). Následující příklad vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který vyvolá <xref:System.ArgumentOutOfRangeException> pokud jeho vstupní hodnota je menší než nula. <xref:System.AggregateException>se vyvolá, když v tomto příkladu volá <xref:System.Threading.Tasks.Task.Wait%2A> na dokončení úlohy. <xref:System.ArgumentOutOfRangeException> Přistupuje prostřednictvím <xref:System.AggregateException.InnerExceptions%2A> vlastnost <xref:System.AggregateException> objektu.  
  
 [!code-csharp[TPLDataflow_Overview#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#10)]
 [!code-vb[TPLDataflow_Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#10)]  
  
 Tento příklad ukazuje tento případ, ve kterém k výjimce přejde neošetřené v delegát bloku toku dat provádění. Doporučujeme vám, že zpracování výjimek v těla takové bloků. Ale pokud jste to možné, bloku se chová jako kdyby se zrušila a nezpracovává příchozí zprávy.  
  
 Když explicitně, zrušení bloku toku dat <xref:System.AggregateException> objekt obsahuje <xref:System.OperationCanceledException> v <xref:System.AggregateException.InnerExceptions%2A> vlastnost. Další informace o zrušení toku dat najdete v tématu Povolení zrušení později v tomto dokumentu.  
  
 Druhý způsob jak určit stav dokončení bloku toku dat je použití pokračování z dokončení úlohy nebo použít asynchronní jazykové funkce jazyka C# a Visual Basic asynchronně čekání na dokončení úlohy. Delegáta, který poskytnete <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metoda trvá <xref:System.Threading.Tasks.Task> objekt, který reprezentuje předchozí úlohou. U <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> vlastnost delegáta pro pokračování trvá dokončení úlohy sám sebe. V následujícím příkladu se podobá předchozímu, s tím rozdílem, že se také používá <xref:System.Threading.Tasks.Task.ContinueWith%2A> metodu pro vytvoření dokončení úlohy, která se zobrazí stav celkové toku dat operace.  
  
 [!code-csharp[TPLDataflow_Overview#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#11)]
 [!code-vb[TPLDataflow_Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#11)]  
  
 Můžete také použít vlastnosti jako <xref:System.Threading.Tasks.Task.IsCanceled%2A> v těle úkolů pokračování určit další informace o stavu dokončení bloku toku dat. Další informace o úlohách pokračování a jak se vztahují k zrušení a zpracování chyb najdete v tématu [řetězení úloh pomocí úloh pokračování pomocí](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md), [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md), [výjimky Zpracování](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md), a [NIB: postupy: zpracování výjimek vyvolaných úlohami](http://msdn.microsoft.com/library/d6c47ec8-9de9-4880-beb3-ff19ae51565d).  
  
 [[přejděte do horní části](#top)]  
  
<a name="predefined_types"></a>   
## <a name="predefined-dataflow-block-types"></a>Typy předdefinované bloku toku dat  
 Knihovna toku dat TPL poskytuje několik typů bloku toku dat předdefinované. Tyto typy jsou rozdělené do tří kategorií: *ukládání do vyrovnávací paměti bloky*, *provádění bloky*, a *seskupení bloky*. Následující části popisují typy bloku, které tvoří těchto kategorií.  
  
### <a name="buffering-blocks"></a>Ukládání do vyrovnávací paměti bloky  
 Vyrovnávací paměti bloky obsahovat data pro použití spotřebitelé dat. Knihovna toku dat TPL poskytuje tři typy bloku ukládání do vyrovnávací paměti: <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601?displayProperty=nameWithType>.  
  
#### <a name="bufferblockt"></a>BufferBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Třída reprezentuje strukturou univerzální asynchronní zasílání zpráv. Tato třída ukládá první v první out (FIFO) fronty zpráv, které mohou být zápis více zdrojů nebo číst z více cílů. Když cíl obdrží zprávu od <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu zpráva, že je odebrána z fronty zpráv. Proto i když <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objekt může mít více cílů, pouze jeden cíl obdrží každou zprávu. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Třída je užitečná, když chcete předat více zpráv na jiné komponenty, a tuto součást musí obdržet každou zprávu.  
  
 Následující příklad základní odešle několik <xref:System.Int32> hodnoty k <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objekt a potom načte tyto hodnoty zpět z tohoto objektu.  
  
 [!code-csharp[TPLDataflow_Overview#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#1)]
 [!code-vb[TPLDataflow_Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#1)]  
  
 Úplný příklad, který ukazuje, jak pro zápis zpráv do a čtení zpráv z <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu, najdete v části [postupy: zápis zpráv a čtení zpráv z bloku toku dat](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md).  
  
#### <a name="broadcastblockt"></a>BroadcastBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> Třída je užitečné, když je nutné předat více zpráv do jiné komponenty, ale je potřeba tuto součást pouze nejnovější hodnotu. Tato třída je také užitečné, pokud chcete k vysílání zprávy, která se víc součástí.  
  
 V následujících příspěvcích základních příkladů <xref:System.Double> hodnotu <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> objekt a potom čtení, které zálohují hodnotu z tohoto objektu několikrát. Protože hodnoty nejsou odebrány z <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> objekty po jejich přečtení, stejnou hodnotu je k dispozici pokaždé, když.  
  
 [!code-csharp[TPLDataflow_Overview#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#2)]
 [!code-vb[TPLDataflow_Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#2)]  
  
 Úplný příklad, který ukazuje, jak používat <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> k vysílání zprávy, která se více bloků cíl, najdete v části [postupy: určení plánovače úloh v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md).  
  
#### <a name="writeonceblockt"></a>WriteOnceBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> Vypadá takto: Třída <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> třídy, vyjma toho, že <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu je možné zapsat do pouze jednou. Si můžete představit <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> , že je podobná jazyka C# [jen pro čtení](~/docs/csharp/language-reference/keywords/readonly.md) ([jen pro čtení](~/docs/visual-basic/language-reference/modifiers/readonly.md) v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) – klíčové slovo, vyjma toho, že <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu bude neměnné, když obdrží hodnotu místo na vytváření. Podobně jako <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> třída, když cíl obdrží zprávu od <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu, zprávy se neodebere z tohoto objektu. Proto více cílů obdrží kopii zprávy. <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> Třída je užitečná, pokud chcete rozšířit pouze první z více zpráv.  
  
 Následující příklad základní odešle více <xref:System.String> hodnoty k <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt a potom čtení hodnota zpět z tohoto objektu. Protože <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu je možné zapsat do jednou pouze po <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt přijme nějakou zprávu, zahodí dalších zpráv.  
  
 [!code-csharp[TPLDataflow_Overview#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#3)]
 [!code-vb[TPLDataflow_Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#3)]  
  
 Úplný příklad, který ukazuje, jak používat <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> zobrazí hodnotu první operaci, která se dokončí, najdete v tématu [postupy: zrušení propojení bloků toku dat](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md).  
  
### <a name="execution-blocks"></a>Provádění bloky  
 Bloky provádění volání delegáta zadaný uživatelem pro každého jednotlivého přijatá data. Knihovna toku dat TPL poskytuje tři typy spuštění bloku: <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.  
  
#### <a name="actionblockt"></a>ActionBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Třída je cílový blok, který volá delegáta, když obdrží data. Představte si, že <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu jako delegáta, který se spustí asynchronně v případě, že data bude možné. Delegáta, který poskytnete <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt může být typu <xref:System.Action> nebo typ `System.Func\<TInput, Task>`. Když použijete <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu s <xref:System.Action>, zpracování jednotlivé elementy vstupu je považovány za dokončené, když se vrátí delegáta. Když použijete <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu s `System.Func\<TInput, Task>`, zpracování jednotlivé elementy vstupu považuje za dokončené pouze tehdy, když vrácený <xref:System.Threading.Tasks.Task> dokončení objektu. Pomocí těchto dvou mechanismů, můžete použít <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> pro jednotlivé elementy vstupu synchronní a asynchronní zpracování.  
  
 Následující příklad základní odešle více <xref:System.Int32> hodnoty k <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objekt vytiskne tyto hodnoty do konzoly. Tento příklad poté nastaví bloku na stavu dokončení a čeká na dokončení všech úloh toku dat.  
  
 [!code-csharp[TPLDataflow_Overview#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#4)]
 [!code-vb[TPLDataflow_Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#4)]  
  
 Pro dokončení příklady, které ukazují, jak používat delegáty s <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> třídy najdete v tématu [postup: provedení akce při toku dat bloku obdrží Data](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md).  
  
#### <a name="transformblocktinput-toutput"></a>TransformBlock (TInput, TOutput)  
 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Vypadá takto: Třída <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> třídy, s tím rozdílem, že funguje jako obou zdroj a jako cíl. Delegáta, který můžete předat <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt vrátí hodnotu typu `TOutput`. Delegáta, který poskytnete <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt může být typu `System.Func<TInput, TOutput>` nebo typ `System.Func<TInput, Task>`. Při použití <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu s `System.Func\<TInput, TOutput>`, zpracování jednotlivé elementy vstupu je považovány za dokončené, když se vrátí delegáta. Při použití <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt používaný s `System.Func<TInput, Task<TOutput>>`, zpracování jednotlivé elementy vstupu považuje za dokončené pouze tehdy, když vrácený <xref:System.Threading.Tasks.Task> dokončení objektu. Stejně jako u <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, pomocí těchto dvou mechanismů, můžete použít <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pro jednotlivé elementy vstupu synchronní a asynchronní zpracování.  
  
 Následující příklad základní vytvoří <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt, který vypočítá druhou odmocninu čísla vstupem. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Objektu trvá <xref:System.Int32> hodnoty jako vstup a vytváří <xref:System.Double> hodnoty jako výstup.  
  
 [!code-csharp[TPLDataflow_Overview#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#5)]
 [!code-vb[TPLDataflow_Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#5)]  
  
 Pro dokončení příklady, které používá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> v síti bloků toku dat, který provádí zpracování obrázků v aplikaci Windows Forms, najdete v části [návod: použití toku dat ve formulářové aplikaci Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
#### <a name="transformmanyblocktinput-toutput"></a>TransformManyBlock (TInput, TOutput)  
 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> Vypadá takto: Třída <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> třídy, vyjma toho, že <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> vytváří nula nebo více hodnot výstup pro každý vstupní hodnotu, místo jen jednu výstupní hodnotu pro každý vstupní hodnoty. Delegáta, který poskytnete <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekt může být typu `System.Func<TInput, IEnumerable<TOutput>>` nebo `type System.Func<TInput, Task<IEnumerable<TOutput>>>`. Při použití <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objektu s `System.Func<TInput, IEnumerable<TOutput>>`, zpracování jednotlivé elementy vstupu je považovány za dokončené, když se vrátí delegáta. Při použití <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objektu s `System.Func<TInput, Task<IEnumerable<TOutput>>>`, zpracování jednotlivé elementy vstupu považuje za dokončení pouze tehdy, když vrácený `System.Threading.Tasks.Task<IEnumerable<TOutput>>` dokončení objektu.  
  
 Následující příklad základní vytvoří <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objektu, která rozdělí řetězce na jejich pořadí jednotlivých znak. <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> Objektu trvá <xref:System.String> hodnoty jako vstup a vytváří <xref:System.Char> hodnoty jako výstup.  
  
 [!code-csharp[TPLDataflow_Overview#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#6)]
 [!code-vb[TPLDataflow_Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#6)]  
  
 Pro dokončení příklady, které používají <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> Pokud chcete vytvořit několik nezávislých výstupů pro každý vstupní v kanálu toku dat, přečtěte si téma [návod: vytvoření kanálu toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md).  
  
#### <a name="degree-of-parallelism"></a>Stupně paralelního zpracování  
 Každý <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> vyrovnávací paměti objektu vstupní zprávy, dokud blok je připraven pro jejich zpracování. Ve výchozím nastavení tyto třídy zpracování zpráv v pořadí, ve kterém jsou přijata, jednu zprávu současně. Můžete také zadat stupně paralelního zpracování povolit <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekty, které chcete zpracovat více zpráv souběžně. Další informace o souběžné provádění najdete v části určení stupně stupně paralelního zpracování později v tomto dokumentu. Příklad, který nastaví stupně paralelního zpracování povolit bloku toku dat provádění zpracovat více než jeden zprávu najednou, naleznete v části [postupy: určení stupně paralelismus v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md).  
  
#### <a name="summary-of-delegate-types"></a>Souhrn typů delegátů.  
 Následující tabulka shrnuje typy delegáta, které můžou poskytnout <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekty. Tato tabulka také určuje, zda typ delegáta pracuje synchronně nebo asynchronně.  
  
|Typ|Typ synchronní delegáta|Typ asynchronní delegáta|  
|----------|-------------------------------|--------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|`System.Action`|`System.Func\<TInput, Task>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|`System.Func\<TInput, TOutput>`2`|`System.Func<TInput, Task<TOutput>>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|`System.Func<TInput, IEnumerable<TOutput>>`|`System.Func<TInput, Task<IEnumerable<TOutput>>>`|  
  
 Lambda – výrazy můžete použít také při práci s typy spuštění bloku. Příklad ukazuje, jak pomocí výrazu lambda bloku spuštění, naleznete v části [postup: provedení akce při toku dat bloku obdrží Data](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md).  
  
### <a name="grouping-blocks"></a>Seskupení bloky  
 Seskupení bloky kombinovat data z jednoho nebo více zdrojů a v rámci různých omezení. Knihovna toku dat TPL poskytuje tři bloku typy připojení: <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>, a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>.  
  
#### <a name="batchblockt"></a>BatchBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> Třída kombinuje sady vstupních dat, která se označuje jako dávky, do pole výstupní data. Zadejte velikost každé dávce, při vytváření <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu. Když <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt dostane zadaný počet elementů vstupu, se asynchronně rozšíří na pole, které obsahují tyto elementy. Pokud <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu je nastaven na stavu dokončení, ale neobsahuje dostatečný počet elementů k vytvoření dávky, se rozšíří na konečné pole, které obsahuje zbývající elementy vstupu.  
  
 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> Třída funguje buď *typu greedy* nebo *typu non-greedy* režimu. V typu greedy režimu, který je výchozím nastavením, <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt přijímá všechny zprávy o se nabízí a rozšíří na pole po přijetí zadaný počet elementů. V typu non-greedy režimu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt odloží všechny příchozí zprávy, dokud dostatek zdrojů nabídl zpráv do bloku na formuláři dávce. Typu greedy režim obvykle provádí lépe než typu non-greedy režimu protože vyžaduje méně zpracování režie. Když je třeba koordinovat spotřeby z více zdrojů v atomic způsobem, ale můžete použít typu non-greedy režim. Určení typu non-greedy režimu nastavením <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> k `False` v `dataflowBlockOptions` parametr ve <xref:System.Threading.Tasks.Dataflow.BatchBlock%601.%23ctor%2A> konstruktor.  
  
 Následující příklad základní odešle několik <xref:System.Int32> hodnoty k <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt, který obsahuje deset elementy v dávce. Zaručit, že všechny hodnoty šířit z <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, volá v tomto příkladu <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metoda. <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> Metoda nastaví <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt, který chcete stavu dokončení a proto <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt rozšíří na všechny zbývající elementy jako poslední dávky.  
  
 [!code-csharp[TPLDataflow_Overview#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#7)]
 [!code-vb[TPLDataflow_Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#7)]  
  
 Úplný příklad používající <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> zlepšit efektivitu databázových operací vložení, najdete v tématu [návod: použití tříd BatchBlock a BatchedJoinBlock pro zlepšení efektivity](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md).  
  
#### <a name="joinblockt1-t2-"></a>Třídy JoinBlock (T1, T2,...)  
 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> třídy shromažďovat elementy vstupu a šířit se <xref:System.Tuple%602?displayProperty=nameWithType> nebo <xref:System.Tuple%603?displayProperty=nameWithType> objekty, které obsahují tyto elementy. <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> nedědí z třídy <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>. Místo toho poskytují vlastnosti, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target1%2A>, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target2%2A>, a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603.Target3%2A>, které implementují <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Jako <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> fungovat v režimu typu greedy nebo typu non-greedy. V typu greedy režimu, který je výchozím nastavením, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nebo <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objekt přijímá všechny zprávy o se nabízí a šíří se řazené kolekce členů po každé jeho cílů obdrží minimálně jednu zprávu. V typu non-greedy režimu <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nebo <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objekt odloží všechny příchozí zprávy, dokud všechny cíle byly nabídnuty data, která je potřeba vytvořit řazené kolekce členů. V tomto okamžiku bloku mezi protokolu dvoufázového potvrzení atomicky načíst všechny požadované položky ze zdroje. Tato odložení umožňuje jinou entitou využívat data do té doby, aby celého systému, aby postup směrem vpřed.  
  
 Následující základní příklad ukazuje případ, ve kterém <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objekt vyžaduje více dat k výpočtu hodnoty. Tento příklad vytvoří <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objekt, který vyžaduje dva <xref:System.Int32> hodnoty a <xref:System.Char> hodnota při provádění aritmetických operací.  
  
 [!code-csharp[TPLDataflow_Overview#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#8)]
 [!code-vb[TPLDataflow_Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#8)]  
  
 Úplný příklad používající <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objektů v režimu typu non-greedy spolupráce při sdílení prostředku, najdete v části [postupy: použití třídy JoinBlock pro čtení dat z více zdrojů](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md).  
  
#### <a name="batchedjoinblockt1-t2-"></a>BatchedJoinBlock (T1, T2,...)  
 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%603> třídy shromažďovat dávek elementů vstupu a šířit se `System.Tuple(IList(T1), IList(T2))` nebo `System.Tuple(IList(T1), IList(T2), IList(T3))` objekty, které obsahují tyto elementy. Představte si, že <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> jako kombinace <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>. Zadejte velikost každé dávce, když vytvoříte <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objektu. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>poskytuje také vlastnosti, <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A>, které implementují <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>. Při přijímání zadaný počet elementů vstupu z napříč všechny cíle, <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objekt asynchronně šíří se `System.Tuple(IList(T1), IList(T2))` objekt, který obsahuje těchto elementů.  
  
 Následující příklad základní vytvoří <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objekt, který obsahuje výsledky, <xref:System.Int32> hodnoty a chyby, které jsou <xref:System.Exception> objekty. Tento příklad provádí více operací a zapíše výsledky <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A> vlastnost a jestli nedošlo k chybám <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A> vlastnost z <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objektu. Protože je počet úspěšných a neúspěšných operací Neznámá předem, <xref:System.Collections.Generic.IList%601> objekty povolit každém cíli přijímat nula nebo více hodnot.  
  
 [!code-csharp[TPLDataflow_Overview#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#9)]
 [!code-vb[TPLDataflow_Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#9)]  
  
 Úplný příklad používající <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Pokud chcete zachytit výsledky a jakékoli výjimky, ke kterým dojde během program načte z databáze, přečtěte si téma [návod: použití tříd BatchBlock a BatchedJoinBlock pro zlepšení efektivity](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md).  
  
 [[přejděte do horní části](#top)]  
  
<a name="behavior"></a>   
## <a name="configuring-dataflow--block-behavior"></a>Konfigurace chování bloku toku dat  
 Můžete povolit další možnosti tím, že poskytuje <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=nameWithType> objektu do konstruktoru objektu typy bloku toku dat. Tyto možnosti určují chování těchto Plánovač spravující základní úlohy a stupně paralelního zpracování. <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions> Má také odvozených typů, které určují chování, která je specifická pro určité typy bloku toku dat. Následující tabulka shrnuje, které možnosti typ se přidruží každý typ bloku toku dat.  
  
|Typ bloku toku dat|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>Typ|  
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
  
 Následující části obsahují další informace o důležitých druhy toku dat bloku možnosti, které jsou k dispozici prostřednictvím <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions?displayProperty=nameWithType> třídy.  
  
### <a name="specifying-the-task-scheduler"></a>Určení plánovače úloh  
 Každý blok předdefinované toku dat používá mechanismus pro aktivity, například rozmnožovací dat na cílový, příjem dat ze zdroje a spuštěné uživatelem definované Delegáti v případě, že data bude možné provést plánování úloh TPL. <xref:System.Threading.Tasks.TaskScheduler>je abstraktní třída, která představuje plánovače úloh této fronty úloh do vláken. Plánovač úloh výchozí, <xref:System.Threading.Tasks.TaskScheduler.Default%2A>, používá <xref:System.Threading.ThreadPool> třídy fronty a spouštět pracovní. Plánovač úloh výchozí můžete přepsat pomocí nastavení <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> při vytvoření objektu bloku toku dat.  
  
 Pokud stejný Plánovač úloh spravuje více bloků toku dat, ho můžete vynutit zásady mezi nimi. Například, pokud každý více bloků toku dat jsou nakonfigurované pro výhradní Plánovač stejného <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu, všechny fungovat, že je serializováno spustí mezi tyto bloky. Podobně pokud jsou tyto bloky nakonfigurované pro cílové souběžných Plánovač stejného <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objekt a že scheduler je nakonfigurován tak, aby měl souběžnosti maximální úroveň, všechny pracovní z těchto bloků je omezená na tento počet souběžných operací. Pro příklad, který používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> třída pro povolení operací čtení být provedeny souběžně, ale operací dojít výhradně všech ostatních operací, najdete v článku zápisu [postupy: určení plánovače úloh v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md). Další informace o plánovače úloh v TPL najdete v tématu <xref:System.Threading.Tasks.TaskScheduler> třída tématu.  
  
### <a name="specifying-the-degree-of-parallelism"></a>Určení stupně paralelního zpracování  
 Ve výchozím nastavení jsou tři provádění bloku typy, které poskytuje knihovna toku dat TPL, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>, jednu zprávu zpracovat najednou. Tyto typy bloku toku dat také zpracování zpráv v pořadí, ve kterém jsou přijaty. Chcete-li povolit tyto bloků toku dat ke zpracování zpráv souběžně, nastavte <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> při sestavení objektu bloku toku dat.  
  
 Výchozí hodnota <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> je 1, což zaručuje, že bloku toku dat zpracovává jednu zprávu najednou. Nastavení této vlastnosti na hodnotu, která je větší než 1 umožňuje bloku toku dat současně zpracovat více zpráv. Nastavení této vlastnosti na <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=nameWithType> umožňuje základní Plánovač úloh pro správu Maximální stupeň souběžnosti.  
  
> [!IMPORTANT]
>  Při zadání maximálního stupně paralelního zpracování, která je větší než 1 současně zpracování několika zpráv, a proto nemusí zprávy zpracovány v pořadí, ve kterém jsou přijaty. Pořadí, ve kterém zprávy jsou výstupem bude bloku, ale, správné seřazení.  
  
 Protože <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnost představuje maximální stupně paralelního zpracování, bloku toku dat může spustit s nižší úrovní stupně paralelního zpracování, než jste určili. Bloku toku dat může použít v menší míře paralelismus jeho funkční splnění nebo protože je nedostatek dostupné prostředky systému. Blok toku dat nikdy zvolí další paralelismus než zadáte.  
  
 Hodnota <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnost je určena výhradně pro každý objekt bloku toku dat. Například pokud všechny čtyři bloku objekty toku dat zadat 1 pro maximální stupně paralelního zpracování, všechny čtyři objekty bloku toku dat může potenciálně běžet paralelně.  
  
 Příklad, který nastaví maximální stupně paralelního zpracování pro povolení operací zdlouhavé proběhnout paralelně, naleznete v části [postupy: určení stupně paralelismus v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md).  
  
### <a name="specifying-the-number-of-messages-per-task"></a>Určující počet zpráv za úloh  
 Typy bloku toku dat předdefinované používat ke zpracování více elementy vstupu úlohy. Tím se může minimalizovat počet úloh objekty, které jsou potřebné ke zpracování dat, která umožňuje aplikacím efektivněji. Ale pokud úlohy z jednu sadu bloků toku dat jsou zpracování dat, úlohy z jiných bloků toku dat může být potřeba čekat na doba zpracování pomocí služby Řízení front zpráv. Chcete-li povolit lepší rovné zacházení s úlohy toku dat, nastavte <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> vlastnost. Když <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> je nastaven na <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=nameWithType>, který je výchozí, úloha používá bloku toku dat zpracovává tolik zprávy, protože nejsou k dispozici. Když <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> nastavena na hodnotu s výjimkou <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded>, bloku toku dat zpracovává maximálně tento počet zpráv za <xref:System.Threading.Tasks.Task> objektu. I když nastavení <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> vlastnost zvýšit rovné zacházení s úkoly, může to způsobit systému vytvořte další úkoly, než je potřeba, což může snížit výkon.  
  
### <a name="enabling-cancellation"></a>Povolení zrušení  
 TPL poskytuje mechanismus, který umožňuje úlohy pro koordinaci zrušení spolupráci způsobem. Chcete-li povolit bloků toku dat se účastnit tento mechanismus zrušení, nastavte <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost. Pokud to <xref:System.Threading.CancellationToken> objektu nastavena na stav zrušených, všechny bloky toku dat, které sledují tento token dokončí provádění své aktuální položky, ale není spuštěno zpracování další položky. Tyto bloků toku dat také zrušte všechny uložená do vyrovnávací paměti zprávy, verze připojení na žádný zdroj a cíl bloky a přechod do stavu zrušena. Pomocí přechodu do zrušené stavu, <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> vlastnost má <xref:System.Threading.Tasks.Task.Status%2A> vlastnost nastavena na hodnotu <xref:System.Threading.Tasks.TaskStatus.Canceled>, pokud došlo k výjimce během zpracování. V takovém případě <xref:System.Threading.Tasks.Task.Status%2A> je nastaven na <xref:System.Threading.Tasks.TaskStatus.Faulted>.  
  
 Příklad, který ukazuje, jak používat zrušení v aplikaci Windows Forms, naleznete v části [postupy: zrušení bloku toku dat](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md). Další informace o zrušení v TPL najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="specifying-greedy-versus-non-greedy-behavior"></a>Určení typu Greedy Versus chování typu Non-Greedy  
 Několik typů bloku toku dat seskupení může fungovat v obou *typu greedy* nebo *typu non-greedy* režimu. Ve výchozím nastavení typy bloku toku dat předdefinované pracovat v typu greedy režimu.  
  
 Pro připojení k blokování typů <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>, typu greedy režimu znamená, že bloku okamžitě přijímá data i v případě, že odpovídající data, ke které má být připojení k ještě nejsou k dispozici. Typu non-greedy režimu znamená, že bloku odloží všechny příchozí zprávy, dokud je k dispozici na všech jeho cíle k dokončení spojení. Pokud některá z odložených zprávy již nebudou k dispozici, spojení bloku uvolní všech odložených zprávy a restartování procesu. Pro <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídy, typu greedy a typu non-greedy chování je podobné, vyjma toho, že v typu non-greedy režimu, <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt odloží všechny příchozí zprávy, dokud dostatek jsou dostupné z různých zdrojů k dokončení dávky.  
  
 Chcete-li zadat typu non-greedy režim pro bloku toku dat, nastavte <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> k `False`. Příklad, který ukazuje, jak používat typu non-greedy režim povolit více připojení k bloků efektivněji sdílet zdroj dat, naleznete v části [postupy: použití třídy JoinBlock pro čtení dat z více zdrojů](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md).  
  
 [[přejděte do horní části](#top)]  
  
<a name="custom"></a>   
## <a name="custom-dataflow-blocks"></a>Vlastních bloků toku dat  
 Přestože knihovna toku dat TPL poskytuje mnoho typů předdefinované blok, můžete vytvořit další blok typy, které provádějí vlastní chování. Implementace <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nebo <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> přímo rozhraní nebo pomocí <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metoda pro vytvoření komplexní blok, který zapouzdřuje chování existující typy bloku. Příklady, které ukazují, jak implementovat funkci bloku toku dat vlastního najdete v tématu [návod: vytvoření vlastní typ bloku toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md).  
  
 [[přejděte do horní části](#top)]  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Zápis zpráv do bloku toku dat a čtení zpráv z bloku toku dat](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md)|Ukazuje, jak pro zápis zpráv do a čtení zpráv z <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu.|  
|[Postupy: Implementace vzoru toku dat producent–příjemce](../../../docs/standard/parallel-programming/how-to-implement-a-producer-consumer-dataflow-pattern.md)|Popisuje, jak použít model toku dat implementace vzoru producent – příjemce, které autor odešle zprávy do bloku toku dat a příjemce čte zprávy z tohoto bloku.|  
|[Postupy: Provádění akcí po přijetí dat do bloku toku dat](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)|Popisuje, jak poskytnout delegáti typy bloku toku dat provádění, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>.|  
|[Návod: Vytvoření kanálu toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)|Popisuje postup vytvoření kanálu toku dat, který stahuje text z webu a provádí operace na tomto textu.|  
|[Postupy: Zrušení propojení bloků toku dat](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)|Ukazuje, jak používat <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metoda zrušení propojení cílový blok z její zdroj po zdroj nabízí zprávu do cílové.|  
|[Návod: Použití toku dat v aplikaci Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)|Ukazuje, jak vytvořit síť bloků toku dat, které provádějí zpracování obrázků v aplikaci Windows Forms.|  
|[Postupy: Zrušení bloku toku dat](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)|Ukazuje, jak používat zrušení v aplikaci Windows Forms.|  
|[Postupy: Načítání dat z více zdrojů pomocí třídy JoinBlock](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)|Vysvětluje, jak používat <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> třída k provedení určité operace, pokud jsou k dispozici data z více zdrojů a jak používat typu non-greedy režim povolit více připojení k bloků sdílet zdroj dat efektivněji.|  
|[Postupy: Určení stupně paralelního zpracování v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)|Popisuje, jak nastavit <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnost umožňující bloku toku dat provádění zpracovat více než jeden zprávu najednou.|  
|[Postupy: Určení plánovače úloh v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)|Ukazuje, jak přidružit plánovače úloh konkrétní při použití toku dat ve vaší aplikaci.|  
|[Návod: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)|Popisuje způsob použití <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třída zlepšit efektivitu databáze vložit operace a jak používat <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třída zaznamenat výsledky a jakékoli výjimky, ke kterým dojde během program načte z databáze.|  
|[Návod: Vytvoření bloku toku dat vlastního typu](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)|Ukazuje dva způsoby, jak vytvořit typ bloku toku dat, který implementuje vlastní chování.|  
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Představuje rozhraní TPL knihovnu, která zjednodušuje paralelní a souběžné programování v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikace.|
