---
title: 'Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: e151eb7f428fecb330970210fd7addb1603a211f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534229"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku
Tento návod ukazuje, jak vytvořit vlastní uživatelský ovládací prvek, který se můžete podílet přenos dat a přetahování v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 V tomto návodu vytvoříte vlastní WPF <xref:System.Windows.Controls.UserControl> , která představuje kulaté. Funkce provede na ovládacím prvku povolit přenos dat pomocí přetahování myší. Například přetažením z jednoho ovládacího prvku kruh do jiného data Barva výplně je zkopírován ze zdroje kruh k cíli. Přetažením z ovládacího prvku kruh k <xref:System.Windows.Controls.TextBox>, řetězcová reprezentace barvu výplně se zkopíruje do <xref:System.Windows.Controls.TextBox>. Také vytvoříte malou aplikaci, která obsahuje dva ovládací prvky panelu a <xref:System.Windows.Controls.TextBox> k testování funkcí a přetažení. Budete psát kód, který umožňuje panelů ke zpracování vynechaných kruh dat, která vám umožní se přesunout nebo kopírovat kruhy kolekci Children v panel jeden na druhý.  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Vytvořte vlastní uživatelský ovládací prvek.  
  
-   Povolení nástroje Řízení uživatelských jako zdroj přetažení.  
  
-   Povolte uživatelský ovládací prvek jako cíl přetažení.  
  
-   Povolte panel přijímat data z uživatelského ovládacího prvku vyřadit.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Visual Studio 2010  
  
## <a name="creating-the-application-project"></a>Vytvoření projektu aplikace  
 V této části vytvoříte aplikační infrastruktury, který obsahuje hlavní stránka s dva panely a <xref:System.Windows.Controls.TextBox>.  
  
### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvoření nového projektu aplikace WPF v jazyce Visual Basic nebo Visual C# s názvem `DragDropExample`. Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  Otevřete soubor MainWindow.xaml.  
  
3.  Přidejte následující kód mezi otevírací a zavírací <xref:System.Windows.Controls.Grid> značky.  
  
     Tento kód vytvoří uživatelské rozhraní pro testovací aplikace.  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a>Přidání nového uživatelského ovládacího prvku do projektu  
 V této části přidáte nový uživatelský ovládací prvek do projektu.  
  
### <a name="to-add-a-new-user-control"></a>Chcete-li přidat nového uživatelského ovládacího prvku  
  
1.  V nabídce Projekt vyberte **přidat uživatelský ovládací prvek**.  
  
2.  V dialogovém okně Přidat novou položku změnit název, který má `Circle.xaml`a klikněte na tlačítko **přidat**.  
  
     Circle.XAML a jeho použití modelu code-behind se přidá do projektu.  
  
3.  Otevřete Circle.xaml.  
  
     Tento soubor bude obsahovat prvky uživatelského rozhraní uživatelského ovládacího prvku.  
  
4.  Přidejte následující kód do kořenového adresáře <xref:System.Windows.Controls.Grid> k vytvoření jednoduché uživatelský ovládací prvek, který má kruh jako jeho uživatelské rozhraní.  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
6.  V jazyce C# přidejte následující kód za výchozí konstruktor pro vytvoření kopie konstruktoru. V jazyce Visual Basic přidejte následující kód k vytvoření výchozí konstruktor a kopírovací konstruktor.  
  
     Aby bylo možné povolit uživatelského ovládacího prvku, které se mají zkopírovat, přidejte metodu konstruktoru kopie v souboru kódu na pozadí. Ve zjednodušené kruh uživatelského ovládacího prvku, bude pouze zkopírujte výplně a velikost uživatelského ovládacího prvku.  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a>Chcete-li přidat uživatelský ovládací prvek do hlavního okna  
  
1.  Otevřete soubor MainWindow.xaml.  
  
