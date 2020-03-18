---
title: Přehled asynchronních vzorů založených na událostech
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 792aa8da-918b-458e-b154-9836b97735f3
ms.openlocfilehash: cce01a7c87f6f20b5e6c46881b8c863bb5a72a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160064"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Přehled asynchronních vzorů založených na událostech
Aplikace, které provádějí mnoho úloh současně, ale přesto zůstávají reagovat na interakci s uživatelem, často vyžadují návrh, který používá více vláken. Obor <xref:System.Threading> názvů poskytuje všechny nástroje potřebné k vytvoření vysoce výkonných vícevláknových aplikací, ale použití těchto nástrojů efektivně vyžaduje značné zkušenosti s vícevláknovým softwarovým inženýrstvím. Pro relativně jednoduché aplikace s <xref:System.ComponentModel.BackgroundWorker> více vlákny poskytuje komponenta jednoduché řešení. Pro sofistikovanější asynchronní aplikace zvažte implementaci třídy, která dodržuje asynchronní vzor založený na událostech.  
  
 Asynchronní vzor založený na událostech zpřístupňuje výhody vícevláknových aplikací a zároveň skrývá mnoho složitých problémů, které jsou vlastní návrhu s více vlákny. Použití třídy, která podporuje tento vzor, vám může umožnit:  
  
- Provádějte časově náročné úlohy, jako je stahování a databázové operace, "na pozadí", aniž byste přerušili aplikaci.  
  
- Proveďte více operací současně a při každém dokončení obdržíte oznámení.  
  
- Počkejte na prostředky, které budou k dispozici bez zastavení ("blokování") aplikace.  
  
- Komunikujte s čekajícími asynchronními operacemi pomocí známého modelu událostí a delegátů. Další informace o použití obslužných rutin událostí a delegátů naleznete v [tématu Události](../../../docs/standard/events/index.md).  
  
 Třída, která podporuje asynchronní vzorek založený na událostech, bude mít jednu nebo více metod s názvem _MethodName_**Async**. Tyto metody mohou zrcadlit synchronní verze, které provádějí stejnou operaci v aktuálním vlákně. Třída může mít také _MethodName_**Completed** událost a může mít _MethodName_**AsyncCancel** (nebo jednoduše **CancelAsync)** metoda.  
  
 <xref:System.Windows.Forms.PictureBox>je typická součást, která podporuje asynchronní vzorek založený na událostech. Bitovou kopii můžete stáhnout synchronně <xref:System.Windows.Forms.PictureBox.Load%2A> voláním její metody, ale pokud je bitová kopie velká nebo pokud je síťové připojení <xref:System.Windows.Forms.PictureBox.Load%2A> pomalé, aplikace přestane reagovat, dokud nebude dokončena operace stahování a volání vrátí.  
  
 Pokud chcete, aby vaše aplikace stále běží, zatímco <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> image se <xref:System.Windows.Forms.PictureBox.LoadCompleted> načítá, můžete volat metodu a zpracování události, stejně jako byste zpracovat všechny ostatní události. Při volání <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> metody aplikace bude pokračovat v běhu, zatímco stahování pokračuje v samostatném vlákně ("na pozadí"). Obslužná rutina události bude volána po dokončení operace <xref:System.ComponentModel.AsyncCompletedEventArgs> načítání bitové kopie a obslužná rutina události může zkontrolovat parametr a zjistit, zda bylo stahování úspěšně dokončeno.  
  
 Asynchronní vzor založený na událostech vyžaduje, aby bylo možné zrušit <xref:System.Windows.Forms.PictureBox> asynchronní operaci <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> a ovládací prvek tento požadavek podporuje svou metodou. Volání <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> odešle požadavek na zastavení čekající stahování a když <xref:System.Windows.Forms.PictureBox.LoadCompleted> je úloha zrušena, je vyvolána událost.  
  
