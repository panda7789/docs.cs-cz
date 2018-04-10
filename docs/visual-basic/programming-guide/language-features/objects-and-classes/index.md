---
title: Objekty a třídy v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be5e0156b4cacc39e1613e06fe3c138838b02700
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="objects-and-classes-in-visual-basic"></a>Objekty a třídy v jazyce Visual Basic
*Objekt* je kombinací kód a data, která lze považovat za jednotku. Objekt může být část aplikace, jako je ovládacího prvku nebo formuláře. Celá aplikace může být také objekt.

Když vytvoříte aplikaci v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], neustále práce s objekty. Můžete použít objekty poskytované [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], jako jsou například ovládací prvky, formulářů a dat přístup k objektům. Můžete taky objektů z jiných aplikací v rámci vaší [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] aplikace. Můžete dokonce vytvořit vlastní objekty a definovat další vlastnosti a metody pro ně. Objekty fungovat stejně jako prefabrikované stavební bloky pro programy – umožňují můžete napsat kód jednou a znovu použít opakovaně.  
  
Toto téma popisuje objekty podrobně.  

## <a name="objects-and-classes"></a>Objekty a třídy
Každý objekt v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] je definované *třída*. Třída popisuje proměnné, vlastnosti, postupy a události objektu. Objekty jsou instance třídy; můžete vytvořit libovolný počet objektů, které potřebujete, jakmile definujete třídu.

Vztah mezi objektem a její třída pochopit, vezměte v úvahu řezačky souboru cookie a soubory cookie. Ořezávání soubor cookie je třída. Definuje vlastnosti každého souboru cookie, například velikost a tvar. Třída slouží k vytváření objektů. Objekty jsou soubory cookie.

Objekt je nutné vytvořit před přístupem k její členy.  

#### <a name="to-create-an-object-from-a-class"></a>Chcete-li vytvořit objekt ze třídy

1. Určete, ze které třídy, kterou chcete vytvořit objekt.  

2. Zápis [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) vytvoření proměnné, do které můžete přiřadit instance třídy. Proměnná by měla být typ požadovanou třídu.

   ```vb
   Dim nextCustomer As customer
   ```

