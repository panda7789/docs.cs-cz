---
title: Implementace asynchronního vzoru založeného na událostech
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
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
ms.openlocfilehash: 9865fa169e0776765f9a97ec0a7b4555bf253886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67663705"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Implementace asynchronního vzoru založeného na událostech

Pokud píšete třídu s některými operacemi, které mohou způsobit znatelné zpoždění, zvažte poskytnutí asynchronní funkce implementací [přehledu asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).

Asynchronní vzor založený na událostech poskytuje standardizovaný způsob, jak zabalit třídu, která má asynchronní funkce. Pokud je implementována <xref:System.ComponentModel.AsyncOperationManager>s pomocné třídy, jako je , bude vaše třída pracovat správně v rámci libovolného modelu aplikace, včetně ASP.NET, konzolové aplikace a windows forms aplikace.

Příklad, který implementuje asynchronní vzor založený na událostech, naleznete v tématu [How to: Implement a Component that Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).

Pro jednoduché asynchronní operace můžete <xref:System.ComponentModel.BackgroundWorker> najít součást vhodné. Další informace <xref:System.ComponentModel.BackgroundWorker>o [aplikaci naleznete v tématu Postup: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).

Následující seznam popisuje funkce asynchronního vzoru založeného na událostech popsané v tomto tématu.

- Příležitosti pro implementaci asynchronního vzoru založeného na událostech

- Pojmenování asynchronních metod

- Volitelně podpora zrušení

- Volitelně podporovat vlastnost IsBusy

- Volitelně poskytovat podporu pro vykazování průběhu

- Volitelně poskytují podporu pro vrácení přírůstkových výsledků

- Zpracování a ref parametry v metodách

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Příležitosti pro implementaci asynchronního vzoru založeného na událostech

Zvažte implementaci asynchronního vzoru založeného na událostech, pokud:

- Klienti vaší třídy <xref:System.Threading.WaitHandle> nepotřebují a <xref:System.IAsyncResult> objekty, které jsou k <xref:System.Threading.WaitHandle.WaitAll%2A> <xref:System.Threading.WaitHandle.WaitAny%2A> dispozici pro asynchronní operace, což znamená, že dotazování a nebo bude muset být vytvořen klientem.

- Chcete, aby asynchronní operace byly spravovány klientem se známým modelem události/delegáta.

Každá operace je kandidátem pro asynchronní implementaci, ale ty, které očekáváte, že vynaloží dlouhé latence by měly být považovány za. Zvláště vhodné jsou operace, při kterých klienti volají metodu a jsou upozorněni na dokončení, bez nutnosti dalšího zásahu. Vhodné jsou také operace, které běží nepřetržitě a pravidelně upozorňují klienty na průběh, přírůstkové výsledky nebo změny stavu.

Další informace o rozhodování o tom, kdy podporovat asynchronní vzor založený na událostech, naleznete [v tématu Rozhodování o tom, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).

## <a name="naming-asynchronous-methods"></a>Pojmenování asynchronních metod

Pro každou synchronní metodu *MethodName,* pro kterou chcete poskytnout asynchronní protějšek:

Definujte metodu _MethodName_**Async,** která:

- Vrací objekt `void`.

- Přebírá stejné parametry jako *MethodName Method.*

- Přijímá více vyvolání.

Volitelně definujte přetížení _MethodName_**Async,** identické s _MethodName_**Async**, `userState`ale s dalším nazývaným parametrem s hodnotou objektu . Toto akci proveďte, pokud jste připraveni spravovat více souběžných `userState` vyvolání metody, v takovém případě bude hodnota doručena zpět všem obslužným rutinám událostí k rozlišení vyvolání metody. Můžete také provést jednoduše jako místo pro uložení stavu uživatele pro pozdější načtení.

Pro každý samostatný podpis metody _MethodName_**Async:**

1. Definujte následující událost ve stejné třídě jako metoda:

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. Definujte následující <xref:System.ComponentModel.AsyncCompletedEventArgs>hodelegáta a . Ty budou pravděpodobně definovány mimo samotnou třídu, ale ve stejném oboru názvů.

    ```vb
    Public Delegate Sub MethodNameCompletedEventHandler( _
        ByVal sender As Object, _
        ByVal e As MethodNameCompletedEventArgs)

    Public Class MethodNameCompletedEventArgs
        Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As MyReturnType
    End Property
    ```

    ```csharp
    public delegate void MethodNameCompletedEventHandler(object sender,
        MethodNameCompletedEventArgs e);

    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
    {
        public MyReturnType Result { get; }
    }
    ```

    - Ujistěte se, že třída _MethodName_**CompletedEventArgs** zveřejňuje své členy jako vlastnosti jen pro čtení a nikoli pole, protože pole zabraňují datové vazbě.

    - Nedefinujte <xref:System.ComponentModel.AsyncCompletedEventArgs>žádné odvozené třídy pro metody, které nevytvářejí výsledky. Jednoduše použijte instanci <xref:System.ComponentModel.AsyncCompletedEventArgs> sám o sobě.

      > [!NOTE]
      > Je naprosto přijatelné, pokud je to proveditelné a <xref:System.ComponentModel.AsyncCompletedEventArgs> vhodné, znovu použít delegáta a typy. V tomto případě nebude pojmenování tak konzistentní s názvem metody, <xref:System.ComponentModel.AsyncCompletedEventArgs> protože daný delegát a nebude vázán a jedinou metodou.

