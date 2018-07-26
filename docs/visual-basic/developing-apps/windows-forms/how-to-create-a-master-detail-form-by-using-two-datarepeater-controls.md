---
title: 'Postupy: vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245524"
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>Postupy: Vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)
Související data můžete zobrazit pomocí dvou nebo více <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvky pro vytvoření hlavního/podrobného formuláře. Například můžete chtít zobrazit seznam zákazníků v jednom <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>a když uživatel vybere zákazník, zobrazí se seznam objednávek tohoto zákazníka za sekundu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
 Můžete zobrazit související data přetažením podrobnosti položky, které sdílejí stejný uzel hlavní tabulky z **zdroje dat** okna do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Například pokud máte zdroj dat obsahující tabulky Zákazníci a související tabulku Orders, zobrazí obě tabulky jako uzly nejvyšší úrovně ve stromovém zobrazení v **zdroje dat** okna. Rozbalte uzel zákazníky, kde můžete zobrazit sloupce. Všimněte si, že poslední sloupec v seznamu je rozbalitelný uzel, který představuje tabulku objednávky. Tento uzel představuje související objednávky zákazníka.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>K zobrazení souvisejících dat ve dvou ovládacích prvků DataRepeater  
  
1.  Přetáhněte dva <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacích prvků z **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.  
  
2.  Přetáhněte velikosti a pozice popisovače k určení velikosti ovládacích prvků a umístit je vedle sebe.  
  
3.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
    > [!NOTE]
    >  Pokud **zdroje dat** okna je prázdný, přidat zdroj dat k němu. Další informace najdete v tématu [přidat nové zdroje dat](/visualstudio/data-tools/add-new-data-sources).  
  
4.  V **zdroje dat** okna, vyberte uzel nejvyšší úrovně pro hlavní tabulku.  
  
5.  Změňte typ přetažení hlavní tabulky Podrobnosti kliknutím **podrobnosti** v rozevíracím seznamu na uzel tabulky.  
  
6.  Přetáhněte uzel hlavní tabulky na oblast šablony položky prvního <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
7.  Rozbalte uzel hlavní tabulka a vyberte uzel podrobností pro související tabulky.  
  
8.  Změňte typ přetažení tabulky Podrobnosti kliknutím **podrobnosti** v rozevíracím seznamu na uzel tabulky.  
  
9. Vyberte uzel této tabulky a přetáhněte ji na oblast šablony položky druhého <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: zobrazení souvisejících dat v Windows Forms aplikace](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
