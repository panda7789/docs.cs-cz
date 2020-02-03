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
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Výchozí funkce v ovládacím prvku Windows Forms DataGridView
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DataGridView> poskytuje uživatelům významné množství výchozích funkcí.  
  
## <a name="default-functionality"></a>Výchozí funkce  
 Ve výchozím nastavení <xref:System.Windows.Forms.DataGridView> ovládací prvek:  
  
- Automaticky zobrazí záhlaví sloupců a záhlaví řádků, která zůstávají viditelná, když se tabulka posouvá svisle.  
  
- Má záhlaví řádku, které obsahuje indikátor výběru pro aktuální řádek.  
  
- Má v první buňce obdélník výběru.  
  
- Má sloupce, u kterých se dá automaticky změnit velikost, když uživatel dvakrát klikne na oddělovače sloupců.  
  
- Automaticky podporuje vizuální styly v systémech Windows XP a Windows Server 2003 při volání metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> z metody `Main` aplikace.  
  
 Kromě toho je možné upravit obsah <xref:System.Windows.Forms.DataGridView>ho ovládacího prvku ve výchozím nastavení:  
  
- Pokud uživatel dvakrát klikne nebo stiskne F2 v buňce, ovládací prvek automaticky vloží buňku do režimu úprav a aktualizuje obsah buňky jako uživatelské typy.  
  
- Pokud se uživatel posune na konec mřížky, uživatel uvidí, že je k dispozici řádek pro přidávání nových záznamů. Když uživatel klikne na tento řádek, přidá se do ovládacího prvku <xref:System.Windows.Forms.DataGridView> nový řádek s výchozími hodnotami. Když uživatel stiskne klávesu ESC, tento nový řádek zmizí.  
  
- Pokud uživatel klikne na záhlaví řádku, je vybrán celý řádek.  
  
 Při vázání ovládacího prvku <xref:System.Windows.Forms.DataGridView> ke zdroji dat nastavením jeho vlastnosti <xref:System.Windows.Forms.DataGridView.DataSource%2A> ovládací prvek:  
  
- Automaticky používá názvy sloupců datového zdroje jako text záhlaví sloupce.  
  
- Se naplní obsahem zdroje dat. <xref:System.Windows.Forms.DataGridView> sloupce jsou automaticky vytvořeny pro každý sloupec ve zdroji dat.  
  
- Vytvoří řádek pro každý viditelný řádek v tabulce.  
  
- Když uživatel klikne na záhlaví sloupce, automaticky seřadí řádky na základě podkladových dat.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
