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
ms.openlocfilehash: 28f04e12d17d65788b0f894d3bd777a700b712f9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785801"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Přehled asynchronních vzorů založených na událostech
Aplikace, které provádějí celou řadu úloh současně, ale stále reagovat na interakci uživatele, často vyžadují návrh, který používá více vláken. <xref:System.Threading> Obor názvů poskytuje všechny nástroje potřebné k vytvoření vysoce výkonné aplikace s více vlákny, ale efektivně pomocí těchto nástrojů vyžaduje významné prostředí s více vlákny softwarového inženýrství. Pro vícevláknové aplikace s poměrně jednoduché <xref:System.ComponentModel.BackgroundWorker> součást poskytuje jednoduché řešení. Pro složitější asynchronní aplikace zvažte implementaci třídy, která dodržuje asynchronního vzoru založeného na událostech.  
  
 Asynchronní vzor založený na událostech zpřístupňuje výhody vícevláknové aplikace při skrytí mnoho složitých problémů vyplývající vícevláknový návrhu. Použití třídy, která podporuje tento vzor vám umožní:  
  
-   Proveďte časově náročné úkoly, jako jsou soubory ke stažení a databázových operací, "v pozadí," bez přerušení vaší aplikace.  
  
-   Současně spusťte více operací příjem oznámení po dokončení každého.  
  
-   Čekání na prostředky k dispozici bez zastavení ("předsazení") vaší aplikace.  
  
-   Komunikovat s čekajících asynchronních operací s použitím známým modelem Delegáti a události. Další informace o použití delegátů a obslužné rutiny událostí, naleznete v tématu [události](../../../docs/standard/events/index.md).  
  
 Třída, která podporuje asynchronní vzor založený na událostech bude mít jednu nebo více metod s názvem *MethodName ***asynchronní**. Tyto metody mohou zrcadlí synchronní verze, které provádět stejnou operaci i u aktuálního vlákna. Třídy mohou mít i *MethodName *** dokončeno**  událostí a může obsahovat *MethodName *** AsyncCancel** (nebo jednoduše **CancelAsync**) metody.  
  
 <xref:System.Windows.Forms.PictureBox> je typické komponenty, která podporuje asynchronní vzor založený na událostech. Si můžete stáhnout bitovou kopii synchronně voláním jeho <xref:System.Windows.Forms.PictureBox.Load%2A> metody, ale pokud je velký obrázek, nebo pokud je pomalé síťové připojení, pro vaše aplikace přestane ("zablokování"), dokud se nedokončí operaci stahování a volání <xref:System.Windows.Forms.PictureBox.Load%2A> vrátí.  
  
 Pokud chcete, aby vaše aplikace běžela při image se načítá, můžete volat <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> metoda a popisovač <xref:System.Windows.Forms.PictureBox.LoadCompleted> události, stejně jako by zpracovat všechny události. Při volání <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> metodu, aplikace bude nadále spuštěna při stahování pokračuje na samostatném vlákně ("v pozadí"). Vaše obslužná rutina události zavolá se po dokončení operace načítání obrázku a vaší obslužné rutiny události můžete prozkoumat <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr k určení, pokud se stahování byla úspěšně dokončena.  
  
 Asynchronní vzor založený na událostech vyžaduje, aby se dají zrušit asynchronní operaci a <xref:System.Windows.Forms.PictureBox> ovládací prvek podporuje tento požadavek s jeho <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> metoda. Volání <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> odešle požadavek na zastavení čeká na stažení a při zrušení úkolu <xref:System.Windows.Forms.PictureBox.LoadCompleted> událost se vyvolá.  
  
