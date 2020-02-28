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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156046"
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
  
- Definujte třídu <xref:System.EventArgs> a doprovodného delegáta pro událost <em>methodName</em>**dokončenou** , která je odvozena od <xref:System.ComponentModel.AsyncCompletedEventArgs> třídy. Název výchozí třídy by měl mít formu <em>methodName</em>**CompletedEventArgs**.  
  
- Ujistěte se, že třída <xref:System.EventArgs> je specifická pro návratové hodnoty metody <em>methodName</em> . Pokud používáte třídu <xref:System.EventArgs>, neměli byste od vývojářů nikdy vyžadovat, aby přetypování výsledku.  
  
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
  
- Nedefinujte třídu <xref:System.EventArgs> pro vracení metod, které vracejí `void`. Místo toho použijte instanci třídy <xref:System.ComponentModel.AsyncCompletedEventArgs>.  
  
- Ujistěte se, že jste vždycky vyvolali událost <em>methodName</em>**Completed** . Tato událost by měla být vyvolána po úspěšném dokončení, při chybě nebo při zrušení. Aplikace by nikdy neměly narazit na situaci, kdy zůstanou nečinné a k dokončení nedojde.  
  
- Ujistěte se, že máte zachycené výjimky, ke kterým dojde v asynchronní operaci, a přiřaďte Zachycenou výjimku vlastnosti <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>.  
  
- Pokud při dokončování úlohy došlo k chybě, neměli byste mít přístup k výsledkům. Pokud vlastnost <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> není `null`, zajistěte, aby přístup k libovolné vlastnosti ve struktuře <xref:System.EventArgs> vyvolává výjimku. K provedení tohoto ověření použijte metodu <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A>.  
  
- Vyprší časový limit pro chybu. Když dojde k vypršení časového limitu, vyvolejte událost <em>methodName</em>**Completed** a přiřaďte <xref:System.TimeoutException> k vlastnosti <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>.  
  
- Pokud vaše třída podporuje více souběžných volání, ujistěte se, že událost <em>methodName</em>**Completed** obsahuje příslušný objekt `userSuppliedState`.  
  
- Zajistěte, aby se událost <em>methodName</em>**Completed** vyvolala v příslušném vlákně a v odpovídající době v životním cyklu aplikace. Další informace naleznete v části vlákna a kontexty.  
  
### <a name="simultaneously-executing-operations"></a>Souběžné provádění operací  
  
- Pokud vaše třída podporuje více souběžných volání, umožněte vývojářům sledovat každé vyvolání samostatně definováním**asynchronního** přetížení <em>methodName</em>, které přijímá parametr stavu s hodnotou objektu, nebo ID úlohy s názvem `userSuppliedState`. Tento parametr by měl být vždy posledním parametrem v signatuře**asynchronní** metody <em>methodName</em>.  
  
