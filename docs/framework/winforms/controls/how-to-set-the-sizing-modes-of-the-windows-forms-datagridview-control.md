---
title: "Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 811c5edd2f12794035b66260f17255283f405cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView
Následující postupy ukazují některé běžné scénáře, které přizpůsobit nebo v kombinaci k dispozici pro nastavení velikosti možností <xref:System.Windows.Forms.DataGridView> řízení a pro určité sloupce v ovládacím prvku.  
  
### <a name="to-create-a-fixed-width-column"></a>K vytvoření sloupce pevnou šířkou  
  
-   Nastavit <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> vlastnost <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> vlastnost `true`a <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> vlastnost na hodnotu odpovídající.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Chcete-li vytvořit sloupec, který přizpůsobí jeho velikost podle jeho obsahu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnost do režimu nastavení velikosti podle obsahu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Chcete-li vytvořit režim vyplnění sloupce pro hodnoty různou velikost a důležitostí  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> nastavení režimu nastavení velikosti pro všechny sloupce, které nepřepisují tuto hodnotu. Nastavte <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> vlastnosti sloupce, které chcete hodnoty, které jsou přímo úměrná svoje průměru obsahu šířky. Nastavte <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastnosti důležitých sloupcích zajistit částečné zobrazení obsahu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu dokončení poskytuje ukázkový aplikace, která vám může pomoct pochopit nastavení velikosti možností popsaných v tomto tématu.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Používat tuto aplikaci ukázku:  
  
-   Změníte velikost formuláře. Sledovat, jak změnit režim vyplnění sloupce jejich šířky při zachování proporce indikován <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty vlastností. Sledovat, jak sloupec <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> zabraňuje v jeho změnu při formuláře je příliš malá.  
  
-   Změníte velikost sloupců přetažením oddělovače sloupců pomocí myši. Sledovat, jak některé sloupce nesmí být změněnou velikostí a jak s možností změny velikosti sloupce nelze provést užší než jejich minimální šířku.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém a System.Windows.Forms sestavení.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
