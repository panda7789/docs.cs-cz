---
title: "Návod: Vytvoření formuláře MDI se slučováním nabídek a s ovládacími prvky ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b170c3e3311dbbfb070a66107bd4f22407647bae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Návod: Vytvoření formuláře MDI se slučováním nabídek a s ovládacími prvky ToolStrip
<xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů podporuje více aplikací rozhraní (MDI) dokumentu a <xref:System.Windows.Forms.MenuStrip> řízení podporuje slučování nabídek. MDI formuláře může taky <xref:System.Windows.Forms.ToolStrip> ovládací prvky.  
  
 Tento návod ukazuje, jak používat <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků pomocí formuláře MDI. Formulář podporuje také s nabídkami podřízené slučování nabídek. Následující úlohy jsou popsané v tomto návodu:  
  
-   Vytvoření projektu modelu Windows Forms.  
  
-   Vytváření hlavní nabídky pro formulář. Skutečný název nabídky se budou lišit.  
  
-   Přidávání <xref:System.Windows.Forms.ToolStripPanel> řídit k **sada nástrojů**.  
  
-   Vytvoření podřízené formuláře.  
  
-   Uspořádání <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky podle pořadí z-order.  
  
 Jakmile budete hotovi, budete mít formuláře MDI, který podporuje slučování nabídek a movable <xref:System.Windows.Forms.ToolStrip> ovládací prvky.  
  
 Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: vytvoření formuláře MDI s Menu Merging a ToolStrip – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, budete potřebovat:  
  
-   Abyste mohli vytvářet a spouštět projekty aplikací Windows Forms v počítači dostatečná oprávnění kde [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] je nainstalovaná.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavte formulář.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte projekt aplikace Windows názvem **MdiForm**.  
  
     Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  V Návrháři formulářů Windows vyberte formuláře.  
  
3.  V okně vlastností nastavte hodnotu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> k `true`.  
  
## <a name="creating-the-main-menu"></a>Vytváření z hlavní nabídky  
 Nadřazené formuláře MDI obsahuje hlavní nabídky. V hlavní nabídce má jedna položka nabídky s názvem **okno**. Pomocí **okno** položky nabídky, můžete vytvořit podřízených formulářů. Položky nabídky z podřízených formulářů jsou sloučeny do hlavní nabídky.  
  
#### <a name="to-create-the-main-menu"></a>Chcete-li vytvořit v hlavní nabídce  
  
1.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.MenuStrip> ovládací prvek na formuláři.  
  
2.  Přidat <xref:System.Windows.Forms.ToolStripMenuItem> k <xref:System.Windows.Forms.MenuStrip> řízení a pojmenujte ji **okno**.  
  
3.  Vyberte <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.  
  
4.  V okně vlastností nastavte hodnotu <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost `ToolStripMenuItem1`.  
  
5.  Přidat podřízenou položku k **okno** položky nabídky a potom název podpoložek **nový**.  
  
6.  V okně vlastností klikněte na tlačítko **události**.  
  
7.  Dvakrát klikněte <xref:System.Windows.Forms.ToolStripItem.Click> událostí.  
  
     Návrhář formulářů Windows generuje obslužné rutiny události pro <xref:System.Windows.Forms.ToolStripItem.Click> událostí.  
  
8.  Vložte následující kód do obslužné rutiny události.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>Přidání ovládacího prvku ToolStripPanel do sady nástrojů  
 Při použití <xref:System.Windows.Forms.MenuStrip> ovládacích prvků pomocí formuláře MDI musí mít <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku. Je nutné přidat <xref:System.Windows.Forms.ToolStripPanel> řídit k **sada nástrojů** k vytvoření formuláře MDI v Návrháři formulářů Windows.  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>Přidání ovládacího prvku ToolStripPanel do sady nástrojů  
  
1.  Otevřete **sada nástrojů**a pak klikněte na tlačítko **všechny formuláře Windows** zobrazte dostupné ovládací prvky Windows Forms.  
  
2.  Klikněte pravým tlačítkem myši a místní nabídce a vyberte **zvolit položky**.  
  
3.  V **výběr položek sady nástrojů** dialogové okno, přejděte dolů **název** sloupce vyhledejte **ToolStripPanel**.  
  
4.  Zaškrtněte políčko podle **ToolStripPanel**a potom klikněte na **OK**.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Zobrazí ovládací prvek v **sada nástrojů**.  
  
## <a name="creating-a-child-form"></a>Vytvoření podřízené formuláře  
 V tomto postupu bude definovat samostatnou podřízenou formuláře třídy, která má svou vlastní <xref:System.Windows.Forms.MenuStrip> ovládacího prvku. Položky nabídky pro tento formulář jsou sloučeny s těmi, která nadřazeného formuláře.  
  
#### <a name="to-define-a-child-form"></a>Chcete-li definovat podřízené formuláře  
  
