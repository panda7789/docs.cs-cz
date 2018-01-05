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
ms.workload: dotnet
ms.openlocfilehash: ecb8cdaa4e8eb0498259c597e0de3f80c3106549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Výchozí funkce v ovládacím prvku Windows Forms DataGridView
Windows Forms <xref:System.Windows.Forms.DataGridView> řízení poskytuje uživatelům významné množství výchozí funkce.  
  
## <a name="default-functionality"></a>Výchozí funkce  
 Ve výchozím nastavení <xref:System.Windows.Forms.DataGridView> ovládacího prvku:  
  
-   Automaticky zobrazí záhlaví sloupců a záhlaví řádků, které zůstávají zobrazena v tabulce se posouvá společně svisle.  
  
-   Obsahuje řádek záhlaví, která obsahuje indikátor výběru pro aktuální řádek.  
  
-   Má obdélníku výběru v první buňky.  
  
-   Má sloupce, které mohou být automaticky nastavena velikost při poklepání oddělovače sloupců.  
  
-   Vizuální styly na systémy Windows XP a řady Windows Server 2003 podporuje automaticky při <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda je volána z aplikace `Main` metoda.  
  
 Kromě toho obsah <xref:System.Windows.Forms.DataGridView> řízení lze upravovat ve výchozím nastavení:  
  
-   Pokud uživatel poklikáním nebo stiskem tlačítka F2 v buňce, ovládacího prvku automaticky umístí do režimu úprav buňky a aktualizuje obsah buňky jako typy uživatelů.  
  
-   Pokud uživatel posune na konec mřížky, uživatel uvidí, zda je k dispozici řádek pro přidání nové záznamy. Po kliknutí na tento řádek, k přidání nového řádku <xref:System.Windows.Forms.DataGridView> ovládacího prvku s výchozími hodnotami. Když uživatel stiskne ESC, tento nový řádek zmizí.  
  
-   Pokud uživatel klikne řádek záhlaví, vybere se celý řádek.  
  
 Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> řízení ke zdroji dat nastavením jeho <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost, ovládacího prvku:  
  
-   Automaticky použije názvy sloupců zdroji dat jako text záhlaví sloupce.  
  
-   Obsah zdroje dat bude zahrnovat. <xref:System.Windows.Forms.DataGridView>sloupce se automaticky vytvoří pro každý sloupec v datovém zdroji.  
  
-   Vytvoří řádek pro každý řádek viditelné v tabulce.  
  
-   Automaticky seřadí řádky podle zadaných dat, po kliknutí na záhlaví sloupce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 [Ovládací prvek DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
