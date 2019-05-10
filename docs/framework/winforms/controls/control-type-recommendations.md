---
title: Doporučení ohledně typu ovládacího prvku
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: 9416fc3efabc3fef6b678a3aa3ddef048eed5e2f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648239"
---
# <a name="control-type-recommendations"></a>Doporučení ohledně typu ovládacího prvku
Rozhraní .NET Framework vám dává možnost vytvořit a implementovat nové ovládací prvky. Kromě známé uživatelský ovládací prvek nyní zjistíte, že budete moci napsat vlastní ovládací prvky, které vlastní vykreslení a budou moct i rozšiřovat funkce existujících ovládacích prvků prostřednictvím dědičnosti. Rozhodování o tom, jaký typ ovládacího prvku k vytvoření může být matoucí. Tato část ukazuje rozdíly mezi různé typy ovládacích prvků, ze kterého může dědit vlastnosti a poskytuje důležité informace týkající se typu vybrat pro váš projekt.  
  
> [!NOTE]
>  Pokud chcete vytvořit ovládací prvek pro použití na webové formuláře, naleznete v tématu [vývoj vlastních serverových ovládacích prvků ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Ovládací prvek dědění z Windows Forms  
 Zděděný ovládací prvek lze odvodit z jakékoli existující ovládací prvek Windows Forms. Tento přístup umožňuje zachovat všechny vlastní funkce ovládacího prvku Windows Forms a pak rozšířit přidáním vlastní vlastnosti, metody a další funkce, které tuto funkci. Například může vytvořit ovládací prvek odvozen od <xref:System.Windows.Forms.TextBox> , který může přijmout jenom čísla a automaticky převede vstup na hodnotu. Takové ovládací prvek může obsahovat kód pro ověření, která byla volána pokaždé, když se text v textovém poli změněn a může obsahovat další vlastnost, hodnota. V některých ovládacích prvků, můžete také přidat vlastní vzhled ovládacího prvku grafického rozhraní tak, že přepíšete <xref:System.Windows.Forms.Control.OnPaint%2A> metody základní třídy.  
  
 Dědění z ovládacího prvku Windows Forms, pokud:  
  
- Většinu funkcí, které potřebujete, už se shoduje s existujícího ovládacího prvku Windows Forms.  
  
- Není nutné vlastní grafické rozhraní, nebo chcete provést návrh nové grafické front-endu pro existující ovládací prvek.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>Dědění ze třídy UserControl  
 Uživatelský ovládací prvek je kolekce ovládacích prvků Windows Forms zapouzdřené do společný kontejner. Kontejner obsahuje všechny vlastní funkce spojené s jednotlivými ovládacích prvků Windows Forms a umožňuje selektivně vystavení a vytvořit vazbu vlastnosti. Příkladem uživatelského ovládacího prvku může být ovládací prvek navržená tak, aby zobrazení adres zákaznická data z databáze. Tento ovládací prvek bude zahrnovat několik textových polí k zobrazení jednotlivých polích a ovládací prvky tlačítka Procházet záznamy. Datové vazby vlastnosti mohou být vystaveny selektivně a celý ovládací prvek může zabalené a znovu použít z aplikace.  
  
 Dědí <xref:System.Windows.Forms.UserControl> třídy, pokud:  
  
- Je potřeba sloučit funkce několik ovládacích prvků Windows Forms do jediné opakovaně použitelné jednotky.  
  
## <a name="inheriting-from-the-control-class"></a>Dědění ze třídy Control  
 Dalším způsobem, jak vytvořit ovládací prvek je podstatně od nuly vytvořit děděním z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Třída obsahuje všechny základní funkce vyžadované ovládacích prvků (například události), ale žádné funkce specifické pro ovládací prvek nebo grafické rozhraní. Vytvoření pomocí dědění z ovládacího prvku <xref:System.Windows.Forms.Control> třídy vyžaduje mnohem víc myšlenek a úsilí než dědění z uživatelského ovládacího prvku nebo existujícího ovládacího prvku Windows Forms. Autor nutné napsat kód pro <xref:System.Windows.Forms.Control.OnPaint%2A> události ovládacího prvku, stejně jako jakýkoli konkrétní kód funkce, která je potřeba. Větší flexibilita může, ale a můžete je vlastní přizpůsobení ovládacího prvku tak, aby odpovídala vaše konkrétní požadavky. Příklad vlastního ovládacího prvku je hodiny ovládací prvek, který napodobuje vzhled a akce analogové hodiny. Vlastní kreslení by vyvolat a způsobit, že do rukou hodiny tak, aby v reakci na přesunutí <xref:System.Windows.Forms.Timer.Tick> události z komponentu Vnitřní časovač.  
  
 Dědí <xref:System.Windows.Forms.Control> třídy, pokud:  
  
- Chcete poskytnout vlastní grafické reprezentace ovládacího prvku.  
  
- Potřebujete implementovat vlastní funkce, které nejsou k dispozici prostřednictvím standardní ovládací prvky.  
  
- [Postupy: Zobrazení ovládacího prvku v zvolit položky panelu nástrojů – dialogové okno](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
- [Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)  
  
- [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
- [Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
- [Postupy: Dědění z existujících Windows Forms ovládacích prvků](how-to-inherit-from-existing-windows-forms-controls.md)  
  
- [Návod: Ovládací prvky ladění vlastního Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
- [Postupy: Dědit ze třídy Control](how-to-inherit-from-the-control-class.md)  
  
- [Postupy: Testování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
- [Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
- [Postupy: Dědit ze třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)  
  
- [Postupy: Autor ovládacích prvků Windows Forms](how-to-author-controls-for-windows-forms.md)  
  
- [Postupy: Vytváření složených ovládacích prvků](how-to-author-composite-controls.md)  
  
- [Návod: Vytvoření složeného ovládacího prvku s jazykem Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
- [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
- [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
- [Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio Design-Time](creating-a-wf-control-design-time-features.md)  
  
- [Postupy: Vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu aplikace](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vývoj ovládacího prvku jednoduchého Windows Forms](how-to-develop-a-simple-windows-forms-control.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
