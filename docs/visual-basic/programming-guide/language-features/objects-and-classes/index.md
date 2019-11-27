---
title: Objekty a třídy
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: d45aca8b137f56cf058b63b9286504259c0005eb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346702"
---
# <a name="objects-and-classes-in-visual-basic"></a>Objekty a třídy v Visual Basic

*Objekt* je kombinací kódu a dat, která lze považovat za jednotku. Objekt může být částí aplikace, například ovládacím prvkem nebo formulářem. Celá aplikace může být také objekt.

Při vytváření aplikace v Visual Basic stále pracujete s objekty. Můžete použít objekty poskytované Visual Basic, jako jsou ovládací prvky, formuláře a objekty pro přístup k datům. Můžete také použít objekty z jiných aplikací v rámci aplikace Visual Basic. Můžete dokonce vytvořit vlastní objekty a definovat další vlastnosti a metody pro ně. Objekty fungují jako Prefabrikované stavební bloky pro programy – umožňují napsat kód jen jednou a opakovaně ho používat.

V tomto tématu jsou podrobněji popsány objekty.

## <a name="objects-and-classes"></a>Objekty a třídy

Každý objekt v Visual Basic je definován *třídou*. Třída popisuje proměnné, vlastnosti, procedury a události objektu. Objekty jsou instance třídy; Po definování třídy můžete vytvořit tolik objektů, kolik potřebujete.

Pro pochopení vztahu mezi objektem a jeho třídou si můžete představit ořezávání souborů cookie a soubory cookie. Ořezávání souborů cookie je třída. Definuje charakteristiky jednotlivých souborů cookie, například velikost a tvar. Třída se používá k vytvoření objektů. Objekty jsou soubory cookie.

Objekt je nutné vytvořit před tím, než budete moci získat přístup k jeho členům.

### <a name="to-create-an-object-from-a-class"></a>Vytvoření objektu z třídy

1. Určete, ze které třídy chcete vytvořit objekt.