3. Přidat [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo můžete inicializovat do nové instance třídy.

   ```vb
   Dim nextCustomer As New customer
   ```

4. Můžete teď přístup ke členům třídy prostřednictvím proměnné objektu.  

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1  
   ```

> [!NOTE]
>  Kdykoli je to možné, by měly deklarovat proměnnou být typu třídy, kterou chcete přiřadit k němu. To se označuje jako *časné vazby*. Pokud neznáte třídu, zadejte v době kompilace, můžete vyvolat *pozdní vazby* deklarováním proměnné se [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md). Ale pozdní vazby můžete provádět pomalejší výkon a omezení přístupu ke členům běhového objektu. Další informace najdete v tématu [deklarace proměnné objektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).

### <a name="multiple-instances"></a>Více instancí
Objekty nově vytvořený z třídy jsou často identické navzájem. Jakmile existují jako jednotlivé objekty, ale jejich proměnné a vlastnosti lze změnit nezávisle na ostatních instancí. Například pokud přidáte tři políčka na formulář, každý objekt zaškrtávací políčko je instance <xref:System.Windows.Forms.CheckBox> třídy. Jednotlivých <xref:System.Windows.Forms.CheckBox> objekty sdílejí společnou sadu vlastností a funkcí (vlastnosti, proměnné, postupy a události) definované v třídě. Však každý má vlastní název, lze samostatně povolit a zakázat a mohou být umístěny v jiném umístění ve formuláři.

## <a name="object-members"></a>Členové objektu
Element aplikace, je objekt reprezentující *instance* třídy. Pole, vlastnosti, metod a události představují stavební kameny objektů a tvoří jejich *členy*.

### <a name="member-access"></a>Přístup ke členu
Přístup ke členu objektu zadáním v pořadí, název proměnné objektu období (`.`) a název člena. Následující příklad nastavuje <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Label> objektu.

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>IntelliSense seznam členů
IntelliSense zobrazí seznam členy třídy při vyvolání své volby vypsat členy, například když zadáte období (`.`) jako operátor přístup ke členu. Pokud zadáte název proměnné deklarovány jako instance této třídy tečku, IntelliSense zobrazí seznam všech členů instance a žádná sdíleného člena. Pokud zadáte období následující samotný název třídy, IntelliSense zobrazí seznam všech sdíleného člena a žádný z členů instance. Další informace najdete v tématu [pomocí IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="fields-and-properties"></a>Pole a vlastnosti
*Pole* a *vlastnosti* představují informace uložené v objektu. Načtení a nastavení jejich hodnot s příkazy přiřazení stejným způsobem jako načíst a nastavit místní proměnné v postupu. Následující příklad načte <xref:System.Windows.Forms.Control.Width%2A> vlastnost a nastaví <xref:System.Windows.Forms.Control.ForeColor%2A> vlastnost <xref:System.Windows.Forms.Label> objektu.

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

Všimněte si, že pole je také označován *členské proměnné*.
  
Použijte vlastnost postupy při:

- Potřebujete řídit, kdy a jak je nastavit nebo načíst hodnotu.

- Tato vlastnost nemá jasně definované sady hodnot, které je potřeba ověřit.

- Nastavení hodnoty způsobí, že některé postřehnutelné změny ve stavu objektu, například `IsVisible` vlastnost.

- Nastavení vlastnosti způsobí, že změny na ostatní interní proměnné nebo na hodnotách jiných vlastností.

- Sadu kroky je potřeba provést před vlastnost nelze nastavit ani načíst.

Použití polí, když:  

- Hodnota je typu samoobslužné ověřování. Například Chyba nebo převod automatické dat v případě jinou hodnotu než `True` nebo `False` je přiřazena k `Boolean` proměnné.

- Libovolná hodnota v rozsahu nepodporuje datový typ je platný. To platí pro mnoho vlastností typu `Single` nebo `Double`.

- Vlastnost je `String` datový typ, a neexistuje žádné omezení velikosti nebo hodnotu řetězce.

- Další informace najdete v tématu [procedury vlastností](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).

### <a name="methods"></a>Metody
A *metoda* je akce, která může provádět objekt. Například <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> je metoda <xref:System.Windows.Forms.ComboBox> objekt, který přidá novou položku do pole se seznamem.

Následující příklad ukazuje <xref:System.Windows.Forms.Timer.Start%2A> metodu <xref:System.Windows.Forms.Timer> objektu.

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

Všimněte si, že je metoda jednoduše *postup* který je zveřejněný prostřednictvím objektu.

Další informace najdete v tématu [postupy](../../../../visual-basic/programming-guide/language-features/procedures/index.md).

### <a name="events"></a>Události
Událost je akce rozpoznáno objekt, jako je například kliknutí myši nebo stisknutí klávesy, a pro které můžete psát kód reagovat. Události může dojít v důsledku akce uživatele nebo kódu programu, nebo může být způsobeno systému. Kód, který signály událost říká, že je *vyvolat* událostí a kód, který reaguje na něj říká, že je *zpracování* ho.

Také lze vytvářet vlastní události vyvolané vašich objektů a zpracovávat jiné objekty. Další informace najdete v tématu [události](../../../../visual-basic/programming-guide/language-features/events/index.md).

### <a name="instance-members-and-shared-members"></a>Členy instance a sdílení členové
Když vytvoříte objekt ze třídy, výsledkem je instance této třídy. Členové, kteří nejsou deklarovat s [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md) – klíčové slovo jsou *instance členy*, které patří výhradně na tuto konkrétní instanci. Člen instance v jedné instance je nezávislá stejného člena v jiná instance stejné třídy. Členské proměnné instance, například může mít různé hodnoty v různých instancí.

Členy deklarovat s `Shared` – klíčové slovo jsou *sdílené členy*, který patří k třídě jako celek, ne na jakékoli určité instance. Sdíleného člena existuje pouze po, bez ohledu na to, kolik instancí třídy jeho vytvoření nebo i v případě, že vytvoříte žádné instance. Proměnnou sdíleného člena, například obsahuje pouze jednu hodnotu, která je k dispozici pro všechny kód, který může přistupovat k třídě.

#### <a name="accessing-nonshared-members"></a>Přístup ke členům sdíleném  

###### <a name="to-access-a-nonshared-member-of-an-object"></a>O přístup člena sdíleném objektu

1. Zajistěte, aby bylo vytvořeno ze své třídy objektu a přiřazené proměnné objektu.

   ```vb
   Dim secondForm As New System.Windows.Forms.Form  
   ```  

2. V příkazu, který přistupuje k člen, postupujte podle názvu proměnné objektu s *přístup ke členu operátor* (`.`) a potom název člena.

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>Přístup k sdílení členové

###### <a name="to-access-a-shared-member-of-an-object"></a>Přístup sdíleného člena objektu

- Postupujte podle názvu třídy s *přístup ke členu operátor* (`.`) a potom název člena. Byste měli vždy přistupovat `Shared` členem objektu přímo prostřednictvím název třídy.

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)  
   ```

- Pokud jste již vytvořili objekt ze třídy, případně se dostanete `Shared` člen prostřednictvím proměnné objektu.

### <a name="differences-between-classes-and-modules"></a>Rozdíly mezi třídami a modulů
Hlavní rozdíl mezi třídami a moduly je, že třídy se dá vytvořit instance jako objekty při nelze standardní moduly. A proto pouze jedna kopie dat standardní modul, kdy se jeden součástí vašeho programu změní veřejné proměnné ve standardním modulu jiných součástí program získá stejnou hodnotu, pokud je pak přečte tuto proměnnou. Naproti tomu data objektu existuje samostatně pro každou instancí objektu. Další rozdíl je, že na rozdíl od standardní moduly třídy mohou implementovat rozhraní.

> [!NOTE]
> Když `Shared` modifikátor umožňuje člena třídy, je přidružen vlastní místo konkrétní instanci třídy třídy. Člen je přistupovat přímo pomocí názvu třídy, stejné členy modulu způsob, jak se k nim přistupuje.

Třídy a moduly také použít různé obory pro jejich členové. Členové, které jsou definované v rámci třídy jsou určené v rámci konkrétní instanci třídy a existovat jenom pro doba života objektu. Přístup ke členům třídy z mimo třídu, musíte použít plně kvalifikované názvy ve formátu *objekt*. *Člen*.

Na druhé straně členové deklarované v rámci modul jsou veřejně dostupné ve výchozím nastavení a je přístupný kód, který můžete získat přístup k modulu. To znamená, že proměnné ve standardním modulu jsou efektivně globální proměnné, protože jsou viditelné z libovolné místo ve vašem projektu a existují po celou dobu životnosti program.

## <a name="reusing-classes-and-objects"></a>Opětovné použití tříd a objektů  
Objekty umožňují deklarace proměnných a postupy jednou a pak je vždy v případě potřeby znovu použijte. Například pokud chcete přidat nástroj pro kontrolu pravopisu do aplikace můžete definovat všechny proměnné a podporovat funkce nakonfigurovánu pravopisu. Pokud vytvoříte vaše kontrola pravopisu jako třída, můžete je znovu ji v ostatních aplikacích přidáním odkazu na zkompilované sestavení. Ještě lepší nebudete moct uložit sami některé pracovní pomocí kontrola pravopisu třídu, která někdo jiný již vyvinula

[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Obsahuje mnoho příklady součásti, které jsou k dispozici pro použití. Následující příklad používá <xref:System.TimeZone> třídy v <xref:System> oboru názvů. <xref:System.TimeZone>poskytuje členy, které vám umožní načíst informace o časovém pásmu aktuální počítačového systému.

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

V předchozím příkladu první [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) deklaruje proměnné objektu typu <xref:System.TimeZone> a přiřadí ji <xref:System.TimeZone> objekt vrácený <xref:System.TimeZone.CurrentTimeZone%2A> vlastnost.

## <a name="relationships-among-objects"></a>Vztahy mezi objekty  
Objekty může souviset s navzájem několika způsoby. Hlavní typy vztahů jsou *hierarchické* a *členství ve skupině*.

### <a name="hierarchical-relationship"></a>Hierarchický vztah
Když jsou třídy odvozené z více základní třídy, se nazývá mít *hierarchický vztah*. Hierarchie tříd jsou užitečné při popisu položky, které jsou podtypem další obecné třídy.

V následujícím příkladu předpokládejme, že chcete definovat speciální typ <xref:System.Windows.Forms.Button> , funguje jako normální <xref:System.Windows.Forms.Button> , ale také zpřístupní metodu, která obrátí barvy popředí a na pozadí.

##### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a>Chcete-li definovat třídu je odvozený od již existující třídy

1. Použití [Class – příkaz](../../../../visual-basic/language-reference/statements/class-statement.md) do definice třídy, ze které chcete vytvořit objekt potřebujete.

   ```vb
   Public Class reversibleButton
   ```

   Ujistěte se, `End Class` příkaz následuje poslední řádek kódu v třídě. Ve výchozím nastavení, budou automaticky vygeneruje integrované vývojové prostředí (IDE) `End Class` při zadávání `Class` příkaz.

2. Postupujte podle `Class` příkaz okamžitě s [dědí příkaz](../../../../visual-basic/language-reference/statements/inherits-statement.md). Zadejte třídu, ze kterého se nová třída odvozena.  
  
   ```vb
   Inherits System.Windows.Forms.Button
   ```

  Nové třídy dědí všechny členy, které jsou definované v základní třídě.

3. Přidáte kód pro další členy vaší zpřístupňuje odvozené třídy. Například může přidat `reverseColors` metoda a odvozená třída může vypadat takto:

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

   Pokud vytvoříte objekt z `reversibleButton` třídy, že přístup všech členů <xref:System.Windows.Forms.Button> třída, a taky `reverseColors` metoda a nové členy můžete definovat na `reversibleButton`.

Odvozené třídy dědí z třídy, které jsou založené na, že se můžete k přidání složitosti jako o průběhu v hierarchii – třída členů. Další informace najdete v tématu [základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

#### <a name="compiling-the-code"></a>Probíhá kompilace kódu
Ujistěte se, že kompilátor můžete přístup ke třídě, ze kterého chcete odvozena novou třídu. To může znamenat plně kvalifikující jeho název, jako v předchozím příkladu nebo identifikace jeho oboru názvů v [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Pokud třída je v na jiný projekt, možná budete muset přidat odkaz na tento projekt. Další informace najdete v tématu [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).

### <a name="containment-relationship"></a>Vztah členství ve skupině
Dalším způsobem může souviset objekty je *vztah členství ve skupině*. Kontejnerové objekty zapouzdřují logicky jiné objekty. Například <xref:System.OperatingSystem> objekt logicky obsahuje <xref:System.Version> objekt, který vrátí prostřednictvím jeho <xref:System.OperatingSystem.Version%2A> vlastnost. Všimněte si, že objekt kontejneru fyzicky neobsahuje jakýkoliv jiný objekt.

#### <a name="collections"></a>Kolekce
Jeden konkrétní typ omezení objektu je reprezentována *kolekce*. Kolekce jsou podobné objekty, které jsou uvedené skupiny. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]podporuje specifickou syntaxi v [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) , které umožňuje iteraci v rámci položky kolekce. Kromě toho kolekce často umožňují používat <xref:Microsoft.VisualBasic.Collection.Item%2A> načíst elementy pomocí jejich indexu nebo je možné přidružit do jedinečného řetězce. Kolekce může být jednodušší než pole vzhledem k tomu, že umožňují přidat nebo odebrat položky bez použití indexy. Kvůli jejich snadné použití se kolekce často používají k ukládání formuláře a ovládací prvky.

## <a name="related-topics"></a>Související témata  
 [Návod: Definování tříd](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 Poskytuje podrobný popis toho, jak vytvořit třídu.  

 [Vlastnosti a metody přetečení](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 Vlastnosti a metody přetečení  

 [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 Popisuje modifikátory dědičnosti, přepsání metody a vlastnosti, MyBase a MyClass.  

 [Doba života objektu: Objekty vytváření a zničení](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 Popisuje vytvoření a uvolnění instancí třídy.  

 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 Popisuje, jak vytvořit a použít anonymní typy, které umožňují vytvářet objekty bez nutnosti psaní definice třídy pro datový typ.  

 [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 Popisuje inicializátory objektů, které se používají k vytvoření instance pojmenované a anonymní typy pomocí jeden výraz.  

 [Postupy: odvození názvů a typů v deklaracích anonymního typu vlastností](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 Vysvětluje, jak odvození názvů a typů v deklaracích anonymního typu vlastností. Obsahuje příklady odvození úspěšné a neúspěšné.
