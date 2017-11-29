---
title: "Výchozí funkce v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d6b15085c301f074ef6fcf9e60a75299c4b245b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c7575-102">Výchozí funkce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c7575-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c7575-103">Windows Forms <xref:System.Windows.Forms.DataGridView> řízení poskytuje uživatelům významné množství výchozí funkce.</span><span class="sxs-lookup"><span data-stu-id="c7575-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="c7575-104">Výchozí funkce</span><span class="sxs-lookup"><span data-stu-id="c7575-104">Default Functionality</span></span>  
 <span data-ttu-id="c7575-105">Ve výchozím nastavení <xref:System.Windows.Forms.DataGridView> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="c7575-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <span data-ttu-id="c7575-106">Automaticky zobrazí záhlaví sloupců a záhlaví řádků, které zůstávají zobrazena v tabulce se posouvá společně svisle.</span><span class="sxs-lookup"><span data-stu-id="c7575-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
-   <span data-ttu-id="c7575-107">Obsahuje řádek záhlaví, která obsahuje indikátor výběru pro aktuální řádek.</span><span class="sxs-lookup"><span data-stu-id="c7575-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
-   <span data-ttu-id="c7575-108">Má obdélníku výběru v první buňky.</span><span class="sxs-lookup"><span data-stu-id="c7575-108">Has a selection rectangle in the first cell.</span></span>  
  
-   <span data-ttu-id="c7575-109">Má sloupce, které mohou být automaticky nastavena velikost při poklepání oddělovače sloupců.</span><span class="sxs-lookup"><span data-stu-id="c7575-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
-   <span data-ttu-id="c7575-110">Vizuální styly na systémy Windows XP a řady Windows Server 2003 podporuje automaticky při <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda je volána z aplikace `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="c7575-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="c7575-111">Kromě toho obsah <xref:System.Windows.Forms.DataGridView> řízení lze upravovat ve výchozím nastavení:</span><span class="sxs-lookup"><span data-stu-id="c7575-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
-   <span data-ttu-id="c7575-112">Pokud uživatel poklikáním nebo stiskem tlačítka F2 v buňce, ovládacího prvku automaticky umístí do režimu úprav buňky a aktualizuje obsah buňky jako typy uživatelů.</span><span class="sxs-lookup"><span data-stu-id="c7575-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
-   <span data-ttu-id="c7575-113">Pokud uživatel posune na konec mřížky, uživatel uvidí, zda je k dispozici řádek pro přidání nové záznamy.</span><span class="sxs-lookup"><span data-stu-id="c7575-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="c7575-114">Po kliknutí na tento řádek, k přidání nového řádku <xref:System.Windows.Forms.DataGridView> ovládacího prvku s výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="c7575-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="c7575-115">Když uživatel stiskne ESC, tento nový řádek zmizí.</span><span class="sxs-lookup"><span data-stu-id="c7575-115">When the user presses ESC, this new row disappears.</span></span>  
  
-   <span data-ttu-id="c7575-116">Pokud uživatel klikne řádek záhlaví, vybere se celý řádek.</span><span class="sxs-lookup"><span data-stu-id="c7575-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="c7575-117">Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> řízení ke zdroji dat nastavením jeho <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost, ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="c7575-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
-   <span data-ttu-id="c7575-118">Automaticky použije názvy sloupců zdroji dat jako text záhlaví sloupce.</span><span class="sxs-lookup"><span data-stu-id="c7575-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
-   <span data-ttu-id="c7575-119">Obsah zdroje dat bude zahrnovat.</span><span class="sxs-lookup"><span data-stu-id="c7575-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="c7575-120"><xref:System.Windows.Forms.DataGridView>sloupce se automaticky vytvoří pro každý sloupec v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="c7575-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
-   <span data-ttu-id="c7575-121">Vytvoří řádek pro každý řádek viditelné v tabulce.</span><span class="sxs-lookup"><span data-stu-id="c7575-121">Creates a row for each visible row in the table.</span></span>  
  
-   <span data-ttu-id="c7575-122">Automaticky seřadí řádky podle zadaných dat, po kliknutí na záhlaví sloupce.</span><span class="sxs-lookup"><span data-stu-id="c7575-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7575-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7575-123">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="c7575-124">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="c7575-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