> [!CAUTION]
>  Je možné, že se stahování dokončí stejně jako <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> žádosti se tak <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> nemusí odrážet žádost o zrušení. Jedná se *časování* a je běžný problém při programování s více vlákny. Další informace o problémech v programování s více vlákny, naleznete v tématu [spravovaných vláken osvědčené postupy](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Vlastnosti asynchronního vzoru založeného na událostech  
 Asynchronní vzor založený na událostech může mít různé podoby záleží na složitosti operace podporuje určité třídy. Nejjednodušší třídy může mít jeden *MethodName *** asynchronní** metoda a odpovídající *MethodName *** dokončeno** události. Složitější třídy mohou mít několik *MethodName *** asynchronní** metody, každý s odpovídající *MethodName *** dokončeno** události, stejně jako synchronní verze z těchto metod. Třídy může volitelně podporovat zrušení, generování sestav o průběhu a přírůstkové výsledky pro každou asynchronní metodu.  
  
 Asynchronní metoda může podporovat více čekající volání (více souběžných volání), váš kód volat libovolný počet pokusů před dokončením jiné probíhající operace. Správné zpracování této situaci může vyžadovat aplikace ke sledování dokončení každé operace.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Příklady asynchronního vzoru založeného na událostech  
 <xref:System.Media.SoundPlayer> a <xref:System.Windows.Forms.PictureBox> součásti představují jednoduché implementace asynchronního vzoru založeného na událostech. <xref:System.Net.WebClient> a <xref:System.ComponentModel.BackgroundWorker> součásti představují složitější implementace asynchronního vzoru založeného na událostech.  
  
 Níže je příklad deklarace třídy, který odpovídá vzoru:  
  
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
  
 Fiktivní `AsyncExample` třída má dvě metody, které podporují synchronní a asynchronní vyvolání. Synchronní přetížení se chovají stejně jako jakékoli volání metody a provedení operace na volajícím vlákně; Pokud je časově náročná operace, může docházet k významnému zpoždění volání se vrátí. Asynchronní přetížení se spustit operaci v jiném vlákně a pak se vraťte okamžitě, což volající vlákno, chcete-li pokračovat, když se provede operace "v pozadí."  
  
### <a name="asynchronous-method-overloads"></a>Asynchronní metody přetížení  
 Existují potenciálně dvě přetížení pro asynchronní operace: volání jedné a více volání. Tyto dvě formy možné rozlišit podle jejich podpisy metod: více volání formulář obsahuje doplňující parametr s názvem `userState`. Tento formulář umožňuje kódu pro volání `Method1Async(string param, object userState)` vícekrát bez čekání na všechny čekající na dokončení asynchronní operace. Pokud je na druhé straně pokusu o volání `Method1Async(string param)` před dokončením předchozí volání, vyvolá metodu <xref:System.InvalidOperationException>.  
  
 `userState` Parametr pro více volání přetížení umožňuje rozlišit mezi asynchronní operace. Zadejte jedinečnou hodnotu (například identifikátor GUID nebo hodnota hash kódu) pro každé volání `Method1Async(string param, object userState)`, a při dokončení každé operace obslužnou rutinu události můžete určit, která instance operaci vyvolala událost dokončení.  
  
### <a name="tracking-pending-operations"></a>Sledování čekajících operací  
 Pokud používáte více volání přetížení, váš kód bude nutné sledovat `userState` objekty (ID úlohy) pro čekající úlohy. Pro každé volání `Method1Async(string param, object userState)`, obvykle bude generovat nové, jedinečné `userState` objektu a přidat do kolekce. Pokud úlohu, která odpovídá tomuto `userState` objekt vyvolává událost dokončení, bude vaše implementace metody dokončení zkontrolujte <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> a odebrat z kolekce. Použito tímto způsobem, `userState` parametr přebírá roli ID úkolu.  
  
> [!NOTE]
>  Musíte být opatrní a zadejte jedinečnou hodnotu pro `userState` ve volání do více volání přetížení. Způsobí, že není nejedinečný ID úlohy asynchronního třídy throw <xref:System.ArgumentException>.  
  
### <a name="canceling-pending-operations"></a>Rušení čekajících operací  
 Je důležité, aby bylo možné zrušit asynchronní operace kdykoli před jejich dokončení. Bude mít třídy, které implementovat asynchronní vzor založený na událostech `CancelAsync` – metoda (pokud existuje pouze jedna asynchronní metoda) nebo *MethodName *** AsyncCancel** – metoda (pokud existuje více asynchronních metod).  
  
 Metody, které umožňují více volání trvat `userState` parametr, který slouží ke sledování doby života každého úkolu. `CancelAsync` přijímá `userState` parametr, který umožňuje zrušit konkrétní čekající úlohy.  
  
 Metody, které podporují pouze jeden nevyřízenou operaci najednou, jako je třeba `Method1Async(string param)`, nejsou zrušitelné.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Příjem průběh aktualizací a výsledků přírůstkové  
 Třída, která dodržuje asynchronního vzoru založeného na událostech může volitelně zadat události pro sledování průběhu a přírůstkové výsledků. To se obvykle nazývá `ProgressChanged` nebo * MethodName ***ProgressChanged**, a podnikne odpovídající obslužná rutina události <xref:System.ComponentModel.ProgressChangedEventArgs> parametru.  
  
 Obslužnou rutinu události pro `ProgressChanged` můžete zkoumat události <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> a určí, jaké je procento asynchronní úloha se dokončila. Tato vlastnost se v rozsahu od 0 do 100 a je možné použít k aktualizaci <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost <xref:System.Windows.Forms.ProgressBar>. Pokud více asynchronních operací čekají na vyřízení, můžete použít <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> vlastnost k rozlišení operace, která hlásí průběh.  
  
 Některé třídy může hlásit přírůstkové výsledky, protože asynchronní operace pokračovat. Tyto výsledky se uloží do třídy, která je odvozena z <xref:System.ComponentModel.ProgressChangedEventArgs> a zobrazí se jako vlastnosti v odvozené třídě. Se zobrazí tyto výsledky v obslužné rutině události pro `ProgressChanged` události, stejně jako by přístup <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> vlastnost. Pokud více asynchronních operací čekají na vyřízení, můžete použít <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> vlastnost k rozlišení, které operace hlásí přírůstkové výsledky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
