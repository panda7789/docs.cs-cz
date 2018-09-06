---
title: 'Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 95f375d8845c60441aa5eefdd37e32541ea2d5a7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042306"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="e27c2-102">Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="e27c2-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="e27c2-103">Po přidání ovládacích prvků do formuláře a určit uživatelského rozhraní pro vaši aplikaci, lze svázat ovládací prvky zdroje dat, tak, aby v době běhu, uživatelé mohou změnit a uložit data související s aplikací.</span><span class="sxs-lookup"><span data-stu-id="e27c2-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>  
  
 <span data-ttu-id="e27c2-104">Vytvoření vazby ovládacího prvku nebo řadu ovládacích prvků ve Windows Forms nejsnadněji využívá se při něm <xref:System.Windows.Forms.BindingSource> ovládací prvek jako most mezi ovládacími prvky ve formuláři a zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="e27c2-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>  
  
 <span data-ttu-id="e27c2-105">Jeden nebo více ovládacích prvků na formuláři mohou být vázány na data. v následujícím postupu <xref:System.Windows.Forms.TextBox> ovládací prvek vázán na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="e27c2-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>  
  
 <span data-ttu-id="e27c2-106">Dokončete tento postup předpokládá se, že bude vytvoření vazby ke zdroji dat, který je odvozen z databáze.</span><span class="sxs-lookup"><span data-stu-id="e27c2-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="e27c2-107">Další informace o vytvoření zdroje dat z jiných úložišť dat najdete v tématu [přidat nové zdroje dat](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="e27c2-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e27c2-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="e27c2-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e27c2-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="e27c2-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e27c2-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="e27c2-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="e27c2-111">K vytvoření vazby ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="e27c2-111">To bind a control at design time</span></span>  
  
1.  <span data-ttu-id="e27c2-112">Přetáhněte <xref:System.Windows.Forms.TextBox> ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="e27c2-112">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>  
  
2.  <span data-ttu-id="e27c2-113">V **vlastnosti** okno:</span><span class="sxs-lookup"><span data-stu-id="e27c2-113">In the **Properties** window:</span></span>  
  
    1.  <span data-ttu-id="e27c2-114">Rozbalte **(DataBindings)** uzlu.</span><span class="sxs-lookup"><span data-stu-id="e27c2-114">Expand the **(DataBindings)** node.</span></span>  
  
    2.  <span data-ttu-id="e27c2-115">Klikněte na šipku vedle položky <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e27c2-115">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
         <span data-ttu-id="e27c2-116">**DataSource** otevře editor typu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e27c2-116">The **DataSource** UI type editor opens.</span></span>  
  
         <span data-ttu-id="e27c2-117">Pokud zdroj dat byl dříve nakonfigurován pro projekt nebo formuláře, se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="e27c2-117">If a data source has previously been configured for the project or form, it will appear.</span></span>  
  
3.  <span data-ttu-id="e27c2-118">Klikněte na tlačítko **přidat zdroj dat projektu** vytvořit zdroj dat a připojte se k datům.</span><span class="sxs-lookup"><span data-stu-id="e27c2-118">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
4.  <span data-ttu-id="e27c2-119">Na **Průvodce konfigurací zdroje dat** úvodní stránka, klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="e27c2-119">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="e27c2-120">Na **zvolte typ zdroje dat** stránce **databáze**.</span><span class="sxs-lookup"><span data-stu-id="e27c2-120">On the **Choose a Data Source Type** page, select **Database**.</span></span>  
  
6.  <span data-ttu-id="e27c2-121">Na **vyberte datové připojení** vyberte datové připojení ze seznamu dostupných připojení.</span><span class="sxs-lookup"><span data-stu-id="e27c2-121">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="e27c2-122">Pokud požadované datové připojení není k dispozici vyberte **nové připojení** k vytvoření nové datové připojení.</span><span class="sxs-lookup"><span data-stu-id="e27c2-122">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>  
  
7.  <span data-ttu-id="e27c2-123">Vyberte **Ano, uložit připojení** uložit připojovací řetězec do konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="e27c2-123">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
8.  <span data-ttu-id="e27c2-124">Vyberte databázové objekty do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e27c2-124">Select the database objects to bring into your application.</span></span> <span data-ttu-id="e27c2-125">V takovém případě vyberete pole v tabulce, kterou byste uvítali <xref:System.Windows.Forms.TextBox> k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e27c2-125">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>  
  
9. <span data-ttu-id="e27c2-126">Nahraďte výchozí název datové sady, chcete-li.</span><span class="sxs-lookup"><span data-stu-id="e27c2-126">Replace the default dataset name if you want.</span></span>  
  
10. <span data-ttu-id="e27c2-127">Klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="e27c2-127">Click **Finish**.</span></span>  
  
11. <span data-ttu-id="e27c2-128">V **vlastnosti** okna, klikněte na šipku vedle položky <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost znovu.</span><span class="sxs-lookup"><span data-stu-id="e27c2-128">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="e27c2-129">V **DataSource** editoru typů uživatelského rozhraní, vyberte název pole, které chcete vytvořit vazbu <xref:System.Windows.Forms.TextBox> k.</span><span class="sxs-lookup"><span data-stu-id="e27c2-129">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>  
  
     <span data-ttu-id="e27c2-130">**DataSource** typ uživatelského rozhraní editoru zavře a datové sady, <xref:System.Windows.Forms.BindingSource> a specifické pro datové připojení jsou přidaná do svého formuláře tabulku adaptéru.</span><span class="sxs-lookup"><span data-stu-id="e27c2-130">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27c2-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="e27c2-131">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [<span data-ttu-id="e27c2-132">Přidání nových zdrojů dat</span><span class="sxs-lookup"><span data-stu-id="e27c2-132">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)  
 [<span data-ttu-id="e27c2-133">Okno zdroje dat</span><span class="sxs-lookup"><span data-stu-id="e27c2-133">Data Sources Window</span></span>](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
