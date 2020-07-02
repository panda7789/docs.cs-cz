---
title: Režim vyplnění sloupce v ovládacím prvku DataGridView
description: Přečtěte si, jak model Windows Forms ovládací prvek DataGridView v režimu vyplňování sloupců mění velikost sloupců automaticky tak, aby vyplnila šířku dostupné oblasti zobrazení.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: 766a58954250d78ce6e44404730332b3158e1fad
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622819"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView
V režimu vyplnění sloupce <xref:System.Windows.Forms.DataGridView> změní ovládací prvek automaticky své sloupce tak, aby vyplnily šířku dostupné oblasti zobrazení. Ovládací prvek nezobrazuje vodorovný posuvník s výjimkou případů, kdy je nutné zachovat šířku každého sloupce, který se rovná nebo je větší než jeho <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnota vlastnosti.  
  
 Chování při změně velikosti každého sloupce závisí na jeho <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> Vlastnosti. Hodnota této vlastnosti je děděna z vlastnosti sloupce nebo z <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnosti ovládacího prvku, <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> Pokud je hodnota sloupce <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (výchozí hodnota).  
  
 Každý sloupec může mít jiný režim velikosti, ale všechny sloupce s režimem velikosti <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> budou sdílet šířku oblasti zobrazení, která se nepoužívá v ostatních sloupcích. Tato šířka je rozdělena mezi sloupce v režimu výplně v poměrech k jejich <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnotám vlastností. Pokud například dva sloupce mají <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty 100 a 200, bude první sloupec poloviční stejně velký jako druhý sloupec.  
  
## <a name="user-resizing-in-fill-mode"></a>Změna velikosti uživatele v režimu výplně  
 Na rozdíl od režimu změny velikosti, který mění velikost na základě obsahu buňky, nebrání uživatelům měnit velikost sloupců, které mají <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> hodnoty vlastností `true` . Když uživatel změní velikost sloupce v režimu výplně, všechny sloupce v režimu výplně po změně velikosti sloupce ( <xref:System.Windows.Forms.Control.RightToLeft%2A> `false` v opačném případě, pokud je, v opačném případě) se změní i na náhradu za změnu v dostupné šířce. Pokud sloupce se změněnou velikostí neobsahují, pak všechny ostatní sloupce v režimu výplně v ovládacím prvku mají větší velikost, aby bylo možné kompenzovat. Pokud v ovládacím prvku nejsou žádné další sloupce v režimu výplně, změna velikosti se ignoruje. Pokud se změní velikost sloupce, který není v režimu Fill, budou všechny sloupce v režimu výplně v ovládacím prvku měnit velikosti pro kompenzaci.  
  
 Po změně velikosti sloupce v režimu výplně se <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty pro všechny změněné sloupce upraví proporcionálně. Pokud například čtyři sloupce v režimu výplně mají <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty 100, změna velikosti druhého sloupce na polovinu jeho původní šířky bude mít za následek <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty 100, 50, 125 a 125. Změna velikosti sloupce, který není v režimu Fill, nezmění žádné <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty, protože sloupce v režimu výplně budou jednoduše měnit velikost, aby bylo možné kompenzovat stejné poměry.  
  
## <a name="content-based-fillweight-adjustment"></a>Úpravy FillWeight založené na obsahu  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>Hodnoty pro sloupce v režimu výplně můžete inicializovat pomocí <xref:System.Windows.Forms.DataGridView> metod automatické změny velikosti, jako je například <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metoda. Tato metoda nejprve vypočítává šířku, kterou sloupce vyžadovaná pro zobrazení jejich obsahu. V dalším kroku ovládací prvek upraví <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty pro všechny sloupce v režimu výplně tak, aby jejich poměry odpovídaly poměrům vypočítaných šířek. Nakonec ovládací prvek změní velikost sloupců v režimu výplně pomocí nových <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> proporcí tak, aby všechny sloupce v ovládacím prvku vyplnily dostupný vodorovný prostor.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Pomocí vhodných hodnot <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastností,, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> a <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> můžete přizpůsobit chování sloupců při mnoha různých scénářích.  
  
 Následující ukázkový kód umožňuje experimentovat s různými hodnotami pro <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> , a <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastností různých sloupců. V tomto příkladu <xref:System.Windows.Forms.DataGridView> je ovládací prvek vázán na svou vlastní <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekci a jeden sloupec je svázán s každým z <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A> vlastností,,, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> a <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> . Každý sloupec je také reprezentován řádkem v ovládacím prvku a změna hodnot v řádku bude aktualizovat vlastnosti odpovídajícího sloupce tak, aby bylo možné zjistit, jak hodnoty pracují.  
  
### <a name="code"></a>Kód  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Komentáře  
 Chcete-li použít tuto ukázkovou aplikaci:  
  
- Změňte velikost formuláře. Sledujte, jak se sloupce mění na šířku a přitom si zachovávají poměry označené <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnotami vlastností.  
  
- Změňte velikost sloupců přetažením oddělovačů sloupců pomocí myši. Sledujte, jak se <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty mění.  
  
- Změňte <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnotu pro jeden sloupec a přetažením změňte velikost formuláře. Sledujte, jak, když nastavíte dostatečně malý formulář, <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> hodnoty nejdou pod <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnoty.  
  
- Změňte <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnoty pro všechny sloupce na velké, aby kombinované hodnoty překročily šířku ovládacího prvku. Sledujte, jak se zobrazí vodorovný posuvník.  
  
- Změňte <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> hodnoty pro některé sloupce. Sledujte efekt při změně velikosti sloupců nebo formuláře.  
  
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
