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
ms.openlocfilehash: 484050b45b5da72386e9ac29805d7faf0ca9cbd6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289379"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Implementace asynchronního vzoru založeného na událostech

Pokud píšete třídu s některými operacemi, které mohou znamenat znatelné prodlevy, zvažte, že je možné poskytnout asynchronní funkce pomocí [přehledu asynchronního vzoru založeného na událostech](event-based-asynchronous-pattern-overview.md).

Asynchronní vzor založený na událostech poskytuje standardizovaný způsob, jak zabalit třídu, která obsahuje asynchronní funkce. Pokud je tato třída implementována s podpůrnými třídami jako <xref:System.ComponentModel.AsyncOperationManager> , bude správně fungovat v jakémkoli modelu aplikace, včetně ASP.NET, konzolových aplikací a aplikací model Windows Forms.

Příklad, který implementuje asynchronní vzor založený na událostech, naleznete v tématu [How to: Implementing a Component, která podporuje asynchronní vzor založený na událostech](component-that-supports-the-event-based-asynchronous-pattern.md).

U jednoduchých asynchronních operací můžete najít <xref:System.ComponentModel.BackgroundWorker> vhodnou komponentu. Další informace o najdete v <xref:System.ComponentModel.BackgroundWorker> tématu [Postup: spuštění operace na pozadí](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md).

Následující seznam popisuje funkce asynchronního vzoru založeného na událostech, které jsou popsány v tomto tématu.

- Příležitosti pro implementaci asynchronního vzoru založeného na událostech

- Pojmenovávání asynchronních metod

- Volitelně podpora zrušení

- Volitelně podporuje vlastnost Busy

- Volitelně poskytuje podporu pro vytváření sestav o průběhu.

- Volitelně poskytuje podporu pro vracení přírůstkových výsledků.

- Zpracování parametrů a odkazů v metodách

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Příležitosti pro implementaci asynchronního vzoru založeného na událostech

Zvažte implementaci asynchronního vzoru založeného na událostech v těchto případech:

- Klienti vaší třídy nepotřebují <xref:System.Threading.WaitHandle> a <xref:System.IAsyncResult> k dispozici jsou objekty pro asynchronní operace, což znamená, že klient musí vytvořit cyklické dotazování a <xref:System.Threading.WaitHandle.WaitAll%2A> nebo <xref:System.Threading.WaitHandle.WaitAny%2A> bude muset být sestaven.

- Chcete, aby byly asynchronní operace spravovány klientem se známým modelem události nebo delegáta.

Každá operace je kandidátem na asynchronní implementaci, ale je třeba vzít v úvahu, že byste měli zvážit dlouhou latenci. Zvlášť vhodné jsou operace, ve kterých klienti volají metodu a jsou informováni o dokončení, a to bez nutnosti dalšího zásahu. Také vhodné jsou operace, které pracují průběžně a pravidelně upozorňují na jejich průběh, přírůstkové výsledky nebo změny stavu.

Další informace o rozhodování o podpoře asynchronního vzoru založeného na událostech naleznete v tématu [rozhodování, kdy implementovat asynchronní vzor založený na událostech](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).

## <a name="naming-asynchronous-methods"></a>Pojmenovávání asynchronních metod

Pro každou synchronní metodu *methodName* , pro kterou chcete poskytnout asynchronní protějšek:

Definujte**asynchronní** metodu _methodName_, která:

- Vrací objekt `void`.

- Přebírá stejné parametry jako metoda *methodName* .

- Umožňuje přijmout vícenásobná volání.

Volitelně definujte**asynchronní** přetížení _methodName_, které je identické s _methodName_**Async**, ale s dalším parametrem s hodnotou objektu s názvem `userState` . Tuto akci proveďte, pokud jste připraveni ke správě více souběžných volání vaší metody. v takovém případě `userState` bude hodnota doručena zpět do všech obslužných rutin událostí pro odlišení vyvolání metody. Můžete to také provést jednoduše jako místo pro uložení stavu uživatele pro pozdější načtení.

Pro každou samostatnou signaturu**asynchronní** metody _methodName_:

1. Definujte následující událost ve stejné třídě jako metodu:

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. Definujte následujícího delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs> . Tyto prvky budou pravděpodobně definovány mimo samotnou třídu, ale ve stejném oboru názvů.

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

    - Ujistěte se, že třída _methodName_**CompletedEventArgs** zpřístupňuje své členy jako vlastnosti jen pro čtení, nikoli pole, protože pole zabraňují vytváření datových vazeb.

    - Nedefinujte žádné <xref:System.ComponentModel.AsyncCompletedEventArgs> odvozené třídy pro metody, které nevedou k výsledkům. Jednoduše použijte instanci <xref:System.ComponentModel.AsyncCompletedEventArgs> sebe sama.

      > [!NOTE]
      > Je dokonale přijatelné, pokud je to proveditelné a vhodné, k opakovanému použití delegátů a <xref:System.ComponentModel.AsyncCompletedEventArgs> typů. V takovém případě nebude pojmenování konzistentní s názvem metody, protože daný delegát a <xref:System.ComponentModel.AsyncCompletedEventArgs> nebude svázán s jedinou metodou.

