---
title: Doporučení ohledně typu ovládacího prvku
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: d6a2b663c566aae48c694ffc335fcef0ce24034f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="control-type-recommendations"></a>Doporučení ohledně typu ovládacího prvku
Rozhraní .NET Framework poskytuje power vývoji a implementovat nové ovládací prvky. Kromě známých uživatelského ovládacího prvku teď zjistíte, že budete moci napsat vlastní ovládací prvky, které provedení vlastní Malování a dokonce můžou rozšířit funkce existujících ovládacích prvků prostřednictvím dědičnosti. Rozhodnutí, jaké typy ovládacích prvků k vytvoření může být matoucí. V této části jsou zdůrazněné rozdílům mezi různé typy ovládacích prvků, ze kterého může dědit vlastnosti a poskytuje důležité informace týkající se typu vybrat pro váš projekt.  
  
> [!NOTE]
>  Pokud chcete vytvořit ovládacího prvku k použití na webové formuláře naleznete v části [vývoj vlastních serverových ovládacích prvků ASP.NET](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Ovládací prvek, která dědí z Windows Forms  
 Ovládací prvek zděděné lze odvozovat od všechny existující ovládacího prvku Windows Forms. Tento přístup umožňuje zachovat všechny vyplývajících funkce ovládacího prvku Windows Forms a pak tato funkcionalita rozšířit přidáním vlastní vlastnosti, metody nebo další funkce. Můžete například vytvořit odvozenou z ovládacího prvku <xref:System.Windows.Forms.TextBox> který může přijmout pouze čísla a automaticky převede vstup na hodnotu. Takový ovládací prvek může obsahovat ověřovací kód, který byla volána vždy, když text v textovém poli změnit a další vlastnosti, může mít hodnotu. V některé ovládací prvky, můžete také přidat vlastní vzhled grafické rozhraní ovládacího prvku přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metoda základní třídy.  
  
 Dědění z ovládacího prvku Windows Forms, pokud:  
  
-   Již je stejná jako existující ovládacího prvku Windows Forms většinu funkcí, které potřebujete.  
  
-   Není nutné vlastní grafické rozhraní, nebo můžete navrhnout grafické nové front-end pro existujícího ovládacího prvku.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>Dědění ze třídy UserControl  
 Uživatelský ovládací prvek je kolekce ovládacích prvků Windows Forms zapouzdřené do běžné kontejneru. Kontejner obsahuje všechny vyplývajících funkce související s jednotlivými ovládací prvky Windows Forms a umožňuje selektivně vystavit a vytvořte vazbu jejich vlastnosti. Příkladem uživatelský ovládací prvek může být vytvořená tak, aby zobrazení dat zákazníka adresu z databáze ovládacího prvku. Tento ovládací prvek bude zahrnovat několik textových polí k zobrazení každého pole a tlačítko – ovládací prvky procházet záznamy. Datové vazby vlastnosti mohou být vystaveny selektivně a celý ovládací prvek může být zabalené a znovu z aplikace do aplikace.  
  
 Dědit z <xref:System.Windows.Forms.UserControl> třídy, pokud:  
  
-   Chcete zkombinovat do jedné jednotky opakovaně použitelné funkci několik ovládacích prvků Windows Forms.  
  
## <a name="inheriting-from-the-control-class"></a>Dědění ze třídy Control  
 Další způsob vytvoření ovládacího prvku je podstatně od nuly vytvořit dědění ze <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Třída poskytuje všechny základní funkce vyžaduje ovládací prvky (například událostí), ale žádné funkce specifické pro ovládací prvek nebo grafické rozhraní. Vytvoření ovládacího prvku dědění ze <xref:System.Windows.Forms.Control> třída vyžaduje mnohem víc myšlenku a úsilí než dědění z uživatelský ovládací prvek nebo existujícího ovládacího prvku Windows Forms. Autor musíte napsat kód pro <xref:System.Windows.Forms.Control.OnPaint%2A> události ovládacího prvku, jakož i funkce konkrétní kód, který je potřeba. Je-li povolena větší flexibilitu, ale a můžete vlastní přizpůsobení ovládacího prvku tak, aby vyhovovala vašim konkrétním potřebám. Příklad vlastní ovládací prvek je ovládací prvek hodiny, která duplikuje vzhled a akce analogovým hodiny. Vlastní Malování by být volána způsobí do nesprávných rukou hodiny přesunout v reakci na <xref:System.Windows.Forms.Timer.Tick> události z komponentu interní časovače.  
  
 Dědit z <xref:System.Windows.Forms.Control> třídy, pokud:  
  
-   Chcete zadat vlastní grafické reprezentace vlastního ovládacího prvku.  
  
-   Potřebujete implementovat vlastní funkce, která není k dispozici prostřednictvím standardní ovládací prvky.  
  
-   [Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))  
  
-   [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](http://msdn.microsoft.com/library/5h0k2e6x\(v=vs.110\))  
  
-   [Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [Postupy: Dědění ze stávajících ovládacích prvků Windows Forms](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [Postupy: Dědění ze třídy Control](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [Postupy: Otestování běhového chování UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))  
  
-   [Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [Postupy: Dědění ze třídy UserControl](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [Postupy: Vytváření ovládacích prvků pro Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [Postupy: Vytváření složených ovládacích prvků](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](http://msdn.microsoft.com/library/a6h7e207\(v=vs.110\))  
  
-   [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [Postupy: vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [Postupy: vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
