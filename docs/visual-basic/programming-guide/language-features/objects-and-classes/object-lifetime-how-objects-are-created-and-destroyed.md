---
title: 'Doba života objektu: Jak objekty jsou vytvořeny a zničen (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Constructor
helpviewer_keywords:
- destructors, object lifetime
- Sub Finalize destructor
- objects [Visual Basic], destroying
- lifetime [Visual Basic], objects
- Sub New constructor, object lifetime
- Finalize method [Visual Basic], object lifetime
- objects [Visual Basic], creating
- Class_Terminate
- Dispose method [Visual Basic], object lifetime
- Class_Initialize
- object creation [Visual Basic], object lifetime
- parameterized constructors
- objects [Visual Basic], lifetime
- objects [Visual Basic], garbage collection
- constructors [Visual Basic], object lifetime
- Sub Dispose destructor
- garbage collection [Visual Basic], Visual Basic
ms.assetid: f1ee8458-b156-44e0-9a8a-5dd171648cd8
ms.openlocfilehash: 553868ae82501e479acadd04b3d5e4447bcea36e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839818"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Doba života objektu: Jak objekty jsou vytvořeny a zničen (Visual Basic)
Instance třídy objektu, je vytvořen pomocí `New` – klíčové slovo. Inicializace úlohy často je nutné provádět na nové objekty před jejich použití. Běžné úlohy inicializace zahrnují otevírání souborů, připojení k databázím a čtení hodnoty z klíče registru. Visual Basic řídí Inicializace nové objekty pomocí procedury volané *konstruktory* (speciální metody, které umožňují kontrolu nad inicializace).  
  
 Objekt odešel oboru, se uvolní modulem common language runtime (CLR). Visual Basic určuje verzi systémové prostředky pomocí procedury volané *destruktory*. Konstruktory a destruktory společně, podporu vytváření knihoven tříd robustní a předvídatelné.  
  
## <a name="using-constructors-and-destructors"></a>Použití konstruktorů a destruktorů  
 Konstruktory a destruktory řídí vytváření a ničení objektů. `Sub New` a `Sub Finalize` procedury v jazyce Visual Basic, inicializovat a zničit objekty; nahrazují `Class_Initialize` a `Class_Terminate` metod používaných v jazyce Visual Basic 6.0 a starší verze.  
  
### <a name="sub-new"></a>Nový Sub  
 `Sub New` Konstruktor lze spustit pouze jednou při vytvoření třídy. Nelze ji vyvolat explicitně kdekoli jinak než v prvním řádku kódu z jiného konstruktoru ze stejné třídy nebo z odvozené třídy. Kromě toho kód v `Sub New` metoda vždy spouští před ostatním kódem ve třídě. [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] a novějších verzích implicitně vytvářet `Sub New` konstruktor v době běhu, pokud nejsou explicitně definovány `Sub New` postup pro třídu.  
  
 Pokud chcete vytvořit konstruktor pro třídu, vytvořte proceduru s názvem `Sub New` kdekoli v definici třídy. Vytvoření konstruktoru s parametry, zadejte názvy a datové typy argumentů, které mají `Sub New` stejně jako byste měli zadat argumenty pro všechny procedury, stejně jako v následujícím kódu:  
  
 [!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]  
  
 Konstruktory jsou často přetížené, stejně jako v následujícím kódu:  
  
 [!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]  
  
 Při definování třídy odvozené z jiné třídy první řádek konstruktor musí být volání konstruktoru základní třídy, pokud má základní třída přístupný konstruktor, který nepřijímá žádné parametry. Volání na základní třídu, která obsahuje konstruktoru výše, například by `MyBase.New(s)`. V opačném případě `MyBase.New` je volitelný, a modul runtime jazyka Visual Basic volá implicitně.  
  
 Když napíšete kód volání konstruktoru nadřazeného objektu, můžete přidat žádný další inicializační kód `Sub New` postup. `Sub New` může přijímat argumenty při volání jako parametry konstruktoru. Tyto parametry jsou předány z procedury volání konstruktoru, například `Dim AnObject As New ThisClass(X)`.  
  
### <a name="sub-finalize"></a>Sub Finalize  
 Před uvolněním objekty, budou automaticky volá modul CLR `Finalize` metody pro objekty, které definují `Sub Finalize` postup. `Finalize` Metoda může obsahovat kód, který potřebuje provést, těsně před plánovaným začátkem objekt je zničen, jako je například kód pro zavření souborů a ukládání informací o stavu. Je mírné snížení výkonu pro provedení `Sub Finalize`, takže byste měli definovat `Sub Finalize` metodu pouze v případě, že je potřeba explicitně uvolnit objekty.  
  
