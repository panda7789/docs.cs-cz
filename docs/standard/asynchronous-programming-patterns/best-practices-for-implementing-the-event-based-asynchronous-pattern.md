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
ms.openlocfilehash: 561d0759af4f7557bae39540cbb00f8038726ddc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950812"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech
Asynchronní vzor založený na událostech poskytuje efektivní způsob, jak vystavit asynchronní chování ve třídách se známými sémantikou události a delegáta. Chcete-li implementovat asynchronní vzor založený na událostech, je nutné dodržovat určité konkrétní požadavky na chování. Následující části popisují požadavky a pokyny, které byste měli vzít v úvahu při implementaci třídy, která následuje za asynchronním vzorem založeným na událostech.  
  
 Přehled naleznete v tématu [implementace asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Požadované záruky chování  
 Při implementaci asynchronního vzoru založeného na událostech musíte poskytnout řadu záruk, které zajistí, že se vaše třída bude chovat správně a klienti vaší třídy mohou spoléhat na takové chování.  
  
### <a name="completion"></a>Dokončení  
 Vždy vyvolat obslužnou rutinu události <em>methodName</em>**Completed** po úspěšném dokončení, chybě nebo zrušení. Aplikace by nikdy neměly narazit na situaci, kdy zůstanou nečinné a k dokončení nedojde. Jedinou výjimkou z tohoto pravidla je, pokud je asynchronní operace navržená tak, aby se nikdy nedokončila.  
  
### <a name="completed-event-and-eventargs"></a>Dokončená událost a EventArgs  
 Pro každou samostatnou**asynchronní** metodu <em>methodName</em>použijte následující požadavky na návrh:  
  
- Definujte událost <em>methodName</em>**Completed** u stejné třídy jako metodu.  
  
- Definujte třídu a doprovodného <xref:System.ComponentModel.AsyncCompletedEventArgs> delegáta pro událost <em>methodName</em>**dokončenou** , která je odvozena od třídy. <xref:System.EventArgs> Název výchozí třídy by měl mít formu <em>methodName</em>**CompletedEventArgs**.  
  
- Zajistěte <xref:System.EventArgs> , aby byla třída specifická pro návratové hodnoty metody <em>methodName</em> . Při použití <xref:System.EventArgs> třídy byste nikdy neměli vyžadovat, aby vývojáři přetypování výsledku.  
  
     Následující příklad kódu ukazuje dobrou a chybnou implementaci tohoto požadavku na návrh.  
  
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
  
- Nedefinujte <xref:System.EventArgs> třídu pro vrácení metod, které vracejí `void`. Místo toho použijte instanci <xref:System.ComponentModel.AsyncCompletedEventArgs> třídy.  
  
- Ujistěte se, že jste vždycky vyvolali událost <em>methodName</em>**Completed** . Tato událost by měla být vyvolána po úspěšném dokončení, při chybě nebo při zrušení. Aplikace by nikdy neměly narazit na situaci, kdy zůstanou nečinné a k dokončení nedojde.  
  
- Ujistěte se, že máte zachycené výjimky, ke kterým dojde v asynchronní operaci, a přiřaďte <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> k vlastnosti Zachycenou výjimku.  
  
- Pokud při dokončování úlohy došlo k chybě, neměli byste mít přístup k výsledkům. Pokud vlastnost není, zajistěte, aby <xref:System.EventArgs> přístup k libovolné vlastnosti ve struktuře vyvolává výjimku. `null` <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> K provedení tohoto ověření použijte metodu.<xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A>  
  
- Vyprší časový limit pro chybu. Když dojde k vypršení časového limitu, vyvolejte událost <em>methodName</em>**Completed** <xref:System.TimeoutException> a přiřaďte <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnost.  
  
- Pokud vaše třída podporuje více souběžných volání, ujistěte se, že událost <em>methodName</em>**Completed** obsahuje příslušný `userSuppliedState` objekt.  
  
- Zajistěte, aby se událost <em>methodName</em>**Completed** vyvolala v příslušném vlákně a v odpovídající době v životním cyklu aplikace. Další informace naleznete v části vlákna a kontexty.  
  
### <a name="simultaneously-executing-operations"></a>Souběžné provádění operací  
  
- Pokud vaše třída podporuje více souběžných volání, umožněte vývojářům sledovat jednotlivá volání samostatně definováním asynchronního přetížení <em>methodName</em> , které přebírá parametr stavu s hodnotou objektu nebo ID úlohy, která se nazývá `userSuppliedState`. Tento parametr by měl být vždy posledním parametrem v signatuře**asynchronní** metody <em>methodName</em>.  
  
- Pokud vaše třída definuje**asynchronní** přetížení <em>methodName</em>, které přijímá parametr stavu s hodnotou objektu nebo ID úlohy, je nutné sledovat životnost operace s tímto ID úlohy a zajistit, aby byla vrácena zpět do obslužné rutiny dokončení. K dispozici jsou pomocné třídy, které vám můžou pomoct. Další informace o správě souběžnosti najdete v tématu [How to: Implementujte komponentu, která podporuje asynchronní vzor](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)založený na událostech.  
  
- Pokud vaše třída definuje**asynchronní** metodu <em>methodName</em>bez parametru State a nepodporuje více souběžných volání, zajistěte, aby všechny pokusy o vyvolání <em>methodName</em>**Async** před předchozí <em>methodName</em>  **Asynchronní** vyvolání dokončí <xref:System.InvalidOperationException>událost.  
  
- Obecně Nevolejte výjimku, pokud je**asynchronní** `userSuppliedState` Metoda <em>methodName</em>bez parametru vyvolána několikrát, aby bylo více nezpracovaných operací. Můžete vyvolat výjimku, pokud vaše třída explicitně nemůže zvládnout tuto situaci, ale předpokládat, že vývojáři mohou zpracovat tyto vícenásobná zpětná volání, která nerozlišuje.  
  
### <a name="accessing-results"></a>Přístup k výsledkům  
  
- Pokud při provádění asynchronní operace došlo k chybě, neměly by být k dispozici žádné výsledky. Zajistěte, aby přístup k <xref:System.ComponentModel.AsyncCompletedEventArgs> libovolné <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnosti v `null` rozhraní when nevolal výjimku <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>, na kterou odkazuje. <xref:System.ComponentModel.AsyncCompletedEventArgs> Třída<xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> poskytuje metodu pro tento účel.  
  
- Zajistěte, aby se všechny pokusy o <xref:System.InvalidOperationException> přístup k výsledku vyvolaly s oznámením, že operace byla zrušena. K provedení tohoto ověření použijte metodu.<xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType>  
  
### <a name="progress-reporting"></a>Vytváření sestav průběhu  
  
- Podporuje vytváření sestav o průběhu, pokud je to možné. To umožňuje vývojářům poskytnout lepší uživatelské prostředí aplikace při použití vaší třídy.  
  
- Pokud implementujete událost**ProgressChanged** **ProgressChanged** nebo <em>methodName</em>, ujistěte se, že neexistují žádné takové události, které se pro konkrétní asynchronní operace vyvolaly po události <em>methodName</em>**Completed** této operace. byl vyvolán.  
  
- Pokud se standard <xref:System.ComponentModel.ProgressChangedEventArgs> naplňuje, zajistěte <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> , aby bylo možné vždy interpretovat jako procento. Procentuální hodnota nemusí být přesná, ale měla by představovat procento. Pokud vaše metrika vytváření sestav o průběhu musí být jiná než procento, odvozuje třídu od <xref:System.ComponentModel.ProgressChangedEventArgs> třídy a ponechte <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> 0. Nepoužívejte nepoužitou metriku pro vytváření sestav, než je procento.  
  
- Zajistěte `ProgressChanged` , aby se událost vyvolala v příslušném vlákně a v odpovídající době v životním cyklu aplikace. Další informace naleznete v části vlákna a kontexty.  
  
### <a name="isbusy-implementation"></a>Zaneprázdněná implementace  
  
- Nezveřejňujte `IsBusy` vlastnost, pokud vaše třída podporuje více souběžných volání. Například proxy webové služby XML nezveřejňují `IsBusy` vlastnost, protože podporují více souběžných volání asynchronních metod.  
  
- `true` Vlastnost by měla vracet poté, co byla volána asynchronní metoda MethodName a předtím, než byla vyvolána událost MethodName Completed. `IsBusy` V opačném případě `false`by měl vrátit. Komponenty <xref:System.ComponentModel.BackgroundWorker> `IsBusy` a <xref:System.Net.WebClient> jsou příklady tříd, které zpřístupňují vlastnost.  
  
### <a name="cancellation"></a>Zrušení  
  
- Pokud je to možné, je zrušení podpory. To umožňuje vývojářům poskytnout lepší uživatelské prostředí aplikace při použití vaší třídy.  
  
- V případě zrušení nastavte <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> příznak <xref:System.ComponentModel.AsyncCompletedEventArgs> v objektu.  
  
- Zajistěte, aby se všechny pokusy o <xref:System.InvalidOperationException> přístup k výsledku vyvolaly s oznámením, že operace byla zrušena. K provedení tohoto ověření použijte metodu.<xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType>  
  
- Zajistěte, aby volání metody zrušení vždy vracela úspěšně, a nikdy nevyvolávají výjimku. Obecně platí, že klient není informován o tom, zda je operace v určitou dobu skutečně zrušena, a není oznámeno, zda bylo dříve vystavené zrušení úspěšné. Aplikace však bude vždy předána oznámením o úspěšném zrušení, protože aplikace je součástí stavu dokončení.  
  
- Vyvolat událost <em>methodName</em>**Completed** při zrušení operace.  
  
### <a name="errors-and-exceptions"></a>Chyby a výjimky  
  
- Zachyťte všechny výjimky, ke kterým dojde v asynchronní operaci, a nastavte <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> hodnotu vlastnosti na tuto výjimku.  
  
### <a name="threading-and-contexts"></a>Vlákna a kontexty  
 Pro správnou funkčnost vaší třídy je důležité, aby byly obslužné rutiny událostí klienta vyvolány ve správném vlákně nebo kontextu pro daný model aplikace, včetně aplikací ASP.NET a model Windows Forms. K dispozici jsou dvě důležité pomocné třídy, které zajistí, že se asynchronní třída chová správně v rámci <xref:System.ComponentModel.AsyncOperation> jakéhokoli <xref:System.ComponentModel.AsyncOperationManager>modelu aplikace: a.  
  
 <xref:System.ComponentModel.AsyncOperationManager>poskytuje jednu metodu, <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>která <xref:System.ComponentModel.AsyncOperation>vrací. Vaše volání <xref:System.ComponentModel.AsyncOperation> <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> asynchronní metody <em>methodName</em>a vaše třída používá vrácenou pro sledování životnosti asynchronní úlohy.  
  
 Chcete-li ohlásit průběh, přírůstkové výsledky a dokončení pro klienta, zavolejte <xref:System.ComponentModel.AsyncOperation.Post%2A> metody <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> a na <xref:System.ComponentModel.AsyncOperation>. <xref:System.ComponentModel.AsyncOperation>zodpovídá za zařazování volání do obslužných rutin událostí klienta do správného vlákna nebo kontextu.  
  
> [!NOTE]
> Tato pravidla můžete obejít, pokud výslovně chcete přejít na zásadu aplikačního modelu, ale stále výhodou dalších výhod použití asynchronního vzoru založeného na událostech. Například může být vhodné, aby třída provozovaná v model Windows Forms měla volné vlákno. Můžete vytvořit volnou třídu s více vlákny, pokud vývojářům rozumí předpokládaná omezení. Konzolové aplikace nesynchronizují provádění <xref:System.ComponentModel.AsyncOperation.Post%2A> volání. To může způsobit `ProgressChanged` , že události budou vyvolány mimo pořadí. Pokud chcete mít serializované spuštění <xref:System.ComponentModel.AsyncOperation.Post%2A> volání, implementujte a <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> nainstalujte třídu.  
  
 Další informace o použití <xref:System.ComponentModel.AsyncOperation> a <xref:System.ComponentModel.AsyncOperationManager> k povolení asynchronních operací naleznete v tématu [How to: Implementujte komponentu, která podporuje asynchronní vzor](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)založený na událostech.  
  
## <a name="guidelines"></a>Pokyny  
  
- V ideálním případě by každá volání metody měla být nezávislá na dalších. Nemusíte se vyhnout voláním spojení se sdílenými prostředky. Pokud se prostředky mají sdílet mezi vyvoláními, budete muset ve své implementaci zadat správný mechanismus synchronizace.  
  
- Nedoporučujeme návrhy, které vyžadují implementaci synchronizace klienta. Například můžete mít asynchronní metodu, která přijímá globální statický objekt jako parametr; víc souběžných volání takové metody může způsobit poškození dat nebo zablokování.  
  
- Pokud implementujete metodu s přetížením vícenásobného volání (`userState` v signatuře), vaše třída bude potřebovat spravovat kolekci stavů uživatele nebo ID úloh a jejich odpovídající operace, které čekají na zpracování. Tato kolekce by měla být chráněná pomocí `lock` oblastí, protože různá volání přidávají a odstraňují `userState` objekty v kolekci.  
  
- Zvažte možnost znovu `CompletedEventArgs` použít třídy, kde je to proveditelné a vhodné. V tomto případě není pojmenování konzistentní s názvem metody, protože daný delegát a <xref:System.EventArgs> typ nejsou vázané na jedinou metodu. Nicméně vynucení toho, aby vývojáři přetypování hodnoty načtené z vlastnosti <xref:System.EventArgs> na nejsou nikdy přijatelné.  
  
- Pokud vytváříte třídu, která je odvozena z <xref:System.ComponentModel.Component>, Neimplementujte a neinstalujte vlastní <xref:System.Threading.SynchronizationContext> třídu. Aplikační modely, nikoli komponenty, řídí <xref:System.Threading.SynchronizationContext> , který se používá.  
  
- Když použijete Multithreading s více vlákny, můžete si potenciálně vystavit hodně závažných a složitých chyb. Před implementací jakéhokoli řešení, které používá multithreading, si přečtěte téma [osvědčené postupy spravovaného vlákna](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- [Implementace asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Postupy: Použít komponenty, které podporují asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
