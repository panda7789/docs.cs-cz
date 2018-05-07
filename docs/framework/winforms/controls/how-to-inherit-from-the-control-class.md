---
title: 'Postupy: Dědění ze třídy Control'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: da80d46f27d7cd721af7a9600d2b0cde84876d23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-inherit-from-the-control-class"></a>Postupy: Dědění ze třídy Control
Pokud chcete vytvořit zcela vlastního ovládacího prvku na formuláři Windows používat, musí dědit z <xref:System.Windows.Forms.Control> třídy. Při dědění z <xref:System.Windows.Forms.Control> třída vyžaduje provést další plánování a implementace, můžete ho vám rovněž poskytne největší škálu možností. Když je zděděný z <xref:System.Windows.Forms.Control>, dědí velmi základní funkce, která umožňuje ovládací prvky fungovat. Funkci vyplývajících z <xref:System.Windows.Forms.Control> třída zpracovává vstupu uživatele prostřednictvím klávesnici a myš, definuje rozsah a velikost ovládacího prvku, poskytuje popisovačů systému windows a poskytuje zpracování zpráv a zabezpečení. Ho nebere v úvahu žádné Malování, který v tomto případě je skutečný vykreslování grafické rozhraní ovládacího prvku, ani nebude obsahovat žádné funkce interakce konkrétního uživatele. Je nutné zadat všechny tyto aspekty prostřednictvím vlastní kód.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-custom-control"></a>Chcete-li vytvořit vlastní ovládací prvek  
  
1.  Vytvořte novou **aplikace Windows** nebo **knihovny ovládacích prvků Windows** projektu.  
  
2.  Z **projektu** nabídce zvolte **přidat třídu**.  
  
3.  V **přidat novou položku** dialogové okno, klikněte na tlačítko **vlastní ovládací prvek**.  
  
     Nové vlastní ovládací prvek se přidá do projektu.  
  
4.  Stisknutím klávesy F7 otevřete **Editor kódu** pro váš vlastní ovládací prvek.  
  
5.  Vyhledejte <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, která bude prázdný, s výjimkou volání <xref:System.Windows.Forms.Control.OnPaint%2A> metoda základní třídy.  
  
6.  Upravte kód, abyste zapracovali všechny vlastní Malování, které chcete použít pro vlastní ovládací prvek.  
  
     Informace o psaní kódu pro vykreslení grafiky pro ovládací prvky najdete v tématu [vlastní ovládací prvek Malování a vykreslování](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
7.  Implementujte všech vlastních metod, vlastností nebo událostí, které bude obsahovat vlastní ovládací prvek.  
  
8.  Uložte a otestování ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Postupy: Dědění ze třídy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Postupy: Dědění ze stávajících ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Postupy: Vytváření ovládacích prvků pro Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [Vývoj ovládacích prvků Windows Forms v době návrhu](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
