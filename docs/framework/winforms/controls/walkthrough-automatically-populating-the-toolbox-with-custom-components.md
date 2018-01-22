---
title: "Návod: Automatické vyplnění nástrojů vlastními komponentami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b60d4ee7908a5ed9dcb3393132ba7d0bd0a6cb5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>Návod: Automatické vyplnění nástrojů vlastními komponentami
Pokud vaše komponenty jsou definovány na projekt v aktuálně otevřených řešení, se automaticky zobrazí v **sada nástrojů**, třeba akce. Můžete také ručně naplnit **sada nástrojů** s vlastních součástí s použitím [zvolte sady nástrojů položek dialogové okno (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), ale **sada nástrojů** bere v úvahu položek ve vašem řešení sestavení výstupy s následujícími charakteristikami:  
  
-   Implementuje <xref:System.ComponentModel.IComponent>;  
  
-   Nemá <xref:System.ComponentModel.ToolboxItemAttribute> nastavena na `false`;  
  
-   Nemá <xref:System.ComponentModel.DesignTimeVisibleAttribute> nastavena na `false`.  
  
> [!NOTE]
>  **Sada nástrojů** nedodrží řetězy odkaz, nebude se zobrazovat položky, které nejsou vytvořené na projekt v řešení.  
  
 Tento návod ukazuje, jak vlastní součást automaticky zobrazuje v **sada nástrojů** po komponentu. Úkoly v tomto návodu zahrnují:  
  
-   Vytvoření projektu modelu Windows Forms.  
  
-   Vytvoření vlastní komponenty.  
  
-   Vytvoření instance vlastní komponenty.  
  
-   Uvolnění a načíst vlastní komponenty.  
  
 Jakmile budete hotovi, zobrazí se **sada nástrojů** naplněný součást, kterou jste vytvořili.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavte formulář.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte projekt aplikace pro systém Windows s názvem `ToolboxExample`.  
  
     Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Přidáte novou součást do projektu. Volání `DemoComponent`.  
  
     Další informace najdete v tématu [NIB: postupy: Přidání nové položky projektu](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).  
  
3.  Sestavte projekt.  
  
4.  Z **nástroje** nabídky, klikněte na tlačítko **možnosti** položky. Klikněte na tlačítko **Obecné** pod **Návrhář formulářů Windows** položky a ujistěte se, že **AutoToolboxPopulate** je možnost nastavena na **True**.  
  
## <a name="creating-an-instance-of-a-custom-component"></a>Vytvoření Instance vlastní komponenty  
 Dalším krokem je vytvoření instance vlastní součásti na formuláři. Protože **sada nástrojů** automaticky účty pro novou součást, to je stejně snadná jako vytváření další komponenta nebo ovládací prvek.  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a>K vytvoření instance vlastní komponenty  
  
1.  Otevřít formulář projektu v **Návrhář formulářů**.  
  
2.  V **sada nástrojů**, klikněte na kartu nové názvem **ToolboxExample součásti**.  
  
     Jakmile kliknete na kartu, zobrazí se **DemoComponent**.  
  
    > [!NOTE]
    >  Z důvodů výkonu komponenty v oblasti automaticky vyplněna **sada nástrojů** nezobrazují vlastní rastrové obrázky a <xref:System.Drawing.ToolboxBitmapAttribute> není podporován. Zobrazit ikonu pro vlastní součást v **sada nástrojů**, použijte **výběr položek sady nástrojů** dialogové okno načíst příslušné součásti.  
  
3.  Přetáhněte příslušné součásti do formuláře.  
  
     Instance součásti je vytvořen a přidán do **komponent**.  
  
## <a name="unloading-and-reloading-a-custom-component"></a>Uvolnění a načíst vlastní komponenty  
 **Sada nástrojů** načíst účet trvá součástí v každém projektu a když na projekt je odpojen, odebere odkazy na součástí projektu.  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a>A experimentovat s vliv na panelu nástrojů uvolnění a opětovném načtení součásti  
  
1.  Uvolněte projekt z řešení.  
  
     Další informace o uvolnění projekty najdete v tématu [NIB: postupy: uvolnění a načtěte projekty](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b). Pokud se zobrazí výzva k uložení, zvolte **Ano**.  
  
2.  Přidejte nový **aplikace Windows** projektu k řešení. Otevřete formulář v **Návrhář**.  
  
     **ToolboxExample součásti** karta z předchozí projektu je nyní pryč.  
  
3.  Načtěte `ToolboxExample` projektu.  
  
     **ToolboxExample součásti** kartě teď se bude zobrazovat.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje, který **sada nástrojů** bere v úvahu součástí projektu, ale **sada nástrojů** je také účtu trvá ovládacích prvků. Experimentujte s vlastní ovládací prvky podle přidávání a odebírání řízení projektů z vašeho řešení.  
  
## <a name="see-also"></a>Viz také  
 [Obecné, Návrhář formulářů Windows, dialogové okno Možnosti](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [Postupy: manipulace s kartami panelu nástrojů](http://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [Výběr dialogové okno položek sady nástrojů (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Vkládání ovládacích prvků do Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
