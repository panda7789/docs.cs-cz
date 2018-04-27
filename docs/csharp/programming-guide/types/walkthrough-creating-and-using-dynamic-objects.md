---
title: 'Postupy: Vytváření a používání dynamických objektů (C# a Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16c08ff42ce77b3901f5909571c528394d139e03
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>Postupy: Vytváření a používání dynamických objektů (C# a Visual Basic)

Dynamické objekty vystavit členy například vlastnosti a metody za běhu, místo v při kompilaci. To umožňuje vytvářet objekty pro práci s struktury, které neodpovídají statický typ nebo formát. Můžete například použít dynamický objekt tak, aby odkazovaly HTML modelu DOM (Document Object), která může obsahovat libovolnou kombinaci platný elementů značek HTML a atributů. Protože každý dokument HTML je jedinečný, členy u konkrétního dokumentu HTML určuje za běhu. Běžnou metodou k odkazovat na atribut elementu HTML je předat název atributu `GetProperty` metoda elementu. Odkazy `id` atribut elementu HTML `<div id="Div1">`, nejprve získat odkaz na `<div>` element a pak použijte `divElement.GetProperty("id")`. Pokud chcete použít dynamický objekt, můžete odkazovat `id` atribut jako `divElement.id`.  
  
 Dynamické objekty také poskytují pohodlný přístup k dynamické jazyků, například IronPython a IronRuby. Dynamický objekt můžete použít k odkazování na dynamické skript, který je považován za běhu.  
  
 Odkazování na dynamický objekt s použitím pozdní vazba. V jazyce C#, zadejte typ objektu pozdní vazbou jako `dynamic`. V jazyce Visual Basic, zadejte typ objektu pozdní vazbou jako `Object`. Další informace najdete v tématu [dynamické](../../../csharp/language-reference/keywords/dynamic.md) a [Early a pozdní vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
 Můžete vytvořit vlastní dynamických objektů pomocí třídy v <xref:System.Dynamic?displayProperty=nameWithType> oboru názvů. Například můžete vytvořit <xref:System.Dynamic.ExpandoObject> a zadejte členy tohoto objektu v době běhu. Můžete také vytvořit vlastní typ, který dědí <xref:System.Dynamic.DynamicObject> třídy. Potom můžete přepsat členů <xref:System.Dynamic.DynamicObject> třídy poskytují spuštění dynamické funkce.  
  
 V tomto návodu budete provádět následující úlohy:  
  
-   Vytvořte vlastní objekt, který dynamicky zpřístupní obsah textového souboru jako vlastnosti objektu.  
  
-   Vytvořit projekt, který se používá `IronPython` knihovny.  
  
## <a name="prerequisites"></a>Požadavky  
Je třeba [IronPython](http://ironpython.net/) pro .NET pro dokončení tohoto návodu. Přejděte na jejich [stránky pro stažení](http://ironpython.net/download/) získat nejnovější verzi.
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Vytváření vlastních dynamických objektů  
 První projekt, který vytvoříte v tomto názorném postupu definuje vlastní dynamický objekt, který vyhledá obsah textového souboru. Hledaný text je zadán název dynamických vlastností. Například pokud volání kódu určuje `dynamicFile.Sample`, dynamické třídy vrátí obecné seznam řetězců, které obsahuje všechny řádky ze souboru, které začínají řetězcem "Ukázkový". Vyhledávání nerozlišuje velká a malá písmena. Dynamické třída také podporuje dva volitelné argumenty. První argument je hodnota výčtu možnost vyhledávání, která určuje třídu dynamické program hledat odpovídá na začátku řádku, koncem řádku, nebo kdekoli v řádku. Druhý argument určuje, že by měl dynamické třídy trim úvodní i koncové mezery z každého řádku před vyhledáváním. Například pokud volání kódu určuje `dynamicFile.Sample(StringSearchOption.Contains)`, dynamické třídy hledá "Ukázkový" kdekoli v řádku. Pokud volání kódu určuje `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, dynamické Třída hledá "Ukázkový" na začátku každého řádku a neodebere úvodní i koncové mezery. Výchozí chování dynamické třídy je chcete vyhledávat shodu na začátku každého řádku a odebrat úvodní i koncové mezery.  
  
#### <a name="to-create-a-custom-dynamic-class"></a>Chcete-li vytvořit vlastní dynamické – třída  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.  
  
3.  V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána. Vyberte **konzolové aplikace** v **šablony** podokně. V **název** zadejte `DynamicSample`a potom klikněte na **OK**. Vytvoření nového projektu.  
  
4.  Klikněte pravým tlačítkem na projekt DynamicSample a přejděte na **přidat**a potom klikněte na **třída**. V **název** zadejte `ReadOnlyFile`a potom klikněte na **OK**. Která obsahuje třídu ReadOnlyFile přidán nový soubor.  
  
5.  V horní části souboru ReadOnlyFile.cs nebo ReadOnlyFile.vb, přidejte následující kód k importu <xref:System.IO?displayProperty=nameWithType> a <xref:System.Dynamic?displayProperty=nameWithType> obory názvů.  
  
     [!code-csharp[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_1.cs)]

     [!code-vb[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_1.vb)]  
  
6.  Vlastní dynamický objekt výčet používá k určení kritérií vyhledávání. Před příkazem třídy přidejte následující definice výčtu.  
  
     [!code-csharp[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_2.cs)]

     [!code-vb[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_2.vb)]  
  
7.  Aktualizovat Class – příkaz dědění `DynamicObject` třídy, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_3.cs)]

     [!code-vb[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_3.vb)]  
  
8.  Přidejte následující kód, který `ReadOnlyFile` třída zadat soukromé pole pro cestu k souboru a konstruktor pro `ReadOnlyFile` – třída.  
  
     [!code-csharp[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_4.cs)]
     
     [!code-vb[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_4.vb)]  
  
9. Přidejte následující `GetPropertyValue` metodu `ReadOnlyFile` třídy. `GetPropertyValue` Metoda přebírá jako vstup, kritéria hledání a vrátí řádky z textového souboru, které odpovídají, který vyhledávací kritéria. Dynamické metody poskytované `ReadOnlyFile` třídy volání `GetPropertyValue` metoda pro načtení jejich odpovídajících výsledků.  
  
     [!code-csharp[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_5.cs)]
     
     [!code-vb[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_5.vb)]  
  
10. Po `GetPropertyValue` metoda, přidejte následující kód k přepsání <xref:System.Dynamic.DynamicObject.TryGetMember%2A> metodu <xref:System.Dynamic.DynamicObject> třídy. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Metoda je volána, když je požadován členem dynamické třídy a nejsou zadány žádné argumenty. `binder` Argument obsahuje informace o odkazované člen a `result` argument odkazuje výsledek vrácený pro zadaného člena. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Metoda vrací logickou hodnotu, která vrací `true` Pokud požadovaný člena existuje; jinak vrátí `false`.  
  
     [!code-csharp[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_6.cs)]
     
     [!code-vb[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_6.vb)]  
  
11. Po `TryGetMember` metoda, přidejte následující kód k přepsání <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> metodu <xref:System.Dynamic.DynamicObject> třídy. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Metoda je volána, pokud se požaduje členem dynamické třídy s argumenty. `binder` Argument obsahuje informace o odkazované člen a `result` argument odkazuje výsledek vrácený pro zadaného člena. `args` Argument obsahuje pole argumentů, které se předávají do člena. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Metoda vrací logickou hodnotu, která vrací `true` Pokud požadovaný člena existuje; jinak vrátí `false`.  
  
     Vlastní verzi `TryInvokeMember` metoda očekává se hodnota z první argument `StringSearchOption` výčet, který jste zadali v předchozím kroku. `TryInvokeMember` Metoda očekává druhý argument jako logická hodnota. Pokud jeden nebo oba argumenty jsou platné hodnoty, že jsou předány `GetPropertyValue` metoda načíst výsledky.  
  
     [!code-csharp[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_7.cs)]
     
     [!code-vb[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_7.vb)]  
  
12. Soubor uložte a zavřete.  
  
#### <a name="to-create-a-sample-text-file"></a>Chcete-li vytvořit ukázkový textový soubor  
  
1.  Klikněte pravým tlačítkem na projekt DynamicSample a přejděte na **přidat**a potom klikněte na **novou položku**. V **nainstalovaných šablonách** podokně, vyberte **Obecné**a pak vyberte **textový soubor** šablony. Ponechte výchozí název soubory TextFile1.txt v **název** pole a pak klikněte na **přidat**. Nový textový soubor se přidá do projektu.  
  
2.  Zkopírujte následující text do souboru soubory TextFile1.txt.  
  
    ```  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (http://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (http://www.graphicdesigninstitute.com/)   
    Supplier: Fabrikam, Inc. (http://www.fabrikam.com/)   
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)   
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3.  Soubor uložte a zavřete.  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>K vytvoření ukázkové aplikace, která používá vlastní dynamických objektů  
  
1.  V **Průzkumníku**, poklikejte na soubor Module1.vb, pokud používáte Visual Basic nebo souboru Program.cs Pokud používáte Visual C#.  
  
2.  Přidejte následující kód do hlavní postup vytvoření instance `ReadOnlyFile` třídu pro soubory TextFile1.txt souboru. Kód používá pozdní vazba volání dynamické členy a načtení řádků textu, které obsahují řetězec "Zákazník".  
  
     [!code-csharp[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_8.cs)]
     
     [!code-vb[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_8.vb)]  
  
3.  Uložte soubor a stiskněte klávesu CTRL + F5 sestavení a spuštění aplikace.  
  
## <a name="calling-a-dynamic-language-library"></a>Volání metody knihovnu Dynamic Language  

Další projekt, který vytvoříte v tomto návodu přistupuje k knihovny, která se píšou v jazyce dynamické IronPython.
  
#### <a name="to-create-a-custom-dynamic-class"></a>Chcete-li vytvořit vlastní dynamické – třída  
  
1.  V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.  
  
2.  V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána. Vyberte **konzolové aplikace** v **šablony** podokně. V **název** zadejte `DynamicIronPythonSample`a potom klikněte na **OK**. Vytvoření nového projektu.  
  
3.  Pokud používáte Visual Basic, klikněte pravým tlačítkem na projekt DynamicIronPythonSample a pak klikněte na **vlastnosti**. Klikněte **odkazy** kartě. Klikněte **přidat** tlačítko. Pokud používáte Visual C#, v **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** složku a pak klikněte na tlačítko **přidat odkaz na**.  
  
4.  Na **Procházet** kartě, přejděte do složky, kde jsou nainstalovány knihovny IronPython. Například C:\Program pro rozhraní .NET 4.0 2.6 Files\IronPython. Vyberte **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**, a **Microsoft.Dynamic.dll** knihovny . Click **OK**.  
  
5.  Pokud používáte Visual Basic, upravte soubor Module1.vb. Pokud používáte Visual C#, upravte soubor Program.cs.  
  
6.  Na začátek souboru přidejte následující kód k importu `Microsoft.Scripting.Hosting` a `IronPython.Hosting` obory názvů v IronPython knihovny.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_9.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_9.vb)]  
  
7.  V metodě hlavní, přidejte následující kód pro vytvoření nového `Microsoft.Scripting.Hosting.ScriptRuntime` objektu k hostování IronPython knihovny. `ScriptRuntime` Objekt načte random.py IronPython knihovna modulu.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_10.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_10.vb)]  
  
8.  Za kód pro načtení modulu random.py přidejte následující kód k vytvoření pole celých čísel. Toto pole je předána `shuffle` metoda random.py modul, kterým náhodně seřadí hodnoty v poli.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_11.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_11.vb)]  
  
9. Uložte soubor a stiskněte klávesu CTRL + F5 sestavení a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Dynamic?displayProperty=nameWithType>  
 <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
 [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Statické a dynamické vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Implementace rozhraní dynamické (ke stažení PDF z Microsoft TechNet)](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
