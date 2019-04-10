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
ms.openlocfilehash: a85745d39903719ec1e44ccf70df72d472720b7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214725"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView
V režim vyplnění sloupce <xref:System.Windows.Forms.DataGridView> ovládací prvek změní její sloupce automaticky tak, aby Šířka oblasti k dispozici zobrazení. Ovládací prvek nezobrazí vodorovný posuvník, kromě případů, kdy je také k zachování konzistence každý sloupec, rovna nebo větší než jeho <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnotu vlastnosti.  
  
 Nastavení velikosti chování každý sloupec závisí na jeho <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> vlastnost. Hodnota této vlastnosti je zděděno od sloupce <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnosti nebo ovládací prvek <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> vlastnosti, pokud je hodnota sloupce <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (výchozí hodnota).  
  
 Každý sloupec může mít jinou velikost režimu, ale žádné sloupce s velikostí režim <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> budou sdílet šířku zobrazované oblasti, kterou nepoužívají jiné sloupce. Tato šířka je rozdělena mezi režim vyplnění sloupce v proporcích vzhledem k jejich <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnot vlastností. Například, pokud mají dva sloupce <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty 100 až 200, prvního sloupce budou polovinu jako široká jako druhý sloupec.  
  
## <a name="user-resizing-in-fill-mode"></a>Změna velikosti v režim vyplnění uživatele  
 Na rozdíl od velikosti režimy, které mění velikost na základě obsahu buňky, režim vyplnění nezabrání uživatelům Změna velikosti sloupců, které mají <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> hodnoty vlastností `true`. Když uživatel změní režim vyplnění sloupce, žádné režim vyplnění sloupce za sloupcem změněnou velikostí (Pokud správné <xref:System.Windows.Forms.Control.RightToLeft%2A> je `false`; v opačném případě vlevo) se také změní velikost jako kompenzaci za změnu v hodnotě dostupné šířky. Pokud neexistují žádné režim vyplnění sloupce za sloupcem změněnou velikostí, pak všechny ostatní režim vyplnění sloupce v ovládacím prvku se mění velikost odpovídajícím způsobem upravit. Pokud neexistují žádné další režim vyplnění sloupce v ovládacím prvku, změně velikosti se ignoruje. Pokud sloupec, který není v režimu výplň je velikost, všechny režim vyplnění sloupce v ovládacím prvku změnit velikost odpovídajícím způsobem upravit.  
  
 Po změně velikosti režim vyplnění sloupce <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty pro všechny sloupce, které se změnily jsou upraveny proporcionálně. Například pokud máte čtyři režim vyplnění sloupce <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty od 100, změna velikosti druhý sloupec, který se polovina původní šířka způsobí <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty 100, 50, 125 a 125. Změna velikosti sloupce, který není v režimu výplně se nezmění žádný <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty, protože režim vyplnění sloupce jednoduše velikost se odpovídajícím způsobem upravit při zachování stejné rozměry.  
  
## <a name="content-based-fillweight-adjustment"></a>Úprava FillWeight podle obsahu  
 Můžete inicializovat <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty pro režim vyplnění sloupce s použitím <xref:System.Windows.Forms.DataGridView> automatické přizpůsobení velikosti metody, například <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metoda. Tato metoda nejprve vypočítá šířky vyžadované sloupce pro zobrazení jejich obsah. V dalším kroku upraví ovládacího prvku <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> tak, aby odpovídaly jejich proporce poměr šířky počítané hodnoty pro všechny režim vyplnění sloupce. A konečně, ovládací prvek změní režim vyplnění sloupce pomocí nového <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> poměru tak, aby všechny sloupce v ovládacím prvku vyplnit dostupný horizontální prostor.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Pomocí příslušné hodnoty pro <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, a <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> vlastnosti, si můžete přizpůsobit chování nastavení velikosti sloupce pro řadu různých scénářů.  
  
 Následující ukázkový kód umožňuje experimentovat s různými hodnotami parametru <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, a <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastnosti různých sloupců. V tomto příkladu <xref:System.Windows.Forms.DataGridView> ovládací prvek vázán na vlastní <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce a jeden sloupec je vázána na každý <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, a <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> vlastnosti. Jednotlivé sloupce je představováno také řádků v ovládacím prvku a změna hodnoty v řádku aktualizuje vlastnosti odpovídající sloupec tak, abyste viděli, jak pracují hodnoty.  
  
### <a name="code"></a>Kód  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Komentáře  
 Použití této ukázkové aplikaci:  
  
-   Změňte velikost formuláře. Sledujte, jak sloupce změnit jejich šířky při zachování rozměry indikován <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnot vlastností.  
  
-   Změníte velikost sloupce přetažením oddělovače sloupců pomocí myši. Podívejte se jak <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> změní hodnoty.  
  
-   Změnit <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnotu pro jeden sloupec a pak přetáhněte změnit velikost formuláře. Podívejte se jak, když nastavíte, dostatečně malá, formuláře <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> hodnoty se nepřenášejí níže <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnoty.  
  
-   Změnit <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnoty pro všechny sloupce velkému tak, aby součet hodnot být delší než šířka ovládacího prvku. Sledujte, jak se zobrazí vodorovný posuvník.  
  
-   Změnit <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> hodnoty pro některé sloupce. Při změně velikosti sloupce nebo formuláře můžete sledujte účinek.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
-   Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=nameWithType>
- [Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
