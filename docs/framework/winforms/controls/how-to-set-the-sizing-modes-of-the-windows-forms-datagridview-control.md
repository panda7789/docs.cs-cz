---
title: Nastavení režimů změny velikosti ovládacího prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 15b084afa4149ac43d40aeae7f35f0eaff5ac0e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738402"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView
Následující postupy ukazují některé běžné scénáře, které přizpůsobují nebo kombinují možnosti změny velikosti dostupné pro ovládací prvek <xref:System.Windows.Forms.DataGridView> a pro konkrétní sloupce v ovládacím prvku.  
  
### <a name="to-create-a-fixed-width-column"></a>Vytvoření sloupce s pevnou šířkou  
  
- Vlastnost <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> nastavte na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, vlastnost <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> na <xref:System.Windows.Forms.DataGridViewTriState.False>, vlastnost <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> na `true`a vlastnost <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> na odpovídající hodnotu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Vytvoření sloupce, který upraví jeho velikost tak, aby odpovídal jeho obsahu  
  
- Vlastnost <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> nastavte na režim změny velikosti podle obsahu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Vytvoření sloupců v režimu výplně pro hodnoty různé velikosti a důležitosti  
  
- Nastavte vlastnost <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> pro nastavení režimu změny velikosti pro všechny sloupce, které nepřepisují tuto hodnotu. Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> sloupců na hodnoty, které jsou úměrné jejich průměrné šířce obsahu. Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> důležitých sloupců, aby se zajistilo částečné zobrazení obsahu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kompletního kódu poskytuje ukázkovou aplikaci, která vám pomůže pochopit možnosti změny velikosti popsané v tomto tématu.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Chcete-li použít tuto ukázkovou aplikaci:  
  
- Změňte velikost formuláře. Sledujte, jak se sloupce v režimu výplně mění na šířku a přitom zachovávají poměry označené hodnotami <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> vlastností. V případě, že je formulář příliš malý, sledujte, jak se <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> sloupce zabrání v změně.  
  
- Změňte velikost sloupců přetažením oddělovačů sloupců pomocí myši. Sledujte, jak se u některých sloupců nedá změnit velikost, a jak se sloupce s možností změny velikosti nedají zúžit, než jaká je jejich minimální šířka.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