2.  Přidejte následující XAML do otevíracího <xref:System.Windows.Window> značku k vytvoření oboru názvů XML odkaz na aktuální aplikace.  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  V prvním <xref:System.Windows.Controls.StackPanel>, přidejte následující XAML vytvořit dvě instance kruh uživatelského ovládacího prvku na panelu první.  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     Úplné XAML pro panel vypadá takto.  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a>Implementace zdroj události přetažení do uživatelského ovládacího prvku  
 V této části se přepíšou <xref:System.Windows.UIElement.OnMouseMove%2A> metoda a zahájení operace přetažení myší.  
  
 Pokud je spuštěn přetáhněte (stisknutí tlačítka myši a přesunut ukazatel myši), bude balíček data, která mají být převedeny do <xref:System.Windows.DataObject>. V takovém případě bude ovládací prvek kruh balíček tři položky data; řetězcová reprezentace jeho barva výplně, dvojité vyjádření výšku a zkopírujte sebe sama.  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a>K zahájení operace přetažení myší  
  
1.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
2.  Přidejte následující <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.MouseMove> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     To <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání provádí následující úlohy:  
  
    -   Kontroluje, zda se stiskne tlačítko levé tlačítko myši, zatímco ukazatel myši pohybuje.  
  
    -   Balíčky kruh dat do <xref:System.Windows.DataObject>. V tomto případě ovládací prvek kruh balíčky tři položky data; řetězcová reprezentace jeho barva výplně, dvojité vyjádření výšku a zkopírujte sebe sama.  
  
    -   Volání statické <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metoda k zahájení operace přetažení myší. Následující tři parametry předáváte <xref:System.Windows.DragDrop.DoDragDrop%2A> metody:  
  
        -   `dragSource` – Odkaz na tento ovládací prvek.  
  
        -   `data` – Tím <xref:System.Windows.DataObject> vytvořili v předchozím kódu.  
  
        -   `allowedEffects` – Povolené operace přetažení myší, které jsou <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.  
  
3.  Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
4.  Klikněte na jednu z ovládacích prvků kruh a přetáhněte ho na panely na kruh a <xref:System.Windows.Controls.TextBox>. Při přetažení přes <xref:System.Windows.Controls.TextBox>, změní se kurzor na udávajících přesun.  
  
5.  Při přetažení kruh přes <xref:System.Windows.Controls.TextBox>, stiskněte klávesu CTRL. Všimněte si, jak kurzoru se změní jeho kopii.  
  
