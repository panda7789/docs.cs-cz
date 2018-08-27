---
title: Objekty a třídy v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 2917a698f9aa7828c201a048f443f5941797c704
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934287"
---
# <a name="objects-and-classes-in-visual-basic"></a>Objekty a třídy v jazyce Visual Basic
*Objekt* je kombinací kód a data, která lze považovat za jednotku. Objekt může být část aplikace, jako je ovládací prvek nebo formuláře. Objekt může být také celé aplikace.

Když vytvoříte aplikaci v jazyce Visual Basic, neustále práci s objekty. Objekty poskytnuté jazyka Visual Basic, jako je například přístup k objektům ovládacích prvků formulářů a data se dají použít. Objekty z jiných aplikací můžete použít taky v rámci vaší aplikace v jazyce Visual Basic. Dokonce je možné vytvářet vlastní objekty a definovat další vlastnosti a metody pro ně. Objekty fungují jako stavební bloky pro programy prefabrikované – umožňují napsat kód jednou a opakovaně používat pořád dokola.  
  
Toto téma popisuje objekty podrobně.  

## <a name="objects-and-classes"></a>Objekty a třídy
Každý objekt v jazyce Visual Basic je definován *třídy*. Třída popisuje proměnné, vlastnosti, procedury a události objektu. Objekty jsou instancemi třídy; můžete vytvořit libovolný počet objektů, které je nutné po definování třídy.

Informace o tom vztah mezi objektem a své třídy, si můžete Představte řezačky souboru cookie a soubory cookie. Ořezávání soubor cookie je třída. Definuje vlastnosti každého souboru cookie, třeba velikost a tvar. Třída se používá k vytváření objektů. Objekty jsou soubory cookie.

Objekt musíte vytvořit předtím, než může přistupovat k jejím členům.  

#### <a name="to-create-an-object-from-a-class"></a>Chcete-li vytvořit objekt ze třídy

1. Určení, z které třídy, kterou chcete vytvořit objekt.  

2. Zápis [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) vytvoření proměnné, ke kterému lze přiřadit instanci třídy. Proměnné by měl být typu požadovanou třídu.

   ```vb
   Dim nextCustomer As customer
   ```

