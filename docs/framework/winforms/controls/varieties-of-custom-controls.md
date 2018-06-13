---
title: Typy vlastních ovládacích prvků
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], user controls
- controls [Windows Forms], types of
- composite controls [Windows Forms]
- extended controls [Windows Forms]
- controls [Windows Forms], extended
- user controls [Windows Forms]
- custom controls [Windows Forms]
- controls [Windows Forms], composite
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
ms.openlocfilehash: f35fdb0f82370ed3e40aeeda01b3c88f0a8c5ec0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541226"
---
# <a name="varieties-of-custom-controls"></a>Typy vlastních ovládacích prvků
S rozhraním .NET Framework můžete vytvořit a provádět nové ovládací prvky. Stejně jako stávající ovládací prvky prostřednictvím dědičnosti můžete rozšířit funkce známé uživatelského ovládacího prvku. Můžete také psát vlastní ovládací prvky, které provádějí vlastní Malování.  
  
 Rozhodování, jaký druh řízení k vytvoření může být matoucí. Toto téma označuje rozdílům mezi různé typy ovládacích prvků, ze kterého může dědit vlastnosti a poskytuje informace o tom, jak vybrat konkrétní typ ovládacího prvku pro váš projekt.  
  
> [!NOTE]
>  Informace o vytvoření ovládacího prvku na webové formuláře používat najdete v tématu [vývoj vlastních serverových ovládacích prvků ASP.NET](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="base-control-class"></a>Základní třídy ovládacího prvku  
 <xref:System.Windows.Forms.Control> Třída je základní třídou pro Windows Forms – ovládací prvky. Poskytuje infrastrukturu potřebnou pro vizuální zobrazení v aplikacích Windows Forms.  
  
 <xref:System.Windows.Forms.Control> Třída provádí následující úkoly a poskytují vizuální zobrazení v aplikacích Windows Forms:  
  
-   Zpřístupní popisovač okna.  
  
-   Spravuje směrování zpráv.  
  
-   Poskytuje myši a události klávesnice a mnoho dalších událostí rozhraní uživatele.  
  
-   Poskytuje pokročilé rozložení funkce.  
  
-   Obsahuje mnoho vlastnosti specifické pro visual zobrazení, jako jsou například <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, a <xref:System.Windows.Forms.Control.Width%2A>.  
  
-   Poskytuje zabezpečení a vláken podpory potřebné pro ovládací prvek Windows Forms tak, aby fungoval jako ovládacího prvku ActiveX Microsoft®.  
  
 Protože mnoho infrastruktury od základní třídy, je poměrně snadné ho vyvíjet vlastní ovládací prvky Windows Forms.  
  
## <a name="kinds-of-controls"></a>Typy ovládacích prvků  
 Podporuje tři druhy uživatelské ovládací prvky Windows Forms: *složené*, *rozšířené*, a *vlastní*. Následující části popisují jednotlivé typy řízení a poskytnout doporučení pro výběr druh používat ve svých projektech.  
  
### <a name="composite-controls"></a>Složené ovládací prvky  
 Složeného ovládacího prvku je kolekce ovládacích prvků Windows Forms zapouzdřené v běžné kontejneru. Tento druh ovládacího prvku se někdy nazývá *uživatelský ovládací prvek*. Obsažené ovládací prvky se označují jako *základních ovládacích prvků*.  
  
 Složeného ovládacího prvku obsahuje všechny vyplývajících funkce související s jednotlivými obsažené ovládací prvky Windows Forms a umožňuje selektivně vystavit a vytvořte vazbu jejich vlastnosti. Složeného ovládacího prvku také poskytuje značnou část výchozí klávesnice zpracování funkce se žádné další vývoj úsilí na druhé straně.  
  
 Například může být postavená složeného ovládacího prvku k zobrazení dat zákazníka adresu z databáze. Tento ovládací prvek může zahrnovat <xref:System.Windows.Forms.DataGridView> ovládací prvek zobrazí pole databáze <xref:System.Windows.Forms.BindingSource> pro zpracování vazby ke zdroji dat a <xref:System.Windows.Forms.BindingNavigator> řízení k procházení záznamů. Selektivně mohla vystavit vlastnosti datové vazby a můžete balíček a opakovaně používat celý ovládací prvek z aplikace do aplikace. Příklad tento druh složeného ovládacího prvku, naleznete v části [postupy: použití atributů v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
 K vytváření složených prvků, jsou odvozeny od <xref:System.Windows.Forms.UserControl> třídy. <xref:System.Windows.Forms.UserControl> Základní třída poskytuje směrování klávesnice pro podřízené prvky a umožňuje podřízené ovládací prvky pro práci jako skupina. Další informace najdete v tématu [vývoj složeného ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
 **Doporučení**  
  
 Dědit z <xref:System.Windows.Forms.UserControl> třídy, pokud:  
  
-   Chcete zkombinovat do jedné jednotky opakovaně použitelné funkci několik ovládacích prvků Windows Forms.  
  
### <a name="extended-controls"></a>Rozšířené ovládací prvky  
 Ovládací prvek zděděné lze odvozovat od všechny existující ovládacího prvku Windows Forms. S tímto přístupem můžete zachovat všechny vyplývajících funkce ovládacího prvku Windows Forms a pak rozšířit přidáním vlastních vlastností, metod a dalších prvků, které tuto funkci. Pomocí této možnosti můžete přepsat logiku Malování základního ovládacího prvku a potom rozšíří jeho uživatelské rozhraní můžete změnit její vzhled.  
  
 Například můžete vytvořit odvozenou z ovládacího prvku <xref:System.Windows.Forms.Button> ovládací prvek, který sleduje, kolikrát se uživatel klikne ho.  
  
 V některé ovládací prvky, můžete také přidat vlastní vzhled grafické uživatelské rozhraní ovládacího prvku přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metoda základní třídy. Pro rozšířené tlačítko, které sleduje kliknutí, můžete přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metoda se má volat základní implementaci <xref:System.Windows.Forms.Control.OnPaint%2A>a pak kreslení počet kliknutím v jedné horním rohu <xref:System.Windows.Forms.Button> ovládacího prvku klientské oblasti.  
  
 **Doporučení**  
  
 Dědění z ovládacího prvku Windows Forms, pokud:  
  
-   Již je stejná jako existující ovládacího prvku Windows Forms většinu funkcí, které potřebujete.  
  
-   Není nutné vlastní grafické uživatelské rozhraní, nebo můžete navrhnout nové grafické uživatelské rozhraní pro existujícího ovládacího prvku.  
  
### <a name="custom-controls"></a>Vlastní ovládací prvky  
 Další způsob vytvoření ovládacího prvku se má vytvořit podstatně od začátku dědění ze <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Třída poskytuje všechny základní funkce vyžaduje ovládací prvky, včetně myši a klávesnice zpracování událostí, ale žádné funkce specifické pro ovládací prvek nebo grafické rozhraní.  
  
 Vytvoření ovládacího prvku dědění ze <xref:System.Windows.Forms.Control> třída vyžaduje mnohem víc myšlenku a úsilí než dědění z <xref:System.Windows.Forms.UserControl> nebo existujícího ovládacího prvku Windows Forms. Protože značnou část implementace je ponecháno za vás, může mít větší flexibilitu než ovládacího prvku složené nebo rozšířené ovládací prvek a můžete přizpůsobit ovládacího prvku tak, aby vyhovovala vašim konkrétním potřebám.  
  
 Chcete-li implementovat vlastní ovládací prvek, musíte napsat kód pro <xref:System.Windows.Forms.Control.OnPaint%2A> události ovládacího prvku, jakož žádné specifické funkce kód, který potřebujete. Můžete také přepsat <xref:System.Windows.Forms.Control.WndProc%2A> metoda a popisovač zpráv systému windows přímo. Toto je nejúčinnějších způsob vytvoření ovládacího prvku, ale tato technika efektivně používat, musíte se seznámit s rozhraním API Microsoft Win32®.  
  
 Příklad vlastního ovládacího prvku je ovládací prvek hodiny, která duplikuje vzhled a chování analogovým hodiny. Vlastní Malování je vyvolána k způsobit do nesprávných rukou hodiny přesunout v reakci na <xref:System.Windows.Forms.Timer.Tick> události z interní <xref:System.Windows.Forms.Timer> součásti. Další informace najdete v tématu [postup: vývoj jednoduchého prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 **Doporučení**  
  
 Dědit z <xref:System.Windows.Forms.Control> třídy, pokud:  
  
-   Chcete zadat vlastní grafické reprezentace vlastního ovládacího prvku.  
  
-   Potřebujete implementovat vlastní funkce, která není k dispozici prostřednictvím standardní ovládací prvky.  
  
### <a name="activex-controls"></a>ActiveX – ovládací prvky  
 I když infrastruktury formulářů Windows optimalizovaná pro hostitelské ovládací prvky Windows Forms, můžete dál používat ovládací prvky ActiveX. Není poskytována podpora pro tuto úlohu v sadě Visual Studio. Další informace najdete v tématu [postupy: Přidání ovládacích prvků ActiveX do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md).  
  
### <a name="windowless-controls"></a>Bez oken ovládací prvky  
 Podpora technologie ActiveX the Microsoft Visual Basic® 6.0and *bez oken* ovládací prvky. Bez oken ovládací prvky nejsou podporovány v systému Windows Forms.  
  
## <a name="custom-design-experience"></a>Vlastní návrh prostředí  
 Pokud potřebujete implementovat vlastní možnosti návrhu, můžete vytvářet vlastní designer. Složené ovládací prvky jsou odvozeny vaše vlastní třídy návrháře z <xref:System.Windows.Forms.Design.ParentControlDesigner> nebo <xref:System.Windows.Forms.Design.DocumentDesigner> třídy. Rozšířené a vlastní ovládací prvky jsou odvozeny vaše vlastní třídy návrháře z <xref:System.Windows.Forms.Design.ControlDesigner> třídy.  
  
 Použití <xref:System.ComponentModel.DesignerAttribute> přidružit vašeho návrháře vlastního ovládacího prvku. Další informace najdete v tématu [rozšíření podpory návrhu](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2) a [postupy: vytvoření funkce systému Windows Forms ovládací prvek, trvá výhod z návrhu](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).  
  
## <a name="see-also"></a>Viz také  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Vývoj složeného ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [Rozšíření podpory návrhu](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Postupy: vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)
