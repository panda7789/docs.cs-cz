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
ms.openlocfilehash: 9883f9166007405c3f47a9a1d66a3f4c546197d0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884559"
---
# <a name="varieties-of-custom-controls"></a>Typy vlastních ovládacích prvků
Pomocí rozhraní .NET Framework můžete vyvíjet a implementovat nové ovládací prvky. Funkce ovládacího prvku známé uživatelské můžete rozšířit také existující ovládací prvky prostřednictvím dědičnosti. Můžete taky psát vlastní ovládací prvky, které vlastní vykreslení.  
  
 Rozhodování o tom, jaký druh ovládacího prvku k vytvoření může být matoucí. Toto téma ukazuje rozdíly mezi různé typy ovládacích prvků, ze kterého může dědit vlastnosti a poskytuje informace o tom, jak vybrat konkrétní druh ovládacího prvku pro váš projekt.  
  
> [!NOTE]
>  Informace o vytvoření ovládacího prvku pro použití na webové formuláře, naleznete v tématu [vývoj vlastních serverových ovládacích prvků ASP.NET](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="base-control-class"></a>Základní třídy ovládacího prvku  
 <xref:System.Windows.Forms.Control> Třída je základní třída pro ovládací prvky Windows Forms. Poskytuje infrastrukturu potřebnou pro zobrazení vizuálu v aplikacích Windows Forms.  
  
 <xref:System.Windows.Forms.Control> Třída provádí následující úkoly k poskytování vizuálního zobrazení v aplikacích Windows Forms:  
  
-   Zpřístupňuje popisovač okna.  
  
-   Spravuje směrování zpráv.  
  
-   Poskytuje myši a klávesnice události a mnoho dalších události uživatelského rozhraní.  
  
-   Poskytuje funkce Rozšířené rozložení.  
  
-   Obsahuje mnoho vlastností, které jsou specifické pro zobrazení vizuálu, jako jsou například <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, a <xref:System.Windows.Forms.Control.Width%2A>.  
  
-   Poskytuje zabezpečení a dělení na vlákna podpory, které jsou nezbytné pro ovládací prvek Windows Forms tak, aby fungoval jako ovládací prvek ActiveX Microsoft®.  
  
 Protože tolik infrastruktury poskytuje základní třídy, je poměrně snadné pro vývoj vlastních ovládacích prvků Windows Forms.  
  
## <a name="kinds-of-controls"></a>Typy ovládacích prvků  
 Podporuje tři druhy uživatelské ovládací prvky Windows Forms: *složené*, *rozšířené*, a *vlastní*. Následující části popisují každý druh ovládacího prvku a poskytnout doporučení pro výběr typu použití ve vašich projektech.  
  
### <a name="composite-controls"></a>Složené ovládací prvky  
 Složený ovládací prvek je kolekce ovládacích prvků Windows Forms zapouzdřena v společný kontejner. Někdy se označuje jako tento druh ovládacího prvku *uživatelský ovládací prvek*. Obsažené ovládací prvky jsou volány *základní ovládací prvky*.  
  
 Složený ovládací prvek obsahuje všechny vlastní funkce spojené s jednotlivými obsažené ovládací prvky Windows Forms a umožňuje selektivně vystavení a vytvořit vazbu vlastnosti. Složený ovládací prvek také poskytuje spoustu výchozí klávesnice zpracování funkce s žádná náročnost vývoje navíc z vaší strany.  
  
 Například může být postavená složený ovládací prvek pro zobrazení adresy zákaznická data z databáze. Tento ovládací prvek může zahrnovat <xref:System.Windows.Forms.DataGridView> ovládací prvek pro zobrazení databázová pole, <xref:System.Windows.Forms.BindingSource> zpracování vazby ke zdroji dat a <xref:System.Windows.Forms.BindingNavigator> ovládací prvek pro procházení záznamů. Selektivně může zpřístupnit datové vazby vlastnosti, a můžete zabalit a znovu použít celý ovládací prvek z aplikací. Příklad tohoto druhu složeného ovládacího prvku, naleznete v tématu [postupy: použití atributů v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
 Vytvoření složeného ovládacího prvku, odvozovat <xref:System.Windows.Forms.UserControl> třídy. <xref:System.Windows.Forms.UserControl> Základní třída poskytuje směrování klávesnice pro podřízené ovládací prvky a umožňuje podřízené ovládací prvky pro práci s jako skupinu. Další informace najdete v tématu [vývoj složeného ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
 **Doporučení**  
  
 Dědí <xref:System.Windows.Forms.UserControl> třídy, pokud:  
  
-   Je potřeba sloučit funkce několik ovládacích prvků Windows Forms do jediné opakovaně použitelné jednotky.  
  
### <a name="extended-controls"></a>Rozšířené ovládací prvky  
 Zděděný ovládací prvek lze odvodit z jakékoli existující ovládací prvek Windows Forms. Tento přístup můžete zachovat všechny vlastní funkce ovládacího prvku Windows Forms a pak rozšířit přidáním vlastní vlastnosti, metody a další funkce, které tuto funkci. Pomocí této možnosti můžete přepsat logiku programu Malování základního ovládacího prvku a pak rozšířit tak, že změníte její vzhled uživatelského rozhraní.  
  
 Například můžete vytvořit ovládací prvek odvozen od <xref:System.Windows.Forms.Button> ovládací prvek, který sleduje, kolikrát uživatel klikl.  
  
 V některých ovládacích prvků, můžete také přidat vlastní vzhled grafického uživatelského rozhraní ovládacího prvku tak, že přepíšete <xref:System.Windows.Forms.Control.OnPaint%2A> metody základní třídy. Rozšířené tlačítka, který sleduje kliknutí, můžete přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metodu chce volat základní implementaci <xref:System.Windows.Forms.Control.OnPaint%2A>a potom klikněte na počtu vykreslování v roh <xref:System.Windows.Forms.Button> klientské oblasti ovládacího prvku.  
  
 **Doporučení**  
  
 Dědění z ovládacího prvku Windows Forms, pokud:  
  
-   Většinu funkcí, které potřebujete, už se shoduje s existujícího ovládacího prvku Windows Forms.  
  
-   Není nutné vlastní grafické uživatelské rozhraní, nebo chcete provést návrh novým grafickým uživatelským rozhraním pro existující ovládací prvek.  
  
### <a name="custom-controls"></a>Vlastní ovládací prvky  
 Dalším způsobem, jak vytvořit ovládací prvek je podstatně od začátku vytvořit děděním z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Třída obsahuje všechny základní funkce vyžadované ovládacích prvků, včetně myš a klávesnici zpracování událostí, ale žádné funkce specifické pro ovládací prvek nebo grafické rozhraní.  
  
 Vytvoření pomocí dědění z ovládacího prvku <xref:System.Windows.Forms.Control> třídy vyžaduje mnohem více myšlenek a úsilí než dědění z <xref:System.Windows.Forms.UserControl> nebo existujícího ovládacího prvku Windows Forms. Protože spoustu implementace je ponecháno za vás, váš ovládací prvek může mít větší flexibilitu než složený nebo rozšířené ovládací prvek a můžete přizpůsobit ovládacího prvku tak, aby odpovídala vaše konkrétní požadavky.  
  
 Pro implementaci vlastního ovládacího prvku, je nutné napsat kód pro <xref:System.Windows.Forms.Control.OnPaint%2A> události ovládacího prvku, stejně jako jakýkoli kód specifickými funkcemi, budete potřebovat. Můžete také přepsat <xref:System.Windows.Forms.Control.WndProc%2A> metoda a popisovač zpráv systému windows přímo. Jedná se o procesorově nejvýkonnější způsob vytvoření ovládacího prvku, ale efektivně používat tuto techniku, musíte se seznámit s rozhraním API Microsoft Win32®.  
  
 Příklad vlastního ovládacího prvku je hodiny ovládací prvek, který napodobuje vzhled a chování analogové hodiny. Vlastní vykreslování je vyvolán způsobit rukou hodiny tak, aby v reakci na přesunutí <xref:System.Windows.Forms.Timer.Tick> události z interní <xref:System.Windows.Forms.Timer> komponenty. Další informace najdete v tématu [postup: vývoj jednoduchého ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 **Doporučení**  
  
 Dědí <xref:System.Windows.Forms.Control> třídy, pokud:  
  
-   Chcete poskytnout vlastní grafické reprezentace ovládacího prvku.  
  
-   Potřebujete implementovat vlastní funkce, které nejsou k dispozici prostřednictvím standardní ovládací prvky.  
  
### <a name="activex-controls"></a>ActiveX – ovládací prvky  
 I když byla optimalizována pro infrastrukturu formulářů Windows do hostitelské ovládací prvky Windows Forms, můžete stále použít ovládací prvky ActiveX. Není poskytována podpora pro tuto úlohu v sadě Visual Studio. Další informace najdete v tématu [postupy: Přidání ovládacích prvků ActiveX do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md).  
  
### <a name="windowless-controls"></a>Ovládací prvky bez oken  
 Podpora technologie ActiveX the Microsoft Visual Basic® 6.0and *bez oken* ovládacích prvků. Ovládací prvky bez oken nejsou podporovány v rozhraní Windows Forms.  
  
## <a name="custom-design-experience"></a>Vlastní návrhové prostředí  
 Pokud potřebujete implementovat vlastní možnosti času návrhu, můžete vytvářet vlastní návrháře. Složené ovládací prvky, odvodit vlastní třídu návrháře z <xref:System.Windows.Forms.Design.ParentControlDesigner> nebo <xref:System.Windows.Forms.Design.DocumentDesigner> třídy. Rozšířené a vlastních ovládacích prvků, jsou odvozeny z vlastní třídu návrháře <xref:System.Windows.Forms.Design.ControlDesigner> třídy.  
  
 Použití <xref:System.ComponentModel.DesignerAttribute> chcete přidružit k vaší návrhář ovládacího prvku. Další informace najdete v tématu [rozšíření podpory během návrhu](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2) a [postupy: vytvoření Windows Forms ovládací prvek, že trvá výhody z návrhu funkcí](https://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).  
  
## <a name="see-also"></a>Viz také  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Vývoj složeného ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [Rozšíření podpory během návrhu](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Postupy: vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu aplikace](https://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)
