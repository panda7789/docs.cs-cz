---
title: Doporučení ohledně typu ovládacího prvku
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: 40451aea3026a492864cf94031c0bea196a18ff3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930257"
---
# <a name="control-type-recommendations"></a>Doporučení ohledně typu ovládacího prvku
.NET Framework umožňuje vyvíjet a implementovat nové ovládací prvky. Kromě známého uživatelského ovládacího prvku teď zjistíte, že máte možnost psát vlastní ovládací prvky, které provádějí vlastní malování, a dokonce i možnost rozšířit funkce stávajících ovládacích prvků prostřednictvím dědičnosti. Rozhodnutí o tom, který typ ovládacího prvku vytvořit, může být matoucí. V této části jsou zdůrazněny rozdíly mezi různými typy ovládacích prvků, ze kterých lze dědit, a poskytuje požadavky týkající se typu, který se má zvolit pro váš projekt.  
  
> [!NOTE]
> Chcete-li vytvořit ovládací prvek pro použití ve webových formulářích, přečtěte si téma [vývoj vlastních ovládacích prvků ASP.NET serveru](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Dědění z ovládacího prvku model Windows Forms  
 Zděděný ovládací prvek lze odvodit ze všech existujících ovládacích prvků model Windows Forms. Tento přístup umožňuje zachovat všechny podstatné funkce ovládacího prvku model Windows Forms a následně tuto funkci rozšiřuje přidáním vlastních vlastností, metod nebo dalších funkcí. Například můžete vytvořit ovládací prvek odvozený z <xref:System.Windows.Forms.TextBox> , který může přijímat pouze čísla a automaticky převést vstup na hodnotu. Takový ovládací prvek může obsahovat ověřovací kód, který byl volán vždy, když se změní text v textovém poli a může mít další vlastnost, hodnota. V některých ovládacích prvcích můžete také přidat vlastní vzhled do grafického rozhraní ovládacího prvku přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metody základní třídy.  
  
 Zdědit z ovládacího prvku model Windows Forms, pokud:  
  
- Většina funkcí, které potřebujete, je již shodná s existujícím ovládacím prvkem model Windows Forms.  
  
- Nepotřebujete vlastní grafické rozhraní nebo chcete navrhnout nový grafický front-end pro existující ovládací prvek.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>Dědění od třídy UserControl  
 Uživatelský ovládací prvek je kolekce model Windows Formsch ovládacích prvků zapouzdřených do společného kontejneru. Kontejner obsahuje všechny funkce přidružené k jednotlivým ovládacím prvkům model Windows Forms a umožňuje selektivně vystavit a vytvořit vazby na své vlastnosti. Příkladem uživatelského ovládacího prvku může být ovládací prvek sestavený tak, aby zobrazoval data zákaznických adres z databáze. Tento ovládací prvek by obsahoval několik textových polí pro zobrazení každého pole a ovládací prvky tlačítka pro procházení záznamů. Vlastnosti datové vazby by mohly být selektivně vystavené a celý ovládací prvek může být zabalen a znovu použit z aplikace do aplikace.  
  
 Zdědit z třídy <xref:System.Windows.Forms.UserControl> , pokud:  
  
- Chcete kombinovat funkce několika model Windows Formsch ovládacích prvků do jediné opakovaně použitelné jednotky.  
  
## <a name="inheriting-from-the-control-class"></a>Dědění z třídy ovládacího prvku  
 Dalším způsobem, jak vytvořit ovládací prvek, je vytvořit z něj zcela nové, protože dědí <xref:System.Windows.Forms.Control>z. <xref:System.Windows.Forms.Control> Třída poskytuje všechny základní funkce vyžadované ovládacími prvky (například události), ale žádné funkce pro konkrétní ovládací prvky nebo grafické rozhraní. Vytvoření ovládacího prvku děděním z <xref:System.Windows.Forms.Control> třídy vyžaduje mnohem více myšlenosti a úsilí než dědění z uživatelského ovládacího prvku nebo z existujícího ovládacího prvku model Windows Forms. Autor musí napsat kód pro <xref:System.Windows.Forms.Control.OnPaint%2A> událost ovládacího prvku a také jakýkoli kód specifický pro konkrétní funkce, který je potřeba. Větší flexibilita je ale povolená a vlastní ovládací prvek můžete přizpůsobit tak, aby vyhovoval vašim přesným potřebám. Příkladem vlastního ovládacího prvku je ovládací prvek hodin, který duplikuje vzhled a akci analogových hodin. Vyvolalo se vlastní malování, které způsobí, že se v reakci <xref:System.Windows.Forms.Timer.Tick> na události z interní komponenty časovače přesune hodiny.  
  
 Zdědit z třídy <xref:System.Windows.Forms.Control> , pokud:  
  
- Chcete poskytnout vlastní grafické znázornění ovládacího prvku.  
  
- Je nutné implementovat vlastní funkce, které nejsou k dispozici prostřednictvím standardních ovládacích prvků.  
  
- [Postupy: Zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
- [Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)  
  
- [Návod: Dědění z ovládacího prvku model Windows Forms pomocí vizuáluC#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
- [Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
- [Postupy: Zdědit z existujících ovládacích prvků model Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)  
  
- [Návod: Ladění vlastních ovládacích prvků model Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
- [Postupy: Zdědit z třídy ovládacího prvku](how-to-inherit-from-the-control-class.md)  
  
- [Postupy: Testování chování prvku UserControl v době běhu](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
- [Postupy: Zarovnání ovládacího prvku na okraje formulářů v době návrhu](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
- [Postupy: Zdědit z třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)  
  
- [Postupy: Vytváření ovládacích prvků pro model Windows Forms](how-to-author-controls-for-windows-forms.md)  
  
- [Postupy: Vytváření složených ovládacích prvků](how-to-author-composite-controls.md)  
  
- [Návod: Vytváření složeného ovládacího prvku pomocí Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
- [Návod: Vytváření složeného ovládacího prvku pomocí vizuáluC#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
- [Návod: Dědění z ovládacího prvku model Windows Forms s Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
- [Návod: Vytvoření ovládacího prvku model Windows Forms, který využívá výhod funkcí nástroje Visual Studio pro dobu návrhu](creating-a-wf-control-design-time-features.md)  
  
- [Postupy: Vytvoření model Windows Formsho ovládacího prvku, který bude využívat funkce pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vývoj jednoduchého ovládacího prvku model Windows Forms](how-to-develop-a-simple-windows-forms-control.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
