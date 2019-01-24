---
title: Úvod k ovládacímu prvku DataRepeater (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
ms.openlocfilehash: c9d95f41e9857d70e81cafc94e5e3bffd4cbc3d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580704"
---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>Úvod k ovládacímu prvku DataRepeater (Visual Studio)
Visual Basic Power Pack <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> posuvného kontejneru je ovládací prvek pro opakované ovládací prvky, které zobrazují data, například řádky v tabulce databáze. Může sloužit jako alternativu k <xref:System.Windows.Forms.DataGridView> ovládací prvek, když potřebujete větší kontrolu nad rozložením data. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> "Se opakuje" skupina souvisejících ovládacích prvků tak, že vytvoříte více instancí v posouvání zobrazení. To umožňuje uživatelům zobrazit několik záznamů ve stejnou dobu.  
  
## <a name="overview"></a>Přehled  
 V době návrhu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek se skládá ze dvou částí. Vnější oddíl je *zobrazení*, kde posuvné data zobrazí v době běhu. Vnitřní (hlavní) části označované jako *šablony položky*, kam umístit ovládací prvky, které se budou opakovat v době běhu, většinou jeden ovládací prvek pro každé pole ve zdroji dat je. Ovládací prvky v šabloně položky a vlastnosti jsou zapouzdřeny v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> vlastnost.  
  
 V době běhu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> je zkopírován do virtuální <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> objekt, který se používá k zobrazení dat, kdy každý záznam je přesunut do oblasti zobrazení. Můžete přizpůsobit zobrazení jednotlivých záznamů v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> události, například zvýraznění pole na základě hodnoty, které obsahuje. Další informace najdete v tématu [jak: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Nejběžnějším využitím <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> je ovládací prvek pro zobrazení dat z databázové tabulky nebo jiných připojených dat zdroje. Kromě [!INCLUDE[vstecado](~/includes/vstecado-md.md)] datové objekty <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek mohl vytvořit vazbu na jakoukoli třídu, která implementuje <xref:System.Collections.IList> rozhraní (včetně polí), všechny třídy, která implementuje <xref:System.ComponentModel.IListSource> jakékoli třída, která implementuje rozhraní <xref:System.ComponentModel.IBindingList> rozhraní nebo jakékoli třídy, která implementuje <xref:System.ComponentModel.IBindingListView> rozhraní.  
  
### <a name="data-binding"></a>Datová vazba  
 Obvykle provést vazba na data přetažením polí z **zdroje dat** okna do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Další informace najdete v tématu [jak: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
 Při práci s velkými objemy dat, můžete nastavit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> vlastnost `True` zobrazíte podmnožinu dat k dispozici. Virtuální režim vyžaduje implementaci mezipaměti dat, ze kterého <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> naplněn, a je nutné řídit všechny interakce s mezipaměti dat v době běhu. Další informace najdete v tématu [virtuálního režimu v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 Můžete také zobrazit nevázaných ovládacích prvků na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Můžete například zobrazit bitovou kopii, která se opakuje pro každou položku. Další informace najdete v tématu [jak: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
### <a name="events"></a>Události  
 Nejdůležitější události <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> událost, která se vyvolá, když nové položky jsou přešla do oblasti zobrazení, a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> událost, která se vyvolá, když je položka vybrána. Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> události změnit vzhled položky. Můžete třeba zvýraznit záporné hodnoty. Použití <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> události přístup k hodnot ovládacích prvků, když je položka vybrána.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Ovládacího prvku poskytuje všechny tyto události standardního ovládacího prvku v editoru kódu. Ale by neměly být použít některé z těchto událostí. Klávesnice a myši události, jako `KeyDown`, `Click`, a `MouseDown` nebude vyvolána v době běhu, protože <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> samotný ovládací prvek nikdy má fokus.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Nevystavuje událostí v době návrhu, protože je vytvořen pouze za běhu. Pokud chcete zpracovávat události klávesnice a myši, můžete přidat <xref:System.Windows.Forms.Panel> ovládací prvek <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> v době návrhu a následně zpracovat události <xref:System.Windows.Forms.Panel>. Další informace najdete v tématu [řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md).  
  
### <a name="customizations"></a>Vlastní nastavení  
 Existuje mnoho způsobů, jak přizpůsobit vzhled a chování <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit, za běhu i během návrhu. Vlastnosti můžete nastavit změnit barvy, skrýt nebo úprava položky záhlaví, změna orientace svislé na vodorovnou a spoustu dalších věcí. Další informace najdete v tématu [jak: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md), [jak: Zobrazení položek záhlaví v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md), a [jak: Změna rozložení ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md).  
  
 Všimněte si, že některé vlastnosti se vztahují <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> samotného ovládacího prvku, že ostatní se vztahují pouze <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>. Ujistěte se, že máte správný oddíl ovládací prvek před nastavením vlastnosti. Další informace najdete v tématu [jak: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Další vlastní nastavení zahrnují možnost přidávat a odstraňovat záznamy řízení, přidání schopností vyhledávání a zobrazování souvisejících dat ve formátu seznamu a podrobností. Další informace najdete v tématu [jak: Zákaz přidávání a odstraňování položek DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md), [jak: Vyhledávání dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md), a [jak: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md).  
  
## <a name="see-also"></a>Viz také:
- [Ovládací prvek DataRepeater](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)
- [Návod: Zobrazení dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)
- [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
