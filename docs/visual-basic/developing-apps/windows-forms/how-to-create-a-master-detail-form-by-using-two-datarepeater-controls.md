---
title: "Postupy: vytvoření hlavního podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f17cb86c3ea0ea056291a51becd7ecf9f73d0a73
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>Postupy: Vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)
Související data můžete zobrazit pomocí dvou nebo více <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvky pro vytvoření hlavního a podrobného formuláře. Například můžete chtít zobrazit seznam zákazníků v jednom <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>a když uživatel vybere zákazníka, zobrazí se seznam objednávek tohoto zákazníka za sekundu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
 Související data můžete zobrazit přetažením podrobné položky, které sdílejí stejný uzel hlavní tabulky z **zdroje dat** okna do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Například pokud je zdroj dat, který má tabulku zákazníků a související tabulky objednávky, vidíte obě tabulky jako uzly nejvyšší úrovně ve stromovém zobrazení v **zdroje dat** okno. Rozbalte uzel zákazníkům, aby mohli zobrazit sloupce. Všimněte si, že je posledního sloupce v seznamu rozšíření uzlu, který představuje tabulky objednávky. Tento uzel představuje související objednávky pro zákazníka.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>Pro zobrazení souvisejících dat ve dvou ovládacích prvků DataRepeater  
  
1.  Přetáhněte dva <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> z ovládací prvky **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.  
  
2.  Přetáhněte obslužné rutiny pro změnu velikosti a pozice k určení velikosti ovládacích prvků a umístit je vedle sebe.  
  
3.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
    > [!NOTE]
    >  Pokud **zdroje dat** přidejte do něj zdroj dat, je prázdný. Další informace najdete v tématu [přidat nové zdroje dat](/visualstudio/data-tools/add-new-data-sources).  
  
4.  V **zdroje dat** okně vyberte nejvyšší uzel pro hlavní tabulku.  
  
5.  Změňte typ hlavní tabulky Podrobnosti o kliknutím **podrobnosti** v rozevíracím seznamu na uzlu tabulky.  
  
6.  Přetáhněte uzel hlavní tabulky na oblast šablony položky první <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
7.  Rozbalte uzel hlavní tabulka a vyberte uzel podrobností pro související tabulky.  
  
8.  Změňte typ tabulky Podrobnosti o kliknutím **podrobnosti** v rozevíracím seznamu na uzlu tabulky.  
  
9. Vyberte uzel této tabulky a přetáhněte ji na oblast šablony položky druhý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: zobrazení souvisejících dat v systému Windows Forms aplikace](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
