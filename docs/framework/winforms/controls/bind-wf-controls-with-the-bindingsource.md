---
title: 'Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: a4f87303954494e8e32d32e68fb3f1244f25680a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304555"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře
Po přidání ovládacích prvků do formuláře a určit uživatelského rozhraní pro vaši aplikaci, lze svázat ovládací prvky zdroje dat, tak, aby v době běhu, uživatelé mohou změnit a uložit data související s aplikací.  
  
 Vytvoření vazby ovládacího prvku nebo řadu ovládacích prvků ve Windows Forms nejsnadněji využívá se při něm <xref:System.Windows.Forms.BindingSource> ovládací prvek jako most mezi ovládacími prvky ve formuláři a zdroj dat.  
  
 Jeden nebo více ovládacích prvků na formuláři mohou být vázány na data. v následujícím postupu <xref:System.Windows.Forms.TextBox> ovládací prvek vázán na zdroj dat.  
  
 Dokončete tento postup předpokládá se, že bude vytvoření vazby ke zdroji dat, který je odvozen z databáze. Další informace o vytvoření zdroje dat z jiných úložišť dat najdete v tématu [přidat nové zdroje dat](/visualstudio/data-tools/add-new-data-sources).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-bind-a-control-at-design-time"></a>K vytvoření vazby ovládacího prvku v době návrhu  
  
1. Přetáhněte <xref:System.Windows.Forms.TextBox> ovládací prvek do formuláře.  
  
2. V **vlastnosti** okno:  
  
    1.  Rozbalte **(DataBindings)** uzlu.  
  
    2.  Klikněte na šipku vedle položky <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.  
  
         **DataSource** otevře editor typu uživatelského rozhraní.  
  
         Pokud zdroj dat byl dříve nakonfigurován pro projekt nebo formuláře, se zobrazí.  
  
3. Klikněte na tlačítko **přidat zdroj dat projektu** vytvořit zdroj dat a připojte se k datům.  
  
4. Na **Průvodce konfigurací zdroje dat** úvodní stránka, klikněte na tlačítko **Další**.  
  
5. Na **zvolte typ zdroje dat** stránce **databáze**.  
  
6. Na **vyberte datové připojení** vyberte datové připojení ze seznamu dostupných připojení. Pokud požadované datové připojení není k dispozici vyberte **nové připojení** k vytvoření nové datové připojení.  
  
7. Vyberte **Ano, uložit připojení** uložit připojovací řetězec do konfiguračního souboru aplikace.  
  
8. Vyberte databázové objekty do vaší aplikace. V takovém případě vyberete pole v tabulce, kterou byste uvítali <xref:System.Windows.Forms.TextBox> k zobrazení.  
  
9. Nahraďte výchozí název datové sady, chcete-li.  
  
10. Klikněte na tlačítko **Dokončit**.  
  
11. V **vlastnosti** okna, klikněte na šipku vedle položky <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost znovu. V **DataSource** editoru typů uživatelského rozhraní, vyberte název pole, které chcete vytvořit vazbu <xref:System.Windows.Forms.TextBox> k.  
  
     **DataSource** typ uživatelského rozhraní editoru zavře a datové sady, <xref:System.Windows.Forms.BindingSource> a specifické pro datové připojení jsou přidaná do svého formuláře tabulku adaptéru.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Přidání nových zdrojů dat](/visualstudio/data-tools/add-new-data-sources)
- [Okno zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))