---
title: "Postupy: vytvoření hlavního podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f17cb86c3ea0ea056291a51becd7ecf9f73d0a73
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a><span data-ttu-id="8e194-102">Postupy: Vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="8e194-102">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>
<span data-ttu-id="8e194-103">Související data můžete zobrazit pomocí dvou nebo více <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvky pro vytvoření hlavního a podrobného formuláře.</span><span class="sxs-lookup"><span data-stu-id="8e194-103">You can display related data by using two or more <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls to create a master/detail form.</span></span> <span data-ttu-id="8e194-104">Například můžete chtít zobrazit seznam zákazníků v jednom <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>a když uživatel vybere zákazníka, zobrazí se seznam objednávek tohoto zákazníka za sekundu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="8e194-104">For example, you might want to display a list of customers in one <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and when the user selects a customer, display a list of that customer's orders in a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
 <span data-ttu-id="8e194-105">Související data můžete zobrazit přetažením podrobné položky, které sdílejí stejný uzel hlavní tabulky z **zdroje dat** okna do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8e194-105">You can display related data by dragging detail items that share the same master table node from the **Data Sources** window onto a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="8e194-106">Například pokud je zdroj dat, který má tabulku zákazníků a související tabulky objednávky, vidíte obě tabulky jako uzly nejvyšší úrovně ve stromovém zobrazení v **zdroje dat** okno.</span><span class="sxs-lookup"><span data-stu-id="8e194-106">For example, if you have a data source that has a Customers table and a related Orders table, you see both tables as top-level nodes in the tree view in the **Data Sources** window.</span></span> <span data-ttu-id="8e194-107">Rozbalte uzel zákazníkům, aby mohli zobrazit sloupce.</span><span class="sxs-lookup"><span data-stu-id="8e194-107">Expand the Customers node so that you can see the columns.</span></span> <span data-ttu-id="8e194-108">Všimněte si, že je posledního sloupce v seznamu rozšíření uzlu, který představuje tabulky objednávky.</span><span class="sxs-lookup"><span data-stu-id="8e194-108">Notice that the last column in the list is an expandable node that represents the Orders table.</span></span> <span data-ttu-id="8e194-109">Tento uzel představuje související objednávky pro zákazníka.</span><span class="sxs-lookup"><span data-stu-id="8e194-109">This node represents the related orders for a customer.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a><span data-ttu-id="8e194-110">Pro zobrazení souvisejících dat ve dvou ovládacích prvků DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8e194-110">To display related data in two DataRepeater controls</span></span>  
  
1.  <span data-ttu-id="8e194-111">Přetáhněte dva <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> z ovládací prvky **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8e194-111">Drag two <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="8e194-112">Přetáhněte obslužné rutiny pro změnu velikosti a pozice k určení velikosti ovládacích prvků a umístit je vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="8e194-112">Drag the sizing and position handles to size the controls and position them side-by-side.</span></span>  
  
3.  <span data-ttu-id="8e194-113">Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.</span><span class="sxs-lookup"><span data-stu-id="8e194-113">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e194-114">Pokud **zdroje dat** přidejte do něj zdroj dat, je prázdný.</span><span class="sxs-lookup"><span data-stu-id="8e194-114">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="8e194-115">Další informace najdete v tématu [přidat nové zdroje dat](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="8e194-115">For more information, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="8e194-116">V **zdroje dat** okně vyberte nejvyšší uzel pro hlavní tabulku.</span><span class="sxs-lookup"><span data-stu-id="8e194-116">In the **Data Sources** window, select the top-level node for the master table.</span></span>  
  
5.  <span data-ttu-id="8e194-117">Změňte typ hlavní tabulky Podrobnosti o kliknutím **podrobnosti** v rozevíracím seznamu na uzlu tabulky.</span><span class="sxs-lookup"><span data-stu-id="8e194-117">Change the drop type of the master table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="8e194-118">Přetáhněte uzel hlavní tabulky na oblast šablony položky první <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8e194-118">Drag the master table node onto the item template region of the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
7.  <span data-ttu-id="8e194-119">Rozbalte uzel hlavní tabulka a vyberte uzel podrobností pro související tabulky.</span><span class="sxs-lookup"><span data-stu-id="8e194-119">Expand the master table node and select the detail node for the related table.</span></span>  
  
8.  <span data-ttu-id="8e194-120">Změňte typ tabulky Podrobnosti o kliknutím **podrobnosti** v rozevíracím seznamu na uzlu tabulky.</span><span class="sxs-lookup"><span data-stu-id="8e194-120">Change the drop type of the detail table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
9. <span data-ttu-id="8e194-121">Vyberte uzel této tabulky a přetáhněte ji na oblast šablony položky druhý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8e194-121">Select this table node and drag it onto the item template region of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e194-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e194-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="8e194-123">Úvod do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8e194-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8e194-124">Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8e194-124">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8e194-125">Postupy: zobrazení souvisejících dat v systému Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="8e194-125">How to: Display Related Data in a Windows Forms Application</span></span>](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [<span data-ttu-id="8e194-126">Postupy: Změna vzhledu ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8e194-126">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8e194-127">Řešení potíží s ovládacím prvkem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8e194-127">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