3. Přidat [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo inicializace proměnné do nové instance třídy.

   ```vb
   Dim nextCustomer As New customer
   ```

4. Členy třídy nyní přístupné prostřednictvím proměnné objektu.  

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1  
   ```

> [!NOTE]
>  Kdykoli je to možné, by měla deklarovat proměnnou typu třídy, kterou chcete přiřadit k ní. Tento postup se nazývá *časné vazby*. Pokud si nejste jisti třídy typu v době kompilace, můžete vyvolat *pozdní vazby* deklarováním proměnné bude [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md). Ale pozdní vazby můžete provádět pomalejší výkon a omezit přístup k členům run-time objekt. Další informace najdete v tématu [deklarace proměnné objektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).

### <a name="multiple-instances"></a>Více instancí
Objekty nově vytvořené ze třídy jsou často identické k sobě navzájem. Jakmile existují jako jednotlivé objekty, ale jejich proměnných a vlastností můžete změnit nezávisle na ostatních instancí. Například pokud přidáte tři políčka na formulář, každý objekt zaškrtávací políčko je instance <xref:System.Windows.Forms.CheckBox> třídy. Jednotlivé <xref:System.Windows.Forms.CheckBox> objekty sdílejí společnou sadu vlastností a možnosti (vlastnosti, proměnné, procedury a události) určené třídy. Ale každý má svůj vlastní název, můžete samostatně povolit a zakázané a je možné použít v jiném umístění ve formuláři.

## <a name="object-members"></a>Členové objektu
Element aplikace, je objekt reprezentující *instance* třídy. Pole, vlastnosti, metody a události jsou stavebními bloky objektů a představují jejich *členy*.

### <a name="member-access"></a>Přístup ke členu
Přístup ke členu objektu tak, že zadáte název proměnné objektu v pořadí, tečku (`.`) a název členu. Následující příklad nastaví <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Label> objektu.

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>Technologie IntelliSense seznam členů
Technologie IntelliSense uvádí členy třídy při vyvolání jeho členů seznamu možnost, například když zadáte tečku (`.`) jako operátor přístupu členů. Pokud zadáte tečku za název proměnné deklarované jako instance této třídy, IntelliSense vypíše všechny členy instance a žádné sdílené členy. Pokud zadáte tečku samotný název třídy, IntelliSense vypíše všechny sdílené členy a žádné členy instance. Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="fields-and-properties"></a>Pole a vlastnosti
*Pole* a *vlastnosti* představují informace uložené v objektu. Načíst a nastavit jejich hodnoty pomocí přiřazovací příkazy stejným způsobem jako načíst a nastavit místní proměnné v postupu. Následující příklad načte <xref:System.Windows.Forms.Control.Width%2A> vlastnost a nastaví <xref:System.Windows.Forms.Control.ForeColor%2A> vlastnost <xref:System.Windows.Forms.Label> objektu.

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

Všimněte si, že se také nazývá pole *členskou proměnnou*.
  
Použijte vlastnost postupy při:

- Je nutné určit, kdy a jak je nastavit nebo načíst hodnotu.

- Vlastnost má kvalitně definované sady hodnot, které je potřeba ověřit.

- Nastavením této hodnoty způsobí, že některé postřehnutelné změny ve stavu objektu, například `IsVisible` vlastnost.

- Nastavení vlastnosti způsobí, že změny na jiné interní proměnné nebo na hodnotách jiných vlastností.

- Před vlastnost můžete nastavit nebo načíst, je nutné provést sadu kroků.

Použití polí při:  

- Hodnota je držitelem ověřování typu. Například chyby nebo převod automatické dat v případě jinou hodnotu než `True` nebo `False` je přiřazen `Boolean` proměnné.

- Libovolná hodnota v rozsahu podporovaném parametrem datový typ je platný. To platí pro mnoho vlastností typu `Single` nebo `Double`.

- Vlastnost je `String` datový typ a neexistuje žádné omezení velikosti nebo hodnotu řetězce.

- Další informace najdete v tématu [procedury vlastnosti](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).

### <a name="methods"></a>Metody
A *metoda* je akce, které může objekt provádět. Například <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> je metoda <xref:System.Windows.Forms.ComboBox> objekt, který přidá nový záznam do pole se seznamem.

Následující příklad ukazuje <xref:System.Windows.Forms.Timer.Start%2A> metodu <xref:System.Windows.Forms.Timer> objektu.

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

Všimněte si, že metoda je jednoduše *postup* , který je zveřejněný prostřednictvím objektu.

Další informace najdete v tématu [postupy](../../../../visual-basic/programming-guide/language-features/procedures/index.md).

### <a name="events"></a>Události
Událost je akce rozpoznána v objektu, jako je například kliknutí myší nebo stisknutí klávesy a pro která můžete napsat kód reagovat. Události může dojít v důsledku akcí uživatele nebo kódu programu, nebo může být způsobeno systému. Kód, který signalizuje událost se říká, že *vyvolat* událostí a kód, který reaguje na něj se říká, že *zpracování* ho.

Můžete také vyvíjet vlastní události vyvolané službou objekty a zpracovány jinými objekty. Další informace najdete v tématu [události](../../../../visual-basic/programming-guide/language-features/events/index.md).

### <a name="instance-members-and-shared-members"></a>Členy instance a sdílené členy
Když vytvoříte objekt ze třídy, výsledkem je instance této třídy. Členy, které nejsou deklarovány s [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) – klíčové slovo se *členy instance*, které patří výhradně pro tuto konkrétní instanci. Člen instance. v jedné instanci je nezávislá na stejný člen v jiná instance stejné třídy. Členskou proměnnou instance například může mít různé hodnoty v různých instancích.

Členy deklarované s `Shared` – klíčové slovo se *sdílené členy*, který patří do třídy jako celek a ne do jakékoli určité instance. Sdílenému členu existuje pouze jednou, bez ohledu na to, kolik instancí své třídy vytvoříte, nebo i v případě, že vytvoříte žádné instance. Proměnná sdílenému členu, například má pouze jednu hodnotu, která je k dispozici pro veškerý kód, který může přistupovat k třídě.

#### <a name="accessing-nonshared-members"></a>Přístup k nesdílené členy  

###### <a name="to-access-a-nonshared-member-of-an-object"></a>Pro přístup k nesdílené člen objektu

1. Ujistěte se, že objekt byl vytvořen ze své třídy a přiřazen do proměnné objektu.

   ```vb
   Dim secondForm As New System.Windows.Forms.Form  
   ```  

2. V příkazu, který přistupuje k členu, postupujte podle názvu proměnné objektu s *operátor přístup člena* (`.`) a potom název člena.

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>Přístup ke sdílené členy

###### <a name="to-access-a-shared-member-of-an-object"></a>Pro přístup ke sdílenému členu objektu

- Postupujte podle názvu třídy s *operátor přístup člena* (`.`) a potom název člena. Vždy byste měli přistupovat k `Shared` člen objektu přímo prostřednictvím názvu třídy.

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)  
   ```

- Pokud jste již vytvořili objekt ze třídy, případně se dostanete `Shared` člen prostřednictvím proměnné objektu.

### <a name="differences-between-classes-and-modules"></a>Rozdíly mezi třídami a moduly
Hlavní rozdíl mezi třídami a moduly je, že třídy může být vytvořen jako objekty, zatímco standardní moduly nelze. Protože existuje jenom jednu kopii standardních modulu dat při změně veřejné proměnné v modulu standardních jedné části programu, získá další část programu stejnou hodnotu, pokud je pak přečte tuto proměnnou. Naproti tomu datový objekt existuje samostatně pro každý objekt instance. Další rozdíl je, že na rozdíl od standardní moduly tříd mohou implementovat rozhraní.

> [!NOTE]
> Když `Shared` modifikátor se použijí na člen třídy, je přidružen k samotné místo konkrétní instanci třídy třídy. Člen lze přistupovat přímo pomocí názvu třídy, jsou přístupné stejné členy způsob, jak modul.

Třídy a moduly také použít jiné rámce jejich členy. Členy definované v rámci třídy mají rozsah v rámci konkrétní instanci třídy a existují jenom po dobu životnosti objektu. Pro přístup ke členům třídy z mimo třídu, je nutné použít plně kvalifikované názvy ve formátu *objekt*. *Člen*.

Na druhé straně členy deklarované v rámci modulu jsou veřejně dostupné ve výchozím nastavení a je možný přes jakýkoli kód, který může přistupovat k modulu. To znamená, že proměnné v modulu standardních jsou účinně globální proměnné, protože jsou viditelné z kdekoli ve vašem projektu a existují po celou dobu životnosti programu.

## <a name="reusing-classes-and-objects"></a>Opětovné použití tříd a objektů  
Objekty vám umožňují deklarovat proměnné a procedury jednou a pak znovu použít kdykoli je to třeba. Například pokud chcete přidat kontrolu pravopisu do aplikace můžete definovat všechny proměnné a funkce pro kontrolu pravopisu nakonfigurovánu podporu. Pokud vytvoříte vaše kontroly pravopisu jako třída, můžete je znovu ji v jiných aplikacích tak, že přidáte odkaz na kompilované sestavení. Ještě lepší je je možné uložit sami nějakou práci pomocí kontroly pravopisu třídu, která už někdo vyvinula.

[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Poskytuje mnoho příkladů součásti, které jsou k dispozici pro použití. V následujícím příkladu <xref:System.TimeZone> třídy v <xref:System> oboru názvů. <xref:System.TimeZone> obsahuje členy, které umožňují načítat informace o časovém pásmu systému aktuálního počítače.

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

V předchozím příkladu první [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklaruje proměnnou objektu typu <xref:System.TimeZone> a přiřadí ji <xref:System.TimeZone> vrácený <xref:System.TimeZone.CurrentTimeZone%2A> vlastnost.

## <a name="relationships-among-objects"></a>Vztahy mezi objekty  
Objekty mohou být propojeny k sobě navzájem několika způsoby. Hlavní typy vztahů jsou *hierarchické* a *členství ve skupině*.

### <a name="hierarchical-relationship"></a>Hierarchický vztah
Když jsou třídy odvozeny z více základních tříd, jejich se říká, že jste *hierarchický vztah*. Hierarchie tříd jsou užitečné při popisu položky, které jsou podtyp další obecné třídy.

V následujícím příkladu předpokládejme, že chcete definovat zvláštní druh <xref:System.Windows.Forms.Button> , že funguje jako normální <xref:System.Windows.Forms.Button> , ale také zpřístupní metodu, která obrací barvy popředí a pozadí.

##### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a>Definování třídy je odvozen z již existující třídu

1. Použití [Class – příkaz](../../../../visual-basic/language-reference/statements/class-statement.md) definování třídy, ze kterého chcete vytvořit objekt potřebujete.

   ```vb
   Public Class reversibleButton
   ```

   Ujistěte se, `End Class` příkaz následuje poslední řádek kódu ve své třídě. Ve výchozím nastavení, budou automaticky generuje integrovaného vývojového prostředí (IDE) `End Class` při zadávání `Class` příkazu.

2. Postupujte podle `Class` příkaz okamžitě [dědí příkaz](../../../../visual-basic/language-reference/statements/inherits-statement.md). Zadejte třídu, ze kterého vaše nová třída odvozena.  
  
   ```vb
   Inherits System.Windows.Forms.Button
   ```

  Nové třídy dědí všechny členy definované prostřednictvím základní třídy.

3. Přidejte kód pro další členové vaší odvozené třídě zpřístupňuje. Například můžete přidat `reverseColors` metoda a odvozené třídy může vypadat takto:

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

   Je-li vytvořit objekt `reversibleButton` třídu, má přístup všichni členové <xref:System.Windows.Forms.Button> třídu, stejně jako `reverseColors` metoda a všemi novými členy můžete definovat na `reversibleButton`.

Odvozené třídy dědí členy třídy, které jsou založené na, vám umožňuje přidat složitost, jak budete v hierarchii tříd. Další informace najdete v tématu [základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

#### <a name="compiling-the-code"></a>Kompilování kódu
Ujistěte se, že kompilátor může přistupovat k třídě, ze kterého máte v úmyslu odvozovat nové třídy. To může znamenat plně kvalifikováním názvu, jako v předchozím příkladu, nebo při identifikaci svůj obor názvů v [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Pokud je třída v jiném projektu, můžete potřebovat přidat odkaz na tento projekt. Další informace najdete v tématu [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).

### <a name="containment-relationship"></a>Vztah členství ve skupině
Dalším způsobem, že můžete související objekty, je *vztah členství ve skupině*. Kontejnerové objekty zapouzdřují logicky jiné objekty. Například <xref:System.OperatingSystem> logicky obsahuje objekt <xref:System.Version> objektu, který vrací přes jeho <xref:System.OperatingSystem.Version%2A> vlastnost. Všimněte si, že objekt kontejneru fyzicky neobsahuje jakýkoli jiný objekt.

#### <a name="collections"></a>Kolekce
Jeden konkrétní typ objektu členství ve skupině je reprezentována *kolekce*. Kolekce jsou skupiny podobně jako objekty, které jsou uvedené. Podporuje specifickou syntaxi v jazyce Visual Basic [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) , který umožňuje iterování položek v kolekci. Kromě toho kolekce často bylo možné použít <xref:Microsoft.VisualBasic.Collection.Item%2A> načíst prvky podle jejich indexu nebo tím, že přidružíte s jedinečným řetězcem. Kolekce může být snadnější použití než pole, protože umožňují přidat nebo odebrat položky bez použití indexů. Z důvodu jejich snadné použití kolekce často se používají k ukládání formuláře a ovládací prvky.

## <a name="related-topics"></a>Související témata  
 [Návod: Definování tříd](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 Poskytuje podrobný popis toho, jak vytvořit třídu.  

 [Vlastnosti a metody přetížení](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 Vlastnosti a metody přetečení  

 [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 Popisuje modifikátory dědění, přepisování metody a vlastnosti, MyBase a MyClass.  

 [Doba života objektu: Vytváření a zničení objektů](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 Tento článek popisuje vytvoření a uvolnění instancí třídy.  

 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 Popisuje, jak vytvořit a použít anonymní typy, které umožňují vytvářet objekty bez psaní definice třídy datového typu.  

 [Inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 Tento článek popisuje inicializátory objektů, které se používají k vytvoření instance pojmenované a anonymní typy pomocí jediného výrazu.  

 [Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 Vysvětluje, jak k odvození názvů a typů v deklaracích anonymního typu vlastností. Obsahuje příklady úspěšné a neúspěšné odvození.
