---
title: 'Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: 698e518a4ed10ed6cf14ccafc6833b1acf8752db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater (Visual Studio)
Kromě vázané ovládací prvky, můžete přidat další ovládací prvky na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, jako jsou například statické štítek nebo obrázek, který se opakuje pro každou položku v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
> [!NOTE]
>  Je také nutné mít alespoň jeden prvek vázané <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nebo nezobrazí v době běhu.  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>Přidání nevázaných ovládacích prvků DataRepeater  
  
1.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.  
  
2.  Přetáhněte obslužné rutiny pro změnu velikosti a pozice na velikost a umístění ovládacího prvku.  
  
     Můžete také upravit velikost a umístění ovládacího prvku tak, že změníte **velikost** a **pozice** vlastnosti v okně Vlastnosti.  
  
3.  Přidejte alespoň jeden ovládací prvek vázané na data do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Další informace najdete v tématu [postupy: zobrazení vázaný dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Přetáhněte ovládací prvek z **sada nástrojů** na oblast šablony položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
     Všimněte si, že ovládací prvek má dvě obdélníková oblasti. Vnitřní oblast je *šablony položky*; ovládací prvky přidat do šablony budou opakovat v jednotlivé položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku za běhu. Vnější oblast je *zobrazení*, kde se zobrazí položky; ovládací prvky, které jsou přidány do této oblasti se nezobrazí v době běhu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
