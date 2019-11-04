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
ms.openlocfilehash: aa902ffaf93c8e1f273ed476dc7d413bcfce914c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417579"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>Postupy: Vytváření a používání dynamických objektů (C# a Visual Basic)

Dynamické objekty zveřejňují členy, jako jsou vlastnosti a metody v době běhu, místo v době kompilace. To umožňuje vytvářet objekty pro práci se strukturami, které neodpovídají statickému typu nebo formátu. Například můžete použít dynamický objekt pro odkaz na model DOM (Document Object Model) HTML (DOM), který může obsahovat libovolnou kombinaci platných elementů a atributů HTML značek. Vzhledem k tomu, že každý dokument HTML je jedinečný, jsou členy pro konkrétní dokument HTML určeny za běhu. Společná metoda, která odkazuje na atribut prvku jazyka HTML, je předat název atributu metodě `GetProperty` elementu. Chcete-li odkazovat na atribut `id` elementu HTML `<div id="Div1">`, nejprve získejte odkaz na prvek `<div>` a pak použijte `divElement.GetProperty("id")`. Použijete-li dynamický objekt, můžete odkazovat na atribut `id` jako `divElement.id`.  
  
 Dynamické objekty také poskytují pohodlný přístup k dynamickým jazykům, jako jsou Ironpythonu a IronRuby. Můžete použít dynamický objekt pro odkazování na dynamický skript, který je interpretován v době běhu.  
  
 Můžete odkazovat na dynamický objekt pomocí pozdní vazby. V C#zadejte typ objektu s pozdní vazbou jako `dynamic`. V Visual Basic zadáte typ pozdní vázaného objektu jako `Object`. Další informace najdete v tématu [Dynamická](../../language-reference/builtin-types/reference-types.md) a [časná a pozdní vazba](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
 Vlastní dynamické objekty lze vytvořit pomocí tříd v oboru názvů <xref:System.Dynamic?displayProperty=nameWithType>. Můžete například vytvořit <xref:System.Dynamic.ExpandoObject> a určit členy daného objektu v době běhu. Můžete také vytvořit vlastní typ, který dědí třídu <xref:System.Dynamic.DynamicObject>. Pak můžete přepsat členy třídy <xref:System.Dynamic.DynamicObject>, aby poskytovaly dynamické funkce modulu runtime.  
  
 V tomto návodu budete provádět následující úlohy:  
  
- Vytvořte vlastní objekt, který dynamicky zveřejňuje obsah textového souboru jako vlastnosti objektu.  
  
- Vytvořte projekt, který používá knihovnu `IronPython`.  
  
## <a name="prerequisites"></a>Požadavky  