6.  Přetáhnout myší kruhu na <xref:System.Windows.Controls.TextBox>. Řetězcová reprezentace barvu kruhu se připojí <xref:System.Windows.Controls.TextBox>.  
  
     ![Řetězcové vyjádření barvu kruhu](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")  
  
 Ve výchozím nastavení se kurzor změní během operace přetažení myší označíte, jaký vliv má vyřazení dat bude mít. Můžete přizpůsobit poskytnutou zpětnou vazbu pro uživatele pomocí manipulace <xref:System.Windows.UIElement.GiveFeedback> událostí a nastavení různých kurzoru.  
  
### <a name="to-give-feedback-to-the-user"></a>Poskytněte zpětnou vazbu pro uživatele  
  
1.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
2.  Přidejte následující <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.GiveFeedback> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     To <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání provádí následující úlohy:  
  
    -   Kontroluje <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnoty nastavené v cíl přetažení <xref:System.Windows.UIElement.DragOver> obslužné rutiny události.  
  
    -   Nastaví vlastní kurzor na základě <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnotu. Kurzor má předat uživateli o jaký vliv má vyřadit data budou mít vizuální zpětnou vazbu.  
  
3.  Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
4.  Přetáhněte jednu kruhu určuje přes panelů na kruh a <xref:System.Windows.Controls.TextBox>. Všimněte si, že kurzory teď vlastní ukazatele, které jste zadali <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsat.  
  
     ![Přetáhnout myší s vlastní ukazatele](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")  
  
5.  Vyberte text `green` z <xref:System.Windows.Controls.TextBox>.  
  
6.  Přetáhněte `green` text do ovládacího prvku kruh. Všimněte si, že jsou zobrazeny kurzory výchozí udávajících účinky operace přetažení myší. Kurzor zpětná vazba je vždycky nastavený zdroj přetažení.  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a>Implementace události cíl přetažení do uživatelského ovládacího prvku  
 V této části určíte, že uživatelský ovládací prvek je cíl přetažení, přepsání metody, které umožňují uživateli ovládací prvek jako cíl přetažení a zpracovávat data, která je na něm vyřadit.  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Chcete-li povolit uživatelský ovládací prvek jako cíl přetažení  
  
1.  Otevřete Circle.xaml.  
  
2.  Při otevírání <xref:System.Windows.Controls.UserControl> značky, přidejte <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost a nastavte ho na `true`.  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <xref:System.Windows.UIElement.OnDrop%2A> Metoda je volána, když <xref:System.Windows.UIElement.AllowDrop%2A> je nastavena na `true` a data ze zdroje přetáhněte přesunuta uživatelský ovládací prvek kruh. V této metodě budou zpracovávat data, která byla zahozena a použít data kruhu.  
  
### <a name="to-process-the-dropped-data"></a>Ke zpracování vynechaných dat  
  
1.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
2.  Přidejte následující <xref:System.Windows.UIElement.OnDrop%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.Drop> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     To <xref:System.Windows.UIElement.OnDrop%2A> přepsání provádí následující úlohy:  
  
    -   Používá <xref:System.Windows.DataObject.GetDataPresent%2A> metodu ke kontrole, pokud Přetahované dat obsahuje objekt řetězce.  
  
    -   Používá <xref:System.Windows.DataObject.GetData%2A> metody se extrahují data řetězce, pokud je k dispozici.  
  
    -   Používá <xref:System.Windows.Media.BrushConverter> pokusí převést řetězec, který má <xref:System.Windows.Media.Brush>.  
  
    -   Pokud převod je úspěšný, štětce, který se vztahuje <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> , který poskytuje uživatelské rozhraní ovládacího prvku kruh.  
  
    -   Značky <xref:System.Windows.UIElement.Drop> události jako zpracování. Událost přetažení by měla označit jako ošetřenou, takže další prvky, které se zobrazí tato událost vědět, že uživatelský ovládací prvek kruh zpracovává ji.  
  
3.  Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
4.  Vyberte text `green` v <xref:System.Windows.Controls.TextBox>.  
  
5.  Text do ovládacího prvku kruh přetáhnout. Kruh se změní z modrá na zelenou.  
  
     ![Převod řetězce na stopu](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")  
  
6.  Zadejte text `green` v <xref:System.Windows.Controls.TextBox>.  
  
7.  Vyberte text `gre` v <xref:System.Windows.Controls.TextBox>.  
  
8.  Přetáhněte do ovládacího prvku kruhu a umístěte jej. Všimněte si, že se ukazatel změní na ukazují, že rozevírací je povoleno, ale barvu kruhu se nemění, protože `gre` není platná barva.  
  
9. Z ovládacího prvku zelený kroužek přetažením na ovládacím prvku modré kruh. Kruh se změní z modrá na zelenou. Všimněte si, že se zobrazí kurzor, který závisí na tom, zda <xref:System.Windows.Controls.TextBox> nebo kruhu je zdroji přetažení.  
  
 Nastavení <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost `true` a zpracování dat vynechaných je vše, co je potřeba povolit element, který má být cíl přetažení. Však zajistit lepší výkon, můžete také pracovat <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, a <xref:System.Windows.UIElement.DragOver> události. V těchto událostí můžete provést kontroly a zadejte víc uživateli předtím, než se ukončí data.  
  
 Když data je přetažený na ovládací prvek uživatele kruh, ovládací prvek by měl oznámení zdroji přetažení, zda může zpracovat data, která je právě přetáhli. Pokud ovládací prvek není známo, jak ke zpracování dat, by měl odmítnout rozevírací nabídku. K tomuto účelu bude zpracovávat <xref:System.Windows.UIElement.DragOver> událostí a nastavte <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost.  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a>Chcete-li ověřit, že rozevírací dat není povolené  
  
1.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
2.  Přidejte následující <xref:System.Windows.UIElement.OnDragOver%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.DragOver> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     To <xref:System.Windows.UIElement.OnDragOver%2A> přepsání provádí následující úlohy:  
  
    -   Nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.None>.  
  
    -   Provádí stejné kontroly, které se provádí v <xref:System.Windows.UIElement.OnDrop%2A> metodou ke zjištění, zda uživatelský ovládací prvek kruh může zpracovávat Přetahované data.  
  
    -   Pokud uživatelský ovládací prvek můžete zpracovávat data, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.  
  
3.  Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
4.  Vyberte text `gre` v <xref:System.Windows.Controls.TextBox>.  
  
5.  Přetáhněte text do ovládacího prvku kruh. Všimněte si, že se kurzor změní teď označuje, že rozevírací není povolená, protože `gre` není platná barva.  
  
 Můžete dále vylepšit uživatelské prostředí s použitím operace přetažení ve verzi preview. Pro uživatelský ovládací prvek kruh, přepíše <xref:System.Windows.UIElement.OnDragEnter%2A> a <xref:System.Windows.UIElement.OnDragLeave%2A> metody. Když jsou data přetažený na ovládací prvek, aktuální pozadí <xref:System.Windows.Shapes.Shape.Fill%2A> je uložen v proměnné zástupný symbol. Pak převedena na štětce a použít na řetězec <xref:System.Windows.Shapes.Ellipse> kruhu, která poskytuje uživatelské rozhraní. Pokud data ocitne mimo kruh bez probíhá vyřazování původní <xref:System.Windows.Shapes.Shape.Fill%2A> hodnota je znovu použita v kruhu.  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Náhled účinky operace přetažení myší  
  
1.  Otevřete Circle.xaml.cs nebo Circle.xaml.vb.  
  
2.  Ve třídě kruh deklarovat soukromé <xref:System.Windows.Media.Brush> proměnnou s názvem `_previousFill` a inicializujte ji na `null`.  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  Přidejte následující <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.DragEnter> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     To <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání provádí následující úlohy:  
  
    -   Uloží <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost <xref:System.Windows.Shapes.Ellipse> v `_previousFill` proměnné.  
  
    -   Provádí stejné kontroly, které se provádí v <xref:System.Windows.UIElement.OnDrop%2A> metodou ke zjištění, zda data lze převést na <xref:System.Windows.Media.Brush>.  
  
    -   Pokud data je převést na platnou <xref:System.Windows.Media.Brush>, použije ho k <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse>.  
  
4.  Přidejte následující <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.DragLeave> událostí.  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     To <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání provádí následující úlohy:  
  
    -   Se vztahuje <xref:System.Windows.Media.Brush> uložené v `_previousFill` proměnnou <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> , který poskytuje uživatelské rozhraní uživatelského ovládacího prvku kruh.  
  
5.  Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
6.  Vyberte text `green` v <xref:System.Windows.Controls.TextBox>.  
  
7.  Přetáhněte text myší na ovládací prvek kruh bez zastaví. Kruh se změní z modrá na zelenou.  
  
     ![Ve verzi Preview efekty přetáhněte&#45;a&#45;operace odstranění](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")  
  
8.  Přetáhněte text z ovládacího prvku kruh. Kruh se změní z zelené zpět na modrou.  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a>Povolení panely přijímat vyřadit dat  
 V této části vám umožní panely, které jsou hostiteli uživatelské ovládací prvky kruh tak, aby fungoval jako cíle přetažení pro Přetahované data kruh. Budete implementovat kód, který umožňuje přesunout kruh z jednoho panelu na jiný, nebo vytvořte kopii kruh ovládací prvek tím, že podržíte stisknutou klávesu CTRL při přetahování kruh.  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a>Povolit panelu bude cíle přetažení  
  
1.  Otevřete soubor MainWindow.xaml.  
  
2.  Jak je znázorněno v následující XAML v každém <xref:System.Windows.Controls.StackPanel> přidat obslužné rutiny pro ovládací prvky, <xref:System.Windows.UIElement.DragOver> a <xref:System.Windows.UIElement.Drop> události. Název <xref:System.Windows.UIElement.DragOver> obslužná rutina události `panel_DragOver`a pojmenujte <xref:System.Windows.UIElement.Drop> obslužná rutina události, `panel_Drop`.  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  Otevřete MainWindows.xaml.cs nebo soubor MainWindow.xaml.vb.  
  
4.  Přidejte následující kód <xref:System.Windows.UIElement.DragOver> obslužné rutiny události.  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     To <xref:System.Windows.UIElement.DragOver> obslužná rutina události provádí následující úlohy:  
  
    -   Kontroluje, že Přetahované data obsahují data "Object", který byl zabalen do <xref:System.Windows.DataObject> v uživatelském ovládacím prvku kruhu a předat ve volání do <xref:System.Windows.DragDrop.DoDragDrop%2A>.  
  
    -   Pokud jsou k dispozici data "Object", zkontroluje, zda je klávesa CTRL stisknuta.  
  
    -   Pokud se stiskne klávesu CTRL, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Copy>. V opačném případě nastavte <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Move>.  
  
5.  Přidejte následující kód <xref:System.Windows.UIElement.Drop> obslužné rutiny události.  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     To <xref:System.Windows.UIElement.Drop> obslužná rutina události provádí následující úlohy:  
  
    -   Kontroluje, zda <xref:System.Windows.UIElement.Drop> události již byla zpracována. Pro instanci, která kroužek ztracené kruhu na jiném obslužné rutiny <xref:System.Windows.UIElement.Drop> události, nechcete, aby panelu, který obsahuje kruhu také ji zpracovat.  
  
    -   Pokud <xref:System.Windows.UIElement.Drop> událostí není zpracována, zkontroluje, zda je klávesa CTRL stisknuta.  
  
    -   Pokud se stiskne klávesa CTRL, kdy <xref:System.Windows.UIElement.Drop> se stane, vytvoří kopii kruhu ovládací prvek a přidat ji do <xref:System.Windows.Controls.Panel.Children%2A> kolekce <xref:System.Windows.Controls.StackPanel>.  
  
    -   Pokud se stiskne klávesu CTRL, přesune kruh z <xref:System.Windows.Controls.Panel.Children%2A> kolekce jeho nadřazeného panelu <xref:System.Windows.Controls.Panel.Children%2A> kolekce, která byla vynechána na panelu.  
  
    -   Sady <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost upozornit <xref:System.Windows.DragDrop.DoDragDrop%2A> metody Určuje, zda byla provedena operace přesunutí nebo kopírování.  
  
6.  Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
7.  Vyberte text `green` z <xref:System.Windows.Controls.TextBox>.  
  
8.  Přetáhněte myší na ovládací prvek kruh text a umístěte jej.  
  
9. Přetáhněte ovládací prvek kruhu na levém panelu na pravém panelu a umístěte ho. Kruh se odebere z <xref:System.Windows.Controls.Panel.Children%2A> kolekce na levém panelu a přidat do podřízené kolekce pravého panelu.  
  
10. Přetáhněte ovládací prvek kruh z panelu, které se nachází na panel a umístěte jej při stisknutí klávesy CTRL. Kruh se zkopíruje a kopie je přidána do <xref:System.Windows.Controls.Panel.Children%2A> kolekce přijímající panelu.  
  
     ![Přetažení kruh při stisknutí klávesy CTRL](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")  
  
## <a name="see-also"></a>Viz také  
 [Přehled přetažení](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
