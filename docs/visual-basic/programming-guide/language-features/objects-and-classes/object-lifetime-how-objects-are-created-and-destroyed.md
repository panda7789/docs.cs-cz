---
title: 'Doba života objektu: Vytváření a zničení objektů'
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
ms.openlocfilehash: 8d9647fa490077f9f6ef82f30eccc4d5ee271985
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346110"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Doba života objektu: Vytváření a zničení objektů (Visual Basic)

Instance třídy, objektu, je vytvořena pomocí klíčového slova `New`. Inicializační úlohy je často nutné provést u nových objektů před jejich použitím. Mezi běžné inicializační úlohy patří otevírání souborů, připojování k databázím a čtení hodnot klíčů registru. Visual Basic řídí inicializaci nových objektů pomocí procedur nazývaných *konstruktory* (speciální metody, které umožňují kontrolu při inicializaci).

Poté, co objekt opustí rozsah, je vydaný modulem CLR (Common Language Runtime). Visual Basic řídí vydání systémových prostředků pomocí procedur nazývaných *destruktory*. Společně konstruktory a destruktory podporují vytváření robustních a předvídatelných knihoven tříd.

## <a name="using-constructors-and-destructors"></a>Použití konstruktorů a destruktorů

Konstruktory a destruktory řídí vytváření a zničení objektů. Postupy `Sub New` a `Sub Finalize` v Visual Basic inicializaci a zničení objektů; nahrazují `Class_Initialize` a `Class_Terminate` metody používané v Visual Basic 6,0 a starších verzích.

### <a name="sub-new"></a>Sub New

Konstruktor `Sub New` lze spustit pouze jednou při vytvoření třídy. Nemůže být volána explicitně jinde než v prvním řádku kódu jiného konstruktoru ze stejné třídy nebo z odvozené třídy. Kromě toho kód v metodě `Sub New` vždy běží před jakýmkoli jiným kódem ve třídě. Visual Basic implicitně vytvoří konstruktor `Sub New` v době běhu, pokud explicitně nedefinujete `Sub New` proceduru pro třídu.

Chcete-li vytvořit konstruktor pro třídu, vytvořte proceduru s názvem `Sub New` kdekoli v definici třídy. Chcete-li vytvořit parametrizovaný konstruktor, zadejte názvy a datové typy argumentů, které mají být `Sub New` stejně, jako byste zadali argumenty pro jakékoli jiné procedury, jako v následujícím kódu:

[!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]

Konstruktory jsou často přetíženy, jak je uvedeno v následujícím kódu:

[!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]

Při definování třídy odvozené z jiné třídy musí být prvním řádkem konstruktoru volání konstruktoru základní třídy, pokud základní třída nemá přístupný konstruktor, který nepřijímá žádné parametry. Volání základní třídy, která obsahuje výše konstruktor, by mohla být například `MyBase.New(s)`. V opačném případě je `MyBase.New` volitelné a modul runtime Visual Basic ho implicitně volá.

Po napsání kódu pro volání konstruktoru nadřazeného objektu můžete přidat libovolný další inicializační kód do `Sub New` procedury. `Sub New` může přijmout argumenty při volání jako parametrizovaný konstruktor. Tyto parametry jsou předány z procedury, která volá konstruktor, například `Dim AnObject As New ThisClass(X)`.

### <a name="sub-finalize"></a>Dílčí finalizace

Před uvolněním objektů modul CLR automaticky volá metodu `Finalize` pro objekty, které definují `Sub Finalize` postup. Metoda `Finalize` může obsahovat kód, který musí být proveden těsně před tím, než je objekt zničen, například kód pro zavírání souborů a ukládání informací o stavu. Při provádění `Sub Finalize`existuje mírné snížení výkonu, takže byste měli definovat `Sub Finalize` metodu pouze v případě, že potřebujete objekty vydávat explicitně.

> [!NOTE]
> Systém uvolňování paměti v modulu CLR (a nemůže) Dispose *nespravovaných objektů*, objektů, které operační systém provádí přímo, mimo prostředí CLR. Důvodem je, že různé nespravované objekty musí být vyřazeny různými způsoby. Tyto informace nejsou přímo přidruženy k nespravovanému objektu; musí být nalezen v dokumentaci pro daný objekt. Třída, která používá nespravované objekty, musí být ve své `Finalize` metodou odstraněna.

