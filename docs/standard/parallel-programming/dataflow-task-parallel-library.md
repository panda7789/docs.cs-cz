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
ms.openlocfilehash: 7058e7857c03a2fc82a3d978ef7c8066a9e272bc
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589651"
---
# <a name="dataflow-task-parallel-library"></a>Tok dat (Task Parallel Library)
<a name="top"></a> Task Parallel Library (TPL) poskytuje součásti toku dat a pomáhá tak zvýšit odolnost aplikace pro práci s souběžnosti. Tyto součásti toku dat se souhrnně označují jako *Knihovna TPL datového toku*. Tento model toku dat podporuje programování založené na objektu actor pomocí poskytující zprávy v procesu předávání pro hrubých toku dat a paralelní zpracování úloh. Sestavení na typy a plánování infrastruktury TPL součásti toku dat a integrovat C#, Visual Basic a F# jazykovou podporu pro asynchronní programování. Tyto součásti toku dat jsou užitečné v případě, že máte více operací, které musí komunikovat mezi sebou asynchronně, nebo pokud chcete zpracovávat data, jakmile je k dispozici. Zvažte například aplikaci, která zpracovává data bitové kopie z webové kamery. Pomocí vzoru toku dat aplikace dokáže zpracovat bitové kopie snímků, jakmile budou k dispozici. Pokud aplikace rozšiřuje bitové kopie snímků, například tím, že provádí světla opravy nebo červených snížení, můžete vytvořit *kanálu* toku dat komponent. Každá fáze kanálu může používat další funkce paralelismu hrubých, například funkce, která je poskytována TPL k transformaci na obrázku.  
  
 Tento dokument obsahuje přehled Knihovna TPL datového toku. Popisuje programovací model, typy bloků předdefinovaných toku dat a jak nakonfigurovat bloků toku dat podle specifických požadavků vašich aplikací.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
 Tento dokument obsahuje následující části:  
  