K dokončení tohoto Názorného postupu potřebujete [ironpythonu](https://ironpython.net/) pro .NET. Nejnovější verzi získáte tak, že přejdete na [stránku pro stažení](https://ironpython.net/download/) .
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Vytvoření vlastního dynamického objektu

První projekt, který vytvoříte v tomto návodu, definuje vlastní dynamický objekt, který vyhledá obsah textového souboru. Text, který se má hledat, je určený názvem dynamické vlastnosti. Například pokud volání kódu určuje `dynamicFile.Sample`, dynamická třída vrátí obecný seznam řetězců, které obsahují všechny řádky ze souboru, který začíná "Sample". Při hledání se nerozlišují malá a velká písmena. Dynamická třída také podporuje dva nepovinné argumenty. První argument je hodnota výčtu možnosti vyhledávání, která určuje, že Dynamická třída by měla vyhledat shody na začátku řádku, na konci řádku nebo kdekoli na řádku. Druhý argument určuje, že Dynamická třída by měla před vyhledáváním oříznout úvodní a koncové mezery z každého řádku. Například pokud volání kódu určuje `dynamicFile.Sample(StringSearchOption.Contains)`, dynamická třída vyhledá "Sample" kdekoli na řádku. Pokud volání Code určuje `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, dynamická třída vyhledá "Sample" na začátku každého řádku a neodstraní úvodní a koncové mezery. Výchozím chováním dynamické třídy je vyhledat shodu na začátku každého řádku a odebrat úvodní a koncové mezery.  
  
### <a name="to-create-a-custom-dynamic-class"></a>Vytvoření vlastní dynamické třídy  
  
1. Spusťte Visual Studio.  
  
2. V nabídce **soubor** přejděte na příkaz **Nový** a klikněte na **projekt**.  
  
3. V dialogovém okně **Nový projekt** v podokně **typy projektů** se ujistěte, že je vybrána možnost **Windows** . V podokně **šablony** vyberte **Konzolová aplikace** . Do pole **název** zadejte `DynamicSample`a pak klikněte na **OK**. Vytvoří se nový projekt.  
  
4. Klikněte pravým tlačítkem na projekt DynamicSample a přejděte na **Přidat**a pak klikněte na **Třída**. Do pole **název** zadejte `ReadOnlyFile`a pak klikněte na **OK**. Přidá se nový soubor, který obsahuje třídu ReadOnlyFile.  
  
5. V horní části souboru ReadOnlyFile.cs nebo ReadOnlyFile. vb přidejte následující kód, který importuje obory názvů <xref:System.IO?displayProperty=nameWithType> a <xref:System.Dynamic?displayProperty=nameWithType>.  

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]  

6. Vlastní dynamický objekt používá výčet k určení kritérií vyhledávání. Před příkazem třídy přidejte následující definici výčtu.  
  
    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]
  
7. Aktualizujte příkaz Class tak, aby dědil třídu `DynamicObject`, jak je znázorněno v následujícím příkladu kódu.  
  
    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8. Přidejte následující kód do třídy `ReadOnlyFile` pro definování soukromého pole pro cestu k souboru a konstruktor pro třídu `ReadOnlyFile`.  
  
    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]
  
9. Do `ReadOnlyFile` třídy přidejte následující metodu `GetPropertyValue`. Metoda `GetPropertyValue` přijímá jako vstup kritéria hledání a vrací řádky z textového souboru, které odpovídají kritériím vyhledávání. Dynamické metody, které poskytuje třída `ReadOnlyFile`, volají metodu `GetPropertyValue` k načtení příslušných výsledků.  
  
    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]  
  
10. Po `GetPropertyValue` metody přidejte následující kód pro přepsání metody <xref:System.Dynamic.DynamicObject.TryGetMember%2A> třídy <xref:System.Dynamic.DynamicObject>. Metoda <xref:System.Dynamic.DynamicObject.TryGetMember%2A> je volána, když je požadován člen dynamické třídy a nejsou zadány žádné argumenty. Argument `binder` obsahuje informace o odkazovaném členu a argument `result` odkazuje na výsledek vráceného pro zadaného člena. Metoda <xref:System.Dynamic.DynamicObject.TryGetMember%2A> vrací logickou hodnotu, která vrátí `true`, pokud požadovaný člen existuje; v opačném případě vrátí `false`.  
  
    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]
  
11. Po `TryGetMember` metody přidejte následující kód pro přepsání metody <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> třídy <xref:System.Dynamic.DynamicObject>. Metoda <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> se volá, když se na argumentu žádá člen dynamické třídy. Argument `binder` obsahuje informace o odkazovaném členu a argument `result` odkazuje na výsledek vráceného pro zadaného člena. Argument `args` obsahuje pole argumentů, které jsou předány členu. Metoda <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> vrací logickou hodnotu, která vrátí `true`, pokud požadovaný člen existuje; v opačném případě vrátí `false`.  
  
    Vlastní verze `TryInvokeMember` metoda očekává, že první argument bude hodnota z výčtu `StringSearchOption`, který jste definovali v předchozím kroku. Metoda `TryInvokeMember` očekává, že druhý argument bude logická hodnota. Pokud jsou jeden nebo oba argumenty platné hodnoty, jsou předány metodě `GetPropertyValue` pro načtení výsledků.  
  
    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]
  
12. Soubor uložte a zavřete.  
  
#### <a name="to-create-a-sample-text-file"></a>Vytvoření ukázkového textového souboru  
  
1. Klikněte pravým tlačítkem na projekt DynamicSample, přejděte na **Přidat**a klikněte na **Nová položka**. V podokně **Nainstalované šablony** vyberte **Obecné**a potom vyberte šablonu **textový soubor** . V poli **název** ponechte výchozí název TextFile1. txt a pak klikněte na **Přidat**. Do projektu se přidá nový textový soubor.  
  
2. Zkopírujte následující text do souboru TextFile1. txt.  
  
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
  
3. Soubor uložte a zavřete.  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>Vytvoření ukázkové aplikace, která používá vlastní dynamický objekt  
  
1. V **Průzkumník řešení**dvakrát klikněte na soubor Module1. vb, pokud používáte Visual Basic nebo soubor program.cs, pokud používáte vizuál C#.  
  
2. Do hlavní procedury přidejte následující kód, který vytvoří instanci třídy `ReadOnlyFile` pro soubor TextFile1. txt. Kód používá pozdní vazbu k volání dynamických členů a načítají řádky textu, které obsahují řetězec "Customer".  
  
     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]
  
3. Uložte soubor a stisknutím kombinace kláves CTRL + F5 Sestavte a spusťte aplikaci.  
  
## <a name="calling-a-dynamic-language-library"></a>Volání knihovny dynamického jazyka  

Následující projekt, který vytvoříte v tomto návodu, přistupuje k knihovně, která je napsaná v dynamické jazykové Ironpythonu.
  
### <a name="to-create-a-custom-dynamic-class"></a>Vytvoření vlastní dynamické třídy
  
1. V aplikaci Visual Studio v nabídce **soubor** přejděte na možnost **Nový** a poté klikněte na položku **projekt**.  
  
2. V dialogovém okně **Nový projekt** v podokně **typy projektů** se ujistěte, že je vybrána možnost **Windows** . V podokně **šablony** vyberte **Konzolová aplikace** . Do pole **název** zadejte `DynamicIronPythonSample`a pak klikněte na **OK**. Vytvoří se nový projekt.  
  
3. Pokud používáte Visual Basic, klikněte pravým tlačítkem na projekt DynamicIronPythonSample a pak klikněte na **vlastnosti**. Klikněte na kartu **odkazy** . klikněte na tlačítko **Přidat** . C#Pokud používáte vizuál, klikněte v **Průzkumník řešení**pravým tlačítkem myši na složku **odkazy** a pak klikněte na **Přidat odkaz**.  
  
4. Na kartě **Procházet** přejděte do složky, ve které jsou nainstalované knihovny ironpythonu. Například C:\Program Files\IronPython 2,6 pro .NET 4,0. Vyberte knihovny **ironpythonu. dll**, **ironpythonu. Modules. dll**, **Microsoft. Scripting. dll**a **Microsoft. Dynamic. dll** . Klikněte na tlačítko **OK**.  
  
5. Pokud používáte Visual Basic, upravte soubor Module1. vb. Pokud používáte vizuál C#, upravte soubor program.cs.  
  
6. V horní části souboru přidejte následující kód, který importuje `Microsoft.Scripting.Hosting` a `IronPython.Hosting` obory názvů z knihoven Ironpythonu.  
  
    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]
  
7. Do metody Main přidejte následující kód, který vytvoří nový objekt `Microsoft.Scripting.Hosting.ScriptRuntime` pro hostování knihoven Ironpythonu. Objekt `ScriptRuntime` načte modul random.py knihovny Ironpythonu.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]
  
8. Poté, co kód načte modul random.py, přidejte následující kód pro vytvoření pole celých čísel. Pole je předáno metodě `shuffle` modulu random.py, která náhodně seřadí hodnoty v poli.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]
  
9. Uložte soubor a stisknutím kombinace kláves CTRL + F5 Sestavte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [Použití typu dynamic](./using-type-dynamic.md)
- [Statické a dynamické vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Implementace dynamických rozhraní (ke stažení PDF z webu Microsoft TechNet)](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
