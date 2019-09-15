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
ms.openlocfilehash: 172e49c2c255db4d24d2180f919b1305326b5e82
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991799"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku

Tento návod ukazuje, jak vytvořit vlastní uživatelský ovládací prvek, který se může zúčastnit přenosu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]dat přetahováním myší.

V tomto návodu vytvoříte vlastní WPF <xref:System.Windows.Controls.UserControl> , který představuje kruhový tvar. V ovládacím prvku implementujete funkce pro povolení přenosu dat pomocí přetahování myší. Například pokud přetáhnete jeden ovládací prvek kruh do druhého, data barvy výplně se zkopírují ze zdrojového kruhu do cíle. Pokud přetáhnete z ovládacího prvku Circle do <xref:System.Windows.Controls.TextBox>, Řetězcová reprezentace barvy výplně je zkopírována <xref:System.Windows.Controls.TextBox>do. Také vytvoříte malou aplikaci, která obsahuje dva ovládací prvky panelu a a <xref:System.Windows.Controls.TextBox> k otestování funkcí přetahování myší. Napíšete kód, který panelům umožní zpracovat vyhozená data kruhů, což vám umožní přesouvat nebo kopírovat kružnice z kolekce podřízených prvků jednoho panelu na druhý.

Tento návod znázorňuje následující úlohy:

- Vytvořte vlastní uživatelský ovládací prvek.

- Povolit uživatelský ovládací prvek jako zdroj přetažení.

- Povolit uživatelský ovládací prvek jako cíl přetažení.

- Umožňuje panelu, aby přijímal data vyřazená z uživatelského ovládacího prvku.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="create-the-application-project"></a>Vytvoření projektu aplikace
 V této části vytvoříte aplikační infrastrukturu, která bude obsahovat hlavní stránku se dvěma panely a <xref:System.Windows.Controls.TextBox>.

1. Vytvořte nový projekt aplikace WPF v Visual Basic nebo vizuálu C# s názvem `DragDropExample`. Další informace najdete v tématu [Návod: Moje první desktopová aplikace](../getting-started/walkthrough-my-first-wpf-desktop-application.md)WPF.

2. Otevřete MainWindow. XAML.

3. Přidejte následující značku mezi otevírací a uzavírací <xref:System.Windows.Controls.Grid> značku.

     Tento kód vytvoří uživatelské rozhraní pro testovací aplikaci.

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a>Přidat do projektu nový uživatelský ovládací prvek
 V této části přidáte do projektu nový uživatelský ovládací prvek.

1. V nabídce projekt vyberte **Přidat uživatelský ovládací prvek**.

2. V dialogovém okně **Přidat novou položku** změňte název na `Circle.xaml`a klikněte na **Přidat**.

     Do projektu se přidá Circle. XAML a jeho kód na pozadí.

3. Otevřete Circle. XAML.

     Tento soubor bude obsahovat prvky uživatelského rozhraní uživatelského ovládacího prvku.

4. Přidejte následující kód do kořenového adresáře <xref:System.Windows.Controls.Grid> pro vytvoření jednoduchého uživatelského ovládacího prvku, který má modrý kroužek jako své uživatelské rozhraní.

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. Otevřete Circle.xaml.cs nebo Circle. XAML. vb.

6. V C#přidejte následující kód za konstruktor bez parametrů k vytvoření kopírovacího konstruktoru. V Visual Basic přidejte následující kód pro vytvoření konstruktoru bez parametrů a kopírovacího konstruktoru.

     Chcete-li, aby byl uživatelský ovládací prvek zkopírován, přidejte do souboru kódu na pozadí metodu kopírovacího konstruktoru. V uživatelském ovládacím prvku zjednodušený kruh budete kopírovat pouze výplň a velikost uživatelského ovládacího prvku.

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a>Přidání uživatelského ovládacího prvku do hlavního okna

1. Otevřete MainWindow. XAML.

