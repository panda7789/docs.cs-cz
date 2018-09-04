---
title: Doporučení ohledně typu ovládacího prvku
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: 5ce801a96bc4ef48934b983838dcf8578a5bc6e6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503014"
---
# <a name="control-type-recommendations"></a>Doporučení ohledně typu ovládacího prvku
Rozhraní .NET Framework vám dává možnost vytvořit a implementovat nové ovládací prvky. Kromě známé uživatelský ovládací prvek nyní zjistíte, že budete moci napsat vlastní ovládací prvky, které vlastní vykreslení a budou moct i rozšiřovat funkce existujících ovládacích prvků prostřednictvím dědičnosti. Rozhodování o tom, jaký typ ovládacího prvku k vytvoření může být matoucí. Tato část ukazuje rozdíly mezi různé typy ovládacích prvků, ze kterého může dědit vlastnosti a poskytuje důležité informace týkající se typu vybrat pro váš projekt.  
  
> [!NOTE]
>  Pokud chcete vytvořit ovládací prvek pro použití na webové formuláře, naleznete v tématu [vývoj vlastních serverových ovládacích prvků ASP.NET](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Ovládací prvek dědění z Windows Forms  
 Zděděný ovládací prvek lze odvodit z jakékoli existující ovládací prvek Windows Forms. Tento přístup umožňuje zachovat všechny vlastní funkce ovládacího prvku Windows Forms a pak rozšířit přidáním vlastní vlastnosti, metody a další funkce, které tuto funkci. Například může vytvořit ovládací prvek odvozen od <xref:System.Windows.Forms.TextBox> , který může přijmout jenom čísla a automaticky převede vstup na hodnotu. Takové ovládací prvek může obsahovat kód pro ověření, která byla volána pokaždé, když se text v textovém poli změněn a může obsahovat další vlastnost, hodnota. V některých ovládacích prvků, můžete také přidat vlastní vzhled ovládacího prvku grafického rozhraní tak, že přepíšete <xref:System.Windows.Forms.Control.OnPaint%2A> metody základní třídy.  
  
 Dědění z ovládacího prvku Windows Forms, pokud:  
  
-   Většinu funkcí, které potřebujete, už se shoduje s existujícího ovládacího prvku Windows Forms.  
  
-   Není nutné vlastní grafické rozhraní, nebo chcete provést návrh nové grafické front-endu pro existující ovládací prvek.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>Dědění ze třídy UserControl  
 Uživatelský ovládací prvek je kolekce ovládacích prvků Windows Forms zapouzdřené do společný kontejner. Kontejner obsahuje všechny vlastní funkce spojené s jednotlivými ovládacích prvků Windows Forms a umožňuje selektivně vystavení a vytvořit vazbu vlastnosti. Příkladem uživatelského ovládacího prvku může být ovládací prvek navržená tak, aby zobrazení adres zákaznická data z databáze. Tento ovládací prvek bude zahrnovat několik textových polí k zobrazení jednotlivých polích a ovládací prvky tlačítka Procházet záznamy. Datové vazby vlastnosti mohou být vystaveny selektivně a celý ovládací prvek může zabalené a znovu použít z aplikace.  
  
 Dědí <xref:System.Windows.Forms.UserControl> třídy, pokud:  
  
-   Je potřeba sloučit funkce několik ovládacích prvků Windows Forms do jediné opakovaně použitelné jednotky.  
  
## <a name="inheriting-from-the-control-class"></a>Dědění ze třídy Control  
 Dalším způsobem, jak vytvořit ovládací prvek je podstatně od nuly vytvořit děděním z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Třída obsahuje všechny základní funkce vyžadované ovládacích prvků (například události), ale žádné funkce specifické pro ovládací prvek nebo grafické rozhraní. Vytvoření pomocí dědění z ovládacího prvku <xref:System.Windows.Forms.Control> třídy vyžaduje mnohem víc myšlenek a úsilí než dědění z uživatelského ovládacího prvku nebo existujícího ovládacího prvku Windows Forms. Autor nutné napsat kód pro <xref:System.Windows.Forms.Control.OnPaint%2A> události ovládacího prvku, stejně jako jakýkoli konkrétní kód funkce, která je potřeba. Větší flexibilita může, ale a můžete je vlastní přizpůsobení ovládacího prvku tak, aby odpovídala vaše konkrétní požadavky. Příklad vlastního ovládacího prvku je hodiny ovládací prvek, který napodobuje vzhled a akce analogové hodiny. Vlastní kreslení by vyvolat a způsobit, že do rukou hodiny tak, aby v reakci na přesunutí <xref:System.Windows.Forms.Timer.Tick> události z komponentu Vnitřní časovač.  
  
 Dědí <xref:System.Windows.Forms.Control> třídy, pokud:  
  
-   Chcete poskytnout vlastní grafické reprezentace ovládacího prvku.  
  
-   Potřebujete implementovat vlastní funkce, které nejsou k dispozici prostřednictvím standardní ovládací prvky.  
  
-   [Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](https://msdn.microsoft.com/library/5h0k2e6x\(v=vs.110\))  
  
-   [Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [Postupy: Dědění ze stávajících ovládacích prvků Windows Forms](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [Postupy: Dědění ze třídy Control](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [Postupy: Otestování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   [Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [Postupy: Dědění ze třídy UserControl](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [Postupy: Vytváření ovládacích prvků pro Windows Forms](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [Postupy: Vytváření složených ovládacích prvků](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](https://msdn.microsoft.com/library/a6h7e207\(v=vs.110\))  
  
-   [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [Postupy: vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu aplikace](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [Postupy: vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu aplikace](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