1.  Přidejte nový formulář s názvem `ChildForm` do projektu.  
  
     Další informace najdete v tématu [postupy: Přidání Windows Forms do projektu](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
2.  Z **sada nástrojů**, přetáhněte <xref:System.Windows.Forms.MenuStrip> na formuláři podřízený ovládací prvek.  
  
3.  Klikněte na tlačítko <xref:System.Windows.Forms.MenuStrip> glyfy inteligentní značky ovládacího prvku (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a potom vyberte **upravit položky**.  
  
4.  V **Editor kolekce položek** dialogové okno pole, přidejte nový <xref:System.Windows.Forms.ToolStripMenuItem> s názvem **ChildMenuItem** do nabídky podřízené.  
  
     Další informace najdete v tématu [Editor kolekce položek ToolStrip](http://msdn.microsoft.com/en-us/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).  
  
## <a name="testing-the-form"></a>Testování formuláře  
  
#### <a name="to-test-your-form"></a>Testování formuláře  
  
1.  Stisknutím klávesy F5 zkompilování a spuštění svého formuláře.  
  
2.  Klikněte **okno** otevřete nabídku a pak klikněte na položku nabídky **nový**.  
  
     V klientské oblasti formuláře MDI se vytvoří nový formulář podřízené. Podřízené formuláře nabídky je sloučen s v hlavní nabídce.  
  
3.  Podřízené formulář zavřete.  
  
     Podřízené formuláře nabídky se odebere z hlavní nabídky.  
  
4.  Klikněte na tlačítko **nový** několikrát.  
  
     Podřízené formuláře jsou automaticky uvedené v části olit**ipomenutí** položky nabídky, protože <xref:System.Windows.Forms.MenuStrip> ovládacího prvku <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost je přiřazen.  
  
## <a name="adding-toolstrip-support"></a>Přidání podpory ToolStrip  
 V tomto postupu budete přidávat čtyři <xref:System.Windows.Forms.ToolStrip> ovládacích prvků formuláře MDI nadřazené. Každý <xref:System.Windows.Forms.ToolStrip> ovládací prvek přidán uvnitř <xref:System.Windows.Forms.ToolStripPanel> řízení, které je ukotvena hrany formuláře.  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>Přidání ovládacích prvků ToolStrip do nadřazeného formuláře MDI  
  
1.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek na formuláři.  
  
2.  S <xref:System.Windows.Forms.ToolStripPanel> vybraný ovládací prvek, dvakrát klikněte <xref:System.Windows.Forms.ToolStrip> řídit ve **sada nástrojů**.  
  
     A <xref:System.Windows.Forms.ToolStrip> ovládací prvek je vytvořen v <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.  
  
3.  Vyberte <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.  
  
4.  V okně vlastností změňte hodnotu ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Left>.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Řízení přepraviště na levé straně formuláře, pod v hlavní nabídce. Klientské oblasti MDI přizpůsobí <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.  
  
5.  Opakujte kroky 1 až 4.  
  
     Ukotvení – nové <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku do horní části formuláře.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Řízení ukotven pod hlavní nabídky, ale napravo od první <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku. Tento krok ukazuje význam pořadí z-order v správně umístění <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky.  
  
6.  Opakujte kroky 1 až 4 pro dva další <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky.  
  
     Ukotvení – nové <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky vpravo a dolní části formuláře.  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>Uspořádání ovládacích prvků ToolStripPanel podle pořadí Z-order  
 Pozice ukotveného <xref:System.Windows.Forms.ToolStripPanel> ovládacím prvku formuláře MDI je určen podle umístění ovládacího prvku v pořadí. Můžete snadno uspořádat pořadí vykreslování ovládacích prvků v okně Osnova dokumentu.  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>Chcete-li uspořádat ovládací prvky ToolStripPanel podle pořadí Z-order  
  
1.  V **zobrazení** nabídky, klikněte na tlačítko **ostatní okna**a potom klikněte na **Osnova dokumentu**.  
  
     Uspořádání vaší <xref:System.Windows.Forms.ToolStripPanel> je nestandardní ovládací prvky v předchozím postupu. Je to proto, že pořadí z-order není správná. Chcete-li změnit pořadí vykreslování ovládacích prvků použijte okno Osnova dokumentu.  
  
2.  V okně Osnova dokumentu vyberte **ToolStripPanel4**.  
  
3.  Klikněte na tlačítko šipky dolů opakovaně, dokud **ToolStripPanel4** je v dolní části seznamu.  
  
     **ToolStripPanel4** řízení ukotven v dolní části formuláře pod ostatní ovládací prvky.  
  
4.  Vyberte **ToolStripPanel2**.  
  
5.  Klikněte na tlačítko šipky dolů jednou na třetí umístění ovládacího prvku v seznamu.  
  
     **ToolStripPanel2** řízení ukotven k horní části formuláře, pod v hlavní nabídce a vyšší jiných ovládacích prvků.  
  
6.  Vyberte různé ovládacích prvků v **Osnova dokumentu** okno a přesuňte je na jiná místa v pořadí. Všimněte si vliv pořadí z-order na umístění ukotvených ovládacích prvků. Pomocí kombinace kláves CTRL-Z nebo **vrátit zpět** na **upravit** nabídky vrátit zpět.  
  
## <a name="checkpoint"></a>Kontrolní bod  
  
#### <a name="to-test-your-form"></a>Testování formuláře  
  
1.  Stisknutím klávesy F5 zkompilování a spuštění svého formuláře.  
  
2.  Klikněte na tlačítko úchytu z <xref:System.Windows.Forms.ToolStrip> řízení a přetáhněte ovládací prvek na formuláři na jiné místo.  
  
     Můžete přetáhnout <xref:System.Windows.Forms.ToolStrip> ovládacího prvku z jedné <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku do jiného.  
  
## <a name="next-steps"></a>Další kroky  
 V tomto návodu jste vytvořili nadřazené formuláře MDI s <xref:System.Windows.Forms.ToolStrip> ovládací prvky a slučování nabídek. Můžete použít <xref:System.Windows.Forms.ToolStrip> rodiny ovládacích prvků pro mnoho jiné účely:  
  
-   Vytvořit místní nabídky pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>. Další informace najdete v tématu [ContextMenu – přehled komponenty](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Vytvořit formulář se automaticky zadané standardní nabídku. Další informace najdete v tématu [návod: poskytnutí standardních položek nabídky do formuláře](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Poskytnout vaše <xref:System.Windows.Forms.ToolStrip> profesionální vzhled ovládací prvky. Další informace najdete v tématu [postupy: nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Postupy: Vytváření nadřazených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Postupy: Vytváření podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
