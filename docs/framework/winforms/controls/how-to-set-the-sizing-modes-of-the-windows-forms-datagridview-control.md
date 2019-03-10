---
title: 'Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 85322afcaae96b07d085d2b44d923542ecbf9bf6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708883"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView
Následující postupy ukazují některé běžné scénáře, které přizpůsobit nebo můžete zkombinovat k dispozici pro nastavení velikosti možností <xref:System.Windows.Forms.DataGridView> ovládacího prvku a pro konkrétní sloupců v ovládacím prvku.  
  
### <a name="to-create-a-fixed-width-column"></a>Chcete-li vytvořit sloupec pevnou šířkou  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> vlastnost <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> vlastnost `true`a <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> vlastnost na odpovídající hodnotu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Chcete-li vytvořit sloupec, který upraví jeho velikost podle jeho obsahu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnosti k určení velikosti na základě obsahu režimu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Chcete-li vytvořit režim vyplnění sloupce pro hodnoty různých velikostí a význam  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> nastavit režim změny velikosti pro všechny sloupce, které nepřepisují tuto hodnotu. Nastavte <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> šířku obsahu vlastnosti sloupce se mají hodnoty, které jsou přímo úměrná jejich průměr. Nastavte <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastnosti sloupců důležité k zajištění částečné zobrazení obsahu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kompletní kód poskytuje ukázkové aplikace, která vám pomůžou pochopit nastavení velikosti možností popsané v tomto tématu.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Použití této ukázkové aplikaci:  
  
-   Změňte velikost formuláře. Sledujte, jak změnit režim vyplnění sloupce jejich šířky při zachování rozměry indikován <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnot vlastností. Podívejte se jak sloupce <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> brání jeho změnu, když je formulář příliš malá.  
  
-   Změníte velikost sloupce přetažením oddělovače sloupců pomocí myši. Sledujte, jak nemůže být některé sloupce, jehož velikost byla změněna a jak umožňující změnu velikosti sloupců nelze nastavit užší než jeho minimální šířku.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
