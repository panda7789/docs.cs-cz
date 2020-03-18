---
title: 'Postupy: Vytváření a používání dynamických objektů (C# a Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
ms.openlocfilehash: 3b5a92948a3e692a734f3ddee3c7238d5d27588f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157049"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>Postupy: Vytváření a používání dynamických objektů (C# a Visual Basic)

Dynamické objekty vystavit členy, jako jsou vlastnosti a metody v době běhu, nikoli v době kompilace. To umožňuje vytvářet objekty pro práci se strukturami, které neodpovídají statickému typu nebo formátu. Dynamický objekt můžete například použít k odkazování na objektový model dokumentu HTML (DOM), který může obsahovat libovolnou kombinaci platných prvků a atributů značek HTML. Vzhledem k tomu, že každý dokument HTML je jedinečný, jsou členy určitého dokumentu HTML určeny za běhu. Běžnou metodou pro odkazování na atribut prvku HTML je předat `GetProperty` název atributu metodě prvku. Chcete-li `id` odkazovat na `<div id="Div1">`atribut elementu HTML `<div>` , nejprve `divElement.GetProperty("id")`získáte odkaz na prvek a potom použijte . Pokud používáte dynamický objekt, můžete `id` na `divElement.id`atribut odkazovat jako na .  
  
 Dynamické objekty také poskytují pohodlný přístup k dynamickým jazykům, jako jsou IronPython a IronRuby. Dynamický objekt můžete použít k odkazování na dynamický skript, který je interpretován za běhu.  
  
 Dynamický objekt odkazujete pomocí pozdní vazby. V c# zadáte typ objektu s pozdní `dynamic`vazbou jako . V jazyce Visual Basic určíte typ objektu s pozdní vazbou jako `Object`. Další informace naleznete [v tématu dynamické](../../language-reference/builtin-types/reference-types.md) a včasné a pozdní [vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
 Vlastní dynamické objekty můžete vytvořit pomocí <xref:System.Dynamic?displayProperty=nameWithType> tříd v oboru názvů. Můžete například vytvořit <xref:System.Dynamic.ExpandoObject> a určit členy tohoto objektu za běhu. Můžete také vytvořit vlastní typ, <xref:System.Dynamic.DynamicObject> který dědí třídu. Potom můžete přepsat členy třídy <xref:System.Dynamic.DynamicObject> poskytovat dynamické funkce za běhu.  
  
 V tomto návodu budete provádět následující úkoly:  
  
- Vytvořte vlastní objekt, který dynamicky zveřejňuje obsah textového souboru jako vlastnosti objektu.  
  
- Vytvořte projekt, `IronPython` který používá knihovnu.  
  
## <a name="prerequisites"></a>Požadavky  

K dokončení tohoto návodu potřebujete [IronPython](https://ironpython.net/) pro rozhraní .NET. Přejděte na jejich [stránku pro stažení](https://ironpython.net/download/) a získejte nejnovější verzi.
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Vytvoření vlastního dynamického objektu

První projekt, který vytvoříte v tomto návodu, definuje vlastní dynamický objekt, který prohledává obsah textového souboru. Hledaný text je určen názvem dynamické vlastnosti. Pokud například určuje volající `dynamicFile.Sample`kód , vrátí dynamická třída obecný seznam řetězců, které obsahují všechny řádky ze souboru, které začínají řetězcem "Sample". Hledání nerozlišuje malá a velká písmena. Dynamická třída také podporuje dva volitelné argumenty. První argument je hodnota výčtu možnosti hledání, která určuje, že dynamická třída by měla hledat shody na začátku řádku, na konci řádku nebo kdekoli v řádku. Druhý argument určuje, že dynamická třída by měla před hledáním oříznout úvodní a koncové mezery z každého řádku. Pokud například určuje kód `dynamicFile.Sample(StringSearchOption.Contains)`volání , dynamická třída vyhledá "Vzorek" kdekoli v řádku. Pokud určuje kód `dynamicFile.Sample(StringSearchOption.StartsWith, false)`volání , dynamická třída hledá "Ukázka" na začátku každého řádku a neodstraní úvodní a koncové mezery. Výchozí chování dynamické třídy je hledání shody na začátku každého řádku a odebrání úvodních a koncových mezer.  
  
### <a name="to-create-a-custom-dynamic-class"></a>Vytvoření vlastní dynamické třídy  
  
1. Spusťte Visual Studio.  
  
2. V nabídce **Soubor** přejděte na **Nový** a potom klepněte na **položku Project**.  
  
3. V dialogovém okně **Nový projekt** zkontrolujte v podokně **Typy projektů,** zda je vybrán **systém Windows.** V podokně **Šablony** vyberte **Konzolová aplikace.** Do pole **Název** `DynamicSample`zadejte a klepněte na tlačítko **OK**. Nový projekt je vytvořen.  
  
4. Klepněte pravým tlačítkem myši na projekt DynamicSample a přejděte na **Přidat**a potom klepněte na příkaz **Třída**. Do pole **Název** `ReadOnlyFile`zadejte a klepněte na tlačítko **OK**. Je přidán nový soubor, který obsahuje třídu ReadOnlyFile.  
  
5. V horní části souboru ReadOnlyFile.cs nebo ReadOnlyFile.vb přidejte <xref:System.IO?displayProperty=nameWithType> <xref:System.Dynamic?displayProperty=nameWithType> následující kód pro import oborů názvů a.  

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]  

