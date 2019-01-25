---
title: 'Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: a20e1ba83d1963bc3d4c135817767ee02fcbdeda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730786"
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater (Visual Studio)
Kromě vázaných ovládacích prvků, můžete chtít přidat další ovládací prvky k <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, jako je statický popisek nebo obrázek, který se opakuje pro každou položku v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
> [!NOTE]
>  Také musíte mít alespoň jeden ovládací prvek vázaný <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nebo se nezobrazí v době běhu.  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>Přidání nevázaných ovládacích prvků DataRepeater  
  
1.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení z **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.  
  
2.  Přetáhněte úchyty velikosti a pozice na velikost a umístění ovládacího prvku.  
  
     Můžete také změnit velikost a umístění ovládacího prvku tak, že změníte **velikost** a **pozice** vlastnosti v okně Vlastnosti.  
  
3.  Přidejte alespoň jeden ovládací prvek vázaný na data na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Další informace najdete v tématu [jak: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Přetáhněte ovládací prvek z **nástrojů** na oblast šablony položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
     Všimněte si, že ovládací prvek má dvě oblasti obdélníkový. Vnitřní oblasti je *šablony položky*; ovládacích prvků přidaných do šablony se budou opakovat v každé položce <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek v době běhu. Vnější oblast je *zobrazení*, kde se zobrazí položky; ovládací prvky, které se přidají do této oblasti se nezobrazí v době běhu.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