## <a name="optionally-support-cancellation"></a>Volitelně podpora zrušení

Pokud vaše třída bude podporovat zrušení asynchronní operace, zrušení by měla být vystavena klientovi, jak je popsáno níže. Všimněte si, že existují dva body rozhodnutí, které je třeba dosáhnout před definováním podpory zrušení:

- Má vaše třída, včetně budoucích očekávaných dodatků k ní, pouze jednu asynchronní operaci, která podporuje zrušení?

- Mohou asynchronní operace, které podporují zrušení, podporovat více čekajících operací? To znamená, že metoda _MethodName_ `userState` **Async** trvá parametr a umožňuje více vyvolání před čekáním na dokončení jakékoli?

Pomocí odpovědí na tyto dvě otázky v následující tabulce určete, jaký by měl být podpis pro metodu zrušení.

### <a name="visual-basic"></a>Visual Basic

||Podporováno více souběžných operací|Pouze jedna operace najednou|
|------|------------------------------------------------|----------------------------------|
|Jedna asynchronní operace v celé třídě|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|Více asynchronních operací ve třídě|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a>C\#

||Podporováno více souběžných operací|Pouze jedna operace najednou|
|------|------------------------------------------------|----------------------------------|
|Jedna asynchronní operace v celé třídě|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|Více asynchronních operací ve třídě|`void CancelAsync(object userState);`|`void CancelAsync();`|

Pokud definujete `CancelAsync(object userState)` metodu, klienti musí být opatrní při výběru jejich hodnoty stavu, aby byly schopny rozlišit mezi všechny asynchronní metody vyvolané na objektu a nikoli pouze mezi všechny vyvolání jedné asynchronní metody.

Rozhodnutí pojmenovat verzi methodname _MethodName_**AsyncCancel** s jednou asynchronní operací je založeno na možnosti snadněji zjistit metodu v návrhovém prostředí, jako je technologie IntelliSense sady Visual Studio. To seskupuje související členy a odlišuje je od ostatních členů, kteří nemají nic společného s asynchronní funkce. Pokud očekáváte, že mohou být přidány další asynchronní operace v `CancelAsync`následujících verzích, je lepší definovat .

Nedefinujte více metod z výše uvedené tabulky ve stejné třídě. To nebude dávat smysl, nebo to bude nepořádek třídy rozhraní s šíření metod.

Tyto metody se obvykle vrátí okamžitě a operace může nebo nemusí ve skutečnosti zrušit. V obslužné rutině události _MethodName_**Completed** objekt _MethodName_**Completed Obsahuje** `Cancelled` pole, které mohou klienti použít k určení, zda došlo ke zrušení.

