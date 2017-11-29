---
title: "Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 360b453b2a25b6822485f18cc81cb43e313949eb
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku
Tento návod ukazuje, jak vytvořit vlastní uživatelský ovládací prvek, které mohou být zahrnuty v přenos dat se přetažení myší v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 V tomto návodu vytvoříte vlastní WPF <xref:System.Windows.Controls.UserControl> představující obrazce kruh. Funkce se implementovat v ovládacím prvku povolit přenos dat pomocí přetahování myší. Například přetažením z jednoho kruh ovládacího prvku do jiného data barvu výplně se zkopíruje ze zdroje kruh k cíli. Přetažením z ovládacího prvku kruh k <xref:System.Windows.Controls.TextBox>, řetězcovou reprezentaci barvu výplně se zkopíruje do <xref:System.Windows.Controls.TextBox>. Také vytvoříte malé aplikaci, která obsahuje dva ovládací prvky panelu a <xref:System.Windows.Controls.TextBox> funkci přetažení myší. Budete psát kód, který umožňuje panelů zpracovat vynechaných kruh data, která vám umožní přesuňte nebo zkopírujte kroužky z podřízené kolekce jednoho z nich na druhý.  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Vytvoření vlastního uživatelského ovládacího prvku.  
  
-   Povolte uživatelského ovládacího prvku jako zdroje operace přetažení.  
  
-   Povolte uživatelského ovládacího prvku jako cíle přetažení.  
  
-   Povolte panel přijímat data z uživatelského ovládacího prvku.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Visual Studio 2010  
  
## <a name="creating-the-application-project"></a>Vytvoření projektu aplikace  
 V této části vytvoříte infrastrukturu aplikace, která zahrnuje na hlavní stránce s dvěma panelů a <xref:System.Windows.Controls.TextBox>.  
  
### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte nový projekt aplikace WPF v jazyce Visual Basic a Visual C# s názvem `DragDropExample`. Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  Otevřete MainWindow.xaml.  
  
3.  Přidejte následující kód mezi počáteční a koncovou <xref:System.Windows.Controls.Grid> značky.  
  
     Tento kód vytvoří uživatelské rozhraní pro testovací aplikace.  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a>Přidávání nového uživatele do projektu  
 V této části přidáte nový uživatelský ovládací prvek do projektu.  
  
### <a name="to-add-a-new-user-control"></a>Chcete-li přidat nový uživatelský ovládací prvek  
  
1.  V nabídce Projekt, vyberte **přidat uživatelský ovládací prvek**.  
  
2.  V dialogovém okně Přidat novou položku změňte název `Circle.xaml`a klikněte na tlačítko **přidat**.  
  
     Circle.XAML a jeho kódu se přidá do projektu.  
  
3.  Otevřete Circle.xaml.  
  
     Tento soubor bude obsahovat prvky uživatelského rozhraní uživatelského ovládacího prvku.  
  
4.  Přidejte následující kód do kořenového adresáře <xref:System.Windows.Controls.Grid> vytvoření jednoduché uživatelského ovládacího prvku, který má modrý kruh jako jeho uživatelském rozhraní.  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
6.  V jazyce C# přidejte následující kód po výchozí konstruktor k vytvoření kopírovacího konstruktoru. V jazyce Visual Basic přidejte následující kód k vytvoření výchozí konstruktor a kopírovacího konstruktoru.  
  
     Chcete-li povolit uživatelský ovládací prvek, který se má zkopírovat, přidejte metodu konstruktoru kopírování v souboru kódu na pozadí. V zjednodušené kruh uživatelského ovládacího prvku, pouze zkopírujete výplně a velikost uživatelského ovládacího prvku.  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a>Chcete-li přidat uživatelský ovládací prvek do hlavního okna  
  
1.  Otevřete MainWindow.xaml.  
  
2.  Přidejte následující XAML pro otevření <xref:System.Windows.Window> značka vytvořit odkaz na obor názvů XML pro aktuální aplikaci.  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  V prvním <xref:System.Windows.Controls.StackPanel>, přidejte následující XAML vytvořit dvě instance kruh uživatelského ovládacího prvku v prvním panelu.  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     Úplné XAML pro panel vypadá takto.  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a>Implementace události zdroje přetažení z uživatelského ovládacího prvku  
 V této části se přepíše <xref:System.Windows.UIElement.OnMouseMove%2A> metoda a spustit operaci přetažení myší.  
  
 Pokud je spuštěná přetáhněte (stisknutí tlačítka myši a myší), bude balíček data, která mají být převedeny do <xref:System.Windows.DataObject>. V takovém případě bude ovládací prvek kruh balíček tři položky data; řetězcová reprezentace jeho barvu výplně, double reprezentace výšku a kopii sám sebe.  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a>Inicializace operace přetažení myší  
  