`Finalize` destruktor je chráněná metoda, kterou lze volat pouze z třídy, do které patří, nebo z odvozených tříd. Systém volá `Finalize` automaticky, když je objekt zničen, takže byste neměli explicitně volat `Finalize` z vnějšku `Finalize` implementace odvozené třídy.

Na rozdíl od `Class_Terminate`, která se spustí, jakmile je objekt nastaven na hodnotu Nothing, je obvykle zpoždění mezi objektem ztratí rozsah a při Visual Basic volání destruktoru `Finalize`. Visual Basic .NET umožňuje pro druhý druh destruktoru, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>, který se dá explicitně volat kdykoli, aby se ihned uvolnily prostředky.

> [!NOTE]
> Destruktor `Finalize` by neměl vyvolat výjimky, protože nemůže být zpracován aplikací a může způsobit ukončení aplikace.

### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Jak fungují nové a finalizační metody v hierarchii tříd

Pokaždé, když je vytvořena instance třídy, modul CLR (Common Language Runtime) se pokusí spustit proceduru s názvem `New`, pokud existuje v tomto objektu. `New` je typ procedury označované jako `constructor`, která se používá k inicializaci nových objektů před jakýmkoli jiným kódem v objektu. Konstruktor `New` lze použít k otevření souborů, připojení k databázím, inicializaci proměnných a provádění všech dalších úloh, které je třeba provést před použitím objektu.

Když je vytvořena instance odvozené třídy, nejprve se spustí konstruktor `Sub New` základní třídy následovaný konstruktory v odvozených třídách. K tomu dochází, protože první řádek kódu v konstruktoru `Sub New` používá syntaxi `MyBase.New()`k volání konstruktoru třídy přímo nad sebe v hierarchii tříd. Konstruktor `Sub New` je poté volán pro každou třídu v hierarchii třídy, dokud není dosaženo konstruktoru pro základní třídu. V tomto okamžiku se spustí kód v konstruktoru základní třídy následovaný kódem v každém konstruktoru ve všech odvozených třídách a kód v nejvíce odvozených třídách je proveden jako poslední.

![Snímek obrazovky znázorňující konstruktory a dědičnost hierarchií tříd](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)

Pokud objekt již není požadován, modul CLR před uvolněním paměti zavolá metodu <xref:System.Object.Finalize%2A> pro daný objekt. Metoda <xref:System.Object.Finalize%2A> se nazývá `destructor`, protože provádí úlohy čištění, jako je například ukládání informací o stavu, zavírání souborů a připojení k databázím a další úkoly, které je nutné provést před uvolněním objektu.

![Snímek obrazovky znázorňující destruktor metody Finalize](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)

## <a name="idisposable-interface"></a>Rozhraní IDisposable

Instance tříd často ovládají prostředky nespravované modulem CLR, jako jsou například popisovače systému Windows a databázová připojení. Tyto prostředky musí být vyřazeny z metody `Finalize` třídy, aby byly uvolněny, když je objekt zničen systémem uvolňování paměti. Systém uvolňování paměti však zničí objekty pouze v případě, že modul CLR vyžaduje více volné paměti. To znamená, že prostředky nemusejí být uvolněny až do doby, kdy se objekt dostane mimo rozsah.

Pro doplňování uvolňování paměti vaše třídy mohou poskytnout mechanismus pro aktivně spravovat systémové prostředky, pokud implementují rozhraní <xref:System.IDisposable>. <xref:System.IDisposable> má jednu metodu, <xref:System.IDisposable.Dispose%2A>, která by klienti měli zavolat při dokončení používání objektu. Metodu <xref:System.IDisposable.Dispose%2A> můžete použít k okamžitému vydání prostředků a provádění úloh, jako je například zavírání souborů a připojení k databázi. Na rozdíl od `Finalize` destruktoru není metoda <xref:System.IDisposable.Dispose%2A> volána automaticky. Klienti třídy musí explicitně volat <xref:System.IDisposable.Dispose%2A>, pokud chcete ihned uvolnit prostředky.