> [!CAUTION]
> Je možné, že stahování bude <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> dokončeno stejně <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> jako požadavek, takže nemusí odrážet požadavek na zrušení. To se nazývá *spor* a je běžný problém v programování s více vlákny. Další informace o problémech v programování s více vlákny naleznete v tématu [Osvědčené postupy pro spravované podprocesy](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Charakteristiky asynchronního vzoru založeného na událostech  
 Asynchronní vzor založený na událostech může mít několik podob, v závislosti na složitosti operací podporovaných určitou třídou. Nejjednodušší třídy mohou mít jednu metodu _MethodName_**Async** a odpovídající událost _MethodName_**Completed.** Složitější třídy mohou mít několik _metod MethodName_**Async,** z nichž každá má odpovídající _událost MethodName_**Completed,** stejně jako synchronní verze těchto metod. Třídy mohou volitelně podporovat zrušení, hlášení průběhu a přírůstkové výsledky pro každou asynchronní metodu.  
  
 Asynchronní metoda může také podporovat více čekající volání (více souběžných vyvolání), což umožňuje kódu volat libovolný počet opakování před dokončením dalších čekajících operací. Správné zpracování této situace může vyžadovat, aby aplikace ke sledování dokončení každé operace.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Příklady asynchronního vzoru založeného na událostech  
 <xref:System.Media.SoundPlayer> Komponenty <xref:System.Windows.Forms.PictureBox> a představují jednoduché implementace asynchronního vzoru založeného na událostech. <xref:System.Net.WebClient> Komponenty <xref:System.ComponentModel.BackgroundWorker> a představují složitější implementace asynchronního vzoru založeného na událostech.  
  
 Níže je ukázková deklarace třídy, která odpovídá vzoru:  
  
```vb  
Public Class AsyncExample  
    ' Synchronous methods.  
    Public Function Method1(ByVal param As String) As Integer
    Public Sub Method2(ByVal param As Double)
  
    ' Asynchronous methods.  
    Overloads Public Sub Method1Async(ByVal param As String)
    Overloads Public Sub Method1Async(ByVal param As String, ByVal userState As Object)
    Public Event Method1Completed As Method1CompletedEventHandler  
  
    Overloads Public Sub Method2Async(ByVal param As Double)
    Overloads Public Sub Method2Async(ByVal param As Double, ByVal userState As Object)
    Public Event Method2Completed As Method2CompletedEventHandler  
  
    Public Sub CancelAsync(ByVal userState As Object)
  
    Public ReadOnly Property IsBusy () As Boolean  
  
    ' Class implementation not shown.  
End Class  
```  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 Fiktivní `AsyncExample` třída má dvě metody, z nichž obě podporují synchronní a asynchronní vyvolání. Synchronní přetížení se chovají jako jakékoli volání metody a spouštějí operaci v volajícím vlákně; Pokud je operace časově náročná, může být znatelné zpoždění před volání vrátí. Asynchronní přetížení spustí operaci v jiném vlákně a pak se okamžitě vrátí, což umožní volajícímu vláknu pokračovat, zatímco operace bude spuštěna "na pozadí".  
  
### <a name="asynchronous-method-overloads"></a>Přetížení asynchronní metody  
 Existují potenciálně dvě přetížení pro asynchronní operace: single-invocation a multiple-invocation. Tyto dva formuláře můžete rozlišit podle jejich podpisů metody: formulář `userState`více násobného vyvolání má další parametr nazvaný . Tento formulář umožňuje kód volat `Method1Async(string param, object userState)` vícekrát bez čekání na dokončení všech čekajících asynchronních operací. Pokud se na druhé straně pokusíte volat `Method1Async(string param)` před dokončením předchozího <xref:System.InvalidOperationException>vyvolání, metoda vyvolá .  
  
 Parametr `userState` pro přetížení více vyvolání umožňuje rozlišovat mezi asynchronní operace. Zadáte jedinečnou hodnotu (například GUID nebo hash kód) pro každé volání `Method1Async(string param, object userState)`, a po dokončení každé operace, obslužná rutina události můžete určit, která instance operace vyvolala událost dokončení.  
  
### <a name="tracking-pending-operations"></a>Sledování čekajících operací  
 Pokud použijete přetížení více vyvolání, váš kód bude muset `userState` sledovat objekty (ID úloh) pro čekající úkoly. Pro každé `Method1Async(string param, object userState)`volání , obvykle vygenerujete `userState` nový jedinečný objekt a přidáte jej do kolekce. Když úkol odpovídající `userState` tomuto objektu vyvolá událost dokončení, <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> implementace metody dokončení zkontroluje a odebere ji z kolekce. Používá se tímto způsobem, `userState` parametr přebírá roli ID úkolu.  
  
> [!NOTE]
> Musíte být opatrní poskytnout jedinečnou `userState` hodnotu pro volání přetížení více vyvolání. Nejedinečná ID úloh způsobí, že asynchronní <xref:System.ArgumentException>třída vyvolá .  
  
### <a name="canceling-pending-operations"></a>Zrušení čekajících operací  
 Je důležité mít možnost zrušit asynchronní operace kdykoli před jejich dokončením. Třídy, které implementují asynchronní vzor `CancelAsync` založený na událostech, budou mít metodu (pokud existuje pouze jedna asynchronní metoda) nebo metodu _MethodName_**AsyncCancel** (pokud existuje více asynchronních metod).  
  
 Metody, které umožňují více `userState` vyvolání trvat parametr, který lze použít ke sledování životnosti jednotlivých úkolů. `CancelAsync`přebírá `userState` parametr, který umožňuje zrušit konkrétní čekající úkoly.  
  
 Metody, které podporují pouze jednu čekající `Method1Async(string param)`operaci najednou, jako je například , nejsou zrušitelné.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Příjem aktualizací průběhu a přírůstkových výsledků  
 Třída, která dodržuje asynchronní vzor založený na událostech, může volitelně poskytnout událost pro sledování průběhu a přírůstkové výsledky. To bude obvykle `ProgressChanged` pojmenováno nebo _MethodName_**ProgressChanged**a jeho <xref:System.ComponentModel.ProgressChangedEventArgs> odpovídající obslužná rutina události převezme parametr.  
  
 Obslužná `ProgressChanged` rutina <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> události může zkontrolovat vlastnost a určit, jaké procento asynchronní úlohy bylo dokončeno. Tato vlastnost bude v rozsahu od 0 do 100 <xref:System.Windows.Forms.ProgressBar.Value%2A> a <xref:System.Windows.Forms.ProgressBar>lze ji použít k aktualizaci vlastnosti . Pokud více asynchronních operací čeká na <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> vyřízení, můžete použít vlastnost k rozlišení, která operace hlásí průběh.  
  
 Některé třídy mohou vykazovat přírůstkové výsledky jako asynchronní operace pokračovat. Tyto výsledky budou uloženy ve třídě, která je odvozena z <xref:System.ComponentModel.ProgressChangedEventArgs> a zobrazí se jako vlastnosti v odvozené třídě. K těmto výsledkům můžete přistupovat `ProgressChanged` v obslužné <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> rutině události pro událost, stejně jako byste měli přístup k vlastnosti. Pokud více asynchronních operací čeká na <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> vyřízení, můžete použít vlastnost k rozlišení, která operace hlásí přírůstkové výsledky.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