1.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
2.  Přidejte následující <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.MouseMove> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     To <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání provede následující úlohy:  
  
    -   Kontroluje, zda je levé tlačítko stisknutí při přesunutí myši.  
  
    -   Balíčky kruh dat do <xref:System.Windows.DataObject>. V takovém případě ovládacího prvku kruh balíčky tři položky data; řetězcová reprezentace jeho barvu výplně, double reprezentace výšku a kopii sám sebe.  
  
    -   Volá statických <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metoda inicializace operace přetažení myší. Předejte tyto tři parametry, které chcete <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda:  
  
        -   `dragSource`– Odkaz na tento ovládací prvek.  
  
        -   `data`– Na <xref:System.Windows.DataObject> vytvořené v předchozí kód.  
  
        -   `allowedEffects`– Povolených operací přetažení myší, které jsou <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.  
  
3.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
4.  Klikněte na jednu z ovládacích prvků kruh a přetáhněte jej přes na panely na kruh a <xref:System.Windows.Controls.TextBox>. Při přetažení přes <xref:System.Windows.Controls.TextBox>, změní na znamenat přesunu.  
  
5.  Při přetahování kruh přes <xref:System.Windows.Controls.TextBox>, stiskněte klávesu CTRL. Všimněte si, jak kurzoru změní udávajících kopii.  
  