- [Programovací Model](#model)  
  
- [Typy bloků předdefinovaných toku dat](#predefined_types)  
  
- [Konfigurace chování bloku toku dat](#behavior)  
  
- [Vlastních bloků toku dat](#custom)  
  
<a name="model"></a>   
## <a name="programming-model"></a>Programovací model  
 Knihovna TPL datového toku poskytuje základ pro zprávu, předávání a paralelním zpracováním náročnou na procesor a jsem vstupně-výstupními operacemi aplikace, které mají vysokou propustností a nízkou latencí. Také poskytuje explicitní kontrolu nad jak data do vyrovnávací paměti a stojí v systému. Abyste lépe pochopili programovací model toku dat, vezměte v úvahu aplikace, která asynchronně načítá obrázky z disku a vytvoří složeného těchto imagí. Tradiční programovacích modelů obvykle je nutné použít zpětná volání a synchronizaci objektů, jako je například uzamčení, koordinace úloh a přístup ke sdíleným datům. Programovací model toku dat můžete vytvořit tok dat objektů, které zpracování obrázků, jako jsou čtení z disku. V rámci modelu toku dat je deklarovat způsobu zpracování dat až bude k dispozici a také všechny závislosti mezi daty. Vzhledem k tomu, že modul runtime spravují závislosti mezi daty, často se můžete vyhnout požadavek na synchronizaci přístupu ke sdíleným datům. Navíc vzhledem k tomu, že modul runtime plánuje práci podle asynchronní přijetí dat, toku dat lze zvýšit rychlost odezvy a propustnost efektivní správa základní vlákna. Příklad používá programovací model toku dat k implementaci zpracování obrázků v aplikaci Windows Forms, naleznete v tématu [názorný postup: Použití toku dat v Windows Forms aplikace](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
### <a name="sources-and-targets"></a>Zdroje a cíle  
 Knihovna TPL datového toku se skládá z *bloků toku dat*, které jsou data struktury dat vyrovnávací paměti a procesů. Definuje tři typy bloků toku dat TPL: *zdrojové bloky*, *cílové bloky*, a *Šiřitel bloky*. Zdrojový slouží jako zdroj dat a můžete číst z. Cílový blok fungují jako přijímač dat a je možné zapisovat na. Propagátor funguje jako zdrojový i cílový blok a může být čte a zapisuje do. Definuje TPL <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> rozhraní pro reprezentaci zdroje, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> představující cíle, a <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602?displayProperty=nameWithType> představující propagators. <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> zdědí vlastnosti z obou <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Knihovna TPL datového toku poskytuje několik typů bloků předdefinovaných toku dat, které implementují <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, a <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> rozhraní. Tyto typy bloků toku dat jsou popsané v tomto dokumentu v části [předdefinovaných typů bloků toku dat](#predefined_types).  
  
### <a name="connecting-blocks"></a>Připojování blokuje  
 Bloků toku dat se můžete připojit k formuláři *kanály*, které jsou lineární posloupnosti bloků toku dat, nebo *sítě*, které jsou grafy bloků toku dat. Kanál je jeden formulář sítě. V kanálu nebo síťové zdroje asynchronně šířit data do cíle jako tato data k dispozici. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=nameWithType> Metoda odkazuje bloku toku dat zdrojového na cílový blok. Zdrojem může být propojený nula nebo více cílů; cíle lze propojit z nuly nebo více zdrojů. Můžete přidat nebo odebrat bloků toku dat do nebo z kanálu nebo síti současně. Blok toku dat předdefinované typy zpracovat všechny aspekty zabezpečení vlákna propojení a rušení propojení.  
  
 Příklad, který se připojuje bloků toku dat a vytvoří základní kanál, naleznete v tématu [názorný postup: Vytvoření kanálu toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Příklad, který se připojuje bloků toku dat k vytvoření složitějších sítě, naleznete v tématu [názorný postup: Použití toku dat v Windows Forms aplikace](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md). Příklad, který nebude odpojen cíl ze zdroje po zdroj nabízí cíl zprávy, naleznete v tématu [jak: Zrušení propojení bloků toku dat](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md).  
  
#### <a name="filtering"></a>Filtrování  
 Při volání <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=nameWithType> metoda propojit zdroje do cíle, můžete zadat delegáta, který určuje, zda cílový blok přijme nebo odmítne zprávy na základě hodnoty této zprávy. Tento mechanismus filtrování je užitečný způsob, jak zajistit, že bloku toku dat přijímá jenom konkrétní hodnoty. Pro většinu typů bloků předdefinovaných toku dat Pokud zdrojový blok je připojen k několika cílovým blokům, když cílový blok odmítne zprávy, nabízí zdroj této zprávy do další cíle. Pořadí, ve kterém zdroj nabízí zprávy do cíle je definován ve zdroji a může lišit v závislosti typu zdroje. Většina typů bloků zdroj zastavit nabídky zprávu po tuto zprávu přijme jeden cíl. Jedinou výjimkou tohoto pravidla je <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> třída, která nabízí každou zprávu pro všechny cíle, i když některé cíle odmítnout zprávu. Příklad, který používá filtrování ke zpracování jen některé zprávy, naleznete v tématu [názorný postup: Použití toku dat v Windows Forms aplikace](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
> [!IMPORTANT]
>  Každý typ bloku toku dat předdefinovaného zdroje zaručuje, že jsou zprávy šířen mimo v pořadí, ve kterém jsou přijímány, všechny zprávy musí čtení z zdrojovým blokem, než zdrojový blok může zpracovávat další zprávu. Proto pokud použijete filtrování pro připojení ke zdroji více cílů, ujistěte se, že daný blok minimálně jeden cíl dostane každá zpráva. V opačném případě může být zablokování aplikace.  
  
### <a name="message-passing"></a>Předávání zpráv  
 Programovací model toku dat má vztah k konceptu *předávání zpráv*, kde nezávislé komponenty aplikace komunikovat mezi sebou odesíláním zpráv. Jedním ze způsobů šíření zpráv mezi součástmi aplikace je volání <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> metody pro odeslání zprávy na cíl příspěvek bloků toku dat (<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> pracuje synchronně, hodnota <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> funguje asynchronně) a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>, a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A> metody pro příjem zpráv z zdrojové bloky. Tyto metody můžete kombinovat s kanály toku dat nebo sítě tak, že odesílání vstupní data k hlavnímu uzlu (cílový blok) a přijímání dat výstup z terminálu uzel kanálu nebo terminálu uzlů sítě (jeden nebo více zdrojových bloků). Můžete také použít <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Choose%2A> metodu za účelem čtení z první zadané zdroje, které je k dispozici data a provádět akce na těchto datech.  
  
 Zdrojové bloky nabízí data na cílových bloků voláním <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A?displayProperty=nameWithType> metody. Cílový blok odpoví na zprávu nabízené v jednom ze tří způsobů: dokáže přijmout zprávu, odmítnout zprávu nebo odložit zprávu. Pokud cíl přijímá zprávy, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> metoda vrátí hodnotu <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Accepted>. Když cílový odmítne zprávy, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> metoda vrátí hodnotu <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Declined>. Pokud cílový vyžaduje, že již přijímá všechny zprávy ze zdroje, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.DecliningPermanently>. Typy bloků předdefinovaných zdroj nenabízejí zprávy na propojené cíle po přijetí návratovou hodnotu a jsou automaticky odpojte ho od těchto cílů.  
  
 Když cílový blok odloží zprávu pro pozdější použití <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> vrátí metoda <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Postponed>. Později můžete volat cílový blok, který odloží zprávu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReserveMessage%2A?displayProperty=nameWithType> metoda se pokouší rezervovat nabízené zprávy. V tomto okamžiku zprávě je buď stále k dispozici a je možné cílový blok nebo zpráva má zabrané jiný cíl. Když cílový blok novější vyžaduje zprávy nebo už nepotřebuje zprávy, zavolá <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReleaseReservation%2A> metoda, v uvedeném pořadí. Rezervace zprávy je obvykle používán typů bloků toku dat, které působí v režimu bez metody greedy. Bez metody greedy režimu je vysvětleno dále v tomto dokumentu. Místo rezervace odloženou zprávu, můžete také použít cílový blok <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=nameWithType> metoda pokus o přímo využívat odloženou zprávu.  
  
### <a name="dataflow-block-completion"></a>Dokončení bloku toku dat  
 Bloků toku dat také podporují koncept *dokončení*. Blok toku dat, který je v dokončeném stavu neprovádí žádné další práce. Každý blok toku dat má přiřazený <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objektu, známý jako *dokončení úkolu*, který představuje stav dokončení bloku. Protože můžete počkat <xref:System.Threading.Tasks.Task> objektu dokončete pomocí úlohy dokončení může čekat na jeden nebo více terminálu uzlů toku dat sítě dokončete. <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> Rozhraní definuje <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metoda, která informuje o bloku toku dat požadavku na její dokončení, a <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> vlastnost, která vrací dokončení úloh pro blok toku dat. Obě <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> dědit <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> rozhraní.  
  
 Existují dva způsoby, jak určit, zda blok toku dat dokončena bez chyb, došlo k jedné nebo více chybám nebo byla zrušena. První způsob je volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metoda na dokončení úkolu v `try` - `catch` blok (`Try` - `Catch` v jazyce Visual Basic). Následující příklad vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který vyvolá <xref:System.ArgumentOutOfRangeException> pokud jeho vstupní hodnota je menší než nula. <xref:System.AggregateException> je vyvolána, když v tomto příkladu volá <xref:System.Threading.Tasks.Task.Wait%2A> na dokončení úkolu. <xref:System.ArgumentOutOfRangeException> Je přístupný prostřednictvím <xref:System.AggregateException.InnerExceptions%2A> vlastnost <xref:System.AggregateException> objektu.  
  
 [!code-csharp[TPLDataflow_Overview#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#10)]
 [!code-vb[TPLDataflow_Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#10)]  
  
 Tento příklad ukazuje případ, ve kterém k výjimce zůstane nezpracovaná v delegáta z bloku toku dat provádění. Doporučujeme vám, že zpracování výjimek v těla tyto bloky. Ale pokud nemůžete udělat, bloku chová, jako je zrušený a nezpracovává příchozí zprávy.  
  
 Při explicitně, zrušení bloku toku dat <xref:System.AggregateException> objekt obsahuje <xref:System.OperationCanceledException> v <xref:System.AggregateException.InnerExceptions%2A> vlastnost. Další informace o zrušení toku dat najdete v tématu [povolení zrušení](#enabling-cancellation) oddílu.  
  
 Druhým způsobem určit stav dokončení bloku toku dat je použití pokračování dokončení úkolu nebo použití asynchronních jazykových funkcí jazyka C# a Visual Basic asynchronně čekání na dokončení úkolu. Delegát, který poskytnete <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> přijímá metodu <xref:System.Threading.Tasks.Task> objekt, který reprezentuje předchozí úlohy. V případě třídy <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> vlastnosti delegáta pro pokračování má vlastní úloha dokončení. Následující příklad se podobá předchozímu, s tím rozdílem, že používá také <xref:System.Threading.Tasks.Task.ContinueWith%2A> metodu pro vytvoření pokračování úlohy zobrazí stav celkového toku dat operace.  
  
 [!code-csharp[TPLDataflow_Overview#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#11)]
 [!code-vb[TPLDataflow_Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#11)]  
  
 Můžete také použít vlastnosti jako <xref:System.Threading.Tasks.Task.IsCanceled%2A> těla úkolu pokračování k určení dalších informací o stavu dokončení bloku toku dat. Další informace o pokračování úlohy a jak souvisejí s nabídkou zrušení a zpracování chyb, naleznete v tématu [řetězení úloh pomocí úloh pokračování používání](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md), [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md), a [ Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
 [[přejděte do horní části](#top)]  
  
<a name="predefined_types"></a>   
## <a name="predefined-dataflow-block-types"></a>Typy bloků předdefinovaných toku dat  
 Knihovna TPL datového toku poskytuje několik typů bloků toku dat předdefinované. Tyto typy jsou rozdělené do tří kategorií: *ukládání do vyrovnávací paměti bloky*, *provádění bloky*, a *seskupení bloky*. Následující části popisují typy bloků, které tvoří těchto kategorií.  
  
### <a name="buffering-blocks"></a>Ukládání do vyrovnávací paměti bloky  
 Vyrovnávací paměti bloky uchovávají data pro použití u spotřebitelé dat. Knihovna TPL datového toku poskytuje tři typy bloků ukládání do vyrovnávací paměti: <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601?displayProperty=nameWithType>.  
  
#### <a name="bufferblockt"></a>BufferBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Třída reprezentuje strukturu pro obecné účely asynchronní zasílání zpráv. Tato třída uchovává první in-first-out (FIFO) fronty zpráv, které mohou být zapsaného do více zdrojů nebo číst z více cílů. Když cíl obdrží zprávu od <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu, tato zpráva se odebere z fronty zpráv. Proto i když <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objekt může mít více cílů, získá každou zprávu pouze jeden cíl. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Třídy je užitečné, když chcete předat více zpráv na jiné komponenty a komponenty musí přijmout každou zprávu.  
  
 V následujícím základním příkladu příspěvky několik <xref:System.Int32> hodnoty <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu a pak přečte tyto hodnoty zpět z tohoto objektu.  
  
 [!code-csharp[TPLDataflow_Overview#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#1)]
 [!code-vb[TPLDataflow_Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#1)]  
  
 Úplný příklad, který ukazuje, jak psát zpráv a čtení zpráv z <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu, najdete v článku [jak: Zápis zpráv a čtení zpráv z bloku toku dat](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md).  
  
#### <a name="broadcastblockt"></a>BroadcastBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> Třídy je užitečné, když je nutné předat více zpráv do jiné součásti, ale, že součást potřebuje pouze nejnovější hodnotu. Tato třída je také užitečné, když chcete vysílání zpráv do více komponent.  
  
 Následující základní příklad příspěvky <xref:System.Double> hodnota, která se <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> objekt a potom čtení, která hodnotu zpět z tohoto objektu několikrát. Protože hodnoty nejsou odebrány z <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> objekty po jejich přečtení, stejnou hodnotu je k dispozici pokaždé, když.  
  
 [!code-csharp[TPLDataflow_Overview#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#2)]
 [!code-vb[TPLDataflow_Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#2)]  
  
 Úplný příklad, který ukazuje, jak používat <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> vysílání zpráv do více cílových bloků, najdete v článku [jak: Určení plánovače úloh v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md).  
  
#### <a name="writeonceblockt"></a>WriteOnceBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> Třídy vypadá podobně jako <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> třídy s výjimkou, že <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt je možné zapisovat na pouze jednou. Si můžete představit <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> jako podobný jazyka C# [jen pro čtení](~/docs/csharp/language-reference/keywords/readonly.md) ([jen pro čtení](~/docs/visual-basic/language-reference/modifiers/readonly.md) v jazyce Visual Basic) – klíčové slovo, s výjimkou, že <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt se stane neměnný po přijetí na hodnotu místo konstrukce. Podobně jako <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> třídy, pokud je cíl přijme zprávu z <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu, tato zpráva se neodebere z tohoto objektu. Proto více cílů obdrží kopii zprávy. <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> Třída je užitečná, když chcete rozšířit pouze první z více zpráv.  
  
 V následujícím základním příkladu příspěvky více <xref:System.String> hodnoty <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt a potom čtení hodnotu zpět z tohoto objektu. Protože <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt je možné zapisovat na jednou pouze po <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt obdrží zprávu, zahodí dalších zpráv.  
  
 [!code-csharp[TPLDataflow_Overview#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#3)]
 [!code-vb[TPLDataflow_Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#3)]  
  
 Úplný příklad, který ukazuje, jak používat <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> zobrazí hodnotu, která skončí jako první operace, najdete v článku [jak: Zrušení propojení bloků toku dat](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md).  
  
### <a name="execution-blocks"></a>Spuštění bloků  
 Bloky provádění volání uživatelského delegáta pro každou část přijatá data. Knihovna TPL datového toku poskytuje tři typy bloků spuštění: <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.  
  
#### <a name="actionblockt"></a>ActionBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Třída je cílový blok, který volá delegáta, když přijme data. Představte si, že <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu jako delegát, který se spustí asynchronně, jakmile budou data k dispozici. Delegát, který poskytnete <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu nemůže být typu <xref:System.Action%601> nebo typ `System.Func<TInput, Task>`. Při použití <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt s <xref:System.Action%601>, zpracování jednotlivé elementy vstupu je považován za dokončený návratu delegáta. Při použití <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt s `System.Func<TInput, Task>`, zpracování jednotlivé elementy vstupu se považuje za dokončené pouze v případě vrácený <xref:System.Threading.Tasks.Task> objektu je dokončena. Když použijete tyto dva mechanismy, můžete použít <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> pro synchronní a asynchronní zpracování jednotlivé elementy vstupu.  
  
 V následujícím základním příkladu příspěvky více <xref:System.Int32> hodnoty <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objekt vytiskne tyto hodnoty do konzoly. V tomto příkladu pak nastaví bloku do dokončeného stavu a čeká na dokončení všech úloh datového toku.  
  
 [!code-csharp[TPLDataflow_Overview#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#4)]
 [!code-vb[TPLDataflow_Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#4)]  
  
 Kompletní příklady, které ukazují, jak použít delegáty s <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> najdete v tématu [jak: Provádění akcí po bloku toku dat](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md).  
  
#### <a name="transformblocktinput-toutput"></a>Operace TransformBlock (TInput, TOutput)  
 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Třídy vypadá podobně jako <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> třídy, s tím rozdílem, že funguje jako obou zdroj a jako cíl. Delegát, který můžete předat <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt vrátí hodnotu typu `TOutput`. Delegát, který poskytnete <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu nemůže být typu `System.Func<TInput, TOutput>` nebo typ `System.Func<TInput, Task<TOutput>>`. Při použití <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt s `System.Func<TInput, TOutput>`, zpracování jednotlivé elementy vstupu je považován za dokončený návratu delegáta. Při použití <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu se používá s `System.Func<TInput, Task<TOutput>>`, zpracování jednotlivé elementy vstupu se považuje za dokončené pouze v případě vrácený <xref:System.Threading.Tasks.Task%601> objektu je dokončena. Stejně jako u <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, když použijete tyto dva mechanismy, můžete použít <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pro synchronní a asynchronní zpracování jednotlivé elementy vstupu.  
  
 V následujícím základním příkladu vytvoří <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt, který vypočítá druhou odmocninu vstup. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Přebírá objekt <xref:System.Int32> hodnoty jako vstup a vytvoří <xref:System.Double> hodnoty jako výstup.  
  
 [!code-csharp[TPLDataflow_Overview#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#5)]
 [!code-vb[TPLDataflow_Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#5)]  
  
 Kompletní příklady, které používá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> v síti bloků toku dat, který provádí zpracování obrázků v aplikaci Windows Forms, naleznete v tématu [názorný postup: Použití toku dat v Windows Forms aplikace](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
#### <a name="transformmanyblocktinput-toutput"></a>TransformManyBlock (TInput, TOutput)  
 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> Třídy vypadá podobně jako <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> třídy s výjimkou, že <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> vytváří žádný nebo více výstupních hodnot pro každý vstupní hodnotu, místo jenom pro jednu výstupní hodnotu pro každý vstupní hodnotu. Delegát, který poskytnete <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objektu nemůže být typu `System.Func<TInput, IEnumerable<TOutput>>` nebo typ `System.Func<TInput, Task<IEnumerable<TOutput>>>`. Při použití <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekt s `System.Func<TInput, IEnumerable<TOutput>>`, zpracování jednotlivé elementy vstupu je považován za dokončený návratu delegáta. Při použití <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekt s `System.Func<TInput, Task<IEnumerable<TOutput>>>`, zpracování jednotlivé elementy vstupu je považován za dokončení pouze tehdy, když vráceného `System.Threading.Tasks.Task<IEnumerable<TOutput>>` objektu je dokončena.  
  
 V následujícím základním příkladu vytvoří <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekt, který rozdělí jejich pořadí jednotlivým znakům řetězce. <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> Přebírá objekt <xref:System.String> hodnoty jako vstup a vytvoří <xref:System.Char> hodnoty jako výstup.  
  
 [!code-csharp[TPLDataflow_Overview#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#6)]
 [!code-vb[TPLDataflow_Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#6)]  
  
 Kompletní příklady, které používají <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> vytvoří několik nezávislých výstupů pro každou vstup v kanálu toku dat, naleznete v tématu [názorný postup: Vytvoření kanálu toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md).  
  
#### <a name="degree-of-parallelism"></a>Stupeň paralelismu  
 Každý <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> vyrovnávací paměti objektu vstupní zprávy, dokud blok je připraven k jejich zpracování. Ve výchozím nastavení tyto třídy zpracovávat zprávy v pořadí, ve kterém jsou přijímány, jednu zprávu v čase. Můžete také určit míru paralelismu umožňující <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekty zpracovávat více zpráv souběžně. Další informace o souběžné spouštění najdete v části Určení stupeň paralelismu dále v tomto dokumentu. Příklad, který nastavuje stupeň paralelismu umožňující z bloku toku dat provádění zpracovávat více zpráv najednou, naleznete v tématu [jak: Určení stupně paralelního zpracování v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md).  
  
#### <a name="summary-of-delegate-types"></a>Souhrn typů delegátů.  
 Následující tabulka shrnuje typy delegátů, které můžete poskytnout <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekty. Tato tabulka také určuje, zda typ delegáta pracuje synchronně nebo asynchronně.  
  
|Type|Typ synchronní delegáta|Typ asynchronních delegátů|  
|----------|-------------------------------|--------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|`System.Action`|`System.Func<TInput, Task>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|`System.Func<TInput, TOutput>`|`System.Func<TInput, Task<TOutput>>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|`System.Func<TInput, IEnumerable<TOutput>>`|`System.Func<TInput, Task<IEnumerable<TOutput>>>`|  
  
 Výrazy lambda můžete použít také při práci s typy bloků spuštění. Příklad, který ukazuje, jak použít výraz lambda se z provádění bloku, v tématu [jak: Provádění akcí po bloku toku dat](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md).  
  
### <a name="grouping-blocks"></a>Seskupení bloky  
 Seskupení bloky kombinovat data z jednoho nebo více zdrojů a v rámci různých omezení. Knihovna TPL datového toku poskytuje tři typy bloků join: <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>, a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>.  
  
#### <a name="batchblockt"></a>BatchBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> Třídy kombinuje sad vstupních dat, které jsou označovány jako dávek, do polí výstupní data. Zadejte velikost jednotlivých dávek při vytváření <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu. Když <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt získá zadaný počet elementů vstupu, se asynchronně šíří pole, které obsahuje tyto prvky. Pokud <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu je nastavena do dokončeného stavu, ale neobsahuje dostatečný počet elementů k vytvoření dávky, se šíří poslední pole, která obsahuje zbývající prvky vstupu.  
  
 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> Třída funguje v obou *greedy* nebo *bez metody greedy* režimu. V režimu greedy, což je výchozí <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt přijímá všechny zprávy, že se nabízí a šíří pole až dostane od zadaného počtu prvků. V režimu bez metody greedy <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt odloží všechny příchozí zprávy, dokud dostatek zdrojů nabízejí zpráv do bloku k vytvoření dávky. Greedy režimu obvykle vrací lepší výsledky než režim bez metody greedy protože vyžaduje méně režie zpracování. Můžete však použít bez metody greedy režim při musí koordinovat spotřeby z více zdrojů atomic způsobem. Určení režimu bez metody greedy nastavením <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> k `False` v `dataflowBlockOptions` parametr <xref:System.Threading.Tasks.Dataflow.BatchBlock%601.%23ctor%2A> konstruktoru.  
  
 V následujícím základním příkladu příspěvky několik <xref:System.Int32> hodnoty <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt, který obsahuje 10 prvků v dávce. K zajištění, že všechny hodnoty šířit z <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, tento příklad příkladu volá <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metoda. <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> Metody nastaví <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu do dokončeného stavu a proto <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt šíří všechny zbývající prvky jako poslední dávky.  
  
 [!code-csharp[TPLDataflow_Overview#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#7)]
 [!code-vb[TPLDataflow_Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#7)]  
  
 Úplný příklad používající <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> ke zlepšení efektivity databázových operací vložení, naleznete v tématu [názorný postup: Použití tříd BatchBlock a BatchedJoinBlock ke zvýšení efektivity](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md).  
  
#### <a name="joinblockt1-t2-"></a>Třídy JoinBlock (T1, T2,...)  
 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> třídy shromažďování vstupních prvků a propagaci <xref:System.Tuple%602?displayProperty=nameWithType> nebo <xref:System.Tuple%603?displayProperty=nameWithType> objektů, které obsahují tyto elementy. <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> nedědí ze třídy <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>. Místo toho, že poskytuje vlastnosti, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target1%2A>, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target2%2A>, a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603.Target3%2A>, které implementují <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Stejně jako <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> pracovat v režimu greedy nebo bez metody greedy. V režimu greedy, což je výchozí <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nebo <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objekt přijímá všechny zprávy, že se nabízí a šíří řazené kolekce členů po každý svůj cíl přijímá minimálně jednu zprávu. V režimu bez metody greedy <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nebo <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objekt odloží všechny příchozí zprávy, dokud všechny cíle byly zveřejněny data, která je nezbytná k vytvoření řazené kolekce členů. V tomto okamžiku bloku mezi protokol dvoufázového potvrzení atomicky načíst všechny požadované položky ze zdroje. Tato odložení umožňuje jiné entity, které využívají data do té doby, aby celkový stav systému provést postup směrem vpřed.  
  
 V následujícím základním příkladu ukazuje případ, ve kterém <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objektu vyžaduje více dat k výpočtu hodnoty. Tento příklad vytvoří <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objekt, který vyžaduje dva <xref:System.Int32> hodnoty a <xref:System.Char> hodnotu k provedení aritmetické operace.  
  
 [!code-csharp[TPLDataflow_Overview#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#8)]
 [!code-vb[TPLDataflow_Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#8)]  
  
 Úplný příklad používající <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekty v režimu bez metody greedy kooperativně sdílet prostředek, naleznete v tématu [jak: Data z různých zdrojů pomocí třídy JoinBlock](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md).  
  
#### <a name="batchedjoinblockt1-t2-"></a>BatchedJoinBlock (T1, T2,...)  
 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%603> třídy shromažďovat dávky elementů vstupu a propagaci `System.Tuple(IList(T1), IList(T2))` nebo `System.Tuple(IList(T1), IList(T2), IList(T3))` objektů, které obsahují tyto elementy. Představte si, že <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> jako kombinace <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>. Zadejte velikost jednotlivých dávek při vytváření <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objektu. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> poskytuje také vlastnosti, <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A>, které implementují <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>. Při přijetí zadaný počet elementů vstupu z přes všechny cíle <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objekt asynchronně šíří `System.Tuple(IList(T1), IList(T2))` objekt, který obsahuje tyto prvky.  
  
 V následujícím základním příkladu vytvoří <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objekt, který obsahuje výsledky, <xref:System.Int32> hodnoty a chyby, které jsou <xref:System.Exception> objekty. Tento příklad provádí více operací a zapisuje výsledky <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A> vlastnost a chyby <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A> vlastnost, z <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objektu. Vzhledem k tomu, že počet úspěšných a neúspěšných operací není znám předem, <xref:System.Collections.Generic.IList%601> objekty povolit každý cíl přijímat nula nebo více hodnot.  
  
 [!code-csharp[TPLDataflow_Overview#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#9)]
 [!code-vb[TPLDataflow_Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#9)]  
  
 Úplný příklad používající <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> pro zachycení výsledků i všech výjimek, ke kterým dochází, když program čte z databáze, najdete v článku [názorný postup: Použití tříd BatchBlock a BatchedJoinBlock ke zvýšení efektivity](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md).  
  
 [[přejděte do horní části](#top)]  
  
<a name="behavior"></a>   
## <a name="configuring-dataflow--block-behavior"></a>Konfigurace chování bloku toku dat  
 Můžete povolit další možnosti tím, že poskytuje <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=nameWithType> objekt konstruktoru typů bloků toku dat. Tyto možnosti určují chování těchto plánovače, která spravuje základní úkol a stupně paralelního zpracování. <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions> Také obsahuje odvozené typy, které určují chování, které jsou specifické pro určité typy bloků toku dat. Následující tabulka shrnuje, jaký typ možnosti je spojené s každou typ bloku toku dat.  
  
|Typ bloku toku dat|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions> Typ|  
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
  
 Následující části obsahují další informace o důležitých druhy toku dat možnosti bloků, které jsou k dispozici prostřednictvím <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions?displayProperty=nameWithType> třídy.  
  
### <a name="specifying-the-task-scheduler"></a>Určení plánovače úloh  
 Každý blok toku dat předdefinované používá mechanismus k provedení aktivity, například šířící dat na cílový, příjem dat ze zdroje a spuštění uživatelem definované delegáty, když budou data k dispozici pro plánování úloh TPL. <xref:System.Threading.Tasks.TaskScheduler> je abstraktní třída představující plánovače úloh této fronty úloh do vlákna. Výchozí Plánovač úloh <xref:System.Threading.Tasks.TaskScheduler.Default%2A>, používá <xref:System.Threading.ThreadPool> třídy do fronty a provádění pracovní. Výchozí Plánovač úloh můžete přepsat tak, že nastavíte <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> při vytvoření objektu bloku toku dat.  
  
 Stejné Plánovač úloh spravuje více bloků toku dat, ho můžete vynutit zásady mezi nimi. Například, pokud více bloků toku dat je každý nakonfigurovaný k cílení exkluzivní Plánovač stejného <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu, všechna fungovat, je serializován spuštění napříč tyto bloky. Podobně pokud jsou tyto bloky nakonfigurovaný k cílení souběžných Plánovač stejného <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu a tento plánovač má nastavený na úrovni maximální souběžnosti, veškerou práci z těchto bloků je omezen na tento počet souběžných operací. Příklad, který se používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> třídy umožňující operace čtení paralelně, ale operace dojít pouze z všechny ostatní operace, přečtěte si téma zápisu [jak: Určení plánovače úloh v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md). Další informace o plánovačích úkolů v TPL, najdete v článku <xref:System.Threading.Tasks.TaskScheduler> třídě.  
  
### <a name="specifying-the-degree-of-parallelism"></a>Určení stupně paralelního zpracování  
 Ve výchozím nastavení, typů bloků tři spuštění, které poskytuje Knihovna TPL datového toku <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>, zpracování zpráv v čase. Tyto typy bloků toku dat také zpracovávat zprávy v pořadí, ve kterém jsou přijímány. Chcete-li povolit tyto bloky toku dat ke zpracování zpráv souběžně, nastavte <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> vlastnost při vytváření objektu bloku toku dat.  
  
 Výchozí hodnota <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> 1, což zaručuje, že jednu zprávu zpracuje bloku toku dat najednou. Nastavení této vlastnosti na hodnotu, která je větší než 1 umožňuje bloku toku dat zpracovávat více zpráv souběžně. Nastavení této vlastnosti na <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=nameWithType> umožňuje příslušného plánovače úloh pro správu nejvyšší stupeň souběžnosti.  
  
> [!IMPORTANT]
>  Při zadávání maximální volnost paralelismu, který je větší než 1 více zpráv najednou zpracovávají, a proto nemusí zpracovávat zprávy v pořadí, ve kterém jsou přijímány. Pořadí, ve kterém zprávy se zobrazují v bloku je však stejný jako ten, v jakém jsou přijaty.  
  
 Vzhledem k tomu, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnost představuje maximální volnost paralelismu, bloku toku dat může spustit s menší stupně paralelního zpracování, než jste určili. Blok toku dat použít menší stupeň paralelismu jeho funkční požadavky nebo proto, že je nedostatek systémových prostředků. Blok toku dat nikdy zvolí další paralelismu, než jste určili.  
  
 Hodnota <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> výhradně pro každý objekt bloku toku dat je vlastnost. Například pokud všechny čtyři bloku objekty toku dat určete hodnotu 1 pro maximální volnost paralelismu, všechny čtyři objekty bloku toku dat může potenciálně běžet paralelně.  
  
 Příklad, který nastaví maximální volnost paralelismu umožňující zdlouhavé operace, které mají být provedeny souběžně, naleznete v tématu [jak: Určení stupně paralelního zpracování v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md).  
  
### <a name="specifying-the-number-of-messages-per-task"></a>Určení počtu zpráv za úkol  
 Typy bloků předdefinovaných toku dat pomocí úlohy zpracovat více vstupních prvků. Tím se může minimalizovat počet objektů úloh, které jsou vyžadovány pro zpracování dat, která umožňuje aplikacím využívat efektivněji. Ale při úkoly z jednoho sadu bloků toku dat jsou zpracování dat, úlohy z jiných bloků toku dat může být nutné čekat doba zpracování službou Řízení front zpráv. Chcete-li povolit lepší rovnost mezi úlohy toku dat, nastavte <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> vlastnost. Když <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> je nastavena na <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=nameWithType>, což je výchozí, úkol používá bloku toku dat zpracovává libovolný počet zpráv, jako jsou k dispozici. Když <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> je nastavena na hodnotu jiné než <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded>, bloku toku dat zpracovává maximálně tento počet zpráv za <xref:System.Threading.Tasks.Task> objektu. I když nastavení <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> vlastnost zvětšují prostor pro rovnost mezi úkoly, může to způsobit systému vytvořit více úkolů, než je potřeba, což může snížit výkon.  
  
### <a name="enabling-cancellation"></a>Povolení zrušení  
 Knihovna TPL poskytuje mechanismus, který umožňuje úkoly ke koordinaci na způsob spolupráce za zrušení. Chcete-li povolit bloků toku dat k účasti v tento mechanismus zrušení, nastavte <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost. Když to <xref:System.Threading.CancellationToken> je nastaven na zrušeném stavu, všech bloků toku dat, které sledují tento token dokončí provádění své aktuální položky, ale není spuštěno zpracování další položky. Tyto bloky toku dat také vymazat všechny vyrovnávací paměť zprávy, verze připojení pro všechny zdrojové a cílové bloky a přecházet na zrušeném stavu. Ve zrušeném stavu a přecházející <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> vlastnost má <xref:System.Threading.Tasks.Task.Status%2A> nastavenou na <xref:System.Threading.Tasks.TaskStatus.Canceled>, pokud došlo k výjimce během zpracování. V takovém případě <xref:System.Threading.Tasks.Task.Status%2A> je nastavena na <xref:System.Threading.Tasks.TaskStatus.Faulted>.  
  
 Příklad, který ukazuje, jak pomocí zrušení v aplikaci Windows Forms, naleznete v tématu [jak: Zrušení bloku toku dat](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md). Další informace o zrušení v TPL najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="specifying-greedy-versus-non-greedy-behavior"></a>Určení Greedy a Non-Greedy chování  
 Několik typů bloků toku dat seskupení může probíhat buď *greedy* nebo *bez metody greedy* režimu. Ve výchozím nastavení typy bloků předdefinovaných toku dat pracují v greedy režimu.  
  
 Pro připojení k blokování typů <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>, greedy režim znamená, že blok okamžitě přijímá data i v případě, že se odpovídající data, pomocí kterého se má připojit k ještě není k dispozici. Bez metody greedy režim znamená, že blok odloží všechny příchozí zprávy, dokud je k dispozici na každý svůj cíl pro dokončení připojení. Pokud některý z odložených zprávy již nejsou k dispozici, blok spojení uvolní všechny odložená zprávy a restartování procesu. Pro <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídy greedy a bez metody greedy chování je podobné, s výjimkou, že v režimu bez metody greedy, <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt odloží všechny příchozí zprávy, dokud dostatek jsou dostupné z různých zdrojů a dokončení dávky.  
  
 Chcete-li zadat bez metody greedy režimu pro blok toku dat, nastavte <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> k `False`. Příklad, který ukazuje, jak používat režim bez metody greedy povolit více bloků spojení efektivněji sdílet zdroje dat, naleznete v tématu [jak: Data z různých zdrojů pomocí třídy JoinBlock](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md).  
  
 [[přejděte do horní části](#top)]  
  
<a name="custom"></a>   
## <a name="custom-dataflow-blocks"></a>Vlastních bloků toku dat  
 Přestože Knihovna TPL datového toku poskytuje mnoho typů bloků předdefinovaných, můžete vytvořit další blok typy, které provádějí vlastní chování. Implementace <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nebo <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> rozhraní přímo nebo použijte <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metoda pro vytvoření komplexní blok, který zapouzdřuje chování existující typy bloků. Příklady, které ukazují, jak implementovat vlastní toku dat bloku funkce najdete v tématu [názorný postup: Vytvoření vlastního toku dat typu blok](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md).  
  
 [[přejděte do horní části](#top)]  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Zápis zpráv a čtení zpráv z bloku toku dat](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md)|Ukazuje, jak se zápis zpráv a čtení zpráv z <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu.|  
|[Postupy: Implementace vzoru toku dat producent – příjemce](../../../docs/standard/parallel-programming/how-to-implement-a-producer-consumer-dataflow-pattern.md)|Popisuje, jak použít model toku dat pro implementaci vzoru producent – příjemce, kde producent posílání zpráv do bloku toku dat a příjemce čte zprávy z tohoto bloku.|  
|[Postupy: Provádění akcí po bloku toku dat](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)|Popisuje, jak poskytnout delegátů typů bloků toku dat provádění <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>.|  
|[Návod: Vytvoření kanálu toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)|Popisuje postup vytvoření kanálu toku dat, která stáhne text z webu a provádí operace v tomto textu.|  
|[Postupy: Zrušení propojení bloků toku dat](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)|Popisuje způsob použití <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metoda se zrušit propojení cílový blok z jeho zdroje po zdroj nabízí zprávy na cíl.|  
|[Návod: Použití toku dat ve formulářové aplikaci Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)|Ukazuje, jak vytvořit síť bloků toku dat, které provádějí zpracování obrázků v aplikaci Windows Forms.|  
|[Postupy: Zrušení bloku toku dat](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)|Ukazuje, jak pomocí zrušení v aplikaci Windows Forms.|  
|[Postupy: Data z různých zdrojů pomocí třídy JoinBlock](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)|Vysvětluje způsob používání <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> třídy provádět operace, když jsou k dispozici data z více zdrojů a jak používat režim bez metody greedy povolit více bloků spojení sdílet zdroje dat efektivněji.|  
|[Postupy: Určení stupně paralelního zpracování v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)|Popisuje, jak nastavit <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastností pro povolení z bloku toku dat provádění zpracovávat více zpráv najednou.|  
|[Postupy: Určení plánovače úloh v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)|Ukazuje, jak přiřadit určitým plánovačem úloh, při použití toku dat ve vaší aplikaci.|  
|[Návod: Použití tříd BatchBlock a BatchedJoinBlock ke zvýšení efektivity](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)|Popisuje způsob použití <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídy ke zvýšení efektivity databáze vložit operace a způsob použití <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídy pro zachycení výsledků i všech výjimek, ke kterým dochází, když program čte z databáze.|  
|[Návod: Vytvoření typu blok vlastní toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)|Ukazuje dva způsoby, jak vytvořit typ bloku toku dat, která implementuje vlastní chování.|  
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zavádí TPL knihovnu, která zjednodušuje paralelní aplikace a souběžné programování v rozhraní .NET Framework aplikace.|