2. Zápis [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pro vytvoření proměnné, ke které můžete přiřadit instanci třídy. Proměnná by měla být typu požadované třídy.

   ```vb
   Dim nextCustomer As customer
   ```

3. Přidejte klíčové slovo [New operator](../../../../visual-basic/language-reference/operators/new-operator.md) pro inicializaci proměnné na novou instanci třídy.

   ```vb
   Dim nextCustomer As New customer
   ```

4. Nyní můžete přistupovat ke členům třídy přes proměnnou objektu.

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> Kdykoli je to možné, měli byste deklarovat proměnnou, která má být typu třídy, který chcete přiřadit. Tato metoda se nazývá *časná vazba*. Pokud neznáte typ třídy v době kompilace, můžete vyvolat *pozdní vazbu* tím, že deklarujete proměnnou, která má být [datového typu objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md). Pozdní vazba ale může snížit výkon a omezit přístup k členům objektu run-time. Další informace naleznete v tématu [deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).

### <a name="multiple-instances"></a>Více instancí

Objekty nově vytvořené z třídy jsou často identické. Jakmile však existují jako jednotlivé objekty, jejich proměnné a vlastnosti lze změnit nezávisle na ostatních instancích. Například pokud přidáte tři zaškrtávací políčka do formuláře, každé zaškrtávací políčko objekt je instancí třídy <xref:System.Windows.Forms.CheckBox>. Jednotlivé <xref:System.Windows.Forms.CheckBox> objekty sdílejí společnou sadu vlastností a schopností (vlastnosti, proměnné, procedury a události) definované třídou. Každý má však vlastní název, může být samostatně povolen a zakázán a může být umístěn v jiném umístění ve formuláři.

## <a name="object-members"></a>Členy objektu

Objekt je prvek aplikace, který představuje *instanci* třídy. Pole, vlastnosti, metody a události jsou stavebními bloky objektů a tvoří jejich *členy*.

### <a name="member-access"></a>Přístup ke členu

Ke členu objektu přistupujete zadáním, v pořadí, názvu proměnné objektu, tečkou (`.`) a názvem člena. Následující příklad nastaví vlastnost <xref:System.Windows.Forms.Control.Text%2A> objektu <xref:System.Windows.Forms.Label>.

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>Seznam členů IntelliSense

IntelliSense Vypíše členy třídy při vyvolání možnosti seznamu členů, například při zadání tečky (`.`) jako operátoru přístupu členů. Zadáte-li období za názvem proměnné deklarované jako instance této třídy, technologie IntelliSense Vypíše všechny členy instance a žádné sdílené členy. Zadáte-li období za samotný název třídy, IntelliSense zobrazí seznam všech sdílených členů a žádné členy instance. Další informace najdete v tématu [použití technologie IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="fields-and-properties"></a>Pole a vlastnosti

*Pole* a *vlastnosti* reprezentují informace uložené v objektu. Hodnoty s příkazy přiřazení se načítají a nastavují stejným způsobem jako při načítání a nastavení místních proměnných v proceduře. Následující příklad načte vlastnost <xref:System.Windows.Forms.Control.Width%2A> a nastaví vlastnost <xref:System.Windows.Forms.Control.ForeColor%2A> objektu <xref:System.Windows.Forms.Label>.

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

Všimněte si, že pole se také nazývá *členská proměnná*.

Procedury vlastností použijte v těchto případech:

- Musíte určit, kdy a jak má být hodnota nastavena nebo načtena.

- Vlastnost má dobře definovanou sadu hodnot, které je třeba ověřit.

- Nastavením hodnoty dojde k některému znatelnému změně stavu objektu, jako je například vlastnost `IsVisible`.

- Nastavení vlastnosti způsobí změny jiných interních proměnných nebo hodnot jiných vlastností.

- Aby bylo možné nastavit nebo načíst vlastnost, je nutné provést sadu kroků.

Pole použijte, když:

- Hodnota je typu ověřování při samostatném ověřování. Například chyba nebo automatický převod dat nastane, pokud je jiná hodnota než `True` nebo `False` přiřazena k proměnné `Boolean`.

- Platná je libovolná hodnota rozsahu podporovaná datovým typem. To platí pro mnoho vlastností typu `Single` nebo `Double`.

- Vlastnost je `String` datový typ a neexistuje žádné omezení velikosti nebo hodnoty řetězce.

- Další informace naleznete v tématu [procedury vlastností](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).

### <a name="methods"></a>Metody

*Metoda* je akce, kterou může objekt provádět. <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> je například metoda objektu <xref:System.Windows.Forms.ComboBox>, která přidá novou položku do pole se seznamem.

Následující příklad ukazuje metodu <xref:System.Windows.Forms.Timer.Start%2A> objektu <xref:System.Windows.Forms.Timer>.

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

Všimněte si, že metoda je jednoduše *procedurou* , která je vystavena objektem.

Další informace najdete v tématu [postupy](../../../../visual-basic/programming-guide/language-features/procedures/index.md).

### <a name="events"></a>Události

Událost je akce rozpoznaná objektem, jako je kliknutí myší nebo stisknutí klávesy, a pro kterou můžete napsat kód, který bude reagovat. Události mohou vzniknout v důsledku akce uživatele nebo kódu programu nebo mohou být způsobeny systémem. Kód, který signalizuje událost, se říká k *vyvolání* události a kód, který na něj reaguje, je označován za účelem jeho *zpracování* .

Můžete také vyvíjet vlastní události, které mají být vyvolány objekty a zpracovávány jinými objekty. Další informace najdete v tématu [události](../../../../visual-basic/programming-guide/language-features/events/index.md).

### <a name="instance-members-and-shared-members"></a>Členové instance a sdílené členy

Při vytváření objektu z třídy je výsledkem instance této třídy. Členy, které nejsou deklarovány se [sdíleným](../../../../visual-basic/language-reference/modifiers/shared.md) klíčovým slovem, jsou *členy instance*, které patří výhradně do této konkrétní instance. Člen instance v jedné instanci je nezávislý na stejném členu v jiné instanci stejné třídy. Členská proměnná instance může mít například různé hodnoty v různých instancích.

Členy deklarované s klíčovým slovem `Shared` jsou *sdílené členy*, které patří do třídy jako celek a nikoli do žádné konkrétní instance. Sdílený člen existuje pouze jednou, bez ohledu na to, kolik instancí své třídy vytvoříte, nebo dokonce i v případě, že nevytvoříte žádné instance. Sdílená členská proměnná, například má pouze jednu hodnotu, která je k dispozici pro veškerý kód, který má přístup ke třídě.

#### <a name="accessing-nonshared-members"></a>Přístup k nesdíleným členům

##### <a name="to-access-a-nonshared-member-of-an-object"></a>Přístup k nesdílenému členu objektu

1. Ujistěte se, že objekt byl vytvořen z jeho třídy a přiřazený k proměnné objektu.

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. V příkazu, který přistupuje ke členu, postupujte podle názvu proměnné objektu s *operátorem přístupu členů* (`.`) a potom názvem člena.

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>Přístup ke sdíleným členům

##### <a name="to-access-a-shared-member-of-an-object"></a>Přístup ke sdílenému členu objektu

- Dodržujte název třídy s *operátorem přístupu členů* (`.`) a potom názvem člena. Vždy byste měli přistupovat k `Shared`mu členu objektu přímo prostřednictvím názvu třídy.

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)
   ```

- Pokud jste již vytvořili objekt ze třídy, můžete alternativně přistupovat k `Shared`mu členu prostřednictvím proměnné objektu.

### <a name="differences-between-classes-and-modules"></a>Rozdíly mezi třídami a moduly

Hlavním rozdílem mezi třídami a moduly je, že třídy mohou být vytvořeny jako objekty, zatímco standardní moduly nemůžou. Vzhledem k tomu, že existuje pouze jedna kopie dat standardního modulu, když jedna část programu změní veřejnou proměnnou ve standardním modulu, jakákoli jiná část programu získá stejnou hodnotu, pokud následně přečte tuto proměnnou. Naproti tomu data objektu existují samostatně pro každý objekt s vytvořenou instancí. Dalším rozdílem je, že na rozdíl od standardních modulů můžou třídy implementovat rozhraní.

> [!NOTE]
> Pokud je modifikátor `Shared` použit pro člena třídy, je přidružen k samotné třídě namísto konkrétní instance třídy. Ke členu se má získat přímý odkaz pomocí názvu třídy, stejně jako k nim přistupovali členové modulu.

Třídy a moduly používají pro své členy také různé obory. Členy definované v rámci třídy jsou vymezeny v rámci konkrétní instance třídy a existují pouze za dobu života objektu. Chcete-li získat přístup ke členům třídy z vnějšku třídy, je nutné použít plně kvalifikované názvy ve formátu *objektu*. *Člen*.

Na druhé straně členové deklarované v rámci modulu jsou ve výchozím nastavení veřejně přístupné a lze k němu přistupovat jakýmkoli kódem, který má přístup k modulu. To znamená, že proměnné ve standardním modulu jsou efektivní globální proměnné, protože jsou viditelné z libovolného místa v projektu a existují po dobu života programu.

## <a name="reusing-classes-and-objects"></a>Znovu použití tříd a objektů

Objekty umožňují deklarovat proměnné a procedury jednou a pak je znovu použít, kdykoli je to potřeba. Například pokud chcete přidat kontrolu pravopisu do aplikace, můžete definovat všechny proměnné a funkce podpory, které poskytují funkce kontroly pravopisu. Pokud vytvoříte kontrolu pravopisu jako třídu, můžete ji následně znovu použít v jiných aplikacích přidáním odkazu na zkompilované sestavení. Ještě lepší je, že budete moct Uložit nějakou práci pomocí třídy pro kontrolu pravopisu, kterou už vyvinul někdo jiný.

.NET Framework poskytuje mnoho příkladů součástí, které jsou k dispozici pro použití. Následující příklad používá třídu <xref:System.TimeZone> v oboru názvů <xref:System>. <xref:System.TimeZone> poskytuje členy, které umožňují načíst informace o časovém pásmu aktuálního počítačového systému.

```vb
Public Sub examineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    MsgBox(s)
End Sub
```

V předchozím příkladu příkaz v prvním [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklaruje proměnnou objektu typu <xref:System.TimeZone> a přiřadí jí objekt <xref:System.TimeZone> vrácený vlastností <xref:System.TimeZone.CurrentTimeZone%2A>.

## <a name="relationships-among-objects"></a>Vztahy mezi objekty

Objekty mohou být vzájemně propojené několika způsoby. Hlavní typy vztahů jsou *hierarchické* a *omezení*.

### <a name="hierarchical-relationship"></a>Hierarchický vztah

Pokud třídy jsou odvozeny z více základních tříd, říká se, že mají *hierarchický vztah*. Hierarchie tříd jsou užitečné, pokud popisují položky, které jsou podtypu obecnější třídy.

V následujícím příkladu Předpokládejme, že chcete definovat zvláštní druh <xref:System.Windows.Forms.Button>, který funguje jako normální <xref:System.Windows.Forms.Button>, ale také zpřístupňuje metodu, která vrátí barvy popředí a pozadí.

#### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a>Definování třídy je odvozeno z již existující třídy

1. Použijte [příkaz třídy](../../../../visual-basic/language-reference/statements/class-statement.md) k definování třídy, ze které chcete vytvořit objekt, který potřebujete.

   ```vb
   Public Class reversibleButton
   ```

   Ujistěte se, že příkaz `End Class` dodržuje poslední řádek kódu ve vaší třídě. Ve výchozím nastavení integrované vývojové prostředí (IDE) automaticky vygeneruje `End Class` při zadání příkazu `Class`.

2. Použijte příkaz `Class` okamžitě s [příkazem Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md). Zadejte třídu, ze které je odvozena nová třída.

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   Vaše nová třída zdědí všechny členy definované základní třídou.

3. Přidejte kód pro další členy, které vaše odvozená třída zveřejňuje. Například můžete přidat metodu `reverseColors` a vaše odvozená třída může vypadat takto:

   ```vb
   Public Class reversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub reverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   Vytvoříte-li objekt z třídy `reversibleButton`, může přistupovat ke všem členům třídy <xref:System.Windows.Forms.Button> a také k metodě `reverseColors` a dalším novým členům, které definujete v `reversibleButton`.

Odvozené třídy dědí členy ze třídy, na které jsou založeny, což umožňuje v hierarchii tříd přidat složitost během průběhu. Další informace najdete v tématu [základy dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

### <a name="compiling-the-code"></a>Kompilování kódu

Ujistěte se, že kompilátor má přístup ke třídě, ze které hodláte odvodit novou třídu. To může znamenat, že plně kvalifikované jeho jméno, jako v předchozím příkladu, nebo určení jeho oboru názvů v [příkazu Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Pokud je třída v jiném projektu, může být nutné přidat odkaz na tento projekt. Další informace naleznete v tématu [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).

### <a name="containment-relationship"></a>Vztah členství ve skupině

Jiný způsob, jakým mohou být objekty v relaci, je *vztah zahrnutí*. Objekty kontejneru logicky zapouzdřují jiné objekty. Například objekt <xref:System.OperatingSystem> logicky obsahuje objekt <xref:System.Version>, který se vrátí prostřednictvím jeho vlastnosti <xref:System.OperatingSystem.Version%2A>. Všimněte si, že objekt kontejneru fyzicky neobsahuje žádný jiný objekt.

#### <a name="collections"></a>Kolekce

Jeden konkrétní typ zahrnutí objektu je reprezentován *kolekcemi*. Kolekce jsou skupiny podobných objektů, které lze vyčíslit. Visual Basic podporuje specifickou syntaxi [pro každý... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) , který umožňuje iterovat položky kolekce. Kromě toho kolekce často umožňují použít <xref:Microsoft.VisualBasic.Collection.Item%2A> k načtení prvků podle jejich indexu nebo jejich přidružení k jedinečnému řetězci. Kolekce lze snadněji používat než pole, protože umožňují přidávat nebo odebírat položky bez použití indexů. Z důvodu jejich snadného použití se kolekce často používají k ukládání formulářů a ovládacích prvků.

## <a name="related-topics"></a>Příbuzná témata

[Návod: definování tříd](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)\
Poskytuje podrobný popis postupu vytvoření třídy.

[Přetížené vlastnosti a metody](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)\
Vlastnosti a metody přetečení

[Základy dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)\
Pokrývá modifikátory dědičnosti, přepsání metod a vlastností, MyClass a MyBase.

[Doba života objektu: vytváření a zničení objektů](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)\
Popisuje vytváření a odstraňování instancí třídy.

[Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)\
V této části najdete popis postupu vytvoření a použití anonymních typů, které umožňují vytvářet objekty bez psaní definice třídy pro datový typ.

[Inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)\
Popisuje Inicializátory objektů, které se používají k vytváření instancí pojmenovaných a anonymních typů pomocí jednoho výrazu.

[Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)\
Vysvětluje, jak odvodit názvy vlastností a typy v deklaracích anonymního typu. Poskytuje příklady úspěšného a neúspěšného odvození.
