---
title: Chování AutoSize v ovládacím prvku TableLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
ms.openlocfilehash: 497991106d151cfe1f3944977828e9c77c27e526
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526305"
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a>Chování AutoSize v ovládacím prvku TableLayoutPanel
## <a name="distinct-autosize-behaviors"></a>Chování odlišné AutoSize  
 <xref:System.Windows.Forms.TableLayoutPanel> Řízení podporuje chování Automatická změna velikosti následujícími způsoby:  
  
-   Prostřednictvím <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost;  
  
-   Prostřednictvím <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnost <xref:System.Windows.Forms.TableLayoutPanel> styly ovládacího prvku řádků a sloupců.  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a>S vlastností AutoSize s řádků a sloupců styly  
 Následující tabulka popisuje interakce mezi <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost a <xref:System.Windows.Forms.TableLayoutPanel> styly ovládacího prvku řádků a sloupců.  
  
|Nastavení AutoSize|Styl interakce|  
|----------------------|-----------------------|  
|`false`|<xref:System.Windows.Forms.TableLayoutPanel> Řízení pokračuje zleva doprava a přiděluje místo na sloupec nebo řádek nebo v uvedeném pořadí.<br /><br /> 1.  Pokud <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> je nastavena na <xref:System.Windows.Forms.SizeType.Absolute>, počet pixelů určeného <xref:System.Windows.Forms.ColumnStyle.Width%2A> nebo <xref:System.Windows.Forms.RowStyle.Height%2A> je přidělen.<br />2.  Pokud <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> je nastavena na <xref:System.Windows.Forms.SizeType.AutoSize>, vrácený podřízeného ovládacího prvku v pixelech <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metoda je přidělen.<br />3.  Po místa pro všechny <xref:System.Windows.Forms.SizeType.Absolute> a <xref:System.Windows.Forms.SizeType.AutoSize> sloupců a řádků je přidělen, všechny sloupce nebo řádky s <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> nastavena na <xref:System.Windows.Forms.SizeType.Percent> jsou používány k přidělení úměrně zbývající volné místo|  
|`true`|Podobně jako předchozí interakci s tou výjimkou, který <xref:System.Windows.Forms.SizeType.Percent> sloupců a řádků získat aspekt Automatická změna velikosti.<br /><br /> <xref:System.Windows.Forms.TableLayoutPanel> Řízení rozšíří sloupce nebo řádku k vytvoření dostatkem volného místa, tak, aby žádný sloupec nebo řádek s <xref:System.Windows.Forms.SizeType.Percent> stylů klipy její obsah. <xref:System.Windows.Forms.TableLayoutPanel> Řízení přiděluje nový prostor úměrně souladu se <xref:System.Windows.Forms.ColumnStyle.Width%2A> nebo <xref:System.Windows.Forms.RowStyle.Height%2A> vlastnost.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Přehled ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
