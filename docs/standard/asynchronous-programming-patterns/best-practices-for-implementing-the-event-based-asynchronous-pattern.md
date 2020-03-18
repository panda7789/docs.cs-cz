---
title: Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 4acd2094-4f46-4eff-9190-92d0d9ff47db
ms.openlocfilehash: 439b862612d7997c9277ffb2cf4f15b14bd0b106
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156046"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech
Asynchronní vzor založený na událostech poskytuje efektivní způsob, jak vystavit asynchronní chování ve třídách, se známou sémantikou událostí a delegáta. Chcete-li implementovat asynchronní vzor založený na událostech, musíte dodržovat některé specifické požadavky na chování. Následující části popisují požadavky a pokyny, které byste měli zvážit při implementaci třídy, která následuje asynchronní vzor založený na událostech.  
  
 Přehled naleznete v [tématu implementace asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Požadované záruky chování  
 Pokud implementujete asynchronní vzor založený na událostech, musíte poskytnout řadu záruk, abyste zajistili, že vaše třída se bude chovat správně a klienti vaší třídy se mohou spolehnout na takové chování.  
  
### <a name="completion"></a>Dokončení  
 Vždy vyvolat <em>MethodName</em>**Completed** obslužnou rutinu události, pokud máte úspěšné dokončení, chybu nebo zrušení. Aplikace by nikdy dojít k situaci, kdy zůstanou nečinné a dokončení nikdy nedojde. Jednou z výjimek z tohoto pravidla je, pokud asynchronní operace sama o sobě je navržen tak, aby nikdy nedokončí.  
  
### <a name="completed-event-and-eventargs"></a>Dokončená událost a EventArgs  
 Pro každou samostatnou metodu <em>MethodName</em>**Async** použijte následující požadavky na návrh:  
  
- Definujte událost <em>MethodName</em>**Completed** ve stejné třídě jako metoda.  
  
- Definujte <xref:System.EventArgs> třídu a doprovodný delegát pro událost <em>MethodName</em>**Completed,** která je odvozena <xref:System.ComponentModel.AsyncCompletedEventArgs> od třídy. Výchozí název třídy by měl být ve formuláři <em>MethodName</em>**CompletedEventArgs**.  
  
- Ujistěte <xref:System.EventArgs> se, že třída je specifická pro vrácené hodnoty <em>MethodName</em> metody. Při použití <xref:System.EventArgs> třídy, nikdy byste neměli vyžadovat, aby vývojáři přetypovat výsledek.  
  
     Následující příklad kódu ukazuje dobré a chybné provádění tohoto požadavku návrhu v uvedeném pořadí.  
  
```csharp  
// Good design  
private void Form1_MethodNameCompleted(object sender, xxxCompletedEventArgs e)
{
    DemoType result = e.Result;  
}  
  
// Bad design  
private void Form1_MethodNameCompleted(object sender, MethodNameCompletedEventArgs e)
{
    DemoType result = (DemoType)(e.Result);  
}  
```  
  
- Nedefinujte <xref:System.EventArgs> třídu pro vracející `void`metody, které vracejí . Místo toho použijte instanci třídy. <xref:System.ComponentModel.AsyncCompletedEventArgs>  
  
- Ujistěte se, že vždy navádíte událost <em>MethodName</em>**Completed.** Tato událost by měla být vyvolána při úspěšném dokončení, při chybě nebo při zrušení. Aplikace by nikdy dojít k situaci, kdy zůstanou nečinné a dokončení nikdy nedojde.  
  
- Ujistěte se, že zachytit všechny výjimky, ke kterým dochází v <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> asynchronní operace a přiřadit zachycené výjimky vlastnosti.  
  
- Pokud došlo k chybě dokončení úkolu, výsledky by neměly být přístupné. Pokud <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnost není `null`, ujistěte se, <xref:System.EventArgs> že přístup k jakékoli vlastnosti ve struktuře vyvolá výjimku. K <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> provedení tohoto ověření použijte metodu.  
  
- Model ovat časový čas jako chybu. Když dojde k out out, raise <em>MethodName</em>**Completed** <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> událost a přiřadit <xref:System.TimeoutException> vlastnost.  
  
- Pokud vaše třída podporuje více souběžných vyvolání, ujistěte se, že <em>Událost MethodName</em>**Completed** obsahuje příslušný `userSuppliedState` objekt.  
  
- Ujistěte se, že <em>MethodName</em>**Completed** událost je aktivována v příslušném vlákně a ve vhodnou dobu v životním cyklu aplikace. Další informace naleznete v části Threading and Contexts.  
  
### <a name="simultaneously-executing-operations"></a>Současné provádění operací  
  
- Pokud vaše třída podporuje více souběžných vyvolání, povolte vývojáři sledovat každé vyvolání samostatně definováním <em>Přetížení MethodName</em>**Async,** `userSuppliedState`které přebírá parametr stavu s hodnotou objektu nebo ID úlohy, nazývané . Tento parametr by měl být vždy posledním parametrem v podpisu metody <em>MethodName</em>**Async.**  
  
- Pokud vaše třída definuje <em>Přetížení MethodName</em>**Async,** které přebírá parametr stavu s hodnotou objektu nebo ID úlohy, nezapomeňte sledovat životnost operace s tímto ID úkolu a ujistěte se, že ji poskytnete zpět do obslužné rutiny dokončení. K dispozici jsou pomocné třídy. Další informace o správě souběžnosti naleznete v [tématu How to: Implement a Component that Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
- Pokud vaše třída definuje metodu <em>MethodName</em>**Async** bez parametru stavu a nepodporuje více souběžných volání, ujistěte se, že jakýkoli pokus o <xref:System.InvalidOperationException>vyvolání <em>MethodName</em>**Async** před dokončením předchozího vyvolání**Async** <em>MethodName</em>vyvolá .  
  
- Obecně nevyvolávejte výjimku, pokud metoda <em>MethodName</em>**Async** bez parametru `userSuppliedState` je vyvolána vícekrát, takže existuje více nevyřízených operací. Můžete vyvolat výjimku, když vaše třída explicitně nemůže zpracovat tuto situaci, ale předpokládat, že vývojáři mohou zpracovat tyto více nerozlišitelné zpětná volání  
  
### <a name="accessing-results"></a>Přístup k výsledkům  
  
- Pokud došlo k chybě během provádění asynchronní operace, výsledky by neměly být přístupné. Ujistěte se, že <xref:System.ComponentModel.AsyncCompletedEventArgs> přístup <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> k `null` jakékoli vlastnosti <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>v when není vyvolává výjimku odkazuje . Třída <xref:System.ComponentModel.AsyncCompletedEventArgs> poskytuje <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> metodu pro tento účel.  
  
- Ujistěte se, že jakýkoli <xref:System.InvalidOperationException> pokus o přístup k výsledku vyvolá oznamující, že operace byla zrušena. K <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> provedení tohoto ověření použijte metodu.  
  
### <a name="progress-reporting"></a>Hlášení průběhu  
  
- Pokud je to možné, podpořte vykazování průběhu. To umožňuje vývojářům poskytovat lepší uživatelské prostředí aplikace při použití vaší třídy.  
  
- Pokud implementujete **ProgressChanged** nebo <em>MethodName</em>**ProgressChanged** událost, ujistěte se, že neexistují žádné takové události vyvolané pro konkrétní asynchronní operace po této operace <em>MethodName</em>**Completed** událost byla vyvolána.  
  
- Pokud je <xref:System.ComponentModel.ProgressChangedEventArgs> standard naplněn, ujistěte <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> se, že může být vždy interpretován jako procento. Procento nemusí být přesné, ale mělo by představovat procento. Pokud vaše metrika hlášení průběhu musí být něco jiného než procento, odvodit třídu <xref:System.ComponentModel.ProgressChangedEventArgs> z třídy a ponechat <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> na 0. Nepoužívejte jinou metriku přehledů než procento.  
  
- Ujistěte `ProgressChanged` se, že událost je vyvolána v příslušném vlákně a ve vhodnou dobu v životním cyklu aplikace. Další informace naleznete v části Threading and Contexts.  
  
### <a name="isbusy-implementation"></a>Implementace IsBusy  
  
- Nezveřejňujte `IsBusy` vlastnost, pokud vaše třída podporuje více souběžných vyvolání. Například proxy služby XML nezveřejňují `IsBusy` vlastnost, protože podporují více souběžných vyvolání asynchronních metod.  
  
- Vlastnost `IsBusy` by `true` měla vrátit po <em>MethodName</em>**Async** metoda byla volána a před <em>MethodName</em>**Completed** událost byla vyvolána. V opačném `false`případě by se měl vrátit . <xref:System.ComponentModel.BackgroundWorker> Komponenty <xref:System.Net.WebClient> a jsou příklady tříd, `IsBusy` které zveřejňují vlastnost.  
  
### <a name="cancellation"></a>Zrušení  
  
- Pokud je to možné, zrušení podpory. To umožňuje vývojářům poskytovat lepší uživatelské prostředí aplikace při použití vaší třídy.  
  
- V případě zrušení nastavte <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> příznak v <xref:System.ComponentModel.AsyncCompletedEventArgs> objektu.  
  
- Ujistěte se, že jakýkoli <xref:System.InvalidOperationException> pokus o přístup k výsledku vyvolá oznamující, že operace byla zrušena. K <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> provedení tohoto ověření použijte metodu.  
  
- Ujistěte se, že volání metody zrušení vždy úspěšně vrátit a nikdy vyvolat výjimku. Obecně platí, že klient není upozorněn na to, zda je operace skutečně zrušitelná v daném okamžiku, a není upozorněn na to, zda bylo dříve vydané zrušení úspěšné. Aplikace však bude vždy oznámení, když zrušení proběhlo úspěšně, protože aplikace se účastní stavu dokončení.  
  
- Raise <em>The MethodName</em>**Completed** událost při operaci je zrušena.  
  
### <a name="errors-and-exceptions"></a>Chyby a výjimky  
  
- Zachytit všechny výjimky, ke kterým dochází v asynchronní <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> operace a nastavte hodnotu vlastnosti na tuto výjimku.  
  
### <a name="threading-and-contexts"></a>Zřetězení a kontexty  
 Pro správnou funkci vaší třídy je důležité, aby obslužné rutiny událostí klienta byly vyvolány ve správném vlákně nebo kontextu pro daný model aplikace, včetně aplikací ASP.NET a Windows Forms. Dvě důležité pomocné třídy jsou k dispozici k zajištění, že vaše asynchronní třída se chová správně pod libovolný model aplikace: <xref:System.ComponentModel.AsyncOperation> a <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager>poskytuje jednu <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>metodu <xref:System.ComponentModel.AsyncOperation>, která vrací . Vaše <em>MethodName</em>**Async** metoda volání <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> a <xref:System.ComponentModel.AsyncOperation> vaše třída používá vrácené sledovat životnost asynchronní úlohy.  
  
 Chcete-li ohlásit průběh, přírůstkové výsledky <xref:System.ComponentModel.AsyncOperation.Post%2A> a <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> dokončení <xref:System.ComponentModel.AsyncOperation>klientovi, zavolejte metody a na . <xref:System.ComponentModel.AsyncOperation>je zodpovědný za zařazování volání obslužné rutiny událostí klienta na správné vlákno nebo kontext.  
  
> [!NOTE]
> Tato pravidla můžete obejít, pokud explicitně chcete jít proti zásadám aplikačního modelu, ale stále těžit z dalších výhod použití asynchronního vzoru založeného na událostech. Můžete například chtít, aby třída pracující ve windows forms byla bez vláken. Můžete vytvořit bezplatnou třídu s vlákny, pokud vývojáři chápou implikovaná omezení. Konzolové aplikace nesynchronizují <xref:System.ComponentModel.AsyncOperation.Post%2A> provádění volání. To může `ProgressChanged` způsobit události, které mají být vyvolány mimo pořadí. Pokud chcete mít serializované <xref:System.ComponentModel.AsyncOperation.Post%2A> spuštění volání, implementujte a nainstalujte třídu. <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType>  
  
 Další informace o <xref:System.ComponentModel.AsyncOperation> <xref:System.ComponentModel.AsyncOperationManager> použití a povolení asynchronních operací naleznete v tématu [How to: Implement a Component that Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Pokyny  
  
- V ideálním případě by každá metoda vyvolání by měla být nezávislá na ostatních. Měli byste se vyhnout párování vyvolání se sdílenými prostředky. Pokud prostředky mají být sdíleny mezi vyvolání, budete muset poskytnout mechanismus správné synchronizace v implementaci.  
  
- Návrhy, které vyžadují klienta k implementaci synchronizace se nedoporučuje. Můžete mít například asynchronní metodu, která přijímá globální statický objekt jako parametr; více souběžných vyvolání takové metody může mít za následek poškození dat nebo zablokování.  
  
- Pokud implementujete metodu s přetížením více vyvolání (v`userState` podpisu), vaše třída bude muset spravovat kolekci uživatelských stavů nebo ID úloh a jejich odpovídající čekající operace. Tato kolekce by `lock` měla být chráněna s oblastmi, protože různé vyvolání přidat a odebrat `userState` objekty v kolekci.  
  
- Zvažte `CompletedEventArgs` opětovné použití tříd, pokud je to proveditelné a vhodné. V tomto případě není pojmenování konzistentní s názvem metody, <xref:System.EventArgs> protože daný delegát a typ nejsou vázány na jednu metodu. Však vynucení vývojáři přetypovat hodnotu <xref:System.EventArgs> načtenou z vlastnosti na však není nikdy přijatelné.  
  
- Pokud jste authoring třídy, <xref:System.ComponentModel.Component>která je odvozena z <xref:System.Threading.SynchronizationContext> , neimplementujte a neinstalujte vlastní třídu. Aplikační modely, nikoli součásti, <xref:System.Threading.SynchronizationContext> řídí, který se používá.  
  
- Při použití multithreading jakéhokoli druhu, můžete potenciálně vystavit sami velmi závažné a složité chyby. Před implementací jakéhokoli řešení, které používá vícevláknové, naleznete [v tématu Osvědčené postupy spravovaného podprocesu](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- [Implementace asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
