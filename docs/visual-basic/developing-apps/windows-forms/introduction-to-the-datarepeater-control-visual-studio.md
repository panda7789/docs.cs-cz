---
title: "Úvod k ovládacímu prvku DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 699876cc568b22114e5ed8741c2fd0c053a137af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>Úvod k ovládacímu prvku DataRepeater (Visual Studio)
Visual Basic Power Pack <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek je posuvný kontejner pro ovládací prvky, které zobrazují opakované data, například řádků v tabulce databáze. Může sloužit jako alternativu k <xref:System.Windows.Forms.DataGridView> řízení, pokud potřebujete větší kontrolu nad rozložení data. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> "Opakuje" skupinu souvisejících ovládacích prvků tak, že vytvoříte více instancí v posouvání zobrazení. To umožňuje uživatelům zobrazit více záznamů najednou.  
  
## <a name="overview"></a>Přehled  
 V době návrhu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení se skládá ze dvou částech. Vnější oddíl je *zobrazení*, kde se zobrazí posouvání dat za běhu. Vnitřní (horní) části známé jako *šablony položky*, je umístíte ovládací prvky, které se budou opakovat v době běhu, obvykle jeden ovládací prvek pro každé pole v datovém zdroji. Vlastnosti a ovládací prvky v šabloně položky jsou zapouzdřené v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> vlastnost.  
  
 V době běhu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> se zkopíruje do virtuální <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> objekt, který se používá k zobrazení dat, kdy každý záznam přesunut do zobrazení oblasti. Můžete přizpůsobit zobrazení jednotlivých záznamů <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> události, například zvýraznění poli na základě hodnoty, které obsahuje. Další informace najdete v tématu [postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Nejčastěji používá <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek je pro zobrazení dat z tabulky databáze nebo jiného vázaného zdroje dat. Kromě [!INCLUDE[vstecado](~/includes/vstecado-md.md)] datových objektů <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení můžete vázat na všechny třídy, která implementuje <xref:System.Collections.IList> rozhraní (včetně polí), všechny třídy, která implementuje <xref:System.ComponentModel.IListSource> žádné třída, která implementuje rozhraní <xref:System.ComponentModel.IBindingList> rozhraní nebo jakákoli třída, která implementuje <xref:System.ComponentModel.IBindingListView> rozhraní.  
  
### <a name="data-binding"></a>Datová vazba  
 Obvykle lze provést vazbu dat přetažením polí z **zdroje dat** okna do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Další informace najdete v tématu [postupy: zobrazení vázaný dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
 Při práci s velkými objemy dat, můžete nastavit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> vlastnost `True` zobrazíte podmnožinu dat k dispozici. Virtuální režim vyžaduje, aby implementace datové mezipaměti, ze kterého <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> je vyplněný, a je nutné řídit všechny interakce s datovou mezipaměť v době běhu. Další informace najdete v tématu [virtuální režim ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 Můžete také zobrazit nevázaných ovládacích prvků na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Můžete například zobrazit obrázek, který se opakuje na každou položku. Další informace najdete v tématu [postupy: zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
### <a name="events"></a>Události  
 Nejdůležitější události <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení, představují <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> událost, která se vyvolá, když je přesunut do zobrazení oblasti nové položky, a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> událost, která se vyvolá, když je položka vybrána. Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> událostí Změna vzhledu položky. Můžete například zvýraznit záporné hodnoty. Použití <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> událost, která má přístup k hodnotám ovládacích prvků, když je vybrána položka.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Řízení zpřístupní všechny standardního ovládacího prvku události v editoru kódu. Ale některé události nepoužívejte. Klávesnice a myši události, jako `KeyDown`, `Click`, a `MouseDown` nebudou vyvolávat za běhu, protože <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nikdy má právě fokus, vlastní ovládací prvek.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Nezpřístupňuje události v době návrhu, protože je vytvořen pouze za běhu. Pokud chcete zpracovávat události klávesnice a myši, můžete přidat <xref:System.Windows.Forms.Panel> řídit k <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> v době návrhu a potom zpracovat události pro <xref:System.Windows.Forms.Panel>. Další informace najdete v tématu [řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md).  
  
### <a name="customizations"></a>Přizpůsobení  
 Existuje mnoho způsobů, jak upravit vzhled a chování <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit, v době běhu i v době návrhu. Vlastnosti lze nastavit změnit barvy, skrýt nebo změnit záhlaví položek, změnit orientaci z vertical na vodorovné a mnoho dalšího. Další informace najdete v tématu [postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md), [postupy: zobrazení položek záhlaví v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md), a [postupy: Změna rozložení Prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md).  
  
 Všimněte si, že některé vlastnosti se vztahují na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek, zatímco ostatní se vztahují pouze <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>. Ujistěte se, zda máte správné části Vybrat nastavení vlastností ovládacího prvku. Další informace najdete v tématu [postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Další přizpůsobení zahrnují řízení možnost Přidat nebo odstranit záznamy, přidání schopností vyhledávání a zobrazování souvisejících dat ve formátu, seznamu a podrobností. Další informace najdete v tématu [postupy: zákaz přidávání a odstraňování položek DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md), [postupy: vyhledávání dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md), a [postupy: vytvoření hlavního a podrobného formuláře pomocí dvou pomocí Ovládacích prvků DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md).  
  
## <a name="see-also"></a>Viz také  
 [Prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)  
 [Návod: Zobrazování dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)  
 [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
