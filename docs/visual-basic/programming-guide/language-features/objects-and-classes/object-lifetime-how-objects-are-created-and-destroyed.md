---
title: 'Doba života objektu: Vytváření a zničení objektů (Visual Basic)'
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
ms.openlocfilehash: 441fe91c8c884e59c6399d57e7e55bf6591cb1bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Doba života objektu: Vytváření a zničení objektů (Visual Basic)
Instance třídy objekt, je vytvořená pomocí `New` – klíčové slovo. Úlohy inicializace často musí být provedeny na nové objekty před jejich použití. Běžné úlohy inicializace zahrnují otevírání souborů, připojení k databázím a čtení hodnoty klíčů registru. Inicializace nových objektů pomocí procedury volané ovládací prvky jazyka Visual Basic *konstruktory* (speciální metody, které umožňují řídit inicializace).  
  
 Objekt odešel oboru, vydal common language runtime (CLR). Ovládací prvky jazyka Visual Basic verzi systémové prostředky pomocí procedury volané *destruktory*. Konstruktory a destruktory společně podporují vytvoření knihovny tříd robustní a předvídatelné.  
  
## <a name="using-constructors-and-destructors"></a>Použití konstruktorů a destruktorů  
 Konstruktory a destruktory řídí vytváření a odstraňování objektů. `Sub New` a `Sub Finalize` procedury v jazyce Visual Basic inicializace a zrušení objekty; nahrazují `Class_Initialize` a `Class_Terminate` metody používané v jazyce Visual Basic 6.0 a starší verze.  
  
