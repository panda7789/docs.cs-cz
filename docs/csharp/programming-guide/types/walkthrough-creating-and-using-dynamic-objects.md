---
title: 'Průvodce: Vytváření a používání dynamických objektů (C# a Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
ms.openlocfilehash: 7031fe21e53b38f686d229b350b8dfef7dd93bdc
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204818"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>Průvodce: Vytváření a používání dynamických objektů (C# a Visual Basic)

Dynamické objekty zveřejnit členy jako jsou vlastnosti a metody v době běhu, místo v době kompilace. To umožňuje vytvářet objekty pro práci s struktury, které neodpovídají statický typ nebo formát. Můžete například použít dynamický objekt tak, aby odkazovaly HTML Document Object Model (DOM), který může obsahovat libovolnou kombinaci platné značky elementů a atributů HTML. Vzhledem k tomu, že každý dokument HTML je jedinečný, se určují členy u konkrétního dokumentu HTML v době běhu. Běžnou metodou chcete odkazovat na atribut elementu HTML je předat název atributu, který má `GetProperty` metoda elementu. Odkaz `id` atribut elementu HTML `<div id="Div1">`, nejprve získejte odkaz na `<div>` element a pak použijte `divElement.GetProperty("id")`. Pokud používáte dynamický objekt, můžete odkazovat `id` atribut jako `divElement.id`.  
  
 Dynamické objekty poskytují také pohodlný přístup k dynamické jazyky, jako je například IronPython a IronRuby. Dynamický objekt můžete použít k odkazování na dynamické skript, který je interpretován v době běhu.  
  
 Dynamický objekt můžete odkazovat pomocí pozdní vazbu. V jazyce C#, zadejte typ jako objekt s pozdní vazbou `dynamic`. V jazyce Visual Basic zadejte typ jako objekt s pozdní vazbou `Object`. Další informace najdete v tématu [dynamické](../../../csharp/language-reference/keywords/dynamic.md) a [včasného a pozdní vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
 Můžete vytvořit vlastní dynamických objektů pomocí třídy v <xref:System.Dynamic?displayProperty=nameWithType> oboru názvů. Například můžete vytvořit <xref:System.Dynamic.ExpandoObject> a určují členy tohoto objektu za běhu. Můžete také vytvořit vlastní typ, který dědí <xref:System.Dynamic.DynamicObject> třídy. Potom můžete přepsat členy <xref:System.Dynamic.DynamicObject> třídy dynamické nakonfigurovánu za běhu.  
  
 V tomto návodu budete provádět následující úlohy:  
  
-   Vytvořte vlastní objekt, který dynamicky zpřístupní obsah textového souboru jako vlastnosti objektu.  
  
-   Vytvořit projekt, který se používá `IronPython` knihovny.  
  