2. Přidejte následující kód XAML do úvodní <xref:System.Windows.Window> značky a vytvořte tak odkaz na obor názvů XML na aktuální aplikaci.

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. V prvním <xref:System.Windows.Controls.StackPanel>panelu přidejte následující XAML pro vytvoření dvou instancí uživatelského ovládacího prvku Circle.

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     Úplný kód XAML pro panel vypadá následovně.

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a>Implementace přetáhněte zdrojové události do uživatelského ovládacího prvku
 V této části přepíšete <xref:System.Windows.UIElement.OnMouseMove%2A> metodu a inicializujete operaci přetažení.

 Pokud je spuštěno přetahování (stisknuto tlačítko myši a přesun myši), zabalíte data, která chcete přenést do <xref:System.Windows.DataObject>. V tomto případě bude ovládací prvek kruh zabalit tři datové položky. Řetězcová reprezentace barvy jeho výplně, dvojitá reprezentace jeho výšky a kopie sebe sama.

### <a name="to-initiate-a-drag-and-drop-operation"></a>Zahájení operace přetažení myší

1. Otevřete Circle.xaml.cs nebo Circle. XAML. vb.

2. Přidejte následující <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.MouseMove> pro zpracování události.

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     Toto <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání provádí následující úlohy:

    - Kontroluje, zda se při přesouvání myši stiskne levé tlačítko myši.

    - Zabalí data do kruhu do <xref:System.Windows.DataObject>. V tomto případě ovládací prvek Circle balí tři datové položky; Řetězcová reprezentace barvy jeho výplně, dvojitá reprezentace jeho výšky a kopie sebe sama.

    - Volá statickou <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metodu pro zahájení operace přetažení. <xref:System.Windows.DragDrop.DoDragDrop%2A> Metodě předáte následující tři parametry:

        - `dragSource`– Odkaz na tento ovládací prvek.

        - `data`<xref:System.Windows.DataObject> – Vytvořeno v předchozím kódu.

        - `allowedEffects`– Povolené operace přetažení, které jsou <xref:System.Windows.DragDropEffects.Copy> nebo. <xref:System.Windows.DragDropEffects.Move>

3. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

4. Klikněte na jeden z ovládacích prvků kruh a přetáhněte ho na panely, druhý kruh a <xref:System.Windows.Controls.TextBox>. Při přetahování přes <xref:System.Windows.Controls.TextBox>se kurzor změní, aby označoval přesunutí.

5. Při přetahování kružnice <xref:System.Windows.Controls.TextBox>na stiskněte klávesu **CTRL** . Všimněte si, jak se kurzor změní, aby označoval kopii.

6. Přetáhněte kruh na <xref:System.Windows.Controls.TextBox>. Řetězcová reprezentace barvy výplně kruhu je připojena k <xref:System.Windows.Controls.TextBox>.

     ![Řetězcová reprezentace barvy výplně kruhu](./media/dragdrop-colorstring.png "DragDrop_ColorString")

Ve výchozím nastavení se kurzor během operace přetažení změní, aby označoval, jaký vliv bude mít data na odstranění. Zpětnou vazbu určenou uživateli můžete přizpůsobit zpracováním <xref:System.Windows.UIElement.GiveFeedback> události a nastavením jiného kurzoru.

## <a name="give-feedback-to-the-user"></a>Poskytněte uživateli zpětnou vazbu.

1. Otevřete Circle.xaml.cs nebo Circle. XAML. vb.

2. Přidejte následující <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.GiveFeedback> pro zpracování události.

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     Toto <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání provádí následující úlohy:

    - Kontroluje hodnoty, které jsou nastaveny v obslužné rutině <xref:System.Windows.UIElement.DragOver> události cílového umístění. <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>

    - Nastaví vlastní kurzor na základě <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnoty. Cílem tohoto kurzoru je poskytnout vizuální zpětnou vazbu uživateli o tom, jaký vliv bude mít data přehozena.

3. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