6. Vlastní dynamický objekt používá výčtu k určení kritérií hledání. Před příkaz třídy přidejte následující definici výčtu.  
  
    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]
  
7. Aktualizujte příkaz třídy, aby zdědil třídu, `DynamicObject` jak je znázorněno v následujícím příkladu kódu.  
  
    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8. Přidejte následující kód `ReadOnlyFile` do třídy definovat soukromé pole pro cestu `ReadOnlyFile` k souboru a konstruktor pro třídu.  
  
    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]
  
9. Do třídy `ReadOnlyFile` přidejte následující metodu `GetPropertyValue`. Metoda `GetPropertyValue` přebírá jako vstupní kritéria vyhledávání a vrací řádky z textového souboru, který odpovídá tomuto kritériu hledání. Dynamické metody poskytované třídou `ReadOnlyFile` volají `GetPropertyValue` metodu k načtení jejich příslušných výsledků.  
  
    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]  
  
10. Za `GetPropertyValue` metodu přidejte následující kód <xref:System.Dynamic.DynamicObject.TryGetMember%2A> přepsat metodu třídy. <xref:System.Dynamic.DynamicObject> Metoda <xref:System.Dynamic.DynamicObject.TryGetMember%2A> je volána, když je požadován člen dynamické třídy a nejsou zadány žádné argumenty. Argument `binder` obsahuje informace o odkazovaném `result` členu a argument odkazuje na výsledek vrácený pro zadaný člen. Metoda <xref:System.Dynamic.DynamicObject.TryGetMember%2A> vrátí logickou hodnotu, která vrátí, `true` pokud požadovaný člen existuje; v opačném `false`případě vrátí .  
  
    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]
  
11. Za `TryGetMember` metodu přidejte následující kód <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> přepsat metodu třídy. <xref:System.Dynamic.DynamicObject> Metoda <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> je volána, když je požadován člen dynamické třídy s argumenty. Argument `binder` obsahuje informace o odkazovaném `result` členu a argument odkazuje na výsledek vrácený pro zadaný člen. Argument `args` obsahuje pole argumentů, které jsou předány členu. Metoda <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> vrátí logickou hodnotu, která vrátí, `true` pokud požadovaný člen existuje; v opačném `false`případě vrátí .  
  
    Vlastní verze `TryInvokeMember` metody očekává, že první argument bude `StringSearchOption` hodnota z výčtu, který jste definovali v předchozím kroku. Metoda `TryInvokeMember` očekává, že druhý argument bude logická hodnota. Pokud jeden nebo oba argumenty jsou platné `GetPropertyValue` hodnoty, jsou předány metodě načíst výsledky.  
  
    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]
  
12. Uložte soubor a zavřete ho.  
  