- Pokud vaše třída definuje**asynchronní** přetížení <em>methodName</em>, které přijímá parametr stavu s hodnotou objektu nebo ID úlohy, je nutné sledovat životnost operace s tímto ID úlohy a zajistit, aby byla vrácena zpět do obslužné rutiny dokončení. K dispozici jsou pomocné třídy, které vám můžou pomoct. Další informace o správě souběžnosti naleznete v tématu [How to: Implementing a Component, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
- Pokud vaše třída definuje**asynchronní** metodu <em>methodName</em>bez parametru State a nepodporuje více souběžných volání, zajistěte, aby všechny pokusy o vyvolání <em>methodName</em>**Async** předtím, než se dokončilo předchozí**asynchronní** vyvolání <em>methodName</em>, vyvolává <xref:System.InvalidOperationException>.  
  
- Obecně Nevolejte výjimku, pokud je**asynchronní** metoda <em>MethodName</em>bez parametru `userSuppliedState` vyvolána několikrát, aby bylo více nezpracovaných operací. Můžete vyvolat výjimku, pokud vaše třída explicitně nemůže zvládnout tuto situaci, ale předpokládat, že vývojáři mohou zpracovat tyto vícenásobná zpětná volání, která nerozlišuje.  
  
### <a name="accessing-results"></a>Přístup k výsledkům  
  
- Pokud při provádění asynchronní operace došlo k chybě, neměly by být k dispozici žádné výsledky. Zajistěte, aby přístup k libovolné vlastnosti v <xref:System.ComponentModel.AsyncCompletedEventArgs>, když <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> není `null` vyvolá výjimku, na kterou odkazuje <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>. Třída <xref:System.ComponentModel.AsyncCompletedEventArgs> poskytuje metodu <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> pro tento účel.  
  
- Zajistěte, aby všechny pokusy o přístup k výsledku vyvolaly <xref:System.InvalidOperationException> oznamující, že operace byla zrušena. K provedení tohoto ověření použijte metodu <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType>.  
  
### <a name="progress-reporting"></a>Vytváření sestav průběhu  
  
- Podporuje vytváření sestav o průběhu, pokud je to možné. To umožňuje vývojářům poskytnout lepší uživatelské prostředí aplikace při použití vaší třídy.  
  
- Pokud implementujete událost**ProgressChanged** **ProgressChanged** nebo <em>methodName</em>, zajistěte, aby se žádné takové události neaktivovaly pro konkrétní asynchronní operaci po vygenerování <em>methodName</em>události**dokončení** této operace.  
  
- Pokud se naplní standardní <xref:System.ComponentModel.ProgressChangedEventArgs>, ujistěte se, že <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> může být vždy interpretována jako procento. Procentuální hodnota nemusí být přesná, ale měla by představovat procento. Pokud metrika vytváření sestav průběhu musí být jiná než procento, odvozuje třídu od třídy <xref:System.ComponentModel.ProgressChangedEventArgs> a nechte <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> na 0. Nepoužívejte nepoužitou metriku pro vytváření sestav, než je procento.  
  
- Zajistěte, aby se událost `ProgressChanged`a vyvolala v příslušném vlákně a v odpovídající době v životním cyklu aplikace. Další informace naleznete v části vlákna a kontexty.  
  
### <a name="isbusy-implementation"></a>Zaneprázdněná implementace  
  
- Nezveřejňujte vlastnost `IsBusy`, pokud vaše třída podporuje více souběžných volání. Například proxy webové služby XML nezveřejňují vlastnost `IsBusy`, protože podporují více souběžných volání asynchronních metod.  
  
- Vlastnost `IsBusy` by měla vracet `true` poté, co byla volána**asynchronní** metoda <em>methodName</em>a předtím, než byla vyvolána událost <em>methodName</em>**Completed** . V opačném případě by měl vrátit `false`. Komponenty <xref:System.ComponentModel.BackgroundWorker> a <xref:System.Net.WebClient> jsou příklady tříd, které zpřístupňují vlastnost `IsBusy`.  
  
### <a name="cancellation"></a>Zrušení  
  
- Pokud je to možné, je zrušení podpory. To umožňuje vývojářům poskytnout lepší uživatelské prostředí aplikace při použití vaší třídy.  
  
- V případě zrušení nastavte příznak <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> v objektu <xref:System.ComponentModel.AsyncCompletedEventArgs>.  
  
- Zajistěte, aby všechny pokusy o přístup k výsledku vyvolaly <xref:System.InvalidOperationException> oznamující, že operace byla zrušena. K provedení tohoto ověření použijte metodu <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType>.  
  
- Zajistěte, aby volání metody zrušení vždy vracela úspěšně, a nikdy nevyvolávají výjimku. Obecně platí, že klient není informován o tom, zda je operace v určitou dobu skutečně zrušena, a není oznámeno, zda bylo dříve vystavené zrušení úspěšné. Aplikace však bude vždy předána oznámením o úspěšném zrušení, protože aplikace je součástí stavu dokončení.  
  
- Vyvolat událost <em>methodName</em>**Completed** při zrušení operace.  
  
### <a name="errors-and-exceptions"></a>Chyby a výjimky  
  
- Zachyťte všechny výjimky, ke kterým dojde v asynchronní operaci, a nastavte hodnotu vlastnosti <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> na tuto výjimku.  
  
### <a name="threading-and-contexts"></a>Vlákna a kontexty  
 Pro správnou funkčnost vaší třídy je důležité, aby byly obslužné rutiny událostí klienta vyvolány ve správném vlákně nebo kontextu pro daný model aplikace, včetně aplikací ASP.NET a model Windows Forms. K dispozici jsou dvě důležité pomocné třídy, které zajistí, že se asynchronní třída chová správně v rámci jakéhokoli modelu aplikace: <xref:System.ComponentModel.AsyncOperation> a <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager> poskytuje jednu metodu, <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>, která vrací <xref:System.ComponentModel.AsyncOperation>. **Asynchronní** metoda <em>methodName</em>volá <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> a vaše třída používá vrácenou <xref:System.ComponentModel.AsyncOperation> ke sledování životnosti asynchronní úlohy.  
  
 Chcete-li ohlásit průběh, přírůstkové výsledky a doplňování klienta, zavolejte <xref:System.ComponentModel.AsyncOperation.Post%2A> a <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> metody na <xref:System.ComponentModel.AsyncOperation>. <xref:System.ComponentModel.AsyncOperation> zodpovídá za zařazování volání do obslužných rutin událostí klienta do správného vlákna nebo kontextu.  
  
> [!NOTE]
> Tato pravidla můžete obejít, pokud výslovně chcete přejít na zásadu aplikačního modelu, ale stále výhodou dalších výhod použití asynchronního vzoru založeného na událostech. Například může být vhodné, aby třída provozovaná v model Windows Forms měla volné vlákno. Můžete vytvořit volnou třídu s více vlákny, pokud vývojářům rozumí předpokládaná omezení. Konzolové aplikace nesynchronizují provádění <xref:System.ComponentModel.AsyncOperation.Post%2A> volání. To může způsobit, že `ProgressChanged` události budou vyvolány mimo pořadí. Pokud chcete mít serializované spuštění volání <xref:System.ComponentModel.AsyncOperation.Post%2A>, implementujte a nainstalujte <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> třídu.  
  
 Další informace o použití <xref:System.ComponentModel.AsyncOperation> a <xref:System.ComponentModel.AsyncOperationManager> k povolení asynchronních operací naleznete v tématu [How to: Implementing a Component, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Pokyny  
  
- V ideálním případě by každá volání metody měla být nezávislá na dalších. Nemusíte se vyhnout voláním spojení se sdílenými prostředky. Pokud se prostředky mají sdílet mezi vyvoláními, budete muset ve své implementaci zadat správný mechanismus synchronizace.  
  
- Nedoporučujeme návrhy, které vyžadují implementaci synchronizace klienta. Například můžete mít asynchronní metodu, která přijímá globální statický objekt jako parametr; víc souběžných volání takové metody může způsobit poškození dat nebo zablokování.  
  
- Pokud implementujete metodu s přetížením vícenásobného vyvolání (`userState` v signatuře), vaše třída bude potřebovat spravovat kolekci stavů uživatele nebo ID úloh a jejich odpovídající operace, které čekají na zpracování. Tato kolekce by měla být chráněná `lock`mi oblastmi, protože různá volání v kolekci přidávají a odstraňují `userState` objekty.  
  
- Zvažte možnost znovu použít `CompletedEventArgs` třídy, kde je to proveditelné a vhodné. V tomto případě není pojmenování konzistentní s názvem metody, protože daný delegát a typ <xref:System.EventArgs> nejsou vázány na jedinou metodu. Nicméně vynucování vývojářů k přetypování hodnoty načtené z vlastnosti v <xref:System.EventArgs> nikdy nepřijatelné.  
  
- Pokud vytváříte třídu, která je odvozena z <xref:System.ComponentModel.Component>, Neimplementujte a neinstalujte vlastní třídu <xref:System.Threading.SynchronizationContext>. Aplikační modely, nikoli komponenty, řídí <xref:System.Threading.SynchronizationContext>, který se používá.  
  
- Když použijete Multithreading s více vlákny, můžete si potenciálně vystavit hodně závažných a složitých chyb. Před implementací jakéhokoli řešení, které používá multithreading, si přečtěte téma [osvědčené postupy spravovaného vlákna](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
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
