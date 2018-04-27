---
title: 'Návod: Poskytnutí standardních položek nabídky formuláři'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 00988266804207e85bc715342f888fd29348066e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>Návod: Poskytnutí standardních položek nabídky formuláři
Můžete zadat standardní nabídky svých formulářů s <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.  
  
 Tento návod ukazuje, jak používat <xref:System.Windows.Forms.MenuStrip> řízení vytvořit standardní nabídku. Formulář také odpovědí, pokud uživatel vybere položku nabídky. Následující úlohy jsou popsané v tomto návodu:  
  
-   Vytvoření projektu modelu Windows Forms.  
  
-   Vytvoření standardní nabídky.  
  
-   Vytváření <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.  
  
-   Výběr položek nabídky zpracování.  
  
 Jakmile budete hotovi, budete mít formulář s standardní nabídky, která zobrazuje výběr položek nabídky v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.  
  
 Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: poskytování standardních položek nabídky do formuláře](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, budete potřebovat:  
  
-   Dostatečná oprávnění, abyste mohli vytvořit a spustit projekty aplikací Windows Forms v počítači, kde je nainstalován Visual Studio.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavte formulář.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte projekt aplikace Windows názvem **StandardMenuForm**.  
  
     Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  V Návrháři formulářů Windows vyberte formuláře.  
  
## <a name="creating-a-standard-menu"></a>Vytvoření standardní nabídky  
 Návrhář formulářů Windows může automaticky vyplnit <xref:System.Windows.Forms.MenuStrip> ovládacího prvku pomocí standardních položek nabídky.  
  
#### <a name="to-create-a-standard-menu"></a>Chcete-li vytvořit standardní nabídky  
  
1.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.MenuStrip> ovládacího prvku do formuláře.  
  
2.  Klikněte na tlačítko <xref:System.Windows.Forms.MenuStrip> glyfy inteligentní značky ovládacího prvku (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a vyberte **vložit standardní položky**.  
  
     <xref:System.Windows.Forms.MenuStrip> Standardních položek nabídky se zobrazí v řízení.  
  
3.  Klikněte **souboru** položku nabídky zobrazíte jeho výchozí položky nabídky a odpovídajících ikon.  
  
## <a name="creating-a-statusstrip-control"></a>Vytvoření ovládacího prvku StatusStrip  
 Použití <xref:System.Windows.Forms.StatusStrip> ovládacího prvku pro zobrazení stavu pro aplikace Windows Forms. V aktuální příkladu jsou zobrazené položky nabídky vybraný uživatelem v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.  
  
#### <a name="to-create-a-statusstrip-control"></a>Vytvoření ovládacího prvku StatusStrip  
  
1.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.StatusStrip> ovládacího prvku do formuláře.  
  
     <xref:System.Windows.Forms.StatusStrip> Řízení automaticky ukotvené do dolní části formuláře.  
  
2.  Klikněte na tlačítko <xref:System.Windows.Forms.StatusStrip> tlačítko rozevíracího seznamu a vyberte ovládacího prvku **StatusLabel** přidat <xref:System.Windows.Forms.ToolStripStatusLabel> řídit k <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.  
  
## <a name="handling-item-selection"></a>Výběr položek zpracování  
 Zpracování <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událost, která má reagovat, když uživatel vybere položku nabídky.  
  
#### <a name="to-handle-item-selection"></a>Pro zpracování výběr položek  
  
1.  Klikněte na tlačítko **souboru** položky nabídky, kterou jste vytvořili v části Vytvoření oddílu standardní nabídky.  
  
2.  V **vlastnosti** okně klikněte na tlačítko **události**.  
  
3.  Dvakrát klikněte <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událostí.  
  
     Návrhář formulářů Windows generuje obslužné rutiny události pro <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událostí.  
  
4.  Vložte následující kód do obslužné rutiny události.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  Vložit `UpdateStatus` definici metody nástroj do formuláře.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
  
#### <a name="to-test-your-form"></a>Testování formuláře  
  
1.  Stisknutím klávesy F5 zkompilování a spuštění svého formuláře.  
  
2.  Klikněte **souboru** položku nabídky otevřete nabídku.  
  
3.  Na **souboru** nabídky, klikněte na některou z položek vyberte.  
  
     <xref:System.Windows.Forms.StatusStrip> Zobrazí vybrané položky.  
  
## <a name="next-steps"></a>Další kroky  
 V tomto návodu jste vytvořili formuláře s standardní nabídky. Můžete použít <xref:System.Windows.Forms.ToolStrip> rodiny ovládacích prvků pro mnoho jiné účely:  
  
-   Vytvořit místní nabídky pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>. Další informace najdete v tématu [ContextMenu – přehled komponenty](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Vytvoření více formuláře rozhraní (MDI) dokumentu s ukotvení <xref:System.Windows.Forms.ToolStrip> ovládací prvky. Další informace najdete v tématu [návod: vytvoření formuláře MDI s Menu Merging a ToolStrip – ovládací prvky](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
-   Poskytnout vaše <xref:System.Windows.Forms.ToolStrip> profesionální vzhled ovládací prvky. Další informace najdete v tématu [postupy: nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Ovládací prvek MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