## <a name="prerequisites"></a>Požadavky  
Potřebujete [IronPython](http://ironpython.net/) pro .NET k dokončení tohoto návodu. Přejděte na jejich [stránku pro stažení](http://ironpython.net/download/) získat nejnovější verzi.
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Vytváření vlastních dynamických objektů

První projekt, který vytvoříte v tomto názorném postupu definuje vlastní dynamický objekt, který vyhledá obsah textového souboru. Hledaný text je určen název dynamických vlastností. Například pokud volání kódu určuje `dynamicFile.Sample`, dynamické třídy vrátí obecný seznam řetězců, které obsahuje všechny řádky ze souboru, které začínají řetězcem "Ukázkový". Hledání nerozlišuje velká a malá písmena. Dynamické třídy také podporuje dva volitelné argumenty. První argument je hodnota výčtu možnosti vyhledávání, která určuje, že dynamickou třídu program hledat shody na začátek řádku a koncem řádku, nebo kdekoli na řádku. Druhý argument určuje, že dynamickou třídu by měla oříznout úvodní a koncové mezery z každého řádku před vyhledáváním. Například pokud volání kódu určuje `dynamicFile.Sample(StringSearchOption.Contains)`, dynamické třídy hledá "Ukázkový" kdekoli v řádku. Pokud volání kódu určuje `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, dynamické třídy hledá "Ukázkový" na začátku každého řádku a nedojde k odstranění úvodní a koncové mezery. Výchozí chování dynamické třídy je vyhledávat shodu na začátku každého řádku a odebrat úvodní i koncové mezery.  
  
### <a name="to-create-a-custom-dynamic-class"></a>Pro vytvoření vlastní třídy dynamické  
  
1.  Spusťte Visual Studio.  
  
2.  Na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.  
  
3.  V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto. Vyberte **konzolovou aplikaci** v **šablony** podokně. V **název** zadejte `DynamicSample`a potom klikněte na tlačítko **OK**. Vytvoření nového projektu.  
  
4.  Klikněte pravým tlačítkem na projekt DynamicSample a přejděte na **přidat**a potom klikněte na tlačítko **třídy**. V **název** zadejte `ReadOnlyFile`a potom klikněte na tlačítko **OK**. Přidá nový soubor, který obsahuje třídu ReadOnlyFile.  
  
5.  V horní části souboru ReadOnlyFile.cs nebo ReadOnlyFile.vb, přidejte následující kód k importu <xref:System.IO?displayProperty=nameWithType> a <xref:System.Dynamic?displayProperty=nameWithType> obory názvů.  

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]  

6.  Vlastní dynamický objekt výčtu používá k určení kritérií vyhledávání. Před příkaz třídy přidejte následující definice výčtu.  
  
    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]
  
7.  Aktualizujte příkaz třídy dědit `DynamicObject` třídy, jak je znázorněno v následujícím příkladu kódu.  
  
    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8.  Přidejte následující kód, který `ReadOnlyFile` k definování privátní pole pro cestu k souboru a konstruktor pro třídu `ReadOnlyFile` třídy.  
  
    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]
  
9. Přidejte následující `GetPropertyValue` metodu `ReadOnlyFile` třídy. `GetPropertyValue` Metoda přijímá jako vstup, kritéria hledání a vrátí řádky z textového souboru, které odpovídají, který kritéria vyhledávání. Dynamické metody poskytované objektem `ReadOnlyFile` třídy volání `GetPropertyValue` metody k získání jejich odpovídajících výsledků.  
  
    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]  
  
10. Po `GetPropertyValue` metodu, přidejte následující kód k přepsání <xref:System.Dynamic.DynamicObject.TryGetMember%2A> metodu <xref:System.Dynamic.DynamicObject> třídy. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Metoda se volá, když je požadováno členem dynamické třídy a nejsou zadány žádné argumenty. `binder` Argument obsahuje informace o odkazované členu a `result` argument odkazuje výsledek vrácený pro zadaného člena. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Metoda vrátí logickou hodnotu, která vrací `true` Pokud požadovaného člena existuje; jinak vrátí `false`.  
  
    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]
  
11. Po `TryGetMember` metodu, přidejte následující kód k přepsání <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> metodu <xref:System.Dynamic.DynamicObject> třídy. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Metoda se volá, když je požadováno členem dynamické třídy s argumenty. `binder` Argument obsahuje informace o odkazované členu a `result` argument odkazuje výsledek vrácený pro zadaného člena. `args` Argument obsahuje celou řadu argumenty předávané členovi. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Metoda vrátí logickou hodnotu, která vrací `true` Pokud požadovaného člena existuje; jinak vrátí `false`.  
  
    Vlastní verzi `TryInvokeMember` metoda očekává, že první argument představoval hodnotu z `StringSearchOption` výčet, který jste definovali v předchozím kroku. `TryInvokeMember` Metoda očekává druhý argument představoval hodnotu typu Boolean. Pokud jeden nebo oba argumenty jsou platné hodnoty, jsou předány `GetPropertyValue` metody k načtení výsledků.  
  
    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]
  
12. Soubor uložte a zavřete.  
  
#### <a name="to-create-a-sample-text-file"></a>K vytvoření ukázkového textového souboru  
  
1.  Klikněte pravým tlačítkem na projekt DynamicSample a přejděte na **přidat**a potom klikněte na tlačítko **nová položka**. V **nainstalované šablony** vyberte **Obecné**a pak vyberte **textový soubor** šablony. Ponechat výchozí název soubory TextFile1.txt v **název** pole a potom klikněte na tlačítko **přidat**. Do projektu se přidá nový textový soubor.  
  
2.  Zkopírujte následující text do souboru soubory TextFile1.txt.  
  
    ```  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (https://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (https://www.graphicdesigninstitute.com/)   
    Supplier: Fabrikam, Inc. (https://www.fabrikam.com/)   
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)   
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3.  Soubor uložte a zavřete.  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>K vytvoření ukázkové aplikace, která používá vlastní dynamický objekt  
  
1.  V **Průzkumníka řešení**, poklikejte na soubor Module1.vb, pokud používáte Visual Basic nebo souboru Program.cs Pokud používáte jazyk Visual C#.  
  
2.  Přidejte následující kód do hlavní postup vytvoření instance `ReadOnlyFile` třída pro soubory TextFile1.txt souboru. Kód používá k volání dynamické členy a načítání řádků textu, které obsahují řetězec "Zákazník" pozdní vazbu.  
  
     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]
  
3.  Uložte soubor a stiskněte klávesu CTRL + F5 sestavte a spusťte aplikaci.  
  
## <a name="calling-a-dynamic-language-library"></a>Volání knihovny Dynamic Language  

Dalším projektu, který vytvoříte v tomto názorném postupu má přístup k knihovnu, která je napsána v jazyce dynamické Ironpythonu.
  
### <a name="to-create-a-custom-dynamic-class"></a>Pro vytvoření vlastní třídy dynamické
  
1.  V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto. Vyberte **konzolovou aplikaci** v **šablony** podokně. V **název** zadejte `DynamicIronPythonSample`a potom klikněte na tlačítko **OK**. Vytvoření nového projektu.  
  
3.  Pokud používáte Visual Basic, klikněte pravým tlačítkem na projekt DynamicIronPythonSample a pak klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **odkazy** kartu. Klikněte na tlačítko **Přidat**. Pokud používáte jazyk Visual C# v **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** složku a pak klikněte na tlačítko **přidat odkaz**.  
  
4.  Na **Procházet** kartu, přejděte do složky, ve kterém jsou nainstalované knihovny Ironpythonu. Například C:\Program pro rozhraní .NET 4.0 2.6 Files\IronPython. Vyberte **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**, a **Microsoft.Dynamic.dll** knihovny . Klikněte na **OK**.  
  
5.  Pokud používáte Visual Basic, upravte soubor Module1.vb. Pokud používáte jazyk Visual C#, upravte soubor Program.cs.  
  
6.  Na začátek souboru přidejte následující kód k importu `Microsoft.Scripting.Hosting` a `IronPython.Hosting` oborů názvů z knihoven Ironpythonu.  
  
    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]
  
7.  Do metody Main přidejte následující kód k vytvoření nového `Microsoft.Scripting.Hosting.ScriptRuntime` objektu k hostování knihovny Ironpythonu. `ScriptRuntime` Objekt načte random.py modul knihovny Ironpythonu.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]
  
8.  Za kód pro načtení modulu random.py přidejte následující kód k vytvoření pole celých čísel. Pole je předán `shuffle` metoda random.py modul, který náhodně seřadí hodnoty v poli.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]
  
9. Uložte soubor a stiskněte klávesu CTRL + F5 sestavte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [Statické a dynamické vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)
- [Implementovat dynamické rozhraní (ke stažení PDF z Microsoft TechNet)](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
