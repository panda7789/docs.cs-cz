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
ms.openlocfilehash: bbffed49d0137f3babde8ba75e3f5d91db00751c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61870107"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech
Asynchronní vzor založený na událostech poskytuje účinný způsob, jak vystavit asynchronní chování v třídy pomocí známých události a delegovat sémantiku. K implementaci asynchronního vzoru založeného na událostech, budete muset postupovat podle některých zvláštní chování požadavky. Následující části popisují požadavky a pokyny, které byste měli zvážit při implementaci třídy, která používá asynchronní vzor založený na událostech.  
  
 Přehled najdete v tématu [implementace asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Požadované chování záruky  
 Pokud se rozhodnete implementovat asynchronní vzor založený na událostech, je nutné zadat číslo záruk zajistěte, aby vaše třída se bude chovat správně a na takové chování můžete spoléhat, klienti vaší třídy.  
  
### <a name="completion"></a>Dokončení  
 Vždy vyvolá <em>MethodName</em>**dokončeno** obslužná rutina události, když máte úspěšné dokončení, chybě nebo zrušení. Aplikace by nikdy dojít k situaci, kdy jsou zůstat v nečinnosti a dokončení se nikdy neprovádí. Jedinou výjimkou tohoto pravidla je, pokud asynchronní operace, samotného je navržený tak, aby nikdy nedokončí.  
  
### <a name="completed-event-and-eventargs"></a>Událost dokončení a EventArgs  
 Pro každou zvláštní <em>MethodName</em>**asynchronní** metody, platí následující požadavky na návrh:  
  
- Definování <em>MethodName</em>**dokončeno** události na stejné třídy jako metodu.  
  
- Definování <xref:System.EventArgs> třídy a doprovodných delegáta pro <em>MethodName</em>**dokončeno** událost, která je odvozena z <xref:System.ComponentModel.AsyncCompletedEventArgs> třídy. Výchozí název třídy by měl být ve tvaru <em>MethodName</em>**CompletedEventArgs**.  
  
- Ujistěte se, že <xref:System.EventArgs> třída je specifická pro vrácené hodnoty <em>MethodName</em> metody. Při použití <xref:System.EventArgs> třídy by nikdy vyžadujete vývojářům přetypujte výsledek.  
  
     Následující příklad kódu ukazuje implementaci dobré a špatné tomuto požadavku návrhu v uvedeném pořadí.  
  
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
  
- Nedefinujte <xref:System.EventArgs> třídy pro vrácení metody, které vracejí `void`. Místo toho použijte instanci <xref:System.ComponentModel.AsyncCompletedEventArgs> třídy.  
  
- Ujistěte se, že vždy zvýšit <em>MethodName</em>**dokončeno** událostí. Při úspěšném dokončení, chybě nebo zrušení, by měla tato událost vyvolána. Aplikace by nikdy dojít k situaci, kdy jsou zůstat v nečinnosti a dokončení se nikdy neprovádí.  
  
- Ujistěte se, můžete zachytit žádné výjimky, které probíhá asynchronní operace a přiřaďte Zachycenou výjimku do <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnost.  
  
- Došlo k chybě, dokončení úkolu, výsledky by neměl být přístupný. Když <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnost není `null`, zkontrolujte, že přístup k žádné vlastnosti v <xref:System.EventArgs> struktury vyvolá výjimku. Použití <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> metody k provedení tohoto ověření.  
  
- Model vypršení časového limitu za chybu. Pokud dojde k vypršení časového limitu, zvýšit <em>MethodName</em>**dokončeno** událostí a přiřazení <xref:System.TimeoutException> k <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnost.  
  
- Pokud vaše třída podporuje více souběžných volání, ujistěte se, že <em>MethodName</em>**dokončeno** událost obsahuje odpovídající `userSuppliedState` objektu.  
  
- Ujistěte se, <em>MethodName</em>**dokončeno** událost se vyvolá u příslušné vlákna a v příslušnou dobu v životního cyklu aplikací. Další informace naleznete v oddílu zřetězení a kontexty.  
  
### <a name="simultaneously-executing-operations"></a>Současně provádění operací  
  
- Pokud vaše třída podporuje více souběžných volání, umožňují vývojářům sledovat každé vyvolání samostatně tak, že definujete <em>MethodName</em>**asynchronní** přetížení přebírající stavu s hodnotou objektu parametr nebo ID úlohy, volá `userSuppliedState`. Tento parametr by měl vždy být posledním parametrem v <em>MethodName</em>**asynchronní** podpis metody.  
  
- Pokud vaše třída definuje <em>MethodName</em>**asynchronní** přetížení přebírající parametr s hodnotou objektu stavu nebo ID úlohy, je potřeba sledovat dobu života operace s tímto ID úloh a nezapomeňte uvést zpět obslužné rutině dokončení. Nejsou k dispozici jako pomoc pomocné třídy. Další informace o správě souběžnosti, naleznete v tématu [jak: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
- Pokud vaše třída definuje <em>MethodName</em>**asynchronní** metody bez parametru state a nepodporuje více souběžných volání, ujistěte se, že žádný pokus o vyvolání <em>MethodName</em>  **Asynchronní** před předchozího <em>MethodName</em>**asynchronní** vyvolání dokončení vyvolá <xref:System.InvalidOperationException>.  
  
- Obecně platí, není vyvolána výjimka, pokud <em>MethodName</em>**asynchronní** metody bez `userSuppliedState` parametr je vyvolána více než jednou, takže existují více zbývajících operací. Může vyvolat výjimku, pokud vaše třída explicitně nelze zpracovat takové situaci, ale předpokládá, že vývojáři dokáže zpracovat tyto více odlišitelné zpětná volání  
  
### <a name="accessing-results"></a>Přístup k výsledky  
  
- Pokud došlo k chybě při provádění asynchronní operace, výsledky by neměl být přístupný. Zkontrolujte, že přístup k žádné vlastnosti v <xref:System.ComponentModel.AsyncCompletedEventArgs> při <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> není `null` vyvolá výjimku odkazuje <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>. <xref:System.ComponentModel.AsyncCompletedEventArgs> Třída poskytuje <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> metodu pro tento účel.  
  
- Ujistěte se, že žádný pokus o přístup k výsledku vyvolá <xref:System.InvalidOperationException> s informacemi o tom, že operace byla zrušena. Použití <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> metody k provedení tohoto ověření.  
  
### <a name="progress-reporting"></a>Vykazování průběhu  
  
- Podporu vytváření sestav průběhu, pokud je to možné. To umožňuje vývojářům poskytují lepší výkon aplikací při použití vaší třídy.  
  
- Pokud se rozhodnete implementovat **ProgressChanged** nebo <em>MethodName</em>**ProgressChanged** událostí, ujistěte se, že neexistují žádné takové události vyvolané pro konkrétní asynchronní operace Po provedení této operace <em>MethodName</em>**dokončeno** byla vyvolána událost.  
  
- Pokud standardní <xref:System.ComponentModel.ProgressChangedEventArgs> se zatím připravují, ujistěte se, že <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> může být interpretován vždy v procentech. Procento nemusí být přesné, ale to by měly představovat procenta. Pokud svůj postup vytváření sestav metriky musí být něco jiného než procento, odvoďte třídu z <xref:System.ComponentModel.ProgressChangedEventArgs> třídy a nechat <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> na 0. Vyhněte se použití sestav metriky než procenta.  
  
- Ujistěte se, `ProgressChanged` událost se vyvolá u příslušné vlákna a v příslušnou dobu v životního cyklu aplikací. Další informace naleznete v oddílu zřetězení a kontexty.  
  
### <a name="isbusy-implementation"></a>Implementace IsBusy  
  
- Nezveřejňujte `IsBusy` vlastnosti, pokud vaše třída podporuje více souběžných volání. Například proxy XML webové služby bez odkrytí `IsBusy` vlastnost vzhledem k tomu, které podporují více souběžných volání asynchronní metody.  
  
- `IsBusy` Vlastnost by měla vrátit `true` po <em>MethodName</em>**asynchronní** byla volána metoda a před <em>MethodName</em>  **Dokončení** byla vyvolána událost. V opačném případě by měla vrátit `false`. <xref:System.ComponentModel.BackgroundWorker> a <xref:System.Net.WebClient> komponenty jsou příklady tříd, které zprostředkovávají `IsBusy` vlastnost.  
  
### <a name="cancellation"></a>Zrušení  
  
- Podporu zrušení, pokud je to možné. To umožňuje vývojářům poskytují lepší výkon aplikací při použití vaší třídy.  
  
- V případě zrušení, nastavte <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> příznak v <xref:System.ComponentModel.AsyncCompletedEventArgs> objektu.  
  
- Ujistěte se, že žádný pokus o přístup k výsledku vyvolá <xref:System.InvalidOperationException> s informacemi o tom, že operace byla zrušena. Použití <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> metody k provedení tohoto ověření.  
  
- Zajistěte, aby vždy vrátí úspěšně volání metody zrušení a nikdy vyvolat výjimku. Obecně platí klient nezobrazí upozornění, že jde o tom, zda operace je skutečně možné zrušit v daném okamžiku a nezobrazí upozornění, že jde o tom, jestli byla úspěšná u dřív vydaných zrušení. Ale aplikace vždy dostanou oznámení při zrušení úspěšné, protože aplikace podílí na stav dokončení.  
  
- Vyvolat <em>MethodName</em>**dokončeno** událost v případě, že operace se zrušila.  
  
### <a name="errors-and-exceptions"></a>Chyby a výjimky  
  
- Zachytit žádné výjimky, které probíhá asynchronní operace a nastavte hodnotu <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> vlastnosti pro tuto výjimku.  
  
### <a name="threading-and-contexts"></a>Zřetězení a kontext  
 Pro správné fungování vaší třídy, je velmi důležité, že obslužné rutiny událostí klienta jsou vyvolány na řádné vlákna nebo kontextu pro daný aplikační model, včetně [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] a aplikace Windows Forms. Dvě důležité pomocné třídy jsou poskytovány k zajištění, že vaše asynchronní třída chová všechny aplikační model: <xref:System.ComponentModel.AsyncOperation> a <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager> poskytuje jednu metodu <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>, která vrátí <xref:System.ComponentModel.AsyncOperation>. Vaše <em>MethodName</em>**asynchronní** volání metody <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> a používá třídu vráceného <xref:System.ComponentModel.AsyncOperation> ke sledování doby života asynchronní úlohy.  
  
 K hlášení průběhu, přírůstkové výsledky a dokončování klientovi, zavolejte <xref:System.ComponentModel.AsyncOperation.Post%2A> a <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> metody <xref:System.ComponentModel.AsyncOperation>. <xref:System.ComponentModel.AsyncOperation> je zodpovědná za zařazování volání obslužné rutiny událostí klienta do správné vlákna nebo kontextu.  
  
> [!NOTE]
>  Tato pravidla mohou obejít, pokud explicitně chcete se dostat na zásad aplikačního modelu, ale přesto využívat výhod další výhody plynoucí z použití asynchronního vzoru založeného na událostech. Můžete například, že třída provoz ve Windows Forms to bude zdarma vláken. Můžete vytvořit třídu volného vláken, za předpokladu, seznamte se s vývojáři implicitní omezením. Konzolové aplikace nesynchronizovat provádění <xref:System.ComponentModel.AsyncOperation.Post%2A> volání. To může způsobit `ProgressChanged` události, které mají být vyvolána mimo pořadí. Pokud chcete mít serializovat provádění <xref:System.ComponentModel.AsyncOperation.Post%2A> volání, implementovat a nainstalujte <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> třídy.  
  
 Další informace o používání <xref:System.ComponentModel.AsyncOperation> a <xref:System.ComponentModel.AsyncOperationManager> Povolit asynchronní operace, naleznete v tématu [jak: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Pokyny  
  
- V ideálním případě by měl být každé volání metody nezávisle na ostatních. Měli byste se vyhnout, párování volání se sdílenými prostředky. Pokud prostředky jsou sdílena mezi vyvoláními, musíte poskytnout správný synchronizační mechanismus v implementaci.  
  
- Návrhy, které vyžadují klienta tak, aby implementace synchronizace se nedoporučuje. Můžete mít například asynchronní metodu, která bude přijímat globální statický objekt jako parametr; více souběžných volání této metody by mohlo způsobit poškození dat nebo zablokování.  
  
- Pokud se rozhodnete implementovat metodu s více volání přetížení (`userState` v podpisu), bude nutné spravovat kolekce stavů uživatele nebo ID úlohy a jejich odpovídající čekajících operací vaší třídy. Tato kolekce se dají chránit pomocí `lock` oblastí, protože různé volání přidávat a odebírat `userState` objektů v kolekci.  
  
- Vezměte v úvahu opětovné použití `CompletedEventArgs` třídy tam, kde a proveditelné. V takovém případě není konzistentní s názvem metody pojmenování protože dané delegáta a <xref:System.EventArgs> typu nejsou vázané na jedinou metodu. Ale vynucení vývojářům přetypujte hodnotu na načten z vlastnosti <xref:System.EventArgs> není nikdy přijatelné.  
  
- Vytváříte-li třídu, která je odvozena z <xref:System.ComponentModel.Component>neměňte implementovat a nainstalujte vlastní <xref:System.Threading.SynchronizationContext> třídy. Modely aplikace, není součástí, ovládací prvek <xref:System.Threading.SynchronizationContext> , který se používá.  
  
- Pokud používáte multithreading jakéhokoli druhu, potenciálně zpřístupníte sami velmi závažných a složitých chyb. Před implementací jakéhokoli řešení, které používá multithreadingu naleznete v tématu [spravovaných vláken osvědčené postupy](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
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
- [Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