## <a name="optionally-support-cancellation"></a>Volitelně podpora zrušení

Pokud vaše třída bude podporovat zrušení asynchronních operací, zrušení by mělo být zveřejněno klientovi, jak je popsáno níže. Všimněte si, že před definováním podpory zrušení se musí dosáhnout dva rozhodovací body:

- Obsahuje vaše třída, včetně budoucích předpokládaných dodatků, jenom jednu asynchronní operaci, která podporuje zrušení?

- Mohou asynchronní operace, které podporují zrušení, podporují více operací, které čekají na vyřízení? To znamená, že**asynchronní** metoda _methodName_přijímá `userState` parametr a umožňuje vícenásobné vyvolání před čekáním na dokončení?

Pomocí odpovědí na tyto dvě otázky v následující tabulce zjistíte, jak by měl být signatura metody zrušení.

### <a name="visual-basic"></a>Visual Basic

||Podporuje se víc souběžných operací.|Vždy jen jedna operace|
|------|------------------------------------------------|----------------------------------|
|Jedna asynchronní operace v celé třídě|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|Několik asynchronních operací ve třídě|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a>C\#

||Podporuje se víc souběžných operací.|Vždy jen jedna operace|
|------|------------------------------------------------|----------------------------------|
|Jedna asynchronní operace v celé třídě|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|Několik asynchronních operací ve třídě|`void CancelAsync(object userState);`|`void CancelAsync();`|

Pokud definujete `CancelAsync(object userState)` metodu, musí být klienti opatrní při volbě jejich hodnot stavu, aby je bylo možné rozlišovat mezi všemi asynchronními metodami, které jsou vyvolány u objektu, a nikoli pouze mezi všemi voláními jedné asynchronní metody.

Rozhodnutí o pojmenování jedné asynchronní operace _methodName_**AsyncCancel** je založené na tom, že je možné snadněji zjistit metodu ve vývojovém prostředí, jako je například IntelliSense sady Visual Studio. Seskupení souvisejících členů a jejich rozlišení od jiných členů, kteří nemají nic dělat s asynchronními funkcemi. Pokud očekáváte, že v následných verzích se přidaly další asynchronní operace, je lepší definovat `CancelAsync` .

Nedefinujte více metod z tabulky výše ve stejné třídě. Který nebude dávat smysl, nebo by měl zazbytečně zaměnit rozhraní třídy s přemnožením metod.

Tyto metody se obvykle vrátí okamžitě a operace může nebo nemusí ve skutečnosti zrušit. V obslužné rutině události pro událost _methodName_**Completed** obsahuje objekt _methodName_**CompletedEventArgs** `Cancelled` pole, které klienti mohou použít k určení, zda došlo ke zrušení.

