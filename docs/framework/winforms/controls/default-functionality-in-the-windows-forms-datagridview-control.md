---
title: Výchozí funkce v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: 26633b0abaa8c1c2916153b2236ecf9e4982fd68
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208862"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ea52a-102">Výchozí funkce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ea52a-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ea52a-103">Windows Forms <xref:System.Windows.Forms.DataGridView> řízení poskytuje uživatelům značné množství výchozí funkce.</span><span class="sxs-lookup"><span data-stu-id="ea52a-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="ea52a-104">Výchozí funkce</span><span class="sxs-lookup"><span data-stu-id="ea52a-104">Default Functionality</span></span>  
 <span data-ttu-id="ea52a-105">Ve výchozím nastavení <xref:System.Windows.Forms.DataGridView> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="ea52a-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <span data-ttu-id="ea52a-106">Automaticky zobrazí záhlaví sloupců a záhlaví řádků, které zůstávají viditelné jako tabulka posune svisle.</span><span class="sxs-lookup"><span data-stu-id="ea52a-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
-   <span data-ttu-id="ea52a-107">Má záhlaví řádku, který obsahuje indikátor výběru pro aktuální řádek.</span><span class="sxs-lookup"><span data-stu-id="ea52a-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
-   <span data-ttu-id="ea52a-108">V první buňky má obdélníku výběru.</span><span class="sxs-lookup"><span data-stu-id="ea52a-108">Has a selection rectangle in the first cell.</span></span>  
  
-   <span data-ttu-id="ea52a-109">Má sloupce, které mohou být automaticky nastavena velikost při poklepání oddělovače sloupců.</span><span class="sxs-lookup"><span data-stu-id="ea52a-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
-   <span data-ttu-id="ea52a-110">Automaticky podporuje vizuálních stylů Windows XP a Windows Server 2003 při <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda je volána z aplikace `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="ea52a-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="ea52a-111">Kromě toho obsah <xref:System.Windows.Forms.DataGridView> ovládací prvek lze upravovat ve výchozím nastavení:</span><span class="sxs-lookup"><span data-stu-id="ea52a-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
-   <span data-ttu-id="ea52a-112">Pokud uživatel dvakrát klikne nebo použije klávesu F2 v buňce, ovládací prvek automaticky umístí do režimu úprav buňku a aktualizuje obsah buňky jako zadaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="ea52a-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
-   <span data-ttu-id="ea52a-113">Pokud uživatel přesune na konec objektu mřížky, uživateli se zobrazí, že řádek pro přidávání nových záznamů je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ea52a-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="ea52a-114">Po kliknutí na tento řádek, na přidání nového řádku <xref:System.Windows.Forms.DataGridView> ovládacího prvku s výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="ea52a-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="ea52a-115">Když uživatel stiskne klávesu ESC, tento nový řádek zmizí.</span><span class="sxs-lookup"><span data-stu-id="ea52a-115">When the user presses ESC, this new row disappears.</span></span>  
  
-   <span data-ttu-id="ea52a-116">Pokud uživatel klikne záhlaví řádku, je vybrán celý řádek.</span><span class="sxs-lookup"><span data-stu-id="ea52a-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="ea52a-117">Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> ovládacího prvku do zdroje dat tím, že nastavíte její <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastností, ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="ea52a-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
-   <span data-ttu-id="ea52a-118">Automaticky použije názvy sloupců zdroj dat jako text záhlaví sloupce.</span><span class="sxs-lookup"><span data-stu-id="ea52a-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
-   <span data-ttu-id="ea52a-119">Je vyplněno obsahem datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="ea52a-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="ea52a-120"><xref:System.Windows.Forms.DataGridView> pro každý sloupec ve zdroji dat jsou automaticky vytvořeny sloupce.</span><span class="sxs-lookup"><span data-stu-id="ea52a-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
-   <span data-ttu-id="ea52a-121">Vytvoří řádek pro každý viditelných řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="ea52a-121">Creates a row for each visible row in the table.</span></span>  
  
-   <span data-ttu-id="ea52a-122">Automaticky řadí řádky založené na podkladová data, když uživatel klikne na záhlaví sloupce.</span><span class="sxs-lookup"><span data-stu-id="ea52a-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea52a-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea52a-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="ea52a-124">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="ea52a-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
