---
title: "Postupy: Vytvoření jednoduše připojeného ovládacího prvku na Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 887f5cd89e52cf91c4e18fab5c97f82cba9a5b85
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Postupy: Vytvoření jednoduše připojeného ovládacího prvku na Windows Form
S *jednoduchá vazba*, jeden datový prvek, jako je například hodnota sloupce z tabulky datovou sadu, může zobrazení v ovládacím prvku. Vám může jednoduché bind libovolné vlastnosti ovládacího prvku na hodnotu data.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-simple-bind-a-control"></a>Na jednoduchý vytvořte vazbu ovládacího prvku  
  
1.  Připojení ke zdroji dat. Další informace najdete v tématu [připojení ke zdroji dat](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  Ve formuláři, vyberte ovládací prvek a zobrazit **vlastnosti** okno.  
  
3.  Rozbalte **(datové vazby)** vlastnost.  
  
     Vlastnosti nejčastěji vázaný se zobrazí pod **(datové vazby)** vlastnost. Například v většina ovládacích prvků **Text** vlastnost je nejčastěji vázána.  
  
4.  Pokud vlastnost, kterou chcete vazby není jednou z nejčastěji vázané vlastnosti, klikněte na **třemi tečkami** tlačítko (![VisualStudioEllipsesButton snímek](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton") ) v **(rozšířené)** políčka se zobrazí **formátování a rozšířené vazby** dialogové okno s úplný seznam vlastností pro ovládací prvek.  
  
5.  Vyberte vlastnost, kterou chcete vytvořit vazbu a klikněte na šipku rozevíracího seznamu v části **vazby**.  
  
     Zobrazí se seznam dostupných zdrojů dat.  
  
6.  Rozbalení zdroje dat, které chcete vytvořit vazbu, dokud nebude nalezen jeden datový prvek, který má být. Pokud vytváříte vazbu na hodnotu sloupce v tabulce datové sady, rozbalte název datové sady a potom rozbalte název tabulky k zobrazení názvů sloupců.  
  
7.  Klikněte na název elementu k vytvoření vazby.  
  
8.  Pokud jste pracovali **formátování a rozšířené vazby** dialogové okno, klikněte na tlačítko **OK** se vrátíte do **vlastnosti** okno.  
  
9. Pokud chcete vytvořit vazbu další vlastnosti ovládacího prvku, opakujte kroky 3 až 7.  
  
    > [!NOTE]
    >  Protože ovládací prvky vázané na jednoduchý zobrazit pouze jeden datový prvek, je velmi typické zahrnout logiku navigace ve formuláři Windows s ovládací prvky vázané na jednoduché.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Binding>  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Datové vazby a Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
