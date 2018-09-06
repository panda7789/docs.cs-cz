---
title: Použití událostí klávesnice
ms.date: 03/30/2017
helpviewer_keywords:
- KeyPress event [Windows Forms]
- keyboards [Windows Forms], keyboard events
- KeyUp event
- KeyDown event
- keyboard events
- events [Windows Forms], keyboard
ms.assetid: d3f3e14b-a459-4ee6-9875-8957e34f8ee9
ms.openlocfilehash: 2c6059e5d0957de09dd2c4832573c784935eb510
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786424"
---
# <a name="using-keyboard-events"></a>Použití událostí klávesnice
Většina aplikací Windows Forms zpracovávat vstup z klávesnice ve zpracování událostí klávesnice. Toto téma obsahuje základní informace o události klávesnice, včetně podrobností o použití každé události a data, která je zadána pro každou jednotlivou událost.  Viz také [Přehled obslužných rutin událostí (Windows Forms)](https://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [Přehled událostí (Windows Forms)](https://msdn.microsoft.com/library/1h12f09z\(v=vs.110\)).  
  
## <a name="keyboard-events"></a>Události klávesnice  
 Windows Forms poskytuje dvě události, ke kterým dochází, když uživatel stiskne klávesu a jedna událost, když uživatel uvolní klávesu:  
  
-   <xref:System.Windows.Forms.Control.KeyDown> Jednou dojde k události.  
  
-   <xref:System.Windows.Forms.Control.KeyPress> Událost, která může dojít vícekrát, když uživatel obsahuje stejné klávesy.  
  
-   <xref:System.Windows.Forms.Control.KeyUp> Událost proběhne jednou, když uživatel uvolní klávesu.  
  
 Když uživatel stiskne klávesu, Windows Forms Určuje, která událost pro vyvolání podle Určuje, zda zpráva klávesnice určuje znak klíč nebo klíč do fyzické. Další informace o znak a fyzické klíče najdete v tématu [jak funguje vstup klávesnice](../../../docs/framework/winforms/how-keyboard-input-works.md).  
  
 Následující tabulka popisuje tři klávesnice události.  
  
|Události klávesnice|Popis|výsledky|  
|--------------------|-----------------|-------------|  
|<xref:System.Windows.Forms.Control.KeyDown>|Tato událost je aktivována, když uživatel stiskne klávesu fyzické.|Obslužná rutina pro <xref:System.Windows.Forms.Control.KeyDown> přijímá:<br /><br /> <ul><li>A <xref:System.Windows.Forms.KeyEventArgs> parametr, který poskytuje <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> (který určuje tlačítko fyzické klávesnice).</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> Vlastnosti (SHIFT, CTRL nebo ALT).</li><li><xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> Vlastnosti (která kombinuje kód klávesy a modifikátoru). <xref:System.Windows.Forms.KeyEventArgs> Parametr také poskytuje:<br /><br /> <ul><li><xref:System.Windows.Forms.KeyEventArgs.Handled%2A> Vlastnost, která může být nastaven na zabránit příjem klíč základní ovládacího prvku.</li><li><xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> Vlastnost, která slouží k potlačení <xref:System.Windows.Forms.Control.KeyPress> a <xref:System.Windows.Forms.Control.KeyUp> události pro tento stisk klávesy.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyPress>|Tato událost je aktivována při stisknutí klávesy nebo klávesy výsledek ve znaku. Například uživatel stiskne klávesu SHIFT a malým "a" klíče, které vedou na velké písmeno "A" znak.|<xref:System.Windows.Forms.Control.KeyPress> je aktivována po <xref:System.Windows.Forms.Control.KeyDown>.<br /><br /> <ul><li>Obslužná rutina pro <xref:System.Windows.Forms.Control.KeyPress> přijímá:</li><li>A <xref:System.Windows.Forms.KeyPressEventArgs> parametr, který obsahuje kód znaku klávesy, která byla stisknuta v okamžiku. Tento kód znaku je jedinečný pro každou kombinaci znaků klíč a modifikační klávesa.<br /><br />     Například "A" klíč vygeneruje:<br /><br /> <ul><li>Kód znaku 65, pokud se stiskne pomocí klávesy SHIFT</li><li>Klávesa CAPS LOCK, 97, pokud se stiskne samostatně, nebo</li><li>A 1, pokud se stiskne pomocí klávesy CTRL.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyUp>|Tato událost je aktivována, když uživatel uvolní klávesu fyzické.|Obslužná rutina pro <xref:System.Windows.Forms.Control.KeyUp> přijímá:<br /><br /> <ul><li>A <xref:System.Windows.Forms.KeyEventArgs> parametr:<br /><br /> <ul><li>Která zajišťuje <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> (který určuje tlačítko fyzické klávesnice).</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> Vlastnosti (SHIFT, CTRL nebo ALT).</li><li><xref:System.Globalization.SortKey.KeyData%2A> Vlastnosti (která kombinuje kód klávesy a modifikátoru).</li></ul></li></ul>|  
  
## <a name="see-also"></a>Viz také  
 [Vstup z klávesnice v aplikaci Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Jak funguje vstup z klávesnice](../../../docs/framework/winforms/how-keyboard-input-works.md)  
 [Vstup z myši v aplikaci Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
