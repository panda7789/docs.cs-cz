---
title: 'Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
ms.openlocfilehash: dbcd814edb78c54ce5629a1a8761142674fe6135
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684616"
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater (Visual Studio)
Nejběžnější použití nástroje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> zobrazení vázaných dat z databáze nebo jiného zdroje dat je ovládací prvek.  
  
 Kromě vázaných ovládacích prvků, můžete chtít přidat další ovládací prvky, jako je například statický popisek nebo obrázek, který se opakuje pro každou položku v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Další informace najdete v tématu [jak: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Můžete také navázat na zdroj dat v době běhu tak, že nastavíte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> vlastnost `True` a zdrojem dat pro přiřazení <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> vlastnost. V takovém případě bude nutné spravovat veškerou interakci se zdroji dat. Další informace najdete v tématu [virtuálního režimu v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>Chcete-li vytvořit DataRepeater vázané na data  
  
1.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení z **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.  
  
2.  Přetáhněte úchyty velikosti a pozice na velikost a umístění ovládacího prvku.  
  
     Všimněte si, že ovládací prvek má dvě oblasti obdélníkový. Horní oblast je *šablony položky*; ovládacích prvků přidaných do šablony se budou opakovat v každé položce <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek v době běhu. Dolní oblasti je *zobrazení*, kde se zobrazí položky.  
  
     Můžete také změnit velikost a umístění ovládacího prvku nebo šablony položek tak, že změníte **velikost** a **pozice** vlastnosti v okně Vlastnosti.  
  
3.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
    > [!NOTE]
    >  Pokud **zdroje dat** okna je prázdný, přidat zdroj dat k němu. Další informace najdete v tématu [přidat nové zdroje dat](/visualstudio/data-tools/add-new-data-sources).  
  
4.  V **zdroje dat** okna, vyberte uzel nejvyšší úrovně pro tabulku, která obsahuje data, která chcete vytvořit vazbu.  
  
5.  Změňte typ přetažení tabulky `Details` kliknutím `Details` v rozevíracím seznamu na uzel tabulky.  
  
6.  Vyberte uzel tabulky a přetáhněte ji na oblast šablony položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
     Můžete určit, které typy ovládacích prvků se zobrazí pro každé pole. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
