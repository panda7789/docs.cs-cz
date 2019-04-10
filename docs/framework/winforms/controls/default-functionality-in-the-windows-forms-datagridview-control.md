---
title: Výchozí funkce v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: 26633b0abaa8c1c2916153b2236ecf9e4982fd68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208862"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Výchozí funkce v ovládacím prvku Windows Forms DataGridView
Windows Forms <xref:System.Windows.Forms.DataGridView> řízení poskytuje uživatelům značné množství výchozí funkce.  
  
## <a name="default-functionality"></a>Výchozí funkce  
 Ve výchozím nastavení <xref:System.Windows.Forms.DataGridView> ovládacího prvku:  
  
-   Automaticky zobrazí záhlaví sloupců a záhlaví řádků, které zůstávají viditelné jako tabulka posune svisle.  
  
-   Má záhlaví řádku, který obsahuje indikátor výběru pro aktuální řádek.  
  
-   V první buňky má obdélníku výběru.  
  
-   Má sloupce, které mohou být automaticky nastavena velikost při poklepání oddělovače sloupců.  
  
-   Automaticky podporuje vizuálních stylů Windows XP a Windows Server 2003 při <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda je volána z aplikace `Main` metody.  
  
 Kromě toho obsah <xref:System.Windows.Forms.DataGridView> ovládací prvek lze upravovat ve výchozím nastavení:  
  
-   Pokud uživatel dvakrát klikne nebo použije klávesu F2 v buňce, ovládací prvek automaticky umístí do režimu úprav buňku a aktualizuje obsah buňky jako zadaného uživatelem.  
  
-   Pokud uživatel přesune na konec objektu mřížky, uživateli se zobrazí, že řádek pro přidávání nových záznamů je k dispozici. Po kliknutí na tento řádek, na přidání nového řádku <xref:System.Windows.Forms.DataGridView> ovládacího prvku s výchozími hodnotami. Když uživatel stiskne klávesu ESC, tento nový řádek zmizí.  
  
-   Pokud uživatel klikne záhlaví řádku, je vybrán celý řádek.  
  
 Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> ovládacího prvku do zdroje dat tím, že nastavíte její <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastností, ovládacího prvku:  
  
-   Automaticky použije názvy sloupců zdroj dat jako text záhlaví sloupce.  
  
-   Je vyplněno obsahem datového zdroje. <xref:System.Windows.Forms.DataGridView> pro každý sloupec ve zdroji dat jsou automaticky vytvořeny sloupce.  
  
-   Vytvoří řádek pro každý viditelných řádků v tabulce.  
  
-   Automaticky řadí řádky založené na podkladová data, když uživatel klikne na záhlaví sloupce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView – ovládací prvek](datagridview-control-windows-forms.md)