#### <a name="to-create-a-sample-text-file"></a>Vytvoření ukázkového textového souboru  
  
1. Klepněte pravým tlačítkem myši na projekt DynamicSample a přejděte na **Přidat**a potom klepněte na příkaz **Nová položka**. V podokně **Nainstalované šablony** vyberte **Obecné**a pak vyberte šablonu **Textový soubor.** Ponechte výchozí název textfile1.txt v poli **Název** a klepněte na tlačítko **Přidat**. Do projektu je přidán nový textový soubor.  
  
2. Zkopírujte následující text do souboru TextFile1.txt.  
  
    ```text  
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
  
3. Uložte soubor a zavřete ho.  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>Vytvoření ukázkové aplikace, která používá vlastní dynamický objekt  
  
1. V **Průzkumníku řešení**poklepejte na soubor Module1.vb, pokud používáte visual basic nebo soubor Program.cs, pokud používáte visual c#.  
  
2. Přidejte následující kód do hlavního postupu `ReadOnlyFile` a vytvořte instanci třídy pro soubor TextFile1.txt. Kód používá pozdní vazbu k volání dynamických členů a načtení řádků textu, které obsahují řetězec "Zákazník".  
  
     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]
  
3. Uložte soubor a stisknutím kombinace kláves CTRL+F5 vytvořte a spusťte aplikaci.  
  
## <a name="calling-a-dynamic-language-library"></a>Volání dynamické jazykové knihovny  

Další projekt, který vytvoříte v tomto návodu přistupuje ke knihovně, která je zapsána v dynamickém jazyce IronPython.
  
### <a name="to-create-a-custom-dynamic-class"></a>Vytvoření vlastní dynamické třídy
  
1. V sadě Visual Studio v nabídce **Soubor** přejděte na **Nový** a potom klikněte na **Project**.  
  
2. V dialogovém okně **Nový projekt** zkontrolujte v podokně **Typy projektů,** zda je vybrán **systém Windows.** V podokně **Šablony** vyberte **Konzolová aplikace.** Do pole **Název** `DynamicIronPythonSample`zadejte a klepněte na tlačítko **OK**. Nový projekt je vytvořen.  
  
3. Pokud používáte jazyk Visual Basic, klepněte pravým tlačítkem myši na projekt DynamicIronPythonSample a potom klepněte na příkaz **Vlastnosti**. Klikněte na kartu **Reference.** Klepněte na tlačítko **Přidat.** Pokud používáte Visual C#, klikněte v **Průzkumníku řešení**pravým tlačítkem myši na složku **Reference a** potom klikněte na příkaz **Přidat odkaz**.  
  
4. Na kartě **Procházet** vyhledejte složku, ve které jsou nainstalovány knihovny IronPython. Například C:\Program Files\IronPython 2.6 pro rozhraní .NET 4.0. Vyberte knihovny **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**a **Microsoft.Dynamic.dll.** Klikněte na tlačítko **OK**.  
  
5. Pokud používáte visual basic, upravte soubor Module1.vb. Pokud používáte Visual C#, upravte soubor Program.cs.  
  
6. V horní části souboru přidejte následující `Microsoft.Scripting.Hosting` kód `IronPython.Hosting` pro import a jmenné prostory z knihoven IronPython.  
  
    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]
  
7. V Main metoda, přidejte následující kód `Microsoft.Scripting.Hosting.ScriptRuntime` k vytvoření nového objektu pro hostování IronPython knihovny. Objekt `ScriptRuntime` načte modul knihovny IronPython random.py.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]
  
8. Po kódu pro načtení random.py modulu přidejte následující kód a vytvořte pole celá čísla. Pole je předáno `shuffle` metodě random.py modulu, který náhodně seřadí hodnoty v poli.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]
  
9. Uložte soubor a stisknutím kombinace kláves CTRL+F5 vytvořte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [Použití typu dynamic](./using-type-dynamic.md)
- [Statické a dynamické vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Dynamické](../../language-reference/builtin-types/reference-types.md)
- [Implementace dynamických rozhraní (pdf ke stažení z webu Microsoft TechNet)](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
