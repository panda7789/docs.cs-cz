---
title: Výchozí funkce v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b695883ac7ec3fb0c459adb66214b0eceab3a128
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746130"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="79018-102">Výchozí funkce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="79018-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="79018-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DataGridView> poskytuje uživatelům významné množství výchozích funkcí.</span><span class="sxs-lookup"><span data-stu-id="79018-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="79018-104">Výchozí funkce</span><span class="sxs-lookup"><span data-stu-id="79018-104">Default Functionality</span></span>  
 <span data-ttu-id="79018-105">Ve výchozím nastavení <xref:System.Windows.Forms.DataGridView> ovládací prvek:</span><span class="sxs-lookup"><span data-stu-id="79018-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <span data-ttu-id="79018-106">Automaticky zobrazí záhlaví sloupců a záhlaví řádků, která zůstávají viditelná, když se tabulka posouvá svisle.</span><span class="sxs-lookup"><span data-stu-id="79018-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
- <span data-ttu-id="79018-107">Má záhlaví řádku, které obsahuje indikátor výběru pro aktuální řádek.</span><span class="sxs-lookup"><span data-stu-id="79018-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
- <span data-ttu-id="79018-108">Má v první buňce obdélník výběru.</span><span class="sxs-lookup"><span data-stu-id="79018-108">Has a selection rectangle in the first cell.</span></span>  
  
- <span data-ttu-id="79018-109">Má sloupce, u kterých se dá automaticky změnit velikost, když uživatel dvakrát klikne na oddělovače sloupců.</span><span class="sxs-lookup"><span data-stu-id="79018-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
- <span data-ttu-id="79018-110">Automaticky podporuje vizuální styly v systémech Windows XP a Windows Server 2003 při volání metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> z metody `Main` aplikace.</span><span class="sxs-lookup"><span data-stu-id="79018-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="79018-111">Kromě toho je možné upravit obsah <xref:System.Windows.Forms.DataGridView>ho ovládacího prvku ve výchozím nastavení:</span><span class="sxs-lookup"><span data-stu-id="79018-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
- <span data-ttu-id="79018-112">Pokud uživatel dvakrát klikne nebo stiskne F2 v buňce, ovládací prvek automaticky vloží buňku do režimu úprav a aktualizuje obsah buňky jako uživatelské typy.</span><span class="sxs-lookup"><span data-stu-id="79018-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
- <span data-ttu-id="79018-113">Pokud se uživatel posune na konec mřížky, uživatel uvidí, že je k dispozici řádek pro přidávání nových záznamů.</span><span class="sxs-lookup"><span data-stu-id="79018-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="79018-114">Když uživatel klikne na tento řádek, přidá se do ovládacího prvku <xref:System.Windows.Forms.DataGridView> nový řádek s výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="79018-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="79018-115">Když uživatel stiskne klávesu ESC, tento nový řádek zmizí.</span><span class="sxs-lookup"><span data-stu-id="79018-115">When the user presses ESC, this new row disappears.</span></span>  
  
- <span data-ttu-id="79018-116">Pokud uživatel klikne na záhlaví řádku, je vybrán celý řádek.</span><span class="sxs-lookup"><span data-stu-id="79018-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="79018-117">Při vázání ovládacího prvku <xref:System.Windows.Forms.DataGridView> ke zdroji dat nastavením jeho vlastnosti <xref:System.Windows.Forms.DataGridView.DataSource%2A> ovládací prvek:</span><span class="sxs-lookup"><span data-stu-id="79018-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
- <span data-ttu-id="79018-118">Automaticky používá názvy sloupců datového zdroje jako text záhlaví sloupce.</span><span class="sxs-lookup"><span data-stu-id="79018-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
- <span data-ttu-id="79018-119">Se naplní obsahem zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="79018-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="79018-120"><xref:System.Windows.Forms.DataGridView> sloupce jsou automaticky vytvořeny pro každý sloupec ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="79018-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
- <span data-ttu-id="79018-121">Vytvoří řádek pro každý viditelný řádek v tabulce.</span><span class="sxs-lookup"><span data-stu-id="79018-121">Creates a row for each visible row in the table.</span></span>  
  
- <span data-ttu-id="79018-122">Když uživatel klikne na záhlaví sloupce, automaticky seřadí řádky na základě podkladových dat.</span><span class="sxs-lookup"><span data-stu-id="79018-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79018-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79018-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="79018-124">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="79018-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
