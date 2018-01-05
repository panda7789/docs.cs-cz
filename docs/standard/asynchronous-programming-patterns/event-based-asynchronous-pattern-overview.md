---
title: "Přehled asynchronních vzorů založených na událostech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0ac7795ee0341f9a0dfd80018a71928b8db2bd95
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="event-based-asynchronous-pattern-overview"></a>Přehled asynchronních vzorů založených na událostech
Aplikace, které současně provádět mnoho úloh, ale zůstávají reaguje na interakci s uživatelem, často vyžadují návrh, který používá více vláken. <xref:System.Threading> Obor názvů obsahuje všechny nástroje potřebné k vytvoření vícevláknové aplikace s vysokým výkonem, ale efektivně používání těchto nástrojů vyžaduje významné prostředí s více vlákny inženýrství softwaru. Pro vícevláknové aplikace s relativně jednoduché <xref:System.ComponentModel.BackgroundWorker> součást poskytuje přehledné řešení. Pro sofistikovanější asynchronní aplikace zvažte implementaci třídy, která dodržuje asynchronní vzor založený na událostech.  
  
 Asynchronní vzor založený na událostech zpřístupní výhod vícevláknové aplikace při skrytí mnoho složitých problémů vyplývajících z více vláken návrhu. Použití třídy, která podporuje tento vzor můžete povolit na:  
  
-   Proveďte časově náročné úkoly, jako soubory ke stažení a databázových operací "v pozadí," bez přerušení vaší aplikace.  
  
-   Souběžně spustit více operací příjem oznámení po dokončení každé.  
  
-   Počkejte prostředky k dispozici bez zastavení ("dostupný") vaší aplikace.  
  
-   Komunikovat s čekajících asynchronních operací pomocí známý model události a delegáti. Další informace o používání obslužných rutin událostí a delegáti najdete v tématu [události](../../../docs/standard/events/index.md).  
  
 Třídu, která podporuje asynchronní vzor na základě událostí bude mít jednu nebo více metod s názvem *MethodName*`Async`. Tyto metody mohou zrcadlení synchronní verze, které provádět stejné operace na aktuální vlákno. Třídy mohou mít i *MethodName* `Completed` událostí a může obsahovat *MethodName* `AsyncCancel` (nebo jednoduše `CancelAsync`) metoda.  
  
 <xref:System.Windows.Forms.PictureBox>je typické komponenty, která podporuje asynchronní vzor založený na událostech. Si můžete stáhnout bitovou kopii synchronně voláním jeho <xref:System.Windows.Forms.PictureBox.Load%2A> metoda, ale pokud je velký obrázek, nebo pokud jde o pomalé síťové připojení, pro aplikace zastaví ("přečnívat"), dokud se nedokončí operaci stahování a volání k <xref:System.Windows.Forms.PictureBox.Load%2A> vrátí.  
  
 Pokud chcete, aby vaše aplikace běžet při bitovou kopii načítání, můžete zavolat <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> metoda a popisovač <xref:System.Windows.Forms.PictureBox.LoadCompleted> událostí, stejně jako by zpracovat žádné další událost. Při volání <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> metoda, vaše aplikace bude nadále spuštěna při stahování pokračuje na samostatné vlákno ("v pozadí"). Vaší obslužné rutiny události bude volána po dokončení operace načítání bitovou kopii a vaší obslužné rutiny událostí můžete zkontrolovat <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr k určení, pokud stahování byla úspěšně dokončena.  
  
 Asynchronní vzor založený na událostech vyžaduje, aby asynchronní operaci se dají zrušit a <xref:System.Windows.Forms.PictureBox> řízení podporuje tento požadavek s jeho <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> metoda. Volání metody <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> odešle požadavek na zastavení čeká na stažení a při zrušení úlohy <xref:System.Windows.Forms.PictureBox.LoadCompleted> událost se vyvolá.  
  
