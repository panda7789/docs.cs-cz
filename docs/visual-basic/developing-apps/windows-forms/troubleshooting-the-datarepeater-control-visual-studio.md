---
title: Řešení potíží s ovládacím prvkem DataRepeater (Visual Studio)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d630dbf8601eeddd5ce3ea02696891a1087f71f
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>Řešení potíží s ovládacím prvkem DataRepeater (Visual Studio)
V tomto tématu jsou uvedeny běžné problémy, které mohou nastat při práci se <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>DataRepeater klávesnici a myš události není vyvolána  
 Některé <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nejsou vyvolá události ovládacího prvku, jako je například události klávesnice a myši. Toto je záměrné. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Samotném ovládacím prvku je kontejner pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> objekty a není přístupný v době běhu. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Nezpřístupňuje události v době návrhu. Událost proto nevyvolá kliknutím na položku nebo stisknutí klávesy, když položka má právě fokus.  
  
 Výjimkou je, když <xref:System.Windows.Forms.Control.Padding%2A> vlastnost nastavena na velké dostatek hodnota vystavit okrajů <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. V takovém případě kliknutím na zpřístupněný okraj vyvolá událost myši.  
  
 Chcete-li vyřešit tento problém, přidejte <xref:System.Windows.Forms.Panel> řídit k <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> části <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení a pak přidejte zbylé ovládací prvky <xref:System.Windows.Forms.Panel>. Poté můžete přidat kód pro <xref:System.Windows.Forms.Panel> ovládacího prvku obslužné rutiny události pro události klávesnice a myši.  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>DataRepeater částečně skrytá za Navigátor vazby  
 Po prvním přidání <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení na formulář a poté přidejte ovládací prvky vázané na data z **zdroje dat** okně <xref:System.Windows.Forms.BindingNavigator> řízení může zobrazit v horní části <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Jedná se o známé omezení **zdroje dat** okno a je konzistentní s chováním další ovládací prvky, jako <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 Můžete buď přesunout <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nižší, než <xref:System.Windows.Forms.BindingNavigator> řízení v době návrhu nebo přidat kód podobný tomuto v `Load` obslužné rutiny události.  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```csharp  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>Ovládací prvky se nezobrazí správně v době běhu  
 Některé ovládací prvky v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení, se nemusí zobrazit správně v době běhu. Proces používaný ke klonování ovládacích prvků z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> k <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> nemůže vždy určit všechny vlastnosti všech ovládacích prvků. Například, pokud přidáte nevázaný <xref:System.Windows.Forms.ListBox> řídit k <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení v době návrhu a naplnit její <xref:System.Windows.Forms.ListBox.Items%2A> kolekce s seznam řetězců, <xref:System.Windows.Forms.ListBox> bude prázdný, a to v době běhu. Důvodem je, že proces klonování nemůže vzít v úvahu <xref:System.Windows.Forms.ListBox.Items%2A> vlastnost.  
  
 Tyto problémy lze vyřešit obnovením chybějících vlastnosti v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> událost, která nastane po dokončení klonování výchozí. Následující příklad ukazuje, jak opravit <xref:System.Windows.Forms.ListBox.Items%2A> kolekce <xref:System.Windows.Forms.ListBox> řídit ve <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> obslužné rutiny události.  
  
 [!code-csharp[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>Chybí Symbol výběru v hlavičce položky  
 Pokud změníte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> vlastnost položky hlavičky v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení, některé volby barev může způsobit symbol výběru zmizí. Změna <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> vlastnost může také způsobit symbol výběru zmizí.  
  
 Nelze změnit barvu a velikost symbolu výběru.  
  
-   Pokud nastavíte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> k <xref:System.Drawing.Color.White%2A>, symbol výběru nebudou viditelné, když se vybere první položka.  
  
-   Pokud nastavíte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> k <xref:System.Drawing.Color.Black%2A>, symbol výběru nebudou viditelné, když je vybraný ovládací prvek a symbol tužky nebudou viditelné, když je ovládací prvek v režimu úprav.  
  
-   Pokud <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> je nastavena na hodnotu, která je menší než 11, symbol indikátoru v hlavičce položky se nezobrazí.  
  
 Můžete zadat vlastní symbol hlavičky a výběru položka pomocí <xref:System.Windows.Forms.PictureBox> řízení a monitorování <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> vlastnost <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> události <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: Změna rozložení ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení záhlaví položek v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: Zákaz přidávání a odstraňování položek DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [Postupy: Vyhledávání dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