> [!NOTE]
>  Uvolňování paměti v CLR nepodporuje (a nelze) vyřadit *nespravované objekty*, objekty, které operační systém spustí přímo, mimo prostředí modulu CLR. Je to proto, že různé nespravované objekty musí být odstraněny různými způsoby. Informace o nejsou přímo spojené s neřízeným objektem; je nutné ji najít v dokumentaci k objektu. Třída, která používá nespravované objekty musí uvolnit z nich v jeho `Finalize` metoda.  
  
 `Finalize` Destruktor je chráněná metoda, kterou lze volat pouze z třídy, které patří do nebo z odvozené třídy. Systémová volání `Finalize` automaticky při objekt je zničen, takže byste neměli volat explicitně `Finalize` z mimo odvozené třídy `Finalize` implementace.  
  
 Na rozdíl od `Class_Terminate`, která se spustí poté, co objekt je nastavena na hodnotu nothing, obvykle dochází ke zpoždění mezi když objekt Vyskočení a při volání jazyka Visual Basic `Finalize` destruktor. [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] a novějších verzích povolit pro druhý typ destruktor, <xref:System.IDisposable.Dispose%2A>, kterou můžete kdykoli a uvolnit tak prostředky explicitně volat.  
  
> [!NOTE]
>  A `Finalize` destruktoru by neměla vyvolávat výjimky, protože nemůže být zpracovány aplikací a může způsobit ukončení aplikace.  
  
### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Přiřazení nových a dokončení metody fungují v hierarchii tříd  
 Pokaždé, když je vytvořena instance třídy, se pokusí spustit proceduru s názvem common language runtime (CLR) `New`, pokud existuje v tomto objektu. `New` je typ procedura volána `constructor` , který slouží k inicializaci nové objekty před provedením jakýkoli jiný kód v objektu. A `New` konstruktor lze použít k otevírání souborů, připojit se k nim, inicializovat proměnné a postará o další úlohy, které je potřeba provést před použitím objektu.  
  
 Když je vytvořena instance odvozené třídy, `Sub New` konstruktor základní třídy, spustí nejprve, za nímž následuje konstruktory v odvozených třídách. Je to způsobeno první řádek kódu v `Sub New` konstruktor používá syntaxi `MyBase.New()`volat konstruktor třídy přímo nad sám v hierarchii tříd. `Sub New` Pak volání konstruktoru pro každou třídu v hierarchii tříd do konstruktoru pro dosažení základní třídy. V tu chvíli se kód v konstruktoru pro základní třídu spustí, za nímž následuje kód v jednotlivých konstruktor všechny odvozené třídy a poslední spuštění kódu v nejvíce odvozené třídy.  
  
 ![Snímek obrazovky s konstruktory hierarchie třídy a dědičnost.](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)  
  
 Pokud objekt je už nepotřebujete, kterou volá CLR <xref:System.Object.Finalize%2A> metodu pro tento objekt před uvolněním paměti. <xref:System.Object.Finalize%2A> Metoda je volána `destructor` protože provádí úlohy čištění, jako je například ukládání informací o stavu, zavírání souborů a připojení k databázím a dalších úlohách, které je třeba provést před uvolněním objektu.  
  
 ![Snímek obrazovky zobrazující destruktor metodu Finalize.](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)  
  
## <a name="idisposable-interface"></a>Rozhraní IDisposable  
 Instance třídy často řídit prostředky, které nejsou spravované přes modul CLR, jako jsou popisovače Windows a připojení k databázi. Tyto prostředky musí být odstraněny v `Finalize` metoda třídy, tak, aby se bude vydána při zničení objektu pomocí systému uvolňování paměti. Ale systému uvolňování paměti odstraní objekty pouze v případě, že modul CLR vyžaduje další volné paměti. To znamená, že prostředky nesmí uvolnit dokud dlouho po objekt dostane mimo rozsah.  
  
 K doplnění uvolňování paměti, můžete své třídy poskytují mechanismus pro aktivně spravovat systémové prostředky, pokud je implementovat <xref:System.IDisposable> rozhraní. <xref:System.IDisposable> má jednu metodu <xref:System.IDisposable.Dispose%2A>, kteří klienti by měly volat po dokončení používání objektu. Můžete použít <xref:System.IDisposable.Dispose%2A> metoda okamžitě uvolnění prostředků a provádět úlohy, jako je zavření souborů a připojení k databázi. Na rozdíl od `Finalize` destruktor, <xref:System.IDisposable.Dispose%2A> metoda není volána automaticky. Klienti třídy nutné explicitně volat <xref:System.IDisposable.Dispose%2A> Pokud chcete okamžitě uvolnit prostředky.  
  
