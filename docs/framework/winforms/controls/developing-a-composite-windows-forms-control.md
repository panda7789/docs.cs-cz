---
title: "Vývoj složeného ovládacího prvku Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da180f888031aace892efc770184be53e9341047
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="developing-a-composite-windows-forms-control"></a>Vývoj složeného ovládacího prvku Windows Forms
Složené ovládací prvek Windows Forms můžete vyvíjet kombinací dalších ovládacích prvků Windows Forms. Složené ovládací prvky, které jsou odvozeny od <xref:System.Web.UI.UserControl> se nazývají uživatelské ovládací prvky. Základní třídy, <xref:System.Windows.Forms.UserControl>, poskytuje směrování pro podřízené prvky, čímž zajišťuje, že podřízené ovládací prvky mohou získat fokus klávesnice. Příklad uživatelského ovládacího prvku, naleznete v části <xref:System.Windows.Forms.UserControl> ukázku v [postupy: použití atributů v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
 Windows Forms designerem v [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] poskytuje rozsáhlou podporu návrhu uživatelské ovládací prvky pro vytváření obsahu.  
  
-   [Postupy: zobrazení ovládacího prvku v výběr položek sady nástrojů – dialogové okno](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))  
  
-   [Návod: Dědění z Windows Forms ovládacího prvku pomocí Visual C#](http://msdn.microsoft.com/en-us/09476da0-8d4c-4a4c-b969-649519dfb438))  
  
-   [Postupy: poskytování rastrového obrázku panelu nástrojů pro ovládací prvek](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [Postupy: dědění ze stávajícího systému Windows Forms – ovládací prvky](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [Návod: Ladění vlastních Windows Forms – ovládací prvky v době návrhu](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [Postupy: dědění ze třídy Control](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [Postupy: testování běhového chování UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))  
  
-   [Postupy: zarovnání ovládacího prvku k okrajům formuláře během návrhu](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [Postupy: dědění ze třídy UserControl](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [Postupy: vytváření ovládacích prvků pro Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [Postupy: vytváření složených ovládacích prvků](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](http://msdn.microsoft.com/en-us/f88481a8-c746-4a36-9479-374ce5f2e91f))  
  
-   [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [Postupy: vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [Postupy: vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití atributů v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [Vývoj vlastních Windows Forms – ovládací prvky s rozhraním .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