> [!CAUTION]
>  Je možné, že se stahování dokončí stejně jako <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> požadavku, tak <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> nemusí odrážet žádost o zrušení. Tento postup se nazývá *soupeřit podmínku* a je běžné problémy při vícevláknové programování. Další informace o problémech při vícevláknové programování najdete v tématu [spravované dělení na vlákna osvědčené postupy](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Vlastnosti asynchronního vzoru založeného na událostech  
 Asynchronní vzor založený na událostech může trvat několik formulářů, v závislosti na složitosti operací podporované určité třídy. Nejjednodušší třídy mohou mít jeden *MethodName* `Async` metoda a odpovídající *MethodName* `Completed` událostí. Složitější třídy mohou mít několik *MethodName* `Async` metody, každý s odpovídající *MethodName* `Completed` událostí, jakož i synchronní verze těchto metod. Třídy může volitelně podporovat zrušení, hlášení průběhu a přírůstkové výsledky pro každou asynchronní metodu.  
  
 Asynchronní metodu mohou podporovat více čekající volání (více souběžných volání), aby měl váš kód volat v libovolném počtu před dokončením další čekající operace. Správné zpracování této situaci může vyžadovat aplikace ke sledování dokončení jednotlivých operací.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Příklady asynchronního vzoru založeného na událostech  
 <xref:System.Media.SoundPlayer> a <xref:System.Windows.Forms.PictureBox> součásti představují jednoduché implementace asynchronního vzoru založeného na událostech. <xref:System.Net.WebClient> a <xref:System.ComponentModel.BackgroundWorker> součásti představují složitější implementace asynchronního vzoru založeného na událostech.  
  
 Dole je deklaraci třídy příklad, který odpovídá typu:  
  
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
  
 Fiktivní `AsyncExample` třída má dvě metody, které podporují synchronní a asynchronní volání. Synchronní přetížení chovají jako jakékoli volání metody a spusťte operaci na volající vlákno; Pokud je časově náročná operace, může mít významnému zpoždění předtím, než se volání vrátí. Asynchronní přetížení se spuštění operace na jiné vlákno a pak se vraťte okamžitě, což volající vlákno pokračujte při operaci provede "v pozadí."  
  
### <a name="asynchronous-method-overloads"></a>Přetížení asynchronní metody  
 Existují přetížení pro asynchronní operace potenciálně dvě metody: volání jeden a více volání. Tyto dvě formy možné rozlišit podle jejich metoda podpisů: více volání formulář obsahuje doplňující parametr `userState`. Tento formulář umožňuje na volání `Method1Async(string param, object userState)` vícekrát bez čekání na všechny čekající na dokončení asynchronní operace. Pokud na druhé straně pokusíte volání `Method1Async(string param)` předtím, než byla dokončena předchozí volání, vyvolá metoda <xref:System.InvalidOperationException>.  
  
 `userState` Parametr pro volání více přetížení umožňuje rozlišovat mezi asynchronní operace. Zadejte jedinečnou hodnotu (například kód GUID nebo hodnotu hash) pro každé volání `Method1Async(string param, object userState)`, a po dokončení jednotlivých operací vaší obslužné rutiny událostí můžete určit, která instance operaci vyvolá událost dokončení.  
  
### <a name="tracking-pending-operations"></a>Sledování čekající operace  
 Pokud používáte více volání přetížení, váš kód bude nutné sledovat `userState` objekty (ID úkolu) pro úkolů čekajících na zpracování. Pro každé volání `Method1Async(string param, object userState)`, obvykle bude vygenerujte nový jedinečný `userState` objektu a přidat jej do kolekce. Když úloha odpovídajících tomuto `userState` objekt vyvolá událost, dokončení, bude implementace Metoda dokončení zkontrolujte <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> a jeho odebrání z kolekce. Použít tento způsob `userState` přebírá parametr roli ID úkolu.  
  
> [!NOTE]
>  Je třeba dbát zadejte jedinečnou hodnotu pro `userState` v vaše volání pro vyvolání více přetížení. Způsobí, že není jedinečné ID úkolu throw asynchronní třída <xref:System.ArgumentException>.  
  
### <a name="canceling-pending-operations"></a>Rušení čekajících operací  
 Je důležité, abyste mohli před jejich dokončení kdykoli zrušit asynchronní operace. Bude mít třídy, které implementovat asynchronní vzor založený na událostech `CancelAsync` – metoda (Pokud máte pouze jednu asynchronní metodu) nebo *MethodName* `AsyncCancel` – metoda (pokud existuje několik metod asynchronní).  
  
 Metody, které umožňují více volání přijímají `userState` parametr, který můžete použít ke sledování životnost jednotlivých úloh. `CancelAsync`přijímá `userState` parametr, který umožňuje zrušit konkrétní úkolů čekajících na zpracování.  
  
 Metody, které podporují jenom jeden nevyřízenou operaci najednou, jako je třeba `Method1Async(string param)`, nejsou možné zrušit.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Přijetí průběh aktualizace a přírůstkové výsledky  
 Třídu, která dodržuje asynchronní vzor založený na událostech může volitelně zadat událost pro sledování průběhu a přírůstkové výsledky. To se obvykle nazývá `ProgressChanged` nebo *MethodName*`ProgressChanged`, a jeho odpovídající obslužné rutiny události bude trvat <xref:System.ComponentModel.ProgressChangedEventArgs> parametr.  
  
 Obslužné rutiny události pro `ProgressChanged` událostí můžete zkontrolovat <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> vlastnosti k určení, jaké procento asynchronní úloha byla dokončena. Tato vlastnost bude rozsahu od 0 do 100 a je možné použít k aktualizaci <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost <xref:System.Windows.Forms.ProgressBar>. Pokud jsou více asynchronní operace čekající na vyřízení, můžete použít <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> vlastnost k rozlišení která operace je vytvoření sestavy průběhu.  
  
 Některé třídy mohou sestavy o výsledcích přírůstkové jako asynchronní operace pokračovat. Tyto výsledky se uloží ve třídě, která je odvozena od <xref:System.ComponentModel.ProgressChangedEventArgs> a se zobrazí jako vlastnosti v odvozené třídě. Dostanete těchto výsledků v obslužné rutiny události pro `ProgressChanged` událostí, stejně jako by přístup <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> vlastnost. Pokud jsou více asynchronní operace čekající na vyřízení, můžete použít <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> vlastnost k rozlišení kterou operaci je generování sestav přírůstkové výsledky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Vícevláknové programování s asynchronním vzorem založeným na událostech](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