### <a name="implementing-idisposable"></a>Implementace rozhraní IDisposable  
 Třídu, která implementuje <xref:System.IDisposable> rozhraní by měl obsahovat tyto části kódu:  
  
-   Pole pro udržování přehledu o, zda byl uvolněn objekt:  
  
    ```  
    Protected disposed As Boolean = False  
    ```  
  
-   Přetížení <xref:System.IDisposable.Dispose%2A> , který uvolní prostředky třídy. Tato metoda by měla být volány <xref:System.IDisposable.Dispose%2A> a `Finalize` metody základní třídy:  
  
    ```  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposed Then  
            If disposing Then  
                ' Insert code to free managed resources.  
            End If  
            ' Insert code to free unmanaged resources.  
        End If  
        Me.disposed = True  
    End Sub  
    ```  
  
-   Implementace <xref:System.IDisposable.Dispose%2A> , který obsahuje pouze následující kód:  
  
    ```  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
    ```  
  
-   Přepsání `Finalize` metodu, která obsahuje pouze následující kód:  
  
    ```  
    Protected Overrides Sub Finalize()  
        Dispose(False)  
        MyBase.Finalize()  
    End Sub  
    ```  
  
### <a name="deriving-from-a-class-that-implements-idisposable"></a>Odvozování z třídy, která implementuje rozhraní IDisposable  
 Třída, která je odvozena ze základní třídy, která implementuje <xref:System.IDisposable> rozhraní není nutné přepsat libovolnou metodu základní, pokud používá další prostředky, které je potřeba se dá uvolnit. V takovém případě by měly přepsat odvozené třídy základní třídy `Dispose(disposing)` metoda k uvolnění prostředků odvozené třídy. Toto přepsání musí volat základní třídy `Dispose(disposing)` metody.  
  
```  
Protected Overrides Sub Dispose(ByVal disposing As Boolean)  
    If Not Me.disposed Then  
        If disposing Then  
            ' Insert code to free managed resources.  
        End If  
        ' Insert code to free unmanaged resources.  
    End If  
    MyBase.Dispose(disposing)  
End Sub  
```  
  
 Odvozená třída nesmí přepsat základní třídy <xref:System.IDisposable.Dispose%2A> a `Finalize` metody. Pokud tyto metody jsou volány z instance odvozené třídy, implementaci základní třídy tyto metody volat přepsání odvozené třídě `Dispose(disposing)` metody.  
  
## <a name="garbage-collection-and-the-finalize-destructor"></a>Uvolňování paměti a Finalize – destruktor  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Používá *uvolňování paměti odkaz trasování* systému pravidelně uvolnit nevyužité prostředky. Visual Basic 6.0 a starší používala jiný systém volá *počítání odkazů* ke správě prostředků. I když oba systémy automaticky provádí stejnou funkci, existuje několik důležitých rozdílů.  
  
 Modul CLR pravidelně zničí objekty, když systém zjistí, že tyto objekty už nejsou potřeba. Objekty jsou uvolní rychleji, když jsou systémové prostředky v krátkých dodávek a méně často jinak. Zpoždění mezi když objekt Vyskočení a kdy ho CLR uvolní znamená, že na rozdíl od s objekty v jazyce Visual Basic verze 6.0 a starší, nelze určit přesně když bude objekt zničen. V takové situaci objekty mají často *Nedeterministický životnost*. Ve většině případů není deterministický životnost nezmění jak psát aplikace, za předpokladu, nezapomeňte, že `Finalize` – destruktor nemusí spustit okamžitě, pokud objekt ztratí oboru.  
  
 Další rozdíl mezi systémy uvolnění paměti zahrnuje použití `Nothing`. Výhod počítání referencí v jazyce Visual Basic verze 6.0 a starší, někdy programátoři přiřazené `Nothing` objektu proměnné k uvolnění odkazy na tyto proměnné uchovávat. Pokud je proměnná uložena poslední odkaz na objekt, objektu prostředky byly vydány okamžitě. V pozdějších verzích jazyka Visual Basic zatímco můžou nastat případy, ve kterých je tento postup hodnotný, provádění se nikdy způsobí, že odkazovaného objektu k uvolnění její prostředky okamžitě. K uvolnění prostředků okamžitě, použijte objektu <xref:System.IDisposable.Dispose%2A> metodu, pokud je k dispozici. Jenom byste měli nastavit proměnnou na `Nothing` je, když je jeho životnost dlouho relativní k době systému uvolňování paměti používá ke zjišťování osamocených objektů.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable.Dispose%2A>
- [Inicializace a ukončování komponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))
- [Operátor New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Vymazání nespravovaných prostředků](../../../../standard/garbage-collection/unmanaged.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
