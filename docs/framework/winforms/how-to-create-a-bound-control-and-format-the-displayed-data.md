---
title: "Postupy: Vytvoření připojeného ovládacího prvku a formátování zobrazených dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6088048ed27b2021e297494275f4e80f7c0cb681
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>Postupy: Vytvoření připojeného ovládacího prvku a formátování zobrazených dat
S Windows Forms – datová vazba, můžete ho naformátovat data zobrazená v ovládacím prvku vázané na data pomocí **formátování a rozšířené vazby** dialogové okno.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a>Chcete-li vytvořit vazbu ovládacího prvku a formátování zobrazených dat  
  
1.  Připojení ke zdroji dat.  
  
     Další informace najdete v tématu [připojení ke zdroji dat](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  Ve formuláři vyberte ovládací prvek a potom otevřete okno Vlastnosti.  
  
3.  Rozbalte **(datové vazby)** vlastnost a potom v **(rozšířené)** pole, klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton] (../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) k zobrazení **formátování a rozšířené vazby** dialogové okno, který má úplný seznam vlastností pro ovládací prvek.  
  
4.  Vyberte vlastnost, kterou chcete vytvořit vazbu a potom klikněte na **vazby** šipku.  
  
     Zobrazí se seznam dostupných zdrojů dat.  
  
5.  Rozbalení zdroje dat, které chcete vytvořit vazbu, dokud nebude nalezen jeden datový prvek, který má být.  
  
     Pokud vytváříte vazbu na hodnotu sloupce v tabulce datové sady, rozbalte název datové sady a potom rozbalte název tabulky k zobrazení názvů sloupců.  
  
6.  Klikněte na název elementu k vytvoření vazby.  
  
7.  V **typ** pole, klikněte na formát, který chcete použít pro data zobrazená v ovládacím prvku.  
  
     V každém případě můžete zadat hodnotu, pokud obsahuje zdroj dat, zobrazí v ovládacím prvku <xref:System.DBNull>. Jinak hodnota možnosti mírně lišit v závislosti na typu formátu, který zvolíte. V následující tabulce jsou uvedeny typy formátu a možnosti.  
  
    |Typ formátu|Možnost formátování|  
    |-----------------|-----------------------|  
    |Žádné formátování|Žádné možnosti.|  
    |číselné|Zadejte počet desetinných míst pomocí **desetinných míst** dolů.|  
    |Měna|Zadejte počet desetinných míst pomocí **desetinných míst** dolů.|  
    |Datum a čas|Vyberte, jak datum a čas mají být zobrazeny výběrem jedné z položek v **typ** výběr pole.|  
    |Scientific|Zadejte počet desetinných míst pomocí **desetinných míst** dolů.|  
    |Vlastní|Zadejte řetězec vlastní formát pomocí.<br /><br /> Další informace najdete v tématu [typy formátování](../../../docs/standard/base-types/formatting-types.md). **Poznámka:** vlastní řetězce formátu není zaručena bezpečnost pro úspěšně odezvy mezi zdrojem dat a připojeného ovládacího prvku. Místo toho zpracovat <xref:System.Windows.Forms.Binding.Parse> nebo <xref:System.Windows.Forms.Binding.Format> událostí pro vazbu a použít vlastní formátování v kódu zpracování událostí.|  
  
8.  Klikněte na tlačítko **OK** zavřete **formátování a rozšířené vazby** dialogové okno a vraťte se do okna vlastností.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [Ověřování uživatelského vstupu ve Windows Forms](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)
