---
title: 'Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: a558f6d274f260fc91fd140e9dae2c740b1ae00d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537941"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms
Jak vytvořit formuláře a ovládací prvky pro aplikaci Windows Forms, existují řadu úkolů, které provedete opakovaně. Toto jsou některé běžně prováděné úlohy, které mohou být zobrazeny:  
  
-   Přidání nebo odebrání na kartě <xref:System.Windows.Forms.TabControl>.  
  
-   Ukotvení nadřazenému prvku.  
  
-   Změna orientace <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.  
  
 Pro rychlejší vývoj, nabízí mnoho ovládacích prvků inteligentních značek, které jsou kontextové nabídky, které vám umožní provádět běžné úkoly, jako v jednom gesto v době návrhu. Tyto úlohy se nazývají *technologie Smart příkazy*.  
  
 Inteligentní značky budou připojeny k instanci ovládacího prvku pro své životnosti v návrháři a jsou vždy k dispozici.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytvoření projektu modelu Windows Forms  
  
-   Pomocí inteligentních značek  
  
-   Povolení a zakázání inteligentní značky  
  
 Jakmile budete hotovi, budete mít představu o úloze, kterou tyto funkce důležité rozložení.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavte formulář.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte projekt aplikace pro systém Windows s názvem "SmartTagsExample". Podrobnosti najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Vybrat formuláře v **Návrhář formulářů Windows**.  
  
## <a name="using-smart-tags"></a>Pomocí inteligentních značek  
 Inteligentní značky jsou vždy k dispozici v době návrhu na ovládací prvky, které nabízejí je.  
  
#### <a name="to-use-smart-tags"></a>Použití inteligentních značek  
  
1.  Přetáhněte <xref:System.Windows.Forms.TabControl> z **sada nástrojů** do formuláře. Všimněte si glyfy čipové tag (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), zobrazí se na sebe z <xref:System.Windows.Forms.TabControl>.  
  
2.  Klikněte na tlačítko glyfy čipové tag. V místní nabídce, který se zobrazí vedle glyf, vyberte **přidat karta** položky. Zkontrolujte, že nová stránka karta je přidat do <xref:System.Windows.Forms.TabControl>.  
  
3.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> řídit z **sada nástrojů** do formuláře.  
  
4.  Klikněte na tlačítko glyfy čipové tag. V místní nabídce, který se zobrazí vedle glyf, vyberte **přidat sloupec** položky. Zkontrolujte, že nový sloupec přidán do <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
5.  Přetáhněte <xref:System.Windows.Forms.SplitContainer> řídit z **sada nástrojů** do formuláře.  
  
6.  Klikněte na tlačítko glyfy čipové tag. V místní nabídce, který se zobrazí vedle glyf, vyberte **vodorovný rozdělovač orientaci** položky. Všimněte <xref:System.Windows.Forms.SplitContainer> ovládacího prvku rozdělovač je nyní zaměřené na konkrétní vodorovně.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [Návod: Přidání inteligentních značek k součásti Windows Forms](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
