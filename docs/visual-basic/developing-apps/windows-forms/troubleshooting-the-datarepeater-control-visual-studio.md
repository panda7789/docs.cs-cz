---
title: Řešení potíží s ovládacím prvkem DataRepeater (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
ms.openlocfilehash: 7b045e1c45221cbde82c88286da8e698a763d844
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580600"
---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>Řešení potíží s ovládacím prvkem DataRepeater (Visual Studio)
Toto téma obsahuje seznam běžných problémů, které mohou nastat, když pracujete <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>Události myši a klávesnice DataRepeater není aktivovaná  
 Některé <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nejsou vyvolány události ovládacích prvků, jako je například události klávesnice a myši. Jedná se o účel. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Samotný ovládací prvek slouží jako kontejner pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> objektů a k nim přístup za běhu. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Nevystavuje událostí v době návrhu. Událost proto nevyvolá kliknete na položku nebo stisknutím klávesy v situaci, kdy položka má fokus.  
  
 Výjimkou je, když <xref:System.Windows.Forms.Control.Padding%2A> je nastavena na velkou hodnotu dost vystavit okraji <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. V takovém případě kliknutí na okraji vystavené vyvolá událost myši.  
  
 Chcete-li tento problém vyřešit, přidejte <xref:System.Windows.Forms.Panel> ovládací prvek <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> část <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek a pak přidejte rest ovládací prvky <xref:System.Windows.Forms.Panel>. Poté můžete přidat kód do <xref:System.Windows.Forms.Panel> ovládacího prvku obslužné rutiny událostí pro události klávesnice a myši.  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>DataRepeater je částečně skrytá pod možností Navigátor vazby  
 Pokud nejprve přidáte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek na formuláři a potom přidat ovládací prvky vázané na data z **zdroje dat** okně <xref:System.Windows.Forms.BindingNavigator> ovládací prvek může zobrazit v horní části <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Jedná o známé omezení **zdroje dat** okno a je konzistentní s chováním další ovládací prvky, jako <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 Můžete buď přesunout <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nižší než <xref:System.Windows.Forms.BindingNavigator> ovládací prvek v době návrhu nebo přidejte kód podobný tomuto do `Load` obslužné rutiny události.  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```csharp  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>Ovládací prvky jsou se nezobrazuje správně za běhu  
 Některé ovládací prvky v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> podle očekávání v době běhu se nemusí zobrazit ovládací prvek. Proces klonování ovládacích prvků <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> k <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> vždy nelze určit všechny vlastnosti všech ovládacích prvků. Například, pokud přidáte nevázaný <xref:System.Windows.Forms.ListBox> mít pod kontrolou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek v době návrhu a naplnění jeho <xref:System.Windows.Forms.ListBox.Items%2A> kolekce s seznam řetězců, <xref:System.Windows.Forms.ListBox> za běhu bude prázdný. Důvodem je, že klonování nejde vzít v úvahu <xref:System.Windows.Forms.ListBox.Items%2A> vlastnost.  
  
 Problémy, jako je to můžete vyřešit tak, že obnovíte chybí vlastnosti v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> událost, která nastane po dokončení klonování výchozí. Následující příklad ukazuje, jak opravit <xref:System.Windows.Forms.ListBox.Items%2A> kolekce <xref:System.Windows.Forms.ListBox> v ovládacím prvku <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> obslužné rutiny události.  
  
 [!code-csharp[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>Výběr symbolu na záhlaví položky nebyl nalezen  
 Při změně <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> vlastnost položky hlavičky v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku, některé volby barev může způsobit, že výběr symbol zmizí. Změna <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> vlastnost může také způsobit symbol výběru zmizí.  
  
 Nelze změnit barvu a velikost výběru symbolu.  
  
-   Pokud jste nastavili <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> k <xref:System.Drawing.Color.White%2A>, symbol výběru se nezobrazí, nejprve vybranou položku.  
  
-   Pokud jste nastavili <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> k <xref:System.Drawing.Color.Black%2A>, symbol výběru se nezobrazí, pokud je vybrán ovládací prvek a symbol tužky nebudou viditelné, když je ovládací prvek v režimu úprav.  
  
-   Pokud <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> je nastavena na hodnotu, která je menší než 11, nebude zobrazen indikátor symboly v hlavičce položky.  
  
 Můžete zadat vlastní položky záhlaví a výběr symbolu pomocí <xref:System.Windows.Forms.PictureBox> řízení a monitorování <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> vlastnost <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> událost <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
## <a name="see-also"></a>Viz také:
- [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Změna rozložení ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Postupy: Zobrazení položek záhlaví v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Zákaz přidávání a odstraňování položek DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)
- [Postupy: Vyhledávání dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