### <a name="implementing-idisposable"></a>Implementace rozhraní IDisposable

Třída, která implementuje rozhraní <xref:System.IDisposable> by měla obsahovat tyto části kódu:

- Pole pro udržení přehledu o tom, zda byl objekt vyřazen:

  ```vb
  Protected disposed As Boolean = False
  ```

- Přetížení <xref:System.IDisposable.Dispose%2A>, které uvolní prostředky třídy. Tato metoda by měla být volána metodami <xref:System.IDisposable.Dispose%2A> a `Finalize` základní třídy:

  ```vb
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

- Implementace <xref:System.IDisposable.Dispose%2A>, která obsahuje pouze následující kód:

  ```vb
  Public Sub Dispose() Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
  End Sub
  ```

- Přepsání metody `Finalize`, která obsahuje pouze následující kód:

  ```vb
  Protected Overrides Sub Finalize()
      Dispose(False)
      MyBase.Finalize()
  End Sub
  ```

### <a name="deriving-from-a-class-that-implements-idisposable"></a>Odvození od třídy, která implementuje rozhraní IDisposable

Třída, která je odvozena ze základní třídy, která implementuje rozhraní <xref:System.IDisposable>, nemusí potlačit žádnou základní metodu, pokud nepoužívá další prostředky, které je třeba uvolnit. V takovém případě by měla odvozená třída přepsat metodu `Dispose(disposing)` základní třídy k Dispose prostředků odvozené třídy. Toto přepsání musí volat metodu `Dispose(disposing)` základní třídy.

```vb
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

Odvozená třída nesmí přepisovat metody <xref:System.IDisposable.Dispose%2A> a `Finalize` základní třídy. Pokud jsou tyto metody volány z instance odvozené třídy, implementace těchto metod základní třídy volá přepsání metody `Dispose(disposing)` odvozené třídy.

## <a name="garbage-collection-and-the-finalize-destructor"></a>Uvolňování paměti a destruktor Finalize

.NET Framework používá systém *uvolňování paměti pro trasování odkazů* k pravidelnému uvolňování nepoužívaných prostředků. Visual Basic 6,0 a starší verze používaly pro správu prostředků jiný systém nazvaný *počítání odkazů* . I když oba systémy provádějí stejnou funkci automaticky, existuje několik důležitých rozdílů.

Modul CLR pravidelně zničí objekty, když systém zjistí, že tyto objekty již nejsou potřeba. Objekty jsou vydávány rychleji, když jsou systémové prostředky v krátkém zdroji a méně často, jinak. Zpoždění mezi tím, kdy objekt ztratí rozsah a při vydání CLR znamená, že na rozdíl od objektů v Visual Basic 6,0 a starších verzích, nelze přesně určit, kdy bude objekt zničen. V takové situaci jsou objekty označeny jako *nedeterministické*. Ve většině případů nedeterministické životnost nemění způsob psaní aplikací, pokud si pamatujete, že `Finalize` destruktor se nemusí okamžitě spustit, když objekt ztratí rozsah.

Další rozdíl mezi systémy uvolňování paměti zahrnuje použití `Nothing`. Chcete-li využít výhod počítání odkazů v Visual Basic 6,0 a starších verzích, někdy se programátoři přiřazují `Nothing` k proměnným objektu, aby uvolnili odkazy na tyto proměnné. Pokud proměnná drží poslední odkaz na objekt, prostředky objektu byly vydány okamžitě. V novějších verzích Visual Basic, i když existují případy, kdy je tato procedura stále cenná, nezpůsobí, že se v odkazovaném objektu okamžitě uvolní prostředky. K okamžitému vydání prostředků použijte metodu <xref:System.IDisposable.Dispose%2A> objektu, je-li k dispozici. Jedinou dobu, po kterou byste měli nastavit proměnnou na `Nothing`, je to, že její životnost je dlouhá vzhledem k době, kterou systém uvolňování paměti potřebuje k detekci osamocených objektů.

## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable.Dispose%2A>
- [Inicializace a ukončení komponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))
- [Operátor New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Vymazání nespravovaných prostředků](../../../../standard/garbage-collection/unmanaged.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
