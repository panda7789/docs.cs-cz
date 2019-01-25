---
title: 'Průvodce: Automatické vyplnění nástrojů vlastními komponentami'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 8c40f4a58800183c142602d950e4fe1331c1eaf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730266"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>Průvodce: Automatické vyplnění nástrojů vlastními komponentami
Pokud vaše komponenty jsou definovány projektu v aktuálně otevřené řešení, se automaticky zobrazí v **nástrojů**, třeba akce. Můžete také ručně naplnit **nástrojů** pomocí vlastních součástí s použitím [tlačítko panelu nástrojů položky dialogové okno (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), ale **nástrojů** bere v úvahu položky ve vašem řešení sestavení výstupy s následujícími charakteristikami:  
  
-   Implementuje <xref:System.ComponentModel.IComponent>;  
  
-   Nemá <xref:System.ComponentModel.ToolboxItemAttribute> nastavena na `false`;  
  
-   Nemá <xref:System.ComponentModel.DesignTimeVisibleAttribute> nastavena na `false`.  
  
> [!NOTE]
>  **Nástrojů** nedodržuje odkaz na řetězcích, proto by se nezobrazil položky, které nejsou sestaveny projekt ve vašem řešení.  
  
 Tento návod ukazuje, jak vlastní komponenty se automaticky zobrazí v **nástrojů** po sestavení komponenty. Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření projektu Windows Forms.  
  
-   Vytvoření vlastní komponenty.  
  
-   Vytvoření instance vlastní komponenty.  
  
-   Uvolnění a opětovné načtení volitelná množina komponent.  
  
 Až budete hotovi, uvidíte, že **nástrojů** se vyplní komponentu, kterou jste vytvořili.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a k nastavení tvaru.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte projekt aplikace pro systém Windows s názvem `ToolboxExample` (**souboru** > **nový** > **projektu**  >  **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).  
  
2.  Přidáte novou součást do projektu. Pojmenujte ji `DemoComponent`.  
  
     Další informace najdete v tématu [NIB: jak: Přidání nových položek projektu](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).  
  
3.  Sestavte projekt.  
  
4.  Z **nástroje** nabídky, klikněte na tlačítko **možnosti** položky. Klikněte na tlačítko **Obecné** pod **Návrháře formulářů Windows** položku a ověřte, že **AutoToolboxPopulate** je možnost nastavená na **True**.  
  
## <a name="creating-an-instance-of-a-custom-component"></a>Vytvoření Instance vlastní komponenty  
 Dalším krokem je vytvoření instance vlastní komponenty ve formuláři. Vzhledem k tomu, **nástrojů** automaticky účty pro novou komponentu, to je stejně jednoduché jako vytvoření jakékoli součást nebo ovládací prvek.  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a>K vytvoření instance vlastní komponenty  
  
1.  Otevřete formulář v projektu v **Návrháře formulářů**.  
  
2.  V **nástrojů**, klikněte na novou kartu **ToolboxExample komponenty**.  
  
     Po kliknutí na kartě, zobrazí se **DemoComponent**.  
  
    > [!NOTE]
    >  Z důvodů výkonu komponenty v oblasti vyplní automaticky **nástrojů** vlastních rastrových obrázků, se nezobrazí a <xref:System.Drawing.ToolboxBitmapAttribute> se nepodporuje. Zobrazit ikonu pro vlastní komponenty v **nástrojů**, použijte **zvolit položky nástrojů** dialogové okno načíst vaše komponenta.  
  
3.  Přetáhněte komponenty do formuláře.  
  
     Je vytvořen a přidán do instance komponenty **komponent**.  
  
## <a name="unloading-and-reloading-a-custom-component"></a>Uvolnění a opětovné načtení volitelná množina komponent  
 **Nástrojů** přihlíží komponent v každém načtení projektu a projekt je uvolněna, odebere odkazy na součásti projektu.  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a>Můžete experimentovat s vliv na panelu nástrojů uvolnění a opětovné načítání komponent  
  
1.  Uvolněte projekt z řešení.  
  
     Další informace o uvolnění projektů, naleznete v tématu [NIB: jak: Odebrat a znovu načíst projekty](https://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b). Pokud se zobrazí výzva k uložení, zvolte **Ano**.  
  
2.  Přidat nový **aplikace Windows** projektu do řešení. Otevřete formulář v nástrojích pro **návrháře**.  
  
     **ToolboxExample součásti** kartu z předchozí projektu je teď pryč.  
  
3.  Znovu načíst `ToolboxExample` projektu.  
  
     **ToolboxExample součásti** kartě nyní zobrazí znovu.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje, že **nástrojů** bere v úvahu součástí projektu, ale **nástrojů** je také přihlíží ovládacích prvků. Přidáváním a odebíráním ovládací prvek projekty z řešení můžete experimentovat s vlastní ovládací prvky.  
  
## <a name="see-also"></a>Viz také:
- [Obecné, Návrhář formulářů Windows, dialogové okno Možnosti](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)
- [Postupy: Manipulace s karty panelu nástrojů](https://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)
- [Zvolte dialogové okno položky panelu nástrojů (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)
- [Vkládání ovládacích prvků do Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