Řiďte se sémantikou zrušení popsanou v [doporučených postupech pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="optionally-support-the-isbusy-property"></a>Volitelně podporovat vlastnost IsBusy

Pokud vaše třída nepodporuje více souběžných vyvolání, `IsBusy` zvažte vystavení vlastnosti. To umožňuje vývojářům určit, zda method _MethodName_**Async** je spuštěna bez zachycení výjimky z _MethodName_**Async** metody.

Řiďte `IsBusy` se sémantikou popsanou v [doporučených postupech pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="optionally-provide-support-for-progress-reporting"></a>Volitelně poskytovat podporu pro vykazování průběhu

Často je žádoucí, aby asynchronní operace hlásila průběh během operace. Asynchronní vzor založený na událostech poskytuje pokyny k tomu.

- Volitelně definujte událost, která má být vyvolána asynchronní operací a vyvolána v příslušném vlákně. Objekt <xref:System.ComponentModel.ProgressChangedEventArgs> nese indikátor průběhu s celočíselnou hodnotou, u kterého se očekává hodnota mezi 0 a 100.

- Pojmenujte tuto událost takto:

  - `ProgressChanged`pokud třída má více asynchronních operací (nebo se očekává, že růst zahrnout více asynchronních operací v budoucích verzích);

  - _MethodName_**ProgressChanged** pokud má třída jednu asynchronní operaci.

  Tato volba pojmenování paralely, které byly provedeny pro metodu zrušení, jak je popsáno v volitelně podpora zrušení části.

Tato událost by <xref:System.ComponentModel.ProgressChangedEventHandler> měla používat <xref:System.ComponentModel.ProgressChangedEventArgs> podpis delegáta a třídu. Případně pokud lze poskytnout indikátor průběhu více specifický pro doménu (například bajty pro čtení a celkové bajty pro operaci <xref:System.ComponentModel.ProgressChangedEventArgs>stahování), měli byste definovat odvozenou třídu .

Všimněte si, `ProgressChanged` že existuje pouze jeden nebo _MethodName_**ProgressChanged** událost pro třídu, bez ohledu na počet asynchronních metod, které podporuje. Očekává se, že `userState` klienti budou používat objekt, který je předán metodám _MethodName_**Async,** k rozlišení mezi aktualizacemi průběhu více souběžných operací.

Mohou nastat situace, ve kterých více operací podporují průběh a každý vrátí jiný ukazatel pro průběh. V tomto případě `ProgressChanged` jedna událost není vhodné a můžete `ProgressChanged` zvážit podporu více událostí. V tomto případě použijte vzor pojmenování _MethodName_**ProgressChanged** pro každou _metodu MethodName_**Async.**

Dodržujte sémantiku hlášení průběhu popsanou [doporučené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="optionally-provide-support-for-returning-incremental-results"></a>Volitelně poskytují podporu pro vrácení přírůstkových výsledků

Někdy asynchronní operace může vrátit přírůstkové výsledky před dokončením. Existuje několik možností, které lze použít pro podporu tohoto scénáře. Některé příklady následují.

### <a name="single-operation-class"></a>Třída s jednou operací

Pokud vaše třída podporuje pouze jednu asynchronní operaci a tato operace je schopna vrátit přírůstkové výsledky, pak:

- Rozšiřte <xref:System.ComponentModel.ProgressChangedEventArgs> typ tak, aby přenášel přírůstková data výsledků, a definujte událost _MethodName_**ProgressChanged** s těmito rozšířenými daty.

- Raise this _MethodName_**ProgressChanged** událost když je přírůstkový výsledek sestavy.

Toto řešení platí konkrétně pro třídu single-async-operation, protože neexistuje žádný problém se stejnou událostí, ke které dochází, aby se vrátily přírůstkové výsledky na "všechny operace", jako to dělá událost _MethodName_**ProgressChanged.**

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Třída s více operacemi s homogenními přírůstkovými výsledky

V tomto případě vaše třída podporuje více asynchronních metod, z nichž každá je schopna vracet přírůstkové výsledky a tyto přírůstkové výsledky mají stejný typ dat.

Postupujte podle výše popsaného modelu pro třídy s jednou operací, protože stejná <xref:System.EventArgs> struktura bude fungovat pro všechny přírůstkové výsledky. Definujte `ProgressChanged` událost namísto události _MethodName_**ProgressChanged,** protože se vztahuje na více asynchronních metod.

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Třída s více operacemi s heterogenními přírůstkovými výsledky

Pokud vaše třída podporuje více asynchronních metod, každý vrací jiný typ dat, měli byste:

- Oddělte přírůstkové vykazování výsledků od vykazování průběhu.

- Definujte samostatnou událost _MethodName_**ProgressChanged** s příslušnou <xref:System.EventArgs> pro každou asynchronní metodu pro zpracování přírůstkových dat výsledků této metody.

Vyvolat tuto obslužnou rutinu události v příslušném vlákně, jak je popsáno v [doporučených postupech pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="handling-out-and-ref-parameters-in-methods"></a>Zpracování a ref parametry v metodách

Přestože použití `out` `ref` a je obecně nedoporučuje v rozhraní .NET Framework, zde jsou pravidla dodržovat, když jsou k dispozici:

Vzhledem k tomu, synchronní metoda *MethodName*:

- `out`parametry *MethodName* by neměly být součástí _MethodName_**Async**. Místo toho by měly být součástí _MethodName_**CompletedEventArgs** se stejným názvem jako jeho ekvivalent parametru v *MethodName* (pokud neexistuje vhodnější název).

- `ref`parametry *methodname* by se měly zobrazit jako součást _MethodName_**Async**a jako součást _MethodName_**CompletedEventArgs** se stejným názvem jako jeho ekvivalent parametru v *MethodName* (pokud není vhodnější název).

Například vzhledem k tomu, že:

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

Vaše asynchronní metoda <xref:System.ComponentModel.AsyncCompletedEventArgs> a její třída bude vypadat takto:

```vb
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)

Public Class MethodNameCompletedEventArgs
    Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As Integer
    End Property
    Public ReadOnly Property Arg2() As String
    End Property
    Public ReadOnly Property Arg3() As String
    End Property
End Class
```

```csharp
public void MethodNameAsync(string arg1, string arg2);

public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
{
    public int Result { get; };
    public string Arg2 { get; };
    public string Arg3 { get; };
}
```

## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
