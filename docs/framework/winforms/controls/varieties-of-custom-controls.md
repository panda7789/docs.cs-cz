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
ms.openlocfilehash: 106da550fc6e6c50bc40e103e1f855059a9ffa9c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950091"
---
# <a name="varieties-of-custom-controls"></a>Typy vlastních ovládacích prvků
Pomocí .NET Framework můžete vyvíjet a implementovat nové ovládací prvky. Můžete roztáhnout funkce známého uživatelského ovládacího prvku i existující ovládací prvky prostřednictvím dědičnosti. Můžete také napsat vlastní ovládací prvky, které provádějí vlastní malování.  
  
 Rozhodnutí o tom, jaký druh ovládacího prvku vytvořit, může být matoucí. Toto téma popisuje rozdíly mezi různými druhy ovládacích prvků, ze kterých lze dědit, a poskytuje informace o tom, jak zvolit konkrétní typ ovládacího prvku pro projekt.  
  
> [!NOTE]
> Informace o vytváření ovládacích prvků pro použití ve webových formulářích naleznete v tématu [vývoj vlastních ovládacích prvků ASP.NET serveru](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="base-control-class"></a>Základní třída ovládacího prvku  
 <xref:System.Windows.Forms.Control> Třída je základní třídou pro ovládací prvky model Windows Forms. Poskytuje infrastrukturu potřebnou pro vizuální zobrazení v aplikacích model Windows Forms.  
  
 <xref:System.Windows.Forms.Control> Třída provádí následující úlohy, které poskytují vizuální zobrazení v aplikacích model Windows Forms:  
  
- Zpřístupňuje popisovač okna.  
  
- Spravuje směrování zpráv.  
  
- Poskytuje události myši a klávesnice a mnoho dalších událostí uživatelského rozhraní.  
  
- Poskytuje pokročilé funkce rozložení.  
  
- Obsahuje mnoho vlastností specifických pro vizuální zobrazení <xref:System.Windows.Forms.Control.ForeColor%2A>, například <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, a <xref:System.Windows.Forms.Control.Width%2A>.  
  
- Poskytuje podporu zabezpečení a vláken, která je nezbytná, aby model Windows Forms ovládací prvek pracoval jako ovládací prvek ActiveX Microsoft®®.  
  
 Vzhledem k tomu, že velká část infrastruktury je poskytována základní třídou, je poměrně snadné vyvíjet vlastní ovládací prvky model Windows Forms.  
  
## <a name="kinds-of-controls"></a>Typy ovládacích prvků  
 Model Windows Forms podporuje tři typy uživatelsky definovaných ovládacích prvků: *složené*, *Rozšířené*a *vlastní*. Následující části popisují jednotlivé druhy ovládacích prvků a dávají doporučení pro výběr druhu pro použití ve vašich projektech.  
  
### <a name="composite-controls"></a>Složené ovládací prvky  
 Složený ovládací prvek je kolekce model Windows Formsch ovládacích prvků zapouzdřených ve společném kontejneru. Tento druh ovládacího prvku se někdy označuje jako *uživatelský ovládací prvek*. Obsažené ovládací prvky se nazývají *ovládací prvky prvků*.  
  
 Složený ovládací prvek obsahuje veškerou základní funkčnost spojenou s každým z obsažených ovládacích prvků model Windows Forms a umožňuje selektivní vystavení a vázání jejich vlastností. Složený ovládací prvek také poskytuje skvělou funkci výchozích funkcí pro zpracování klávesnice bez dalšího vývojového úsilí na vaši část.  
  
 Složený ovládací prvek může být například sestaven tak, aby zobrazoval údaje o zákaznických adresách z databáze. Tento ovládací prvek může obsahovat <xref:System.Windows.Forms.DataGridView> ovládací prvek pro zobrazení polí databáze <xref:System.Windows.Forms.BindingSource> , pro zpracování vazby na zdroj <xref:System.Windows.Forms.BindingNavigator> dat a ovládací prvek pro procházení záznamů. Můžete selektivně vystavit vlastnosti datové vazby a můžete zabalit a znovu použít celý ovládací prvek z aplikace do aplikace. Příklad tohoto druhu složeného ovládacího prvku naleznete v tématu [How to: Použití atributů v ovládacích prvcích](how-to-apply-attributes-in-windows-forms-controls.md)model Windows Forms.  
  
 Chcete-li vytvořit složený ovládací prvek, odvozujte z <xref:System.Windows.Forms.UserControl> třídy. <xref:System.Windows.Forms.UserControl> Základní třída poskytuje směrování klávesnice pro podřízené ovládací prvky a umožňuje podřízeným ovládacím prvkům pracovat jako skupina. Další informace naleznete v tématu [Vývoj složeného ovládacího prvku model Windows Forms](developing-a-composite-windows-forms-control.md).  
  
 **Doporučení**  
  
 Zdědit z třídy <xref:System.Windows.Forms.UserControl> , pokud:  
  
- Chcete kombinovat funkce několika model Windows Formsch ovládacích prvků do jediné opakovaně použitelné jednotky.  
  
### <a name="extended-controls"></a>Rozšířené ovládací prvky  
 Zděděný ovládací prvek lze odvodit ze všech existujících ovládacích prvků model Windows Forms. Díky tomuto přístupu můžete uchovávat všechny podstatné funkce ovládacího prvku model Windows Forms a následně tyto funkce roztáhnout přidáním vlastních vlastností, metod nebo dalších funkcí. Pomocí této možnosti můžete přepsat logiku vykreslování základního ovládacího prvku a poté zvětšit jeho uživatelské rozhraní změnou jeho vzhledu.  
  
 Můžete například vytvořit ovládací prvek odvozený z <xref:System.Windows.Forms.Button> ovládacího prvku, který sleduje, kolikrát na něj uživatel kliknul.  
  
 V některých ovládacích prvcích můžete také přidat vlastní vzhled do grafického uživatelského rozhraní ovládacího prvku přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metody základní třídy. Pro rozšířené tlačítko, které sleduje kliknutí, můžete přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metodu pro volání základní <xref:System.Windows.Forms.Control.OnPaint%2A>implementace a potom vykreslit počet kliknutí <xref:System.Windows.Forms.Button> v jednom rohu klientské oblasti ovládacího prvku.  
  
 **Doporučení**  
  
 Zdědit z ovládacího prvku model Windows Forms, pokud:  
  
- Většina funkcí, které potřebujete, je již shodná s existujícím ovládacím prvkem model Windows Forms.  
  
- Nepotřebujete vlastní grafické uživatelské rozhraní nebo chcete navrhnout nové grafické uživatelské rozhraní pro existující ovládací prvek.  
  
### <a name="custom-controls"></a>Vlastní ovládací prvky  
 Dalším způsobem, jak vytvořit ovládací prvek, je vytvořit z něj podstatně od začátku tím, že <xref:System.Windows.Forms.Control>ho zdědí. <xref:System.Windows.Forms.Control> Třída poskytuje všechny základní funkce vyžadované ovládacími prvky, včetně událostí zpracování myší a klávesnicí, ale žádné funkce pro konkrétní ovládací prvek nebo grafické rozhraní.  
  
 Vytvoření ovládacího prvku děděním z <xref:System.Windows.Forms.Control> třídy vyžaduje mnohem více myšlenk a úsilí než dědění z <xref:System.Windows.Forms.UserControl> nebo existujícího ovládacího prvku model Windows Forms. Vzhledem k tomu, že značná implementace je ponechána za vás, váš ovládací prvek může mít větší flexibilitu než složený nebo rozšířený ovládací prvek a můžete přizpůsobit svůj ovládací prvek tak, aby vyhovoval vašim přesným potřebám.  
  
 Chcete-li implementovat vlastní ovládací prvek, je nutné napsat kód <xref:System.Windows.Forms.Control.OnPaint%2A> pro událost ovládacího prvku a také jakýkoli kód specifický pro funkci, který potřebujete. Můžete také přepsat <xref:System.Windows.Forms.Control.WndProc%2A> metodu a zpracovat přímo zprávy systému Windows. Toto je nejúčinnější způsob, jak vytvořit ovládací prvek, ale k efektivnímu použití této techniky je nutné znát rozhraní Microsoft Win32® API.  
  
 Příkladem vlastního ovládacího prvku je ovládací prvek hodin, který duplikuje vzhled a chování analogových hodin. Vyvolá se vlastní malování, které způsobí, že se v reakci <xref:System.Windows.Forms.Timer.Tick> na události z interní <xref:System.Windows.Forms.Timer> komponenty pohybují hodiny. Další informace najdete v tématu [jak: Vývoj jednoduchého ovládacího prvku](how-to-develop-a-simple-windows-forms-control.md)model Windows Forms.  
  
 **Doporučení**  
  
 Zdědit z třídy <xref:System.Windows.Forms.Control> , pokud:  
  
- Chcete poskytnout vlastní grafické znázornění ovládacího prvku.  
  
- Je nutné implementovat vlastní funkce, které nejsou k dispozici prostřednictvím standardních ovládacích prvků.  
  
### <a name="activex-controls"></a>ActiveX – ovládací prvky  
 I když je model Windows Forms infrastruktura optimalizovaná pro hostování model Windows Formsch ovládacích prvků, můžete i nadále používat ovládací prvky ActiveX. Pro tuto úlohu se v aplikaci Visual Studio podporuje. Další informace najdete v tématu [jak: Přidejte ovládací prvky ActiveX do](how-to-add-activex-controls-to-windows-forms.md)model Windows Forms.  
  
### <a name="windowless-controls"></a>Ovládací prvky bez oken  
 Technologie Microsoft Visual Basic® 6.0 a ActiveX podporují ovládací prvky bez *oken* . Ovládací prvky bez oken nejsou v model Windows Forms podporovány.  
  
## <a name="custom-design-experience"></a>Vlastní vývojové prostředí  
 Pokud potřebujete implementovat vlastní prostředí v době návrhu, můžete vytvořit vlastního návrháře. Pro složené ovládací prvky odvodíte vlastní třídu návrháře z <xref:System.Windows.Forms.Design.ParentControlDesigner> <xref:System.Windows.Forms.Design.DocumentDesigner> třídy nebo. Pro rozšířené a vlastní ovládací prvky odvodíte vlastní třídu návrháře z <xref:System.Windows.Forms.Design.ControlDesigner> třídy.  
  
 <xref:System.ComponentModel.DesignerAttribute> Použijte k přidružení ovládacího prvku k vašemu návrháři. Další informace najdete v tématu [rozšíření podpory při návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)) a [postup: Vytvořte model Windows Forms ovládací prvek, který bude využívat funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))pro dobu návrhu.  
  
## <a name="see-also"></a>Viz také:

- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
- [Postupy: Vývoj jednoduchého ovládacího prvku model Windows Forms](how-to-develop-a-simple-windows-forms-control.md)
- [Vývoj složeného ovládacího prvku Windows Forms](developing-a-composite-windows-forms-control.md)
- [Rozšíření podpory pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Postupy: Vytvoření model Windows Formsho ovládacího prvku, který bude využívat funkce pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
