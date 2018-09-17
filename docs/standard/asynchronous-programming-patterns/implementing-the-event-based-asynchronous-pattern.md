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
ms.openlocfilehash: 3cb38cd9d7b27ab28b602e4e4c813d58d904abd3
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746806"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Implementace asynchronního vzoru založeného na událostech
Pokud píšete třída s atributem některé operace, které případně utrpíte významnému zpoždění, zvažte jeho asynchronní funkce implementací [založený na událostech přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Asynchronní vzor založený na událostech poskytuje standardizované způsob, jak zabalit třídu, která obsahuje asynchronní funkce. Pokud se implementuje pomocí tříd pomocných rutin, jako jsou <xref:System.ComponentModel.AsyncOperationManager>, vaše třída bude správně fungovat v jakékoli aplikační model, včetně [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], konzolových aplikací a aplikací Windows Forms.  
  
 Příklad, který implementuje asynchronního vzoru založeného na událostech, naleznete v tématu [postupy: implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Pro jednoduché asynchronní operace, můžete zjistit <xref:System.ComponentModel.BackgroundWorker> komponenty vhodná. Další informace o <xref:System.ComponentModel.BackgroundWorker>, naleznete v tématu [postupy: spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
 Následující seznam popisuje funkce asynchronního vzoru založeného na událostech popsané v tomto tématu.  
  
-   Příležitosti pro implementaci asynchronního vzoru založeného na událostech  
  
-   Názvy asynchronních metod  
  
-   Volitelně podporují zrušení  
  
-   Volitelně podporovat vlastnost IsBusy  
  
-   Volitelně můžete poskytovat podporu pro vykazování průběhu  
  
-   Volitelně můžete poskytovat podporu pro vrácení přírůstkové výsledků  
  
-   Zpracování Out a Ref parametrů metody  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Příležitosti pro implementaci asynchronního vzoru založeného na událostech  
 Zvažte implementaci asynchronního vzoru založeného na událostech při:  
  
-   Není nutné klientům vaší třídy <xref:System.Threading.WaitHandle> a <xref:System.IAsyncResult> objekty, které jsou k dispozici pro asynchronní operace, což znamená, že dotazování a <xref:System.Threading.WaitHandle.WaitAll%2A> nebo <xref:System.Threading.WaitHandle.WaitAny%2A> muset být vytvářeny klientem.  
  
-   Chcete, aby asynchronní operace lze spravovat pomocí klienta s modelem známé události nebo delegáta.  
  
 Všechny operace je kandidátem pro implementaci asynchronních, ale ty očekáváte, že budou účtovat dlouhé latenci by měl být. Operace ve kterých klientech volání metody a upozorněni na dokončení bez dalšího zásahu vyžaduje jsou zvlášť vhodná. Vhodné jsou také operace, které běží nepřetržitě, pravidelně upozornění klientů průběh, přírůstkové výsledky nebo změny stavu.  
  
 Další informace o rozhodování, kdy podporují asynchronní vzor založený na událostech najdete v tématu [rozhodování o tom, když k implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).  
  
## <a name="naming-asynchronous-methods"></a>Názvy asynchronních metod  
 Pro každou metodu synchronní *MethodName* pro které chcete poskytnout asynchronní protějšek:  
  
 Definování _MethodName_**asynchronní** metoda, která:  
  
-   Vrátí `void`.  
  
-   Má stejné parametry jako *MethodName* metody.  
  
-   Přijímá více volání.  
  
 Volitelně můžete definovat _MethodName_**asynchronní** přetížení, stejný jako _MethodName_**asynchronní**, ale ještě objekt s hodnotou Parametr s názvem `userState`. To provést, pokud jste připraveni spravovat více souběžných volání metody, v takovém případě `userState` doručí hodnotu zpět na všechny obslužné rutiny události k rozlišení volání metody. Můžete to udělat jednoduše jako místo k uložení stavu uživatele pro pozdější načtení.  
  
 Pro každou zvláštní _MethodName_**asynchronní** podpis metody:  
  
1.  Definujte následující událost ve stejné třídě, jako metodu:  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  Definovat následující delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs>. Tyto bude mít definici pravděpodobně mimo vlastní třídy, ale stejný obor názvů.  
  
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
  
    -   Ujistěte se, _MethodName_**CompletedEventArgs** třída zveřejňuje její členy jako vlastnosti jen pro čtení a nikoli pole jako pole datové vazby.  
  
    -   Není definován žádný <xref:System.ComponentModel.AsyncCompletedEventArgs>-odvozené třídy pro metody, které neposkytují výsledky. Stačí použít instanci <xref:System.ComponentModel.AsyncCompletedEventArgs> samotný.  
  
        > [!NOTE]
        >  Je zcela přijatelné, když a proveditelné, opakovaně používat delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs> typy. V tomto případě pojmenování nebude odpovídat jako název metody, od daného delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs> nesmí být vázán na jedinou metodu.  
  
## <a name="optionally-support-cancellation"></a>Volitelně podporují zrušení  
 Pokud vaše třída bude podporovat zrušení asynchronní operace, by měly být vystaveny zrušení klientovi, jak je popsáno níže. Všimněte si, že existují dvě rozhodovací body, které je potřeba dosáhnout před definováním podpoře zrušení:  
  
-   Má vaše třída, včetně budoucí očekávané dodatky, pouze jedna asynchronní operace, která podporuje zrušení?  
  
-   Je asynchronní operace, které podporují více čekající operace podporu zrušení? To znamená, nemá _MethodName_**asynchronní** take – metoda `userState` parametr, a to neumožňuje několika vyvoláními čeká na dokončení některého?  
  
 Chcete-li zjistit, co by měl být podpis pro metodu zrušení pomocí odpovědi na tyto dvě otázky v následující tabulce.  
  
### <a name="visual-basic"></a>Visual Basic  
  
||Nepodporuje více souběžných operací.|Pouze jedna operace v čase|  
|------|------------------------------------------------|----------------------------------|  
|Jedna asynchronní operace v celé třídy|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|Více asynchronních operací v třídě|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C#  
  
||Nepodporuje více souběžných operací.|Pouze jedna operace v čase|  
|------|------------------------------------------------|----------------------------------|  
|Jedna asynchronní operace v celé třídy|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|Více asynchronních operací v třídě|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 Pokud definujete `CancelAsync(object userState)` metody, klienti musí být opatrní při volbě jejich stavu hodnoty tak, aby je schopna rozlišovat mezi všechny asynchronní metody vyvolané na objekt a ne jenom mezi všechny volání jedné asynchronní metody.  
  
 Rozhodnutí o název verze jedním. asynchronní operace _MethodName_**AsyncCancel** vychází nebudou moct snadněji zjistit metodu v návrhovém prostředí, jako je IntelliSense ve Visual Studio. Tím se skupiny souvisejících členů a odlišuje od ostatních členů, které nesouvisí s asynchronní funkcí. Pokud očekáváte, že můžou existovat další asynchronních operací přibylo v dalších verzích, je lepší definovat `CancelAsync`.  
  
 Ve stejné třídě nedefinují více metod z výše uvedené tabulce. Který nebude dávat smysl, nebo ji bude dál sbližuje tyto rozhraní třídy s růst počtu metody.  
  
 Tyto metody obvykle vrátí okamžitě, a tato operace může nebo nemusí skutečně zrušit. V obslužné rutině události pro _MethodName_**dokončeno** událostí, _MethodName_**CompletedEventArgs** objekt obsahuje `Cancelled` pole, které můžou klienti použít k určení, zda došlo k zrušení.  
  
 Dodržováním podle sémantiky zrušení [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-support-the-isbusy-property"></a>Volitelně podporovat vlastnost IsBusy  
 Pokud vaše třída nepodporuje více souběžných volání, vezměte v úvahu vystavení `IsBusy` vlastnost. To umožňuje vývojářům určit, jestli _MethodName_**asynchronní** metodu je spuštěna bez zachycování výjimky z _MethodName_**asynchronní**  metody.  
  
 Dodržováním `IsBusy` podle sémantiky [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>Volitelně můžete poskytovat podporu pro vykazování průběhu  
 Je často žádoucí, aby asynchronní operaci na informace o průběhu během jeho operace. Asynchronní vzor založený na událostech poskytuje vodítko to udělat.  
  
-   Volitelně definuje události vyvolané službou asynchronní operace a vyvolána na odpovídající vlákno. <xref:System.ComponentModel.ProgressChangedEventArgs> Objekt představuje indikátor průběhu vracející celé číslo, který má být v rozmezí od 0 do 100.  
  
-   Pojmenujte tuto událost následujícím způsobem:  
  
    -   `ProgressChanged` Pokud třída má více asynchronních operací (nebo se očekává růst zahrnout více asynchronních operací v budoucích verzích);  
  
    -   _MethodName_**ProgressChanged** Pokud má třída jedné asynchronní operace.  
  
     Tato volba názvů, který vytvořil pro metodu zrušení parallels, jak je popsáno v části volitelně podporu zrušení.  
  
 Tato událost používejte <xref:System.ComponentModel.ProgressChangedEventHandler> delegáta a <xref:System.ComponentModel.ProgressChangedEventArgs> třídy. Případně, pokud indikátor průběhu více specifického pro doménu může být poskytnuta (pro instanci, přečtených bajtů a celkový počet bajtů pro operace nástroje download), pak byste měli definovat odvozenou třídu <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
 Všimněte si, že existuje pouze jeden `ProgressChanged` nebo _MethodName_**ProgressChanged** události pro třídu, bez ohledu na počet asynchronních metod, které podporuje. Se očekává, že klienti používat `userState` objekt, který je předán _MethodName_**asynchronní** metody k rozlišení mezi průběh aktualizací na více souběžných operací.  
  
 Může nastat situace, ve kterých více operací podporují průběh a každá vrátí jiný indikátor průběhu. V tomto případě jediný `ProgressChanged` událostí není vhodná, a může být vhodné, podpora více `ProgressChanged` události. V tomto případě použijte vzor pojmenování spočívající v _MethodName_**ProgressChanged** pro každou _MethodName_**asynchronní** metody.  
  
 Dodržováním vykazování průběhu sémantiku popsané [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>Volitelně můžete poskytovat podporu pro vrácení přírůstkové výsledků  
 Asynchronní operace v některých případech může vrátit přírůstkové výsledky před dokončením. Existuje mnoho možností, které lze použít pro podporu tohoto scénáře. Některé příklady.  
  
### <a name="single-operation-class"></a>Jedním operation – třída  
 Pokud vaše třída podporuje pouze jeden asynchronní operace a tato operace se bude moct vrátit přírůstkové výsledky, pak:  
  
-   Rozšíření <xref:System.ComponentModel.ProgressChangedEventArgs> typu provádět přírůstkové Výsledná data a definujte _MethodName_**ProgressChanged** událostí s tímto Rozšířená data.  
  
-   Vyvolat to _MethodName_**ProgressChanged** událost v případě, že je výsledek přírůstkové do sestavy.  
  
 Toto řešení platí konkrétně pro třídu jedním. asynchronní operace, protože neexistuje žádný problém s stejné události, ke kterým dochází pro vracení výsledků přírůstkové "všechny operace", jako _MethodName_**ProgressChanged**  nepodporuje události.  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Třída více operace s homogenní přírůstkové výsledky  
 V tomto případě vaše třída podporuje několik asynchronních metod každý může vracet přírůstkové výsledků, a tyto přírůstkové výsledky všechny mají stejný typ dat.  
  
 Postupujte podle výše uvedeného třídy jedné operace, jako stejný model <xref:System.EventArgs> struktura bude fungovat pro všechny přírůstkové výsledky. Definování `ProgressChanged` události místo _MethodName_**ProgressChanged** událost, protože se vztahuje na několik asynchronních metod.  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Třída více operace s heterogenní přírůstkové výsledky  
 Pokud vaše třída podporuje několik asynchronních metod, každé vrácení jiný typ dat, měli byste:  
  
-   Oddělení přírůstkových výsledků generování sestav z vykazování průběhu.  
  
-   Definujte samostatný _MethodName_**ProgressChanged** událost s odpovídající <xref:System.EventArgs> pro každou asynchronní metodu ke zpracování dat přírůstkové výsledek této metody.  
  
 Vyvolání této obslužné rutiny události v příslušné vláknu, jak je popsáno v [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>Zpracování Out a Ref parametrů metody  
 I když využívání `out` a `ref` se obecně nedoporučuje v rozhraní .NET Framework, jsou zde pravidla při jsou k dispozici:  
  
 Zadaný synchronní metoda *MethodName*:  
  
-   `out` Parametry se mají *MethodName* by neměly být součástí _MethodName_**asynchronní**. Místo toho by měla být součástí _MethodName_**CompletedEventArgs** se stejným názvem jako svůj parametr ekvivalentní v *MethodName* (Pokud není vhodnější Název).  
  
-   `ref` Parametry se mají *MethodName* by se měla zobrazit jako součást _MethodName_**asynchronní**a jako součást _MethodName_  **CompletedEventArgs** se stejným názvem jako svůj parametr ekvivalentní v *MethodName* (Pokud není vhodnější název).  
  
 Mějme například:  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 Asynchronní metody a jeho <xref:System.ComponentModel.AsyncCompletedEventArgs> třídy bude vypadat takto:  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.ProgressChangedEventArgs>  
- <xref:System.ComponentModel.AsyncCompletedEventArgs>  
- [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
- [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
- [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
- [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
- [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