6.  Přetáhnout myší na kruh <xref:System.Windows.Controls.TextBox>. Řetězcová reprezentace barvu výplně na kruh se připojí k <xref:System.Windows.Controls.TextBox>.  
  
     ![Řetězec reprezentace barvu výplně kruhu](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")  
  
 Ve výchozím nastavení bude během operace přetažení myší označíte, jaký vliv má vyřazení dat bude mít změnit kurzor. Můžete přizpůsobit zpětnou vazbu pro uživatele ve zpracování <xref:System.Windows.UIElement.GiveFeedback> událostí a nastavení různých kurzoru.  
  
### <a name="to-give-feedback-to-the-user"></a>Poskytněte zpětnou vazbu pro uživatele  
  
1.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
2.  Přidejte následující <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.GiveFeedback> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     To <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání provede následující úlohy:  
  
    -   Kontroluje <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnoty, které jsou nastaveny v cíle přetažení <xref:System.Windows.UIElement.DragOver> obslužné rutiny události.  
  
    -   Nastaví vlastní kurzor na základě <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnotu. Kurzor je určený pro váš názor visual uživateli o jaký vliv má vyřazení dat bude mít.  
  
3.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
4.  Přetáhněte jeden kruhu určuje přes na panely na kruh a <xref:System.Windows.Controls.TextBox>. Všimněte si, že kurzory jsou nyní vlastní kurzory, které jste zadali v <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsat.  
  
     ![Přetáhnout myší s vlastní kurzory](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")  
  
5.  Vyberte text `green` z <xref:System.Windows.Controls.TextBox>.  
  
6.  Přetáhněte `green` text do ovládacího prvku kruh. Všimněte si, že se zobrazují kurzory výchozí znamenat důsledky operaci přetažení myší. Kurzor zpětná vazba je vždycky nastavený podle zdroje operace přetažení.  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a>Implementace cíl události v uživatelského ovládacího prvku  
 V této části zadáte, zda je uživatelského ovládacího prvku cíle přetažení, přepsání metody, které umožní uživateli řídit jako cíle přetažení a zpracovat data, která je na něm vyřazen.  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Chcete-li povolit uživatelského ovládacího prvku jako cíle přetažení  
  
1.  Otevřete Circle.xaml.  
  
2.  Při otevírání <xref:System.Windows.Controls.UserControl> značky, přidejte <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost a nastavte ji na `true`.  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <xref:System.Windows.UIElement.OnDrop%2A> Metoda je volána, když <xref:System.Windows.UIElement.AllowDrop%2A> je nastavena na `true` a data ze zdroje operace přetažení přetažení na kruh uživatelského ovládacího prvku. Tato metoda bude zpracovávat data, která byla vynechána a použít data na kruh.  
  
### <a name="to-process-the-dropped-data"></a>Zpracování vynechaných dat  
  
1.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
2.  Přidejte následující <xref:System.Windows.UIElement.OnDrop%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.Drop> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     To <xref:System.Windows.UIElement.OnDrop%2A> přepsání provede následující úlohy:  
  
    -   Používá <xref:System.Windows.DataObject.GetDataPresent%2A> metodu za účelem zjištění, zda taženou dat obsahuje objekt řetězce.  
  
    -   Používá <xref:System.Windows.DataObject.GetData%2A> metoda extrahovat data řetězec, pokud je k dispozici.  
  
    -   Používá <xref:System.Windows.Media.BrushConverter> pokusí převést řetězec, který má <xref:System.Windows.Media.Brush>.  
  
    -   Pokud převod úspěšný, použije štětce k <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> , který poskytuje uživatelské rozhraní ovládacího prvku kruh.  
  
    -   Značky <xref:System.Windows.UIElement.Drop> událostí jako zpracování. Událost umístění byste měli označit jako zpracování, další prvky, které obdrží tato událost věděli, že uživatelského ovládacího prvku kruh zajistit jeho.  
  
3.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
4.  Vyberte text `green` v <xref:System.Windows.Controls.TextBox>.  
  
5.  Přetáhněte text do ovládacího prvku kruh a umístěte jej. Kruhu změní z blue zeleně.  
  
     ![Převést řetězec na štětce](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")  
  
6.  Zadejte text `green` v <xref:System.Windows.Controls.TextBox>.  
  
7.  Vyberte text `gre` v <xref:System.Windows.Controls.TextBox>.  
  
8.  Přetáhněte ji do ovládacího prvku kruh a umístěte jej. Všimněte si, že kurzoru změní na znamenat, že rozevírací je povoleno, ale barvu kruhu nezmění, protože `gre` není platnou barvu.  
  
9. Z ovládacího prvku zelená kruh přetažení na modré ovládacího prvku kruh. Kruhu změní z blue zeleně. Všimněte si, že se zobrazí které kurzor závisí na tom, zda <xref:System.Windows.Controls.TextBox> nebo kruhu zdroje operace přetažení.  
  
 Nastavení <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost `true` a zpracování vynechaných dat je všechno, co je potřeba povolit element jako cíle přetažení. Však zajistit lepší uživatelské prostředí, můžete také zpracovávat <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, a <xref:System.Windows.UIElement.DragOver> události. V těchto událostí můžete provést kontroly a poskytnout další zpětnou vazbu pro uživatele předtím, než je vyřazeno data.  
  
 Při přetažení dat nad kruh uživatelského ovládacího prvku, oznámí ovládacího prvku zdroje operace přetažení jestli může zpracovat data, která je právě přetáhli. Pokud ovládací prvek nebude vědět, jak zpracování dat, by měl odmítnout rozevíracího. K tomuto účelu bude zpracovávat <xref:System.Windows.UIElement.DragOver> událostí a sadu <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost.  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a>Chcete-li ověřit, že data vyřadit je povoleno  
  
1.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
2.  Přidejte následující <xref:System.Windows.UIElement.OnDragOver%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.DragOver> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     To <xref:System.Windows.UIElement.OnDragOver%2A> přepsání provede následující úlohy:  
  
    -   Nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.None>.  
  
    -   Provede stejnou kontroly, které se provádějí v <xref:System.Windows.UIElement.OnDrop%2A> metoda k určení, zda uživatelský ovládací prvek kruh může zpracovat taženou data.  
  
    -   Pokud uživatelského ovládacího prvku může zpracovat data, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.  
  
3.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
4.  Vyberte text `gre` v <xref:System.Windows.Controls.TextBox>.  
  
5.  Přetáhněte text do ovládacího prvku kruh. Všimněte si, že kurzor nyní změny znamenat, že rozevírací není povolená, protože `gre` není platnou barvu.  
  
 Činnost koncového uživatele můžete dále vylepšit použitím náhled operace vyřazení. Pro uživatelský ovládací prvek kruh se přepíše <xref:System.Windows.UIElement.OnDragEnter%2A> a <xref:System.Windows.UIElement.OnDragLeave%2A> metody. Když je přetáhnout data přes ovládací prvek na aktuální pozadí <xref:System.Windows.Shapes.Shape.Fill%2A> je uložené v proměnné zástupný symbol. Řetězec je pak převést na štětce a použít <xref:System.Windows.Shapes.Ellipse> na kruh, který poskytuje uživatelské rozhraní. Pokud data ocitne mimo kruhu bez vyřazována původní <xref:System.Windows.Shapes.Shape.Fill%2A> kruhu je znovu použita hodnota.  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Zobrazte náhled důsledky operaci přetažení myší  
  
1.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
2.  Ve třídě kruh deklarovat privátního <xref:System.Windows.Media.Brush> proměnné s názvem `_previousFill` a inicializujte ho, aby `null`.  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  Přidejte následující <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.DragEnter> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     To <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání provede následující úlohy:  
  
    -   Uloží <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost <xref:System.Windows.Shapes.Ellipse> v `_previousFill` proměnné.  
  
    -   Provede stejnou kontroly, které se provádějí v <xref:System.Windows.UIElement.OnDrop%2A> metoda k určení, zda lze převést data na <xref:System.Windows.Media.Brush>.  
  
    -   Pokud data jsou převedeny na platnou <xref:System.Windows.Media.Brush>, použije ji k <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse>.  
  
4.  Přidejte následující <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.DragLeave> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     To <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání provede následující úlohy:  
  
    -   Platí <xref:System.Windows.Media.Brush> uloženy ve `_previousFill` proměnnou <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> , který poskytuje uživatelské rozhraní kruh uživatelského ovládacího prvku.  
  
5.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
6.  Vyberte text `green` v <xref:System.Windows.Controls.TextBox>.  
  
7.  Přetáhněte text přes ovládacího prvku kruh bez vyřadíte. Kruhu změní z blue zeleně.  
  
     ![Náhled důsledky přetáhněte & č. 45; a & č. 45; operace odstranění](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")  
  
8.  Přetáhněte text z ovládacího prvku kruh. Kruhu změní z zelená zpět na modrou.  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a>Povolení panelu přijímat vyřadit dat  
 V této části povolíte panely, které jsou hostiteli uživatelské ovládací prvky kruh tak, aby fungoval jako cílů přemístění dat taženou kruh. Budete implementovat kód, který umožňuje přesunout kruh z jednoho panelu, nebo vytvořit kopii ovládacího prvku kruh a podržte stisknutou klávesu CTRL a přetahování kruh.  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a>Chcete-li povolit panelu jako cíle přetažení  
  
1.  Otevřete MainWindow.xaml.  
  
2.  Jak je znázorněno v následujícím XAML, v každém <xref:System.Windows.Controls.StackPanel> přidejte obslužné rutiny pro ovládací prvky, <xref:System.Windows.UIElement.DragOver> a <xref:System.Windows.UIElement.Drop> události. Název <xref:System.Windows.UIElement.DragOver> obslužné rutiny události, `panel_DragOver`a název <xref:System.Windows.UIElement.Drop> obslužné rutiny události, `panel_Drop`.  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  Otevřete MainWindows.xaml.cs nebo MainWindow.xaml.vb.  
  
4.  Přidejte následující kód pro <xref:System.Windows.UIElement.DragOver> obslužné rutiny události.  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     To <xref:System.Windows.UIElement.DragOver> obslužné rutiny události provede následující úlohy:  
  
    -   Ověří, že taženou datové pole obsahuje "Objekt" data, která byla součástí <xref:System.Windows.DataObject> řízení uživatelských kruh a předána volání <xref:System.Windows.DragDrop.DoDragDrop%2A>.  
  
    -   Pokud se nachází data "Objekt", zkontroluje, zda po stisknutí klávesy CTRL.  
  
    -   Pokud po stisknutí klávesy CTRL, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Copy>. Jinak hodnota nastavená <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Move>.  
  
5.  Přidejte následující kód pro <xref:System.Windows.UIElement.Drop> obslužné rutiny události.  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     To <xref:System.Windows.UIElement.Drop> obslužné rutiny události provede následující úlohy:  
  
    -   Kontroluje, zda <xref:System.Windows.UIElement.Drop> událost již byla zpracována. Pro instanci, která kruhu ztracené kruh na jiném obslužné rutiny <xref:System.Windows.UIElement.Drop> událostí, nechcete, aby panelu obsahující kruhu také ji zpracovat.  
  
    -   Pokud <xref:System.Windows.UIElement.Drop> událost není zpracována, kontroly zda stisknutí klávesy CTRL.  
  
    -   Pokud při stisknutí klávesy CTRL <xref:System.Windows.UIElement.Drop> se stane, díky kopii kruhu řízení a přidejte ho do <xref:System.Windows.Controls.Panel.Children%2A> kolekce <xref:System.Windows.Controls.StackPanel>.  
  
    -   Pokud není stisknuta klávesa CTRL, se přesune na kruh z <xref:System.Windows.Controls.Panel.Children%2A> kolekce jeho nadřazeného panelu <xref:System.Windows.Controls.Panel.Children%2A> kolekce panelu, která byla vynechána na.  
  
    -   Nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost upozornit <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda jestli se provedlo operace přesunutí nebo zkopírování.  
  
6.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
7.  Vyberte text `green` z <xref:System.Windows.Controls.TextBox>.  
  
8.  Přetáhněte text přes ovládacího prvku kruh a umístěte jej.  
  
9. Přetáhněte ovládací prvek kruh v levém panelu na pravém panelu a umístěte jej. Kruhu je odebrán z <xref:System.Windows.Controls.Panel.Children%2A> kolekce levém panelu a přidat do kolekce podřízených pravém panelu.  
  
10. Přetáhněte ovládací prvek kruh z panelu, který je v jiném panelu a umístěte jej při stisknete klávesu CTRL. Se zkopíruje na kruh a o kopírování se přidá <xref:System.Windows.Controls.Panel.Children%2A> kolekce přijímající panelu.  
  
     ![Přetahování kruh stiskněte klávesu CTRL](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")  
  
## <a name="see-also"></a>Viz také  
 [Přetáhnout myší – přehled](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
