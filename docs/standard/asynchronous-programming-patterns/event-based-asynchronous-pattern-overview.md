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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160064"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Přehled asynchronních vzorů založených na událostech
Aplikace, které provádějí mnoho úloh současně, stále reagují na interakci s uživatelem, často vyžadují návrh, který používá více vláken. Obor názvů <xref:System.Threading> poskytuje všechny nástroje, které jsou nezbytné pro vytváření vysoce výkonných aplikací s vysokým výkonem, ale používání těchto nástrojů efektivně vyžaduje významné prostředí pro vícevláknové softwarové inženýry. Pro relativně jednoduché vícevláknové aplikace <xref:System.ComponentModel.BackgroundWorker> komponenta poskytuje jasné řešení. Pro propracovanější asynchronní aplikace zvažte implementaci třídy, která odpovídá asynchronnímu vzoru založenému na událostech.  
  
 Asynchronní vzor založený na událostech zpřístupňuje výhody vícevláknových aplikací a zároveň skrývá mnoho složitých problémů, které jsou v podstatě vícevláknové konstrukce. Použití třídy, která podporuje tento model, vám umožní:  
  
- Provádějte časově náročné úkoly, například soubory ke stažení a databázové operace, na pozadí, aniž by došlo k přerušení aplikace.  
  
- Spouštějte více operací současně a při každém dokončení přijímají oznámení.  
  
- Počkejte, než budou prostředky k dispozici bez zastavení ("blokování") vaší aplikace.  
  
- Komunikujte s nedokončenými asynchronními operacemi pomocí známého modelu událostí a delegátů. Další informace o používání obslužných rutin událostí a delegátů naleznete v tématu [events](../../../docs/standard/events/index.md).  
  
 Třída, která podporuje asynchronní vzor založený na událostech, bude mít jednu nebo více metod s názvem _methodName_**Async**. Tyto metody mohou zrcadlit synchronní verze, které provádějí stejnou operaci v aktuálním vlákně. Třída může mít také událost _methodName_**Completed** a může mít metodu _methodName_**AsyncCancel** (nebo jednoduše **CancelAsync**).  
  
 <xref:System.Windows.Forms.PictureBox> je typická komponenta, která podporuje asynchronní vzor založený na událostech. Bitovou kopii lze synchronně stáhnout voláním její <xref:System.Windows.Forms.PictureBox.Load%2A> metody, ale pokud je bitová kopie velká, nebo pokud je síťové připojení pomalé, přestane vaše aplikace reagovat, dokud nebude dokončena operace stahování a volání <xref:System.Windows.Forms.PictureBox.Load%2A> vrátí.  
  
 Pokud chcete, aby vaše aplikace zůstala v průběhu načítání obrázku, můžete zavolat metodu <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> a zpracovat událost <xref:System.Windows.Forms.PictureBox.LoadCompleted>, stejně jako byste poznamenali jakoukoli jinou událost. Při volání metody <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> bude aplikace nadále běžet, zatímco stahování pokračuje v samostatném vlákně ("na pozadí"). Vaše obslužná rutina události bude volána, když je dokončena operace načítání obrázku, a vaše obslužná rutina události může ověřit parametr <xref:System.ComponentModel.AsyncCompletedEventArgs> a zjistit, zda bylo stahování úspěšně dokončeno.  
  
 Asynchronní vzor založený na událostech vyžaduje zrušení asynchronní operace a ovládací prvek <xref:System.Windows.Forms.PictureBox> tento požadavek podporuje s jeho <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> metodou. Volání <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> odešle požadavek na zastavení čeká na stažení a při zrušení úlohy dojde k vyvolání události <xref:System.Windows.Forms.PictureBox.LoadCompleted>.  
  
