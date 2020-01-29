---
title: Režim vyplnění sloupce v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: 43b8915efe303b6f56cd4adf5fdbd69f51b0b754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736871"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView
V režimu vyplnění sloupce mění ovládací prvek <xref:System.Windows.Forms.DataGridView> své sloupce automaticky tak, aby vyplnil šířku dostupné oblasti zobrazení. Ovládací prvek nezobrazuje vodorovný posuvník s výjimkou případů, kdy je nutné zachovat šířku každého sloupce, který je větší nebo roven hodnotě vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>.  
  
 Chování každého sloupce závisí na jeho vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>. Hodnota této vlastnosti je děděna z vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> sloupce nebo vlastnosti <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> ovládacího prvku, pokud je hodnota sloupce <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (výchozí hodnota).  
  
 Každý sloupec může mít jiný režim velikosti, ale všechny sloupce s režimem velikosti <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> budou sdílet šířku oblasti zobrazení, která se nepoužívá v ostatních sloupcích. Tato šířka je rozdělena mezi sloupce v režimu výplně v poměrech k jejich hodnotám <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> vlastností. Pokud například dva sloupce mají <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty 100 a 200, bude první sloupec poloviční stejně velký jako druhý sloupec.  
  
## <a name="user-resizing-in-fill-mode"></a>Změna velikosti uživatele v režimu výplně  
 Na rozdíl od režimu změny velikosti, který mění velikost na základě obsahu buňky, nebrání uživatelům měnit velikost sloupců, které mají <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> hodnoty vlastností `true`. Když uživatel změní velikost sloupce režimu výplně, všechny sloupce v režimu výplně po změně velikosti sloupce (napravo, pokud <xref:System.Windows.Forms.Control.RightToLeft%2A> je `false`; v opačném případě doleva) se změní také tak, aby se změnila velikost dostupné šířky. Pokud sloupce se změněnou velikostí neobsahují, pak všechny ostatní sloupce v režimu výplně v ovládacím prvku mají větší velikost, aby bylo možné kompenzovat. Pokud v ovládacím prvku nejsou žádné další sloupce v režimu výplně, změna velikosti se ignoruje. Pokud se změní velikost sloupce, který není v režimu Fill, budou všechny sloupce v režimu výplně v ovládacím prvku měnit velikosti pro kompenzaci.  
  
 Po změně velikosti sloupce režimu výplně se hodnoty <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> pro všechny změněné sloupce upraví proporcionálně. Pokud například čtyři sloupce v režimu výplně mají <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty 100, změna velikosti druhého sloupce na polovinu jeho původní šířky bude mít za následek <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty 100, 50, 125 a 125. Změna velikosti sloupce, který není v režimu Fill, nezmění žádné <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty, protože sloupce v režimu výplně budou jednoduše měnit velikost, aby bylo zachováno stejné poměry.  
  
## <a name="content-based-fillweight-adjustment"></a>Úpravy FillWeight založené na obsahu  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty pro sloupce v režimu výplně můžete inicializovat pomocí metod <xref:System.Windows.Forms.DataGridView> automatické změny velikosti, jako je například metoda <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>. Tato metoda nejprve vypočítává šířku, kterou sloupce vyžadovaná pro zobrazení jejich obsahu. V dalším kroku ovládací prvek upraví hodnoty <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> pro všechny sloupce v režimu výplně tak, aby jejich poměry odpovídaly poměrům vypočítaných šířek. Nakonec ovládací prvek změní velikost sloupců v režimu výplně pomocí nových <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>ch proporcí tak, aby všechny sloupce v ovládacím prvku vyplnily dostupný vodorovný prostor.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Pomocí vhodných hodnot vlastností <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>a <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> můžete přizpůsobit chování sloupců pro mnoho různých scénářů.  
  
 Následující ukázkový kód umožňuje experimentovat s různými hodnotami pro <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>a <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastnosti různých sloupců. V tomto příkladu je ovládací prvek <xref:System.Windows.Forms.DataGridView> vázán na svou vlastní <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekci a jeden sloupec je svázán se všemi vlastnostmi <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>a <xref:System.Windows.Forms.DataGridViewColumn.Width%2A>. Každý sloupec je také reprezentován řádkem v ovládacím prvku a změna hodnot v řádku bude aktualizovat vlastnosti odpovídajícího sloupce tak, aby bylo možné zjistit, jak hodnoty pracují.  
  
### <a name="code"></a>Kód  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Komentáře  
 Chcete-li použít tuto ukázkovou aplikaci:  
  
- Změňte velikost formuláře. Sledujte, jak se sloupce mění na šířku a přitom zachovávají poměry označené hodnotami <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> vlastností.  
  
- Změňte velikost sloupců přetažením oddělovačů sloupců pomocí myši. Sledujte, jak se hodnoty <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> mění.  
  
- Změňte hodnotu <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> pro jeden sloupec a přetažením změňte velikost formuláře. Sledujte, jak, když nastavíte dostatečně malý formulář, hodnoty <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> neodpovídají hodnotám <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>.  
  
- Změňte hodnoty <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> všech sloupcích na velká čísla tak, aby kombinované hodnoty překročily šířku ovládacího prvku. Sledujte, jak se zobrazí vodorovný posuvník.  
  
- Změňte hodnoty <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> pro některé sloupce. Sledujte efekt při změně velikosti sloupců nebo formuláře.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
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
