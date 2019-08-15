---
title: 'Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 180fafa9ace5927fd84ec5dc0a1b2a342f771efd
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040017"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="543a3-102">Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="543a3-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="543a3-103">Po přidání ovládacích prvků do formuláře a určení uživatelského rozhraní vaší aplikace můžete navazovat ovládací prvky na zdroj dat, takže v době běhu mohou uživatelé upravovat a ukládat data související s aplikací.</span><span class="sxs-lookup"><span data-stu-id="543a3-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>

 <span data-ttu-id="543a3-104">Svázání ovládacího prvku nebo řady ovládacích prvků v model Windows Forms je nejsnadnějším pomocí <xref:System.Windows.Forms.BindingSource> ovládacího prvku jako most mezi ovládacími prvky ve formuláři a zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="543a3-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>

 <span data-ttu-id="543a3-105">Jeden nebo více ovládacích prvků na formuláři lze svázat s daty; v následujícím postupu <xref:System.Windows.Forms.TextBox> je ovládací prvek svázán se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="543a3-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>

 <span data-ttu-id="543a3-106">K dokončení postupu se předpokládá, že budete Přivážete ke zdroji dat odvozenému z databáze.</span><span class="sxs-lookup"><span data-stu-id="543a3-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="543a3-107">Další informace o vytváření zdrojů dat z jiných úložišť dat najdete v tématu [Přidání nových zdrojů dat](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="543a3-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>

## <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="543a3-108">Navázání ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="543a3-108">To bind a control at design time</span></span>

1. <span data-ttu-id="543a3-109"><xref:System.Windows.Forms.TextBox> Přetáhněte ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="543a3-109">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>

2. <span data-ttu-id="543a3-110">V okně **vlastnosti** :</span><span class="sxs-lookup"><span data-stu-id="543a3-110">In the **Properties** window:</span></span>

    1. <span data-ttu-id="543a3-111">Rozbalte uzel **(datové vazby)** .</span><span class="sxs-lookup"><span data-stu-id="543a3-111">Expand the **(DataBindings)** node.</span></span>

    2. <span data-ttu-id="543a3-112">Klikněte na šipku vedle <xref:System.Windows.Forms.TextBox.Text%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="543a3-112">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>

         <span data-ttu-id="543a3-113">Otevře se Editor typu uživatelského rozhraní **DataSource** .</span><span class="sxs-lookup"><span data-stu-id="543a3-113">The **DataSource** UI type editor opens.</span></span>

         <span data-ttu-id="543a3-114">Pokud byl zdroj dat dříve nakonfigurován pro projekt nebo formulář, zobrazí se.</span><span class="sxs-lookup"><span data-stu-id="543a3-114">If a data source has previously been configured for the project or form, it will appear.</span></span>

3. <span data-ttu-id="543a3-115">Kliknutím na **Přidat zdroj dat projektu** se můžete připojit k datům a vytvořit zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="543a3-115">Click **Add Project Data Source** to connect to data and create a data source.</span></span>

4. <span data-ttu-id="543a3-116">Na úvodní stránce **Průvodce konfigurací zdroje dat** klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="543a3-116">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>

5. <span data-ttu-id="543a3-117">Na stránce **Vybrat typ zdroje dat** vyberte možnost **databáze**.</span><span class="sxs-lookup"><span data-stu-id="543a3-117">On the **Choose a Data Source Type** page, select **Database**.</span></span>

6. <span data-ttu-id="543a3-118">Na stránce **Vyberte datové připojení** vyberte datové připojení ze seznamu dostupných připojení.</span><span class="sxs-lookup"><span data-stu-id="543a3-118">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="543a3-119">Pokud vaše požadované datové připojení není k dispozici, vyberte **nové připojení** a vytvořte nové datové připojení.</span><span class="sxs-lookup"><span data-stu-id="543a3-119">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>

7. <span data-ttu-id="543a3-120">Vyberte **Ano, uložit připojení** pro uložení připojovacího řetězce do konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="543a3-120">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>

8. <span data-ttu-id="543a3-121">Vyberte databázové objekty, které chcete přenést do aplikace.</span><span class="sxs-lookup"><span data-stu-id="543a3-121">Select the database objects to bring into your application.</span></span> <span data-ttu-id="543a3-122">V takovém případě vyberte pole v tabulce, které <xref:System.Windows.Forms.TextBox> chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="543a3-122">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>

9. <span data-ttu-id="543a3-123">Pokud chcete, nahraďte výchozí název datové sady.</span><span class="sxs-lookup"><span data-stu-id="543a3-123">Replace the default dataset name if you want.</span></span>

10. <span data-ttu-id="543a3-124">Klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="543a3-124">Click **Finish**.</span></span>

11. <span data-ttu-id="543a3-125">V okně **vlastnosti** klikněte znovu na šipku vedle <xref:System.Windows.Forms.TextBox.Text%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="543a3-125">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="543a3-126">V editoru typu uživatelského rozhraní **zdroje dat** vyberte název pole, <xref:System.Windows.Forms.TextBox> ke kterému se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="543a3-126">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>

     <span data-ttu-id="543a3-127">Editor typu uživatelského rozhraní **DataSource** se zavře a datová sada a <xref:System.Windows.Forms.BindingSource> adaptér tabulky, který je specifický pro toto datové připojení, se přidá do formuláře.</span><span class="sxs-lookup"><span data-stu-id="543a3-127">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>

## <a name="see-also"></a><span data-ttu-id="543a3-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="543a3-128">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="543a3-129">Přidání nových zdrojů dat</span><span class="sxs-lookup"><span data-stu-id="543a3-129">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)
- <span data-ttu-id="543a3-130">[Okno zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="543a3-130">[Data Sources Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span></span>
