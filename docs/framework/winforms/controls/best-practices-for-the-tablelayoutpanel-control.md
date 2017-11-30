---
title: "Doporučené postupy pro ovládací prvek TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 802cc501b695f6c5cfe990bf72a4d9d2af68ba2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>Doporučené postupy pro ovládací prvek TableLayoutPanel
<xref:System.Windows.Forms.TableLayoutPanel> Rozložení výkonné funkce, které byste měli pečlivě zvážit před použitím v aplikaci Windows Forms poskytuje ovládací prvek.  
  
## <a name="recommendations"></a>Doporučení  
 Následující doporučení vám pomůže používat <xref:System.Windows.Forms.TableLayoutPanel> řízení k jeho nejlepší výhodou.  
  
### <a name="targeted-use"></a>Cílové použití  
 Použití <xref:System.Windows.Forms.TableLayoutPanel> řízení opatrně. Byste neměli používat ve všech situacích, které vyžadují s možností změny velikosti rozložení. Následující seznam popisuje rozložení využívající většinu z použití <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku:  
  
-   Rozložení, ve kterých existuje více částí formuláře, které proporcionálně navzájem.  
  
-   Rozložení, které bude upravena nebo generována dynamicky za běhu, jako jsou formuláře položku dat, které mají uživatele přizpůsobitelné pole přidány nebo odečítat podle preferencí.  
  
-   Rozložení, které by měla zůstat na celkové pevné velikosti. Například můžete mít dialogu, který by měla zůstat menší než 800 × 600, ale budete potřebovat k podpoře lokalizovaných řetězců.  
  
 Následující seznam popisuje rozložení, které nejsou výrazně nijak přínosné pomocí <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku:  
  
-   Jednoduché formuláře pro zadávání dat s jedním sloupcem popisků a zadání textu oblastí jeden sloupec.  
  
-   Zobrazení formulářů s jedním velké oblasti, která by měl vyplnit veškeré dostupné místo v případě změny velikosti. Příkladem je formulář, který zobrazuje jeden <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku. V takovém případě použijte ukotvení, protože nic jiného by měl rozbalit, pokud se změnila velikost formuláře.  
  
 Pečlivě zvolte ovládacích prvků, které musí být v <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Pokud máte místo pro text růst o 30 % pomocí ukotvení, zvažte použití <xref:System.Windows.Forms.Control.Anchor%2A> pouze vlastnost. Pokud chcete-li odhadnout místo vyžadované vaší rozložení, použití <xref:System.Windows.Forms.Control.Dock%2A> a <xref:System.Windows.Forms.Control.Anchor%2A> je jednodušší než odhadnout podrobnosti zbývajícího místa a <xref:System.Windows.Forms.Control.AutoSize%2A> chování.  
  
 Obecně platí, že při navrhování vaší rozložení s <xref:System.Windows.Forms.TableLayoutPanel> řídit, zachovat návrh co nejjednodušší.  
  
### <a name="use-the-document-outline-window"></a>Použití Osnova dokumentu – okno  
 Okno Osnova dokumentu vám rozložení, který můžete použít k manipulaci s pořadí z-order a nadřazený podřízený vztahy pro vaše ovládací prvky zobrazení stromu. Z **nabídka Zobrazit**, vyberte **ostatní okna**, pak vyberte **Osnova dokumentu**.  
  
### <a name="avoid-nesting"></a>Vyhněte se vnoření  
 Vyhněte se vnoření jiných <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvky v rámci <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Ladění rozložení vnořené může být obtížné.  
  
### <a name="avoid-visual-inheritance"></a>Vyhněte se dědičnost vizuálních prvků  
 <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek nepodporuje dědičnost vizuálních prvků v Návrháři formulářů. A <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek v odvozené třídě se zobrazí jako "vyřazené" v době návrhu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