### <a name="sub-new"></a>Sub – nový  
 `Sub New` Konstruktor může spustit pouze po vytvoření třídy. Ji nelze volat explicitně kdekoli jinak než v prvním řádku kódu jiný konstruktor ze stejné třídy nebo z odvozené třídy. Kromě toho kód `Sub New` metoda vždy spuštěna před jakýkoli jiný kód v třídě. [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] a novějších verzích implicitně vytvořit `Sub New` konstruktor za běhu, pokud nejsou explicitně definovány `Sub New` postup pro třídu.  
  
 Pokud chcete vytvořit konstruktor pro třídu, vytvoření procedury s názvem `Sub New` kdekoli v definici třídy. Pokud chcete vytvořit parametrizované konstruktor, zadejte názvy a datové typy argumentů `Sub New` stejně, jako by zadejte argumenty pro další postup, jako v následujícím kódu:  
  
 [!code-vb[VbVbalrOOP#42](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_1.vb)]  
  
 Konstruktory jsou často přetížené, jako v následujícím kódu:  
  
 [!code-vb[VbVbalrOOP#116](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_2.vb)]  
  
 Když definujete třídy odvozené z jiné třídy, první řádek konstruktor musí být volání konstruktoru základní třídy, pokud základní třída má dostupný konstruktor, které nepřijímá žádné parametry. Volání základní třídy, která obsahuje výše konstruktoru, například by `MyBase.New(s)`. V opačném `MyBase.New` je volitelná, a Visual Basic runtime nazve je implicitně.  
  
 Když napíšete kód volat konstruktor nadřazený objekt, můžete přidat žádné další inicializace kód pro `Sub New` postupu. `Sub New` Můžete přijmout argumenty při volání jako parametrizované konstruktor. Tyto parametry se předávají v postupu volání konstruktoru, například `Dim AnObject As New ThisClass(X)`.  
  
### <a name="sub-finalize"></a>Sub Finalize  
 Před uvolněním objekty, budou automaticky volání modulu CLR `Finalize` metodu pro objekty, které definují `Sub Finalize` postupu. `Finalize` Metoda může obsahovat kód, který je potřeba provést těsně před zničení objektu, například kód pro zavírání souborů a ukládání informací o stavu. Je snížení výkonu mírné pro provádění `Sub Finalize`, takže byste měli definovat `Sub Finalize` metoda jenom v případě, že je potřeba explicitně uvolnění objektů.  
  
> [!NOTE]
>  Uvolňování paměti v modulu CLR není (a nemůže) odstranění *nespravované objekty*, objekty, které operační systém provede přímo, mimo prostředí CLR. Je to proto, že různé nespravované objekty je nutné odstranit z různými způsoby. Tyto informace není přímo spojeny s nespravované objektem; je nutné nalézt v dokumentaci pro objekt. Třídu, která využívá nespravované objekty musí dispose z nich v jeho `Finalize` metoda.  
  
 `Finalize` Destruktor je chráněná metoda, kterou lze volat pouze z třídy patří do nebo z odvozené třídy. Systémová volání `Finalize` automaticky při objekt zničení, takže by neměla explicitně volání `Finalize` z mimo odvozené třídy `Finalize` implementace.  
  
 Na rozdíl od `Class_Terminate`, který provede co nejrychleji objekt je nastaven na hodnotu nothing, obvykle dochází ke zpoždění mezi při objekt ztratí oboru a při volání jazyka Visual Basic `Finalize` destruktor. [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] a novějších verzích povolit pro druhý druh destruktor, <xref:System.IDisposable.Dispose%2A>, což může být explicitně volána kdykoli a uvolnit prostředky.  
  
> [!NOTE]
>  A `Finalize` – destruktor nesmí vyvolat výjimky, protože nelze zpracovat, aplikací a může způsobit, že je aplikace ukončena.  
  
### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Jak nové a dokončit pracovní metody v hierarchii – třída  
 Vždy, když je vytvořena instance třídy, modul CLR (CLR) pokusí spustit proceduru s názvem `New`, pokud existuje v tomto objektu. `New` je typ postupu názvem `constructor` sloužící k inicializaci nové objekty, před provedením dalších kódu v objektu. A `New` konstruktor lze použít k otevření souborů, připojení k databázím, inicializace proměnné a postará o další úlohy, které je třeba provést před použitím objektu.  
  
 Při vytváření instance odvozené třídy `Sub New` konstruktor základní třídy provede první, za nímž následuje konstruktorů v odvozených třídách. K tomu dojde, protože první řádek kódu `Sub New` konstruktor se používá syntaxe `MyBase.New()`volání konstruktoru třídy okamžitě výše sám v hierarchii tříd. `Sub New` Pak volání konstruktoru pro každou třídu v hierarchii tříd do konstruktoru pro dosažení základní třídy. V tomto okamžiku kód v konstruktoru pro základní třídu provede, za nímž následuje kód v jednotlivých konstruktor pro všechny odvozené třídy a poslední spuštění kódu v maximální odvozené funkcí.  
  
 ![Konstruktory a dědičnost](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance.gif "vaConstructorsInheritance")  
  
 Pokud objekt je již nepotřebujete, volání modulu CLR <xref:System.Object.Finalize%2A> metodu pro tento objekt před uvolnění paměti. <xref:System.Object.Finalize%2A> Metoda je volána `destructor` protože provádí úlohy čištění, jako je například ukládá informace o stavu, zavírání souborů a připojení k databázím a dalších úlohách, které je třeba provést před uvolněním objektu.  
  
 ![Konstruktory Inheritance2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance_2.gif "vaConstructorsInheritance_2")  
  
## <a name="idisposable-interface"></a>Rozhraní IDisposable  
 Instance třídy často řídit prostředky, které nejsou spravované přes modul CLR, jako je například obslužné rutiny Windows a připojení k databázi. Tyto prostředky je nutné odstranit z v `Finalize` metoda třídy, tak, aby se budou vydané při objekt zničen modulem garbage collector. Uvolňování paměti však odstraní objekty pouze v případě modulu CLR vyžaduje další volné paměti. To znamená, že prostředky nemusí být vydán dokud dlouho po opuštění oboru.  
  
 Doplníte uvolňování paměti, může vaše třídy poskytují mechanismus aktivně Správa systémových prostředků, pokud se implementovat <xref:System.IDisposable> rozhraní. <xref:System.IDisposable> má jednu metodu <xref:System.IDisposable.Dispose%2A>, klienty, kteří by měly volat po ukončení používání objektu. Můžete použít <xref:System.IDisposable.Dispose%2A> metoda okamžitě uvolnění prostředků a provádět úlohy, jako je zavírání souborů a připojení databáze. Na rozdíl od `Finalize` destruktor, <xref:System.IDisposable.Dispose%2A> metoda není volána automaticky. Klienti třídy musí explicitně volat <xref:System.IDisposable.Dispose%2A> když chcete okamžitě uvolnění prostředků.  
  
### <a name="implementing-idisposable"></a>Implementace rozhraní IDisposable  
 Třídu, která implementuje <xref:System.IDisposable> rozhraní by měla obsahovat tyto části kódu:  
  
-   Pole pro udržování přehledu o, zda objekt byl zlikvidován:  
  
    ```  
    Protected disposed As Boolean = False  
    ```  
  
-   Přetížení <xref:System.IDisposable.Dispose%2A> který uvolní prostředky třídy. Tato metoda by měla být volána <xref:System.IDisposable.Dispose%2A> a `Finalize` metody třídy base:  
  
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
  
-   Implementace <xref:System.IDisposable.Dispose%2A> obsahující pouze následující kód:  
  
    ```  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
    ```  
  
-   Přepsání `Finalize` metoda, která obsahuje jenom následující kód:  
  
    ```  
    Protected Overrides Sub Finalize()  
        Dispose(False)  
        MyBase.Finalize()  
    End Sub  
    ```  
  
### <a name="deriving-from-a-class-that-implements-idisposable"></a>Odvozování od třídy, který implementuje rozhraní IDisposable  
 Třída odvozená z databáze třídu, která implementuje <xref:System.IDisposable> rozhraní není potřeba základní metod přepsat, pokud používá další prostředky, které musí být zrušen. V takovém případě by měly přepsat odvozené třídy základní třídy `Dispose(disposing)` metoda k uvolnění prostředků odvozené třídy. Toto přepsání musí volat základní třídy `Dispose(disposing)` metoda.  
  
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
  
 Odvozené třídě by neměl přepsat základní třídy <xref:System.IDisposable.Dispose%2A> a `Finalize` metody. Pokud tyto metody jsou volány z instance odvozené třídy, základní třída implementace těchto metod volání přepsání odvozené třídě `Dispose(disposing)` metoda.  
  
## <a name="garbage-collection-and-the-finalize-destructor"></a>Uvolňování paměti a Finalize – destruktor  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Používá *uvolňování paměti odkaz trasování* systému, aby pravidelně uvolnění prostředků nepoužívá. Visual Basic 6.0 a starší verze použít jiný systém názvem *počítání odkazů* ke správě prostředků. Přestože oba systémy provádí stejnou funkci automaticky, existuje několik důležitých rozdílů.  
  
 Modul CLR pravidelně odstraní objekty, pokud systém zjistí, že tyto objekty už nejsou potřeba. Objekty jsou vydávány rychleji, když jsou systémové prostředky v krátké napájení a méně často jinak. Zpoždění mezi při objekt ztratí oboru a když modulu CLR uvolněním znamená, že na rozdíl od s objekty v jazyce Visual Basic 6.0 a starší verze, nelze určit přesně při objekt budou zničena. V takovém případě jsou uvedená objekty tak, aby měl *Nedeterministický životnost*. Ve většině případů není deterministický životnost nezmění jak psát aplikace, tak dlouho, dokud nezapomeňte, že `Finalize` destruktor nemusí spustit okamžitě, když objekt ztratí oboru.  
  
 Další rozdíl mezi systémy kolekce paměti zahrnuje použití `Nothing`. Umožní využít v jazyce Visual Basic 6.0 a starší verze při počítání referencí programátory někdy přiřazené `Nothing` k objektu proměnné k uvolnění odkazy na tyto proměnné uchovávat. Pokud proměnná uchovávat poslední odkaz na objekt, byly vydané okamžitě objektu prostředky. V novějších verzích jazyka Visual Basic při můžou nastat případy, ve kterých je stále cenné, tento postup provádění ho nikdy způsobí, že odkazovaného objektu k uvolnění jeho prostředků okamžitě. K uvolnění prostředků okamžitě, použijte objektu <xref:System.IDisposable.Dispose%2A> metodu, pokud je k dispozici. Pouze nastavte proměnnou na `Nothing` je po dlouho relativní na dobu, bude systém uvolňování trvá ke zjištění osamocených objektů celé jeho životnosti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IDisposable.Dispose%2A>  
 [Inicializace a ukončování součástí](http://msdn.microsoft.com/library/58444076-a9d2-4c91-b3f6-0e180dc0695d)  
 [Operátor New](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Vymazání nespravovaných prostředků](../../../../standard/garbage-collection/unmanaged.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)
