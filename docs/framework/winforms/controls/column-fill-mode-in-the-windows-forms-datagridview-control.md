---
title: Režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: 372ee5b0eb0101a13e7eb458ee8a8bcc06d3baff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView
V režim vyplnění sloupce <xref:System.Windows.Forms.DataGridView> řízení změní její sloupce automaticky tak, aby šířku oblasti dostupná zobrazení. Ovládací prvek nezobrazí vodorovného posuvníku kromě případů, kdy je potřeba zachovat každý sloupec, rovna nebo větší než jeho <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnotu vlastnosti.  
  
 Nastavení velikosti chování každý sloupec závisí na jeho <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> vlastnost. Hodnota této vlastnosti je zděděn z sloupce <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnost nebo ovládacího prvku <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> vlastnost, pokud je hodnota sloupce <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (výchozí hodnota).  
  
 Každý sloupec může mít jinou velikost režim, ale žádné sloupce s velikost režim <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> budou sdílet šířku zobrazení oblasti, kterou nepoužívají jiné sloupce. Tato šířka je rozdělena mezi režim vyplnění sloupce v poměru vzhledem k jejich <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnot vlastností. Například, pokud mají dva sloupce <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty 100 až 200, první sloupec budou polovinu jako široké jako druhý sloupec.  
  
## <a name="user-resizing-in-fill-mode"></a>Změna velikosti v režim vyplnění uživatele  
 Na rozdíl od režimů, které změna velikosti podle obsahu buňky změny velikosti, režim vyplnění nezabrání uživatelům Změna velikosti sloupců, které mají <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> hodnot vlastností `true`. Když uživatel změní režim vyplnění sloupce, žádné režim vyplnění sloupce po sloupci změněnou (vpravo Pokud <xref:System.Windows.Forms.Control.RightToLeft%2A> je `false`, jinak hodnota doleva) se také změní velikost kompenzovat změnu v hodnotě dostupná šířka. Pokud neexistují žádné režim vyplnění sloupce po sloupci změněnou, jsou všechny ostatní režim vyplnění sloupce v ovládacím prvku velikost odpovídajícím způsobem. Pokud neexistují žádné další režim vyplnění sloupce v ovládacím prvku, změna se ignoruje. Pokud se změnila velikost na sloupec, který není v režimu výplň, všechny režim vyplnění sloupce v ovládacím prvku změnit velikost odpovídajícím způsobem.  
  
 Po změně velikosti režim vyplnění sloupce <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty pro všechny sloupce, které změnily se úměrně upravena. Například pokud máte čtyři režim vyplnění sloupce <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> bude mít za následek hodnoty od 100, změna velikosti druhý sloupec poloviční původní šířku <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty 100, 50, 125 a 125. Změna velikosti na sloupec, který není v režimu výplně nedojde ke změně žádné <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty, protože režim vyplnění sloupce se jednoduše změnit velikost, při zachování stejné proporce odpovídajícím způsobem.  
  
## <a name="content-based-fillweight-adjustment"></a>Na základě obsahu FillWeight úpravy  
 Můžete inicializovat <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty pro režim vyplnění sloupce s použitím <xref:System.Windows.Forms.DataGridView> Automatická změna velikosti metody, jako například <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metoda. Tato metoda nejprve vypočítá šířek vyžadovanou sloupce k zobrazení jejich obsah. V dalším kroku upraví ovládacího prvku <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty pro všechny režim vyplnění sloupce tak, aby odpovídaly jejich proporcí proporce počítané šířky. Nakonec ovládacího prvku změní režim vyplnění sloupce pomocí nové <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> poměru tak, aby všechny sloupce v ovládacím prvku vyplňování dostupného místa vodorovné.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Pomocí příslušné hodnoty pro <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, a <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> vlastnosti, můžete přizpůsobit chování nastavení velikosti sloupce pro mnoho různých scénářů.  
  
 Následující ukázkový kód můžete experimentovat s různými hodnotami <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, a <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastnosti různé sloupce. V tomto příkladu <xref:System.Windows.Forms.DataGridView> ovládací prvek vázán na svůj vlastní <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce a jeden sloupec je vázaná na každý z <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, a <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> vlastnosti. Každý sloupec je také reprezentována řádků v ovládacím prvku a změna hodnoty v řádku, aktualizuje vlastnosti odpovídající sloupec tak, abyste viděli, jak hodnoty komunikovat.  
  
### <a name="code"></a>Kód  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Komentáře  
 Používat tuto aplikaci ukázku:  
  
-   Změníte velikost formuláře. Sledovat, jak se sloupců změnit jejich šířky při zachování proporce indikován <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty vlastností.  
  
-   Změníte velikost sloupců přetažením oddělovače sloupců pomocí myši. Sledovat, jak <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty změnit.  
  
-   Změna <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnotu pro jeden sloupec a pak přetáhněte změnit velikost formuláře. Sledovat, když se tak dostatečně malé formuláře <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> hodnoty se nepřenášejí níže <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnoty.  
  
-   Změna <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnoty pro všechny sloupce velké počty tak, aby součet hodnot překročit šířku ovládacího prvku. Sledujte, jak se zobrazuje vodorovného posuvníku.  
  
-   Změna <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> hodnoty pro některé sloupce. Při změně velikosti sloupce nebo formuláře můžete sledujte účinek.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.  
  
-   Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=nameWithType>  
 [Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