Řídí se sémantikou zrušení popsanou v tématu [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="optionally-support-the-isbusy-property"></a>Volitelně podporuje vlastnost Busy

Pokud vaše třída nepodporuje více souběžných volání, zvažte vystavení `IsBusy` Vlastnosti. To umožňuje vývojářům určit, zda je _methodName_**asynchronní** metoda spuštěna bez zachycení výjimky z**asynchronní** metody _methodName_.

Dodržuje `IsBusy` sémantiku popsanou v tématu [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="optionally-provide-support-for-progress-reporting"></a>Volitelně poskytuje podporu pro vytváření sestav o průběhu.

Je často žádoucí, aby asynchronní operace nahlásila pokrok během jeho provozu. Asynchronní vzor založený na událostech poskytuje pokyny pro to.

- Volitelně můžete definovat událost, která má být vyvolána asynchronní operací a vyvolána v příslušném vlákně. <xref:System.ComponentModel.ProgressChangedEventArgs>Objekt přenese ukazatel průběhu s celočíselnou hodnotou, který by měl být v rozmezí od 0 do 100.

- Pojmenujte tuto událost následujícím způsobem:

  - `ProgressChanged`Pokud má třída více asynchronních operací (nebo se očekává, že se má rozšířit, aby zahrnovalo více asynchronních operací v budoucích verzích);

  - _MethodName_**ProgressChanged** , pokud má třída jedinou asynchronní operaci.

  Tato volba pojmenovává paralelně, kterou vytvořila metoda zrušení, jak je popsáno v části volitelná zrušení podpory.

Tato událost by měla používat <xref:System.ComponentModel.ProgressChangedEventHandler> signaturu delegáta a <xref:System.ComponentModel.ProgressChangedEventArgs> třídu. Případně, pokud je možné zadat více ukazatelů průběhu pro doménu (například přečtené bajty a celkový počet bajtů pro operaci stažení), je třeba definovat odvozenou třídu třídy <xref:System.ComponentModel.ProgressChangedEventArgs> .

Všimněte si, že existuje pouze jedna `ProgressChanged` nebo _methodName_**ProgressChanged** událost pro třídu, bez ohledu na počet asynchronních metod, které podporuje. U klientů se očekává použití `userState` objektu, který je předán**asynchronním** metodám _methodName_k rozlišení mezi aktualizacemi průběhu více souběžných operací.

Mohou nastat situace, kdy více operací podporuje průběh a každý vrací jiný indikátor pro průběh. V takovém případě jedna `ProgressChanged` událost není vhodná a může zvážit podporu více `ProgressChanged` událostí. V tomto případě použijte pro každou _methodName_**asynchronní** metodu vzor pojmenování _methodName_**ProgressChanged** .

Dodržuje sémantické sémantiky vytváření sestav, které popisují [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="optionally-provide-support-for-returning-incremental-results"></a>Volitelně poskytuje podporu pro vracení přírůstkových výsledků.

V některých případech může asynchronní operace vracet přírůstkové výsledky před dokončením. K dispozici je několik možností, které lze použít k podpoře tohoto scénáře. Následuje několik příkladů.

### <a name="single-operation-class"></a>Třída s jednou operací

Pokud vaše třída podporuje jenom jednu asynchronní operaci a tato operace může vracet přírůstkové výsledky, pak:

- Rozšiřte <xref:System.ComponentModel.ProgressChangedEventArgs> typ tak, aby převedl data přírůstkového výsledku, a definujte událost _methodName_**ProgressChanged** s rozšířenými daty.

- Vyvolá tuto událost _methodName_**ProgressChanged** , když se zobrazí přírůstkový výsledek pro sestavu.

Toto řešení se vztahuje konkrétně na třídu s jednou asynchronní operací, protože neexistují žádné potíže se stejnou událostí, která by mohla vracet přírůstkové výsledky pro všechny operace, jako událost _methodName_**ProgressChanged** .

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Třída s vícenásobnou operací s homogenními přírůstkovým výsledkem

V takovém případě vaše třída podporuje několik asynchronních metod, z nichž každý dokáže vracet přírůstkové výsledky a tyto přírůstkové výsledky mají stejný typ dat.

Použijte model popsaný výše pro třídy s jednou operací, protože stejná <xref:System.EventArgs> struktura bude fungovat pro všechny přírůstkové výsledky. Definujte `ProgressChanged` událost namísto události _methodName_**ProgressChanged** , protože se vztahuje na více asynchronních metod.

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Třída vícenásobných operací s heterogenními přírůstkových výsledků

Pokud vaše třída podporuje více asynchronních metod, každý z nich vrátí jiný typ dat, měli byste:

- Oddělte sestavy přírůstkových výsledků od sestav průběhu.

- Definujte samostatnou událost _methodName_**ProgressChanged** , <xref:System.EventArgs> která je vhodná pro každou asynchronní metodu pro zpracování dat přírůstkového výsledku této metody.

Vyvolejte tuto obslužnou rutinu události v příslušném vlákně, jak je popsáno v tématu [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="handling-out-and-ref-parameters-in-methods"></a>Zpracování parametrů a odkazů v metodách

I když použití `out` a `ref` je obecně v .NET Framework nedoporučujeme, tady jsou pravidla, která se mají sledovat, když jsou k dispozici:

Předané synchronní metodě *methodName*:

- `out`parametry *methodName* by neměly být součástí**asynchronního** _methodName_. Místo toho by měly být součástí _methodName_**CompletedEventArgs** se stejným názvem jako má ekvivalentní parametr v *methodName* (Pokud neexistuje vhodnější název).

- `ref`parametry *methodName* by se měly zobrazit jako součást _methodName_**Async**a jako součást _methodName_**CompletedEventArgs** se stejným názvem jako má ekvivalentní parametr v *methodName* (Pokud neexistuje vhodnější název).

Například předané:

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

Asynchronní metoda a její <xref:System.ComponentModel.AsyncCompletedEventArgs> třída by vypadaly takto:

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
- [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](component-that-supports-the-event-based-asynchronous-pattern.md)
- [Postupy: Spuštění operace na pozadí](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Postupy: Implementace formuláře, který používá operaci na pozadí](../../framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md)
