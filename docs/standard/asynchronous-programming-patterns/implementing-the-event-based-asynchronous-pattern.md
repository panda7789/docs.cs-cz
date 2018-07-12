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
ms.openlocfilehash: 89de0690c0f9788120f7805b0b63c22ecafa6b9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577356"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Implementace asynchronního vzoru založeného na událostech
Pokud píšete třídu s některé operace, které může vést k významnému zpoždění, zvažte, udělíte tím, že implementujete asynchronní funkce [na základě událostí přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Asynchronní vzor založený na událostech poskytuje standardizovaného způsobu balíček třídy, která má asynchronní funkce. Pokud se implementuje pomocí pomocné třídy jako <xref:System.ComponentModel.AsyncOperationManager>, třídě nebude pracovat správně v rámci modelu všechny aplikace, včetně [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], konzolové aplikace a aplikace Windows Forms.  
  
 Příklad, který implementuje asynchronní vzor na základě událostí, naleznete v části [postupy: implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Pro jednoduché asynchronní operace, můžete zjistit <xref:System.ComponentModel.BackgroundWorker> součást vhodný. Další informace o <xref:System.ComponentModel.BackgroundWorker>, najdete v části [postupy: spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
 Následující seznam popisuje funkce asynchronního vzoru založeného na událostech popsané v tomto tématu.  
  
-   Možnosti pro implementaci asynchronního vzoru založeného na událostech  
  
-   Pojmenování asynchronních metod  
  
-   Volitelně podporovat zrušení  
  
-   Volitelně podporovat vlastnost IsBusy  
  
-   Volitelně můžete poskytovat podporu pro vytváření sestav průběh  
  
-   Volitelně můžete poskytovat podporu pro vrácení přírůstkové výsledky  
  
-   Zpracování Out a parametry Ref v metody  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Možnosti pro implementaci asynchronního vzoru založeného na událostech  
 Zvažte implementaci asynchronního vzoru založeného na událostech při:  
  
-   Není třeba klienty vaší třídy <xref:System.Threading.WaitHandle> a <xref:System.IAsyncResult> objekty, které jsou k dispozici pro asynchronní operace, což znamená, že dotazování a <xref:System.Threading.WaitHandle.WaitAll%2A> nebo <xref:System.Threading.WaitHandle.WaitAny%2A> muset sestavena klienta.  
  
-   Chcete asynchronní operace lze spravovat pomocí klienta s modelem známé událostí/delegování.  
  
 Všechny operace je kandidátem pro implementaci asynchronního, ale ty očekáváte zabývat dlouho latence potřeba vzít v úvahu. Zejména příslušné jsou operace, ve kterých klientech volání metody, které jsou při dokončení, bez nutnosti zásahu Další. Odpovídající jsou také operací, které spouštět nepřetržitě, pravidelně upozornění klientů průběh, přírůstkové výsledků nebo změny stavu.  
  
 Další informace o rozhodování, kdy podporují asynchronní vzor založený na událostech najdete v tématu [rozhodování při implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).  
  
## <a name="naming-asynchronous-methods"></a>Pojmenování asynchronních metod  
 Pro každou metodu synchronní *MethodName* pro které byste chtěli poskytnout asynchronní protějšku:  
  
 Definování *MethodName *** asynchronní** metoda který:  
  
-   Vrátí `void`.  
  
-   Používá stejný parametry, jako *MethodName* metoda.  
  
-   Přijme více volání.  
  
 Volitelně můžete definovat *MethodName *** asynchronní** přetížení, identické * MethodName ***asynchronní**, ale s další parametr s hodnotou objekt názvem `userState`. To udělat, pokud jste se připravili na správu více souběžných volání metody, v takovém případě `userState` hodnota bude doručen zpět do všech obslužné rutiny událostí k rozlišení volání metody. Také můžete k tomu jednoduše jako místo pro uložení stavu uživatele pro pozdější načtení.  
  
 Pro každou zvláštní *MethodName *** asynchronní** podpis metody:  
  
1.  Ve stejné třídě jako metodu definujte následující událost:  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  Definovat následující delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs>. Ty se být definovány pravděpodobně mimo vlastní třídy, ale o stejný obor názvů.  
  
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
  
    -   Ujistěte se, že *MethodName *** CompletedEventArgs** – třída zveřejňuje jeho členy jako vlastnosti jen pro čtení a nikoli pole jako pole datová vazba.  
  
    -   Nejsou definovány žádné <xref:System.ComponentModel.AsyncCompletedEventArgs>-odvozených tříd pro metody, které neposkytují výsledky. Jednoduše použijte instanci <xref:System.ComponentModel.AsyncCompletedEventArgs> sám sebe.  
  
        > [!NOTE]
        >  Je zcela přijatelné, pokud a proveditelné, znovu použít delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs> typy. V takovém případě pojmenování nebude jako konzistentní s názvem metody od daného delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs> nebude vázaný na jedné metody.  
  
## <a name="optionally-support-cancellation"></a>Volitelně podporovat zrušení  
 Pokud vaše třída bude podporovat zrušení asynchronních operací, by měly být vystaveny zrušení klientovi, jak je popsáno níže. Všimněte si, že existují dvě rozhodovací body, které je třeba dostupný před definováním zrušení podporu:  
  
-   Má vaše třídy, včetně budoucí předpokládaného dodatky, jenom jeden asynchronní operaci, která podporuje zrušení?  
  
-   Můžete asynchronní operace, které podporují více čekající operace zrušení podporu? To znamená, nemá *MethodName *** asynchronní** metoda proveďte `userState` parametr, a tomu více volání před čekání na všechny ukončíte?  
  
 Chcete-li zjistit, co by měl být podpis pro metodu zrušení pomocí odpovědi na tyto otázky dvě v následující tabulce.  
  
### <a name="visual-basic"></a>Visual Basic  
  
||Podporováno více souběžných operací.|Vždy pouze jednu operaci|  
|------|------------------------------------------------|----------------------------------|  
|Jeden asynchronní operace v celé – třída|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|Více asynchronních operací v – třída|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C#  
  
||Podporováno více souběžných operací.|Vždy pouze jednu operaci|  
|------|------------------------------------------------|----------------------------------|  
|Jeden asynchronní operace v celé – třída|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|Více asynchronních operací v – třída|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 Pokud definujete `CancelAsync(object userState)` metody, klienti musí být opatrní při volbě jejich stavu hodnoty tak, aby byly schopna rozlišovat mezi všechny asynchronní metody volá v objektu, ne jenom mezi všechny volání jedné asynchronní metody.  
  
 Rozhodnutí ohledně název verze jedním. asynchronní operace *MethodName *** AsyncCancel** je založena na schopnost snadněji zjistit metodu v prostředí návrhu jako Visual Studio IntelliSense. To související členy skupiny a je odlišuje od ostatních členů, které nemají co dělat s asynchronní funkce. Pokud očekáváte, že mohou být další asynchronních operací přibylo v dalších verzích, je lepší definovat `CancelAsync`.  
  
 Ve stejné třídě nedefinují několik metod z výše uvedené tabulce. Která nebude mít smysl, nebo ho bude zbytečných souborů třídy rozhraní s jak narůstá počet metody.  
  
 Tyto metody se obvykle vrátí okamžitě a tato operace může nebo nemusí ve skutečnosti zrušit. V obslužné rutiny události pro *MethodName *** dokončeno** událostí, *MethodName *** CompletedEventArgs** objekt obsahuje `Cancelled` pole, které můžou klienti použít k určení zda zrušení došlo k chybě.  
  
 Dodržováním sémantiku zrušení popsané v [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-support-the-isbusy-property"></a>Volitelně podporovat vlastnost IsBusy  
 Pokud vaše třída nepodporuje více souběžných volání, vezměte v úvahu vystavení `IsBusy` vlastnost. To umožňuje vývojářům určit, zda *MethodName *** asynchronní** metoda běží bez zachytávání výjimku z *MethodName *** asynchronní** metoda.  
  
 Dodržováním `IsBusy` sémantiku popsané v [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>Volitelně můžete poskytovat podporu pro vytváření sestav průběh  
 Je často žádoucí, aby asynchronní operaci sestava pokroku při své činnosti. Asynchronní vzor založený na událostech uvádí postup, jak to udělat.  
  
-   Volitelně můžete definujte události vyvolané asynchronní operaci a vyvolána na příslušné vlákno. <xref:System.ComponentModel.ProgressChangedEventArgs> Objekt představuje indikátor průběhu celočíselný, který musí být mezi 0 a 100.  
  
-   Tato událost název následujícím způsobem:  
  
    -   `ProgressChanged` Pokud třída má více asynchronních operací (nebo se očekává dosáhnout zahrnují více asynchronních operací v budoucích verzích);  
  
    -   *MethodName *** ProgressChanged** Pokud třída má jeden asynchronní operaci.  
  
     Tato volba pojmenování paralelní s výrobce pro metodu zrušení, jak je popsáno v části volitelně podporu zrušení.  
  
 Tato událost se má použít <xref:System.ComponentModel.ProgressChangedEventHandler> podpisu delegáta a <xref:System.ComponentModel.ProgressChangedEventArgs> třídy. Případně, pokud indikátor průběhu více specifické pro doménu lze zadat (pro instance, čtení bajtů a celkový počet bajtů pro operace nástroje download), pak byste měli definovat třídu odvozenou z <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
 Všimněte si, že pouze jeden `ProgressChanged` nebo *MethodName *** ProgressChanged** události pro třídu, bez ohledu na počet asynchronních metod podporuje. Klienti budou používat `userState` objekt, který je předán *MethodName *** asynchronní** metody k rozlišení mezi průběh aktualizací na více souběžných operací.  
  
 Mohou nastat situace, ve kterých průběh podporovat více operací a každé vrátí na jiný ukazatel průběh. V tomto případě jedné `ProgressChanged` událostí není vhodná, a můžete zvážit podpora více `ProgressChanged` události. V takovém případě pomocí vzoru pro pojmenovávání z *MethodName *** ProgressChanged** pro každou *MethodName *** asynchronní** metoda.  
  
 Dodržováním reporting průběh sémantiky popsané [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>Volitelně můžete poskytovat podporu pro vrácení přírůstkové výsledky  
 Asynchronní operace někdy může vrátit přírůstkové výsledky před dokončením. Existuje několik možností, které lze použít pro podporu tohoto scénáře. Níže jsou uvedeny příklady.  
  
### <a name="single-operation-class"></a>Operace jedním – třída  
 Pokud třídě podporuje pouze jeden asynchronní operaci, a že operace se bude moct vrátit přírůstkové výsledky, pak:  
  
-   Rozšíření <xref:System.ComponentModel.ProgressChangedEventArgs> typu k provedení přírůstkových výsledných dat a definujte *MethodName *** ProgressChanged** událost s tuto rozšířenou data.  
  
-   Vyvolat to *MethodName *** ProgressChanged** událost, pokud je výsledek přírůstkové do sestavy.  
  
 Toto řešení platí konkrétně pro třídu jedním. asynchronní operace, protože žádný problém s stejné událostí, ke kterým dochází k vrácení přírůstkové výsledky v "všechny operace", jako *MethodName *** ProgressChanged** událostí nemá.  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Třída více operaci s homogenní přírůstkové výsledky  
 V takovém případě třídě podporuje více asynchronní metody každý může vrácení přírůstkové výsledky, a tyto přírůstkové výsledky všechny mít stejný typ data.  
  
 Postupujte podle modelu popsané výše pro třídy jedné operace, jako stejné <xref:System.EventArgs> struktura bude fungovat pro všechny přírůstkové výsledky. Definování `ProgressChanged` událostí místo *MethodName *** ProgressChanged** událost, protože se vztahuje na více asynchronních metod.  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Třída více operaci s heterogenní přírůstkové výsledky  
 Pokud vaše třída podporuje více asynchronních metod, každý vrácení jiný typ dat, proveďte následující kroky:  
  
-   Samostatné sady přírůstkové výsledků sestavy průběhu sestav.  
  
-   Definování samostatné *MethodName *** ProgressChanged** událost s příslušnou <xref:System.EventArgs> pro každou asynchronní metodu pro zpracování dat přírůstkové výsledek této metody.  
  
 Vyvolání této obslužné rutiny události ve vlákně, v příslušné, jak je popsáno v [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>Zpracování Out a parametry Ref v metody  
 I když použití `out` a `ref` se nedoporučuje v rozhraní .NET Framework, tady jsou obecně pravidel tak, aby použijte, pokud jsou přítomna:  
  
 Synchronní metoda zadané *MethodName*:  
  
-   `out` parametry, které *MethodName* by neměl být součástí *MethodName ***asynchronní**. Místo toho by měla být součástí *MethodName *** CompletedEventArgs**  se stejným názvem jako jeho parametr ekvivalentní v *MethodName* (Pokud je vhodnější název).  
  
-   `ref` parametry, které *MethodName* mají zobrazit jako součást *MethodName ***asynchronní**a jako součást *MethodName *** CompletedEventArgs**  se stejným názvem jako jeho parametr ekvivalentní v *MethodName* (Pokud je vhodnější název).  
  
 Například uděleno:  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 Asynchronní metoda a jeho <xref:System.ComponentModel.AsyncCompletedEventArgs> třída bude vypadat takto:  
  
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
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Rozhodování, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [Vícevláknové programování s asynchronním vzorem založeným na událostech](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
