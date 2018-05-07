---
title: 'Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
ms.openlocfilehash: b96fb33a0dcf80a86d1fcb6e219e5f35b1f7351c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater (Visual Studio)
Nejběžnější použití <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> zobrazení vázaných dat z databáze nebo jiného zdroje dat je řízení.  
  
 Kromě vázané ovládací prvky, můžete přidat další ovládací prvky, jako je například statické štítek nebo obrázek, který se opakuje pro každou položku v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Další informace najdete v tématu [postupy: zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Můžete také navázat ke zdroji dat za běhu nastavením <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> vlastnost `True` a přiřazení zdroje dat <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> vlastnost. V takovém případě bude muset spravovat všechny interakce se zdrojem dat. Další informace najdete v tématu [virtuální režim ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>Chcete-li vytvořit DataRepeater vázané na data  
  
1.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.  
  
2.  Přetáhněte obslužné rutiny pro změnu velikosti a pozice na velikost a umístění ovládacího prvku.  
  
     Všimněte si, že ovládací prvek má dvě obdélníková oblasti. Horní oblast je *šablony položky*; ovládací prvky přidat do šablony budou opakovat v jednotlivé položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku za běhu. Dolní oblast je *zobrazení*, kde se zobrazí položky.  
  
     Můžete také upravit velikost a umístění ovládacího prvku nebo šablony položky změnou **velikost** a **pozice** vlastnosti v okně Vlastnosti.  
  
3.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
    > [!NOTE]
    >  Pokud **zdroje dat** přidejte do něj zdroj dat, je prázdný. Další informace najdete v tématu [přidat nové zdroje dat](/visualstudio/data-tools/add-new-data-sources).  
  
4.  V **zdroje dat** okně vyberte uzel pro tabulku, která obsahuje data, která chcete vytvořit vazbu na nejvyšší úrovni.  
  
5.  Změňte typ tabulky na `Details` kliknutím `Details` v rozevíracím seznamu na uzlu tabulky.  
  
6.  Vyberte uzel tabulky a přetáhněte ji na oblast šablony položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
     Můžete určit, které typy ovládacích prvků se zobrazují pro každé pole. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