4. Přetáhněte jeden z kruhových ovládacích prvků přes panely, druhý kruh a <xref:System.Windows.Controls.TextBox>. Všimněte si, že kurzory jsou nyní vlastními kurzory, které jste zadali <xref:System.Windows.UIElement.OnGiveFeedback%2A> v přepsání.

     ![Přetahování pomocí vlastních kurzorů](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")

5. Vyberte text `green` <xref:System.Windows.Controls.TextBox>z.

6. `green` Přetáhněte text do ovládacího prvku kruh. Všimněte si, že výchozí kurzory jsou zobrazeny pro indikaci vlivu operace přetažení. Ukazatel zpětné vazby je vždy nastaven zdrojem přetažení.

## <a name="implement-drop-target-events-in-the-user-control"></a>Implementovat události cíle zrušení v uživatelském ovládacím prvku
 V této části určíte, že uživatelský ovládací prvek je cílem přetažení, přepište metody, které umožňují, aby uživatelský ovládací prvek byl cílem přetažení, a zpracovávat data, která jsou na něm vyřazena.

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Povolení uživatelského ovládacího prvku jako cíle přetažení

1. Otevřete Circle. XAML.

2. V otevírací <xref:System.Windows.Controls.UserControl> značce <xref:System.Windows.UIElement.AllowDrop%2A> přidejte vlastnost a nastavte ji na `true`.

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

Metoda je volána, <xref:System.Windows.UIElement.AllowDrop%2A> když je vlastnost nastavena na `true` hodnotu a data ze zdroje přetažení jsou vyřazena v uživatelském ovládacím prvku Circle. <xref:System.Windows.UIElement.OnDrop%2A> V této metodě budete zpracovávat data, která byla vyřazena, a použijí data v kruhu.

### <a name="to-process-the-dropped-data"></a>Zpracování zahozených dat

1. Otevřete Circle.xaml.cs nebo Circle. XAML. vb.

2. Přidejte následující <xref:System.Windows.UIElement.OnDrop%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.Drop> pro zpracování události.

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     Toto <xref:System.Windows.UIElement.OnDrop%2A> přepsání provádí následující úlohy:

    - <xref:System.Windows.DataObject.GetDataPresent%2A> Používá metodu ke kontrole, zda přetažená data obsahují objekt String.

    - <xref:System.Windows.DataObject.GetData%2A> Používá metodu k extrakci řetězcových dat, pokud je k dispozici.

    - Používá k pokusu o převod řetězce <xref:System.Windows.Media.Brush>na. <xref:System.Windows.Media.BrushConverter>

    - Pokud je převod úspěšný, použije štětec na <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> z, který poskytuje uživatelské rozhraní ovládacího prvku Circle.

    - <xref:System.Windows.UIElement.Drop> Označí událost jako zpracovanou. Odkládací událost byste měli označit jako pořízenou, aby ostatní prvky, které obdrží tuto událost, věděly, že ovládací prvek kruhového uživatele ho zpracoval.

3. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

4. Vyberte text `green` v části <xref:System.Windows.Controls.TextBox>.

5. Přetáhněte text do kruhu a pusťte ho do ovládacího prvku. Kruh se změní z modré na zelenou.

     ![Převod řetězce na štětec](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")

6. Zadejte text `green` do pole <xref:System.Windows.Controls.TextBox>.

7. Vyberte text `gre` v části <xref:System.Windows.Controls.TextBox>.

8. Přetáhněte ho do kruhu a pusťte ho do ovládacího prvku. Všimněte si, že se kurzor změní, aby označoval, že je povoleno zrušení, ale barva kružnice se nemění `gre` , protože není platná barva.

9. Přetáhněte z zeleného kruhu ovládacího prvku a umístěte ukazatel myši na ovládací prvek modrého kruhu. Kruh se změní z modré na zelenou. Všimněte si, že se kurzor zobrazuje, závisí na <xref:System.Windows.Controls.TextBox> tom, zda je nebo kroužek zdrojem přetažení.

Nastavení vlastnosti na `true` a zpracování vynechaných dat je vyžadováno pro povolení prvku jako cíle přetažení. <xref:System.Windows.UIElement.AllowDrop%2A> Chcete-li však poskytnout lepší uživatelské prostředí, měli byste také zpracovat <xref:System.Windows.UIElement.DragEnter>události, <xref:System.Windows.UIElement.DragLeave>a. <xref:System.Windows.UIElement.DragOver> V těchto událostech můžete provádět kontroly a před vyřazením dat poskytnout uživateli dodatečnou zpětnou vazbu.

Když jsou data přetažena přes uživatelský ovládací prvek kruh, ovládací prvek by měl informovat zdroj přetažení, zda může zpracovat data, která jsou přetažena. Pokud ovládací prvek neví, jak data zpracovat, měla by být zamítnuta operace drop. K tomu je potřeba zpracovat <xref:System.Windows.UIElement.DragOver> událost a <xref:System.Windows.DragEventArgs.Effects%2A> nastavit vlastnost.

### <a name="to-verify-that-the-data-drop-is-allowed"></a>Ověření, zda je povoleno ukládání dat

1. Otevřete Circle.xaml.cs nebo Circle. XAML. vb.

2. Přidejte následující <xref:System.Windows.UIElement.OnDragOver%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.DragOver> pro zpracování události.

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     Toto <xref:System.Windows.UIElement.OnDragOver%2A> přepsání provádí následující úlohy:

    - Nastaví vlastnost na <xref:System.Windows.DragDropEffects.None>hodnotu. <xref:System.Windows.DragEventArgs.Effects%2A>

    - Provede stejné kontroly, které jsou provedeny v <xref:System.Windows.UIElement.OnDrop%2A> metodě k určení, zda uživatelský ovládací prvek kruh může zpracovat přetažená data.

    - Pokud uživatelský ovládací prvek může zpracovat data, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost na <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.

3. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

4. Vyberte text `gre` v části <xref:System.Windows.Controls.TextBox>.

5. Přetáhněte text do ovládacího prvku kruh. Všimněte si, že kurzor se nyní změní, aby označoval, že zrušení není `gre` povoleno, protože není platná barva.

 Činnost koncového uživatele můžete dále vylepšit použitím náhledu operace přetažení. Pro uživatelský ovládací prvek kruh přepíšete <xref:System.Windows.UIElement.OnDragEnter%2A> metody a. <xref:System.Windows.UIElement.OnDragLeave%2A> Když jsou data přetažena na ovládací prvek, aktuální pozadí <xref:System.Windows.Shapes.Shape.Fill%2A> je uloženo v zástupné proměnné. Řetězec se pak převede na štětec a použije se na <xref:System.Windows.Shapes.Ellipse> rozhraní, které poskytuje kolečko v uživatelském rozhraní. Pokud jsou data přetažena mimo kruh, aniž by byla vynechána, původní <xref:System.Windows.Shapes.Shape.Fill%2A> hodnota se znovu použije na kroužek.

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Náhled efektů operace přetažení

1. Otevřete Circle.xaml.cs nebo Circle. XAML. vb.

2. V kruhu třídy deklarujte privátní <xref:System.Windows.Media.Brush> proměnnou s názvem `_previousFill` a inicializujte ji na `null`.

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. Přidejte následující <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.DragEnter> pro zpracování události.

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     Toto <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání provádí následující úlohy:

    - <xref:System.Windows.Shapes.Shape.Fill%2A> Uloží vlastnost <xref:System.Windows.Shapes.Ellipse> v proměnné.`_previousFill`

    - Provede stejné kontroly, které jsou provedeny v <xref:System.Windows.UIElement.OnDrop%2A> metodě k určení, zda lze data převést <xref:System.Windows.Media.Brush>na.

    - Pokud jsou data převedena na platná <xref:System.Windows.Media.Brush>, aplikuje ji <xref:System.Windows.Shapes.Shape.Fill%2A> na <xref:System.Windows.Shapes.Ellipse>.

4. Přidejte následující <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.DragLeave> pro zpracování události.

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     Toto <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání provádí následující úlohy:

    - Použije uložené v `_previousFill` proměnnéna<xref:System.Windows.Shapes.Shape.Fill%2A> z ,kterýposkytujeuživatelskérozhraníuživatelskéhoovládacíhoprvkuCircle.<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Media.Brush>

5. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

6. Vyberte text `green` v části <xref:System.Windows.Controls.TextBox>.

7. Přetáhněte text přes ovládací prvek Circle, aniž byste ho museli přetahovat. Kruh se změní z modré na zelenou.

     ![Náhled efektů operace přetažení&#45;&#45;](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")

8. Přetáhněte text směrem od ovládacího prvku Circle. Kruh se změní z zelené na modrou.

## <a name="enable-a-panel-to-receive-dropped-data"></a>Povolení panelu pro příjem zahozených dat

V této části povolíte panely, které jsou hostiteli uživatelských ovládacích prvků kruh, aby fungovaly jako cíle přetažení pro přetažená data v kruhu. Budete implementovat kód, který umožňuje přesunout kruh z jednoho panelu na jiný, nebo vytvořit kopii ovládacího prvku Circle tak, že podržíte stisknutou klávesu **CTRL** při přetahování a vyřazení kružnice.

1. Otevřete MainWindow. XAML.

2. Jak je znázorněno v následujícím kódu XAML, v každém <xref:System.Windows.Controls.StackPanel> z ovládacích prvků přidejte obslužné rutiny <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.DragOver> pro události a. Pojmenujte `panel_DragOver`obslužnou rutinu `panel_Drop` <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.DragOver> události, a pojmenujte obslužnou rutinu události.

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. Otevřete MainWindows.xaml.cs nebo MainWindow. XAML. vb.

4. Přidejte následující kód pro <xref:System.Windows.UIElement.DragOver> obslužnou rutinu události.

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     Tato <xref:System.Windows.UIElement.DragOver> obslužná rutina události provádí následující úlohy:

    - Kontroluje, zda přetažená data obsahují data "Object", která byla zabalena <xref:System.Windows.DataObject> v uživatelském ovládacím prvku Circle a předaná <xref:System.Windows.DragDrop.DoDragDrop%2A>volání.

    - Pokud jsou k dispozici data "objekt", aplikace kontroluje, zda je stisknuta klávesa **CTRL** .

    - Pokud stisknete klávesu **CTRL** , nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost na <xref:System.Windows.DragDropEffects.Copy>hodnotu. V opačném případě <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost nastavte <xref:System.Windows.DragDropEffects.Move>na.

5. Přidejte následující kód pro <xref:System.Windows.UIElement.Drop> obslužnou rutinu události.

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     Tato <xref:System.Windows.UIElement.Drop> obslužná rutina události provádí následující úlohy:

    - Kontroluje, zda <xref:System.Windows.UIElement.Drop> událost již byla zpracována. Například pokud je kroužek vyřazen na jiném kruhu, který zpracovává <xref:System.Windows.UIElement.Drop> událost, nechcete, aby byl panel, který obsahuje kroužek, také zpracován.

    - Pokud událost není zpracována, aplikace zkontroluje, zda je stisknuta klávesa **CTRL.** <xref:System.Windows.UIElement.Drop>

    - Pokud je stisknuta klávesa **CTRL** , <xref:System.Windows.UIElement.Drop> když dojde k tomu, vytvoří kopii ovládacího prvku Circle a <xref:System.Windows.Controls.Panel.Children%2A> přidá jej do kolekce <xref:System.Windows.Controls.StackPanel>.

    - Pokud klávesu **CTRL** nestiskne, přesune kruh z <xref:System.Windows.Controls.Panel.Children%2A> kolekce svého <xref:System.Windows.Controls.Panel.Children%2A> nadřazeného panelu do kolekce panelu, ve kterém byl vyřazen.

    - Nastaví vlastnost pro oznamování <xref:System.Windows.DragDrop.DoDragDrop%2A> metody, zda byla provedena operace přesunutí nebo kopírování. <xref:System.Windows.DragEventArgs.Effects%2A>

6. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

7. Vyberte text `green` <xref:System.Windows.Controls.TextBox>z.

8. Přetáhněte text přes ovládací prvek kruh a umístěte ho.

9. Přetáhněte ovládací prvek kruh z levého panelu do pravého panelu a přetáhněte ho. Kruh se odebere z <xref:System.Windows.Controls.Panel.Children%2A> kolekce levého panelu a přidá se do kolekce podřízenosti pravého panelu.

10. Přetáhněte ovládací prvek Circle z panelu, na který se nachází, na jiný panel a při stisknutí klávesy **CTRL** ho umístěte. Kruh se zkopíruje a kopie se přidá do <xref:System.Windows.Controls.Panel.Children%2A> kolekce přijímacího panelu.

     ![Přetažení kruhu při stisknutí klávesy CTRL](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")

## <a name="see-also"></a>Viz také:

- [Přehled přetažení](drag-and-drop-overview.md)