> [!CAUTION]
> Je možné, že stahování se dokončí jenom v případě, že se vyžádá <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> žádost, takže <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> nemusí odrážet požadavek na zrušení. Označuje se jako *konflikt časování* a jedná se o běžný problém v programování s více vlákny. Další informace o problémech v programování s více vlákny najdete v tématu [osvědčené postupy spravovaného vlákna](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Charakteristiky asynchronního vzoru založeného na událostech  
 Asynchronní vzor založený na událostech může v závislosti na složitosti operací podporovaných určitou třídou trvat několik forem. Nejjednodušší třídy mohou mít jednu**asynchronní** metodu _methodName_a odpovídající událost _methodName_**Completed** . Složitější třídy mohou mít několik**asynchronních** metod _methodName_, z nichž každá má odpovídající událost _methodName_**Completed** , a také synchronní verze těchto metod. Třídy mohou volitelně podporovat zrušení, vytváření sestav o průběhu a přírůstkové výsledky pro každou asynchronní metodu.  
  
 Asynchronní metoda může také podporovat více nevyřízených volání (více souběžných vyvolání), což umožňuje vašemu kódu volat je libovolným počtem výskytů, než dokončí jiné operace, které čekají na vyřízení. Správné zpracování této situace může vyžadovat, aby vaše aplikace mohla sledovat dokončení jednotlivých operací.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Příklady asynchronního vzoru založeného na událostech  
 Komponenty <xref:System.Media.SoundPlayer> a <xref:System.Windows.Forms.PictureBox> reprezentují jednoduché implementace asynchronního vzoru založeného na událostech. Komponenty <xref:System.Net.WebClient> a <xref:System.ComponentModel.BackgroundWorker> reprezentují složitější implementace asynchronního vzoru založeného na událostech.  
  
 Níže je příklad deklarace třídy, která odpovídá vzoru:  
  
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
  
 Fiktivní `AsyncExample` třída má dvě metody, které podporují synchronní i asynchronní vyvolání. Synchronní přetížení se chová stejně jako jakékoli volání metody a spustí operaci na volajícím vlákně. Pokud je operace časově náročná, může před vrácením volání dojít k znatelnému zpoždění. Asynchronní přetížení spustí operaci v jiném vlákně a pak okamžitě vrátí, což umožní volajícímu vláknu pokračovat, zatímco operace se spustí na pozadí.  
  
### <a name="asynchronous-method-overloads"></a>Přetížení asynchronní metody  
 Existují potenciálně dvě přetížení pro asynchronní operace: jedno vyvolání a vícenásobné volání. Tyto dva formuláře lze odlišit svými signaturami metod: formulář s vícenásobným voláním má navíc parametr s názvem `userState`. Tento formulář umožňuje vašemu kódu volat `Method1Async(string param, object userState)` několikrát bez čekání na dokončení všech čekajících asynchronních operací. Pokud na druhé straně zkusíte volat `Method1Async(string param)` před dokončením předchozího vyvolání, metoda vyvolá <xref:System.InvalidOperationException>.  
  
 Parametr `userState` pro přetížení vícenásobného navýšení volání umožňuje rozlišovat mezi asynchronními operacemi. Poskytnete jedinečnou hodnotu (například identifikátor GUID nebo kód hash) pro každé volání `Method1Async(string param, object userState)`a po dokončení každé operace může vaše obslužná rutina události určit, která instance operace vyvolala událost dokončení.  
  
### <a name="tracking-pending-operations"></a>Sledování nevyřízených operací  
 Pokud používáte přetížení s vícenásobným vyvoláním, váš kód bude potřebovat sledovat `userState` objektů (ID úloh) pro probíhající úkoly. Pro každé volání `Method1Async(string param, object userState)`obvykle vygenerujete nový jedinečný `userState` objekt a přidáte ho do kolekce. Když úloha odpovídající tomuto objektu `userState` vyvolá událost dokončení, vaše implementace metody dokončení prověřuje <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> a odebere ji z kolekce. Tímto způsobem parametr `userState` přebírá roli ID úlohy.  
  
> [!NOTE]
> Musíte být opatrní, abyste zadali jedinečnou hodnotu pro `userState` v voláních přetížení vícenásobného volání. Nejedinečná ID úlohy způsobí, že asynchronní třída vyvolá <xref:System.ArgumentException>.  
  
### <a name="canceling-pending-operations"></a>Rušení probíhajících operací  
 Je důležité mít schopnost zrušit asynchronní operace kdykoli před jejich dokončením. Třídy, které implementují asynchronní vzor založený na událostech, budou mít metodu `CancelAsync` (pokud existuje pouze jedna asynchronní metoda) nebo metoda _methodName_**AsyncCancel** (pokud existuje více asynchronních metod).  
  
 Metody umožňující vícenásobné vyvolání přebírají `userState` parametr, který lze použít ke sledování životnosti každého úkolu. `CancelAsync` převezme parametr `userState`, který vám umožní zrušit konkrétní nedokončené úlohy.  
  
 Metody, které podporují pouze jednu nevyřízenou operaci v čase, například `Method1Async(string param)`, nelze zrušit.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Přijímání aktualizací průběhu a přírůstkových výsledků  
 Třída, která odpovídá asynchronnímu vzoru založenému na událostech, může volitelně poskytnout událost pro sledování průběhu a přírůstkových výsledků. To se obvykle jmenuje `ProgressChanged` nebo _methodName_**ProgressChanged**a jeho odpovídající obslužná rutina události bude přebírat parametr <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
 Obslužná rutina události `ProgressChanged` může prošetřit vlastnost <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> a určit, jaké procento asynchronního úkolu bylo dokončeno. Tato vlastnost bude v rozsahu od 0 do 100 a lze ji použít k aktualizaci vlastnosti <xref:System.Windows.Forms.ProgressBar.Value%2A> <xref:System.Windows.Forms.ProgressBar>. Pokud čekají více asynchronních operací, můžete pomocí vlastnosti <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> odlišit, kterou operaci oznamuje průběh.  
  
 Některé třídy mohou nahlásit přírůstkové výsledky, jakmile budou asynchronní operace pokračovat. Tyto výsledky budou uloženy ve třídě, která je odvozena od <xref:System.ComponentModel.ProgressChangedEventArgs> a zobrazí se jako vlastnosti v odvozené třídě. K těmto výsledkům můžete přistupovat v obslužné rutině události `ProgressChanged`, stejně jako při přístupu k vlastnosti <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A>. Pokud čekáte na více asynchronních operací, můžete pomocí vlastnosti <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> odlišit, jakou operaci sestavy přírůstkových výsledků vytvářejí.  
  
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
