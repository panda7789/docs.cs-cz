---
title: "Použití událostí klávesnice"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- KeyPress event [Windows Forms]
- keyboards [Windows Forms], keyboard events
- KeyUp event
- KeyDown event
- keyboard events
- events [Windows Forms], keyboard
ms.assetid: d3f3e14b-a459-4ee6-9875-8957e34f8ee9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19bad48188a039baeeb6365a2cd38671f83fca4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-keyboard-events"></a>Použití událostí klávesnice
Zpracování události klávesnice zpracování většiny programů Windows Forms vstup z klávesnice. Toto téma obsahuje základní informace o události klávesnice, včetně podrobnosti o použití každé události a data, která je zadána pro každou jednotlivou událost.  Viz také [Přehled obslužných rutin událostí (Windows Forms)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [Přehled událostí (Windows Forms)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\)).  
  
## <a name="keyboard-events"></a>Události klávesnice  
 Windows Forms poskytuje dvě události, ke kterým došlo po stisknutí kláves a jedné události po uvolnění tlačítka klávesnice:  
  
-   <xref:System.Windows.Forms.Control.KeyDown> Události dojde jednou  
  
-   <xref:System.Windows.Forms.Control.KeyPress> Událost, která může dojít vícekrát, když uživatel obsahuje dolů stejný klíč.  
  
-   <xref:System.Windows.Forms.Control.KeyUp> Událost nastane jednou při uvolnění klíče.  
  
 Po stisknutí klávesy, určuje Windows Forms, která událost se má vyvolat podle jestli určuje zpráva klávesnice znak nebo fyzické klíče. Další informace o znak a fyzické klíčů najdete v tématu [jak funguje vstup klávesnice](../../../docs/framework/winforms/how-keyboard-input-works.md).  
  
 Následující tabulka popisuje tři klávesnice události.  
  
|Události klávesnice|Popis|Výsledky|  
|--------------------|-----------------|-------------|  
|<xref:System.Windows.Forms.Control.KeyDown>|Tato událost se vyvolá, když uživatel stiskne klávesu fyzické.|Obslužná rutina pro <xref:System.Windows.Forms.Control.KeyDown> obdrží:<br /><br /> <ul><li>A <xref:System.Windows.Forms.KeyEventArgs> parametr, který poskytuje <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> (který určuje fyzické klávesnice tlačítko).</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> Vlastnost (SHIFT, CTRL nebo ALT).</li><li><xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> (Který spojuje klíče kódu a modifikátor). <xref:System.Windows.Forms.KeyEventArgs> Parametr také poskytuje:<br /><br /> <ul><li><xref:System.Windows.Forms.KeyEventArgs.Handled%2A> Vlastnosti, která může být nastaven na zakázat přijímání klíč základní ovládacího prvku.</li><li><xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> Vlastnosti, která můžete použít k potlačení <xref:System.Windows.Forms.Control.KeyPress> a <xref:System.Windows.Forms.Control.KeyUp> události pro tento klávesu.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyPress>|Tato událost se vyvolá, když klíče nebo klíče stisknuto výsledek znak. Například uživatel stiskne klávesu SHIFT a malá "a" klíčů, které "A" znak za následek velké písmeno.|<xref:System.Windows.Forms.Control.KeyPress>je vyvolána po <xref:System.Windows.Forms.Control.KeyDown>.<br /><br /> <ul><li>Obslužná rutina pro <xref:System.Windows.Forms.Control.KeyPress> obdrží:</li><li>A <xref:System.Windows.Forms.KeyPressEventArgs> parametr, který obsahuje kód znaku klíče, která byla stisknuta. Tento kód znak je jedinečný pro každou kombinaci znak klíče a modifikační klávesy.<br /><br />     Například "A" klíč vygeneruje:<br /><br /> <ul><li>Kód znaku 65, pokud je stisknutí pomocí klávesy SHIFT</li><li>Klávesa CAPS LOCK 97 při stisknutí samostatně, nebo</li><li>A 1, pokud je stisknutí s klávesu CTRL.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyUp>|Tato událost se vyvolá, když uživatel uvolní fyzické klíč.|Obslužná rutina pro <xref:System.Windows.Forms.Control.KeyUp> obdrží:<br /><br /> <ul><li>A <xref:System.Windows.Forms.KeyEventArgs> parametr:<br /><br /> <ul><li>Který nabízí <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> (který určuje fyzické klávesnice tlačítko).</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> Vlastnost (SHIFT, CTRL nebo ALT).</li><li><xref:System.Globalization.SortKey.KeyData%2A> (Který spojuje klíče kódu a modifikátor).</li></ul></li></ul>|  
  
## <a name="see-also"></a>Viz také  
 [Vstup z klávesnice ve Windows Forms aplikace](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Jak funguje vstup z klávesnice](../../../docs/framework/winforms/how-keyboard-input-works.md)  
 [Vstup z myši ve Windows Forms aplikace](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
