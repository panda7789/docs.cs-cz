---
title: Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 910edb8c79518f63e8b881b8eaecd69060fb6711
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech
Asynchronní vzor založený na událostech nabízí efektivní způsob, jak vystavit asynchronní chování v tříd pomocí známých událostí a delegovat sémantiku. Implementovat asynchronní vzor založený na událostech, budete muset postupovat podle několik požadavků na konkrétní chování. Následující části popisují požadavky a pokyny, které byste měli zvážit při implementaci třídy, která odpovídá asynchronní vzor založený na událostech.  
  
 Přehled najdete v tématu [implementace asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Požadované chování záruky  
 Pokud budete implementovat asynchronní vzor založený na událostech, zadejte počet záruky, aby se zajistilo třídě budou chovat správně a může se spoléhat na takové chování klientů vaší třídy.  
  
### <a name="completion"></a>Dokončení  
 Vždy vyvolat *MethodName *** dokončeno** obslužné rutiny události, když máte úspěšné dokončení, chybu nebo zrušení. Aplikace by nikdy dojít k situaci, kdy se zůstat v nečinnosti a dokončení se nikdy neprovádí. Jedinou výjimkou tohoto pravidla je, pokud asynchronní operaci samotné je navržené tak, aby se nedokončí.  
  
### <a name="completed-event-and-eventargs"></a>Dokončení události a EventArgs  
 Pro každou zvláštní *MethodName *** asynchronní** metoda, platí následující požadavky návrhu:  
  
-   Definování *MethodName *** dokončeno** události u stejné třídy jako metodu.  
  
-   Definovat <xref:System.EventArgs> třídy a doprovodné delegáta pro *MethodName *** dokončeno** událost, která je odvozena z <xref:System.ComponentModel.AsyncCompletedEventArgs> třídy. Výchozí název třídy musí být ve tvaru * MethodName ***CompletedEventArgs**.  
  
-   Ujistěte se, že <xref:System.EventArgs> třída je specifická pro vrácené hodnoty *MethodName* metoda. Při použití <xref:System.EventArgs> třída, byste měli nikdy vyžadovat vývojáři přetypovat výsledek.  
  
     Následující příklad kódu ukazuje funkční a chybný provádění tomuto požadavku návrhu v uvedeném pořadí.  
  
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
  
-   Nejsou definovány <xref:System.EventArgs> třídy pro vrácení metody, které vracejí `void`. Místo toho použít instanci systému <xref:System.ComponentModel.AsyncCompletedEventArgs> třídy.  
  
-   Ujistěte se, že vždy zvýšit *MethodName *** dokončeno** událostí. Tato událost má se vrhnout při úspěšném dokončení, na chybu nebo na zrušení. Aplikace by nikdy dojít k situaci, kdy se zůstat v nečinnosti a dokončení se nikdy neprovádí.  
  
-   Ujistěte se, zachytit všechny výjimky, které ve asynchronní operaci a přiřaďte zachycená výjimka, která má <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnost.  
  
-   Pokud došlo k chybě dokončení úlohy, nesmí být dostupný výsledky. Když <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnost není `null`, ujistěte se, že přístup k libovolné vlastnosti v <xref:System.EventArgs> struktura vyvolá výjimku. Použití <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> metoda k provedení tohoto ověření.  
  
-   Model vypršení časového limitu za chybu. Když dojde k vypršení časového limitu, zvýšit *MethodName *** dokončeno** událostí a přiřadit <xref:System.TimeoutException> k <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnost.  
  
-   Pokud vaše třída podporuje víc souběžných volání, ujistěte se, že *MethodName *** dokončeno** události obsahuje odpovídající `userSuppliedState` objektu.  
  
-   Ujistěte se, že *MethodName *** dokončeno** událost se vyvolá, na odpovídající vlákno a v příslušnou dobu v průběhu životního cyklu aplikace. Další informace najdete v části zřetězení a kontexty.  
  
### <a name="simultaneously-executing-operations"></a>Současně provádění operací  
  
-   Pokud vaše třída podporuje víc souběžných volání, povolte vývojáři sledovat každé vyvolání samostatně definováním *MethodName *** asynchronní** přetížení, které přijímá parametr s hodnotou objekt stavu nebo ID úkolu, nazývá `userSuppliedState`. Tento parametr by měl být vždy poslední parametr v *MethodName *** asynchronní** podpis metody.  
  
-   Pokud vaše třída definuje *MethodName *** asynchronní** přetížení, které přijímá parametr s hodnotou objekt stavu nebo ID úkolu, nezapomeňte sledovat dobu životnosti operace s tímto ID úloh a nezapomeňte poskytnout ho zpátky do obslužné rutiny ukončení . Existují pomocných tříd, které jsou k dispozici na pomoc. Další informace o řízení souběžného zpracování najdete v tématu [návod: implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
-   Pokud vaše třída definuje *MethodName *** asynchronní** metoda bez parametr stavu a nepodporuje více souběžných volání, ujistěte se, že jakýkoli pokus o vyvolání *MethodName *** asynchronní** před předchozího *MethodName *** asynchronní** volání dokončil vyvolá <xref:System.InvalidOperationException>.  
  
-   Obecně platí, nebyla vyvolána výjimka, pokud *MethodName *** asynchronní** metoda bez `userSuppliedState` parametr vyvolání vícekrát, aby byl více zbývajících operací. Může vyvolat výjimku, pokud třídě explicitně nelze zpracování této situace, ale předpokládá, že vývojáři může zpracovat tyto více nelze rozlišit zpětných volání  
  
### <a name="accessing-results"></a>Přístup k výsledky  
  
-   Pokud došlo k chybě při provádění asynchronní operace, nesmí být dostupný výsledky. Ujistěte se, že přístup k libovolné vlastnosti v <xref:System.ComponentModel.AsyncCompletedEventArgs> při <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> není `null` vyvolá výjimku odkazuje <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>. <xref:System.ComponentModel.AsyncCompletedEventArgs> Třída poskytuje <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> metoda pro tento účel.  
  
-   Ujistěte se, že žádný pokus o přístup vyvolá výsledek <xref:System.InvalidOperationException> s oznámením, že operace byla zrušena. Použití <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> metoda k provedení tohoto ověření.  
  
### <a name="progress-reporting"></a>Průběh vytváření sestav  
  
-   Podpora tvorby sestav průběh, pokud je to možné. To umožňuje vývojářům poskytovat lepší uživatelské prostředí aplikace při použití třídě.  
  
-   Pokud budete implementovat **ProgressChanged** nebo *MethodName *** ProgressChanged** událostí, ujistěte se, že neexistují žádné takové události vyvolané pro konkrétní asynchronní operaci po této operaci na *MethodName *** dokončeno** událost byla vyvolána.  
  
-   Pokud standardní <xref:System.ComponentModel.ProgressChangedEventArgs> se naplní, ujistěte se, že <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> vždy jde interpretovat jako procento. Procento nemusí být přesné, ale jeho by měl představovat procento. Pokud průběh reporting metrika musí být něco jiného než procento, odvození třídy z <xref:System.ComponentModel.ProgressChangedEventArgs> třídy a nechte <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> na 0. Nepoužívejte reporting metrika než v procentech.  
  
-   Ujistěte se, že `ProgressChanged` událost se vyvolá, na odpovídající vlákno a v příslušnou dobu v průběhu životního cyklu aplikace. Další informace najdete v části zřetězení a kontexty.  
  
### <a name="isbusy-implementation"></a>Implementace IsBusy  
  
-   Nevystavujte `IsBusy` vlastnost, pokud vaše třída podporuje víc souběžných volání. Například XML webové proxy servery služby nezveřejňují `IsBusy` vlastnost protože podporují více souběžných volání asynchronních metod.  
  
-   `IsBusy` Vlastnost by měla vrátit `true` po *MethodName *** asynchronní** byla volána metoda a před *MethodName *** dokončeno** událost byla vyvolána. V opačném případě by měla vrátit `false`. <xref:System.ComponentModel.BackgroundWorker> a <xref:System.Net.WebClient> součásti jsou příklady tříd, které zveřejňují `IsBusy` vlastnost.  
  
### <a name="cancellation"></a>Zrušení  
  
-   Podpora zrušení, pokud je to možné. To umožňuje vývojářům poskytovat lepší uživatelské prostředí aplikace při použití třídě.  
  
-   V případě zrušení, nastavte <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> příznak v <xref:System.ComponentModel.AsyncCompletedEventArgs> objektu.  
  
-   Ujistěte se, že žádný pokus o přístup vyvolá výsledek <xref:System.InvalidOperationException> s oznámením, že operace byla zrušena. Použití <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> metoda k provedení tohoto ověření.  
  
-   Zajistěte, aby vždy vrátí úspěšně volání metody zrušení a nikdy vyvolat výjimku. Obecně platí klient není upozornění, jestli je možné skutečně zrušit operace v každém okamžiku a nezobrazí upozornění, jestli byl úspěšný dřív vydaných zrušení. Ale aplikace vždy dostanou oznámení při zrušení byly úspěšné, protože aplikace se účastní stav dokončení.  
  
-   Vyvolat *MethodName *** dokončeno** událost v případě, že byla operace zrušena.  
  
### <a name="errors-and-exceptions"></a>Chyby a výjimky  
  
-   Catch – všechny výjimky, které ve asynchronní operaci a nastavte hodnotu <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> vlastnost této výjimky.  
  
### <a name="threading-and-contexts"></a>Zřetězení a kontexty  
 Pro správné fungování třídě, je důležité, aby obslužné rutiny událostí klienta jsou vyvolány na správné vlákno nebo kontext pro dané aplikaci modelu, včetně [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] a formulářových aplikací Windows. K zajištění správně chová asynchronní třídu v rámci modelu všechny aplikace jsou uvedeny dvě důležité pomocné třídy: <xref:System.ComponentModel.AsyncOperation> a <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager> poskytuje jednu metodu <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>, která vrátí <xref:System.ComponentModel.AsyncOperation>. Vaše *MethodName *** asynchronní** volání metod <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> a používá třídu vrácený <xref:System.ComponentModel.AsyncOperation> sledovat životnost asynchronní úlohu.  
  
 Chcete-li sestavy průběhu, přírůstkové výsledky a dokončení klientovi, volejte <xref:System.ComponentModel.AsyncOperation.Post%2A> a <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> metody na <xref:System.ComponentModel.AsyncOperation>. <xref:System.ComponentModel.AsyncOperation> zodpovídá za zařazování volání obslužné rutiny událostí klienta do správné vlákna nebo kontextu.  
  
> [!NOTE]
>  Tato pravidla můžete obejít, pokud explicitně chcete přejít na zásad aplikačního modelu služby, ale stále těžit z další výhody použití asynchronního vzoru založeného na událostech. Můžete například, že třídu operační ve Windows Forms jako volné zařazování. Volné zařazování třídu, můžete vytvořit tak dlouho, dokud vývojáři pochopit předpokládané omezení. Konzolové aplikace nesynchronizovat provádění <xref:System.ComponentModel.AsyncOperation.Post%2A> volání. To může způsobit `ProgressChanged` události, které má být aktivována mimo pořadí. Pokud chcete mít serializovat provádění <xref:System.ComponentModel.AsyncOperation.Post%2A> volání, implementaci a nainstalovat <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> třídy.  
  
 Další informace o používání <xref:System.ComponentModel.AsyncOperation> a <xref:System.ComponentModel.AsyncOperationManager> povolit asynchronních operací, najdete v části [návod: implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Pokyny  
  
-   V ideálním případě by měl být každé volání metody nezávisle na ostatních. Vyhněte se spojovacím volání se sdílenými prostředky. Pokud prostředky se mají být sdílena mezi volání, musíte zadat správný synchronizační mechanismus v implementaci.  
  
-   Návrhy, které vyžadují implementace synchronizace klienta se nedoporučuje. Například můžete mít asynchronní metody, která přijímá objekt globální statické jako parametr; více souběžných volání tato metoda by mohla způsobit poškození dat nebo zablokování.  
  
-   Pokud implementujete metodu s více volání přetížení (`userState` v podpisu), třídě bude muset spravovat kolekci stavů uživatele nebo ID úloh a jejich odpovídajících čekající operace. Tato kolekce by měly být chráněné s `lock` oblastí, protože u různých volání přidávat a odebírat `userState` objekty v kolekci.  
  
-   Zvažte použití `CompletedEventArgs` třídy, pokud je to vhodné a vhodné. V takovém případě není konzistentní s názvem metody pojmenování protože dané delegáta a <xref:System.EventArgs> nejsou typu vázané na jedné metody. Ale vynucení vývojářům načíst z vlastnosti na hodnotu přetypovat <xref:System.EventArgs> nikdy je přijatelná.  
  
-   Vytváříte-li třídu odvozenou z <xref:System.ComponentModel.Component>, není implementovat a nainstalujte si vlastní <xref:System.Threading.SynchronizationContext> třídy. Modely aplikace, není součástí, ovládacího prvku <xref:System.Threading.SynchronizationContext> používané.  
  
-   Při použití více vláken jakéhokoli druhu potenciálně vystavit sami na velmi závažnou a komplexní chyby. Před implementací jakéhokoli řešení, které používá více vláken, najdete v části [spravované dělení na vlákna osvědčené postupy](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Implementace asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [Vícevláknové programování s asynchronním vzorem založeným na událostech](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 [Návod: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
