---
title: Doporučené postupy pro ovládací prvek TableLayoutPanel
ms.date: 03/30/2017
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
ms.openlocfilehash: 57abf3527af146f1ce918bcabbc6a5a34bfb9b34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011725"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>Doporučené postupy pro ovládací prvek TableLayoutPanel
<xref:System.Windows.Forms.TableLayoutPanel> Ovládacího prvku poskytuje výkonné rozložení funkce, které byste měli pečlivě zvážit před použitím ve formulářích Windows.  
  
## <a name="recommendations"></a>Doporučení  
 Následující doporučení vám pomůže s použitím <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek na jeho přinášelo maximální výhody.  
  
### <a name="targeted-use"></a>Cílové použití  
 Použití <xref:System.Windows.Forms.TableLayoutPanel> řídit opatrně. Nepoužívejte ho ve všech situacích, které vyžadují umožňující změnu velikosti rozložení. Následující seznam popisuje rozložení, která je nejužitečnější u použití <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku:  
  
- Rozložení, ve kterém se více částí formuláře, které proporcionálně k sobě navzájem.  
  
- Rozložení, které budou změněny nebo dynamicky generované v době běhu, jako je například formulářích pro zadávání dat, které mají uživatelsky přizpůsobitelnými pole přičíst nebo odečíst podle preferencí.  
  
- Rozložení, které by měla zůstat na celkové pevné velikosti. Například můžete mít dialogové okno, které by měla zůstat menší než 800 × 600, ale budete potřebovat k podpoře lokalizovaných řetězců.  
  
 Následující seznam popisuje rozložení, které nejsou nijak přínosné výrazně pomocí <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku:  
  
- Jednoduchá datová položka formy s jedním sloupcem popisky a jedním sloupcem textového vstupu oblastí.  
  
- Formuláře pomocí jediného velké zobrazit oblast, která by měla zaplnit veškeré dostupné místo, když dojde k Změna velikosti. Příkladem je formulář, který se zobrazí jedna <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku. V takovém případě použijte ukotvení, protože nic jiného by měli rozbalit při změně velikosti formuláře.  
  
 Pečlivě zvolit, jaké ovládací prvky musí být v <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Pokud máte místo pro text zvětší o 30 % pomocí ukotvení, zvažte použití <xref:System.Windows.Forms.Control.Anchor%2A> pouze vlastnost. Pokud chcete-li odhadnout místo vyžadované rozložení, použijte <xref:System.Windows.Forms.Control.Dock%2A> a <xref:System.Windows.Forms.Control.Anchor%2A> je snazší než odhad podrobnosti zbývajícího místa a <xref:System.Windows.Forms.Control.AutoSize%2A> chování.  
  
 Obecně platí, že při návrhu rozložení s <xref:System.Windows.Forms.TableLayoutPanel> řídit, zachovat návrhu co nejjednodušší.  
  
### <a name="use-the-document-outline-window"></a>Použijte okno osnovy dokumentu  
 Osnova dokumentu – okno nabízí stromového zobrazení rozložení, který můžete použít k manipulaci s pořadí vykreslování a hierarchické vztahy své ovládací prvky. Z **nabídka zobrazení**vyberte **ostatní Windows**a pak vyberte **Osnova dokumentu**.  
  
### <a name="avoid-nesting"></a>Avoid Nesting  
 Vyhnout se vnoření jiných <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvky v rámci <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Ladění rozložení vnořeného může být obtížné.  
  
### <a name="avoid-visual-inheritance"></a>Vyhněte se vizuálního dědění  
 <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek nepodporuje vizuálního dědění v Návrháři formulářů Windows. A <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek v odvozené třídě se zobrazí jako "uzamčená" v době návrhu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
