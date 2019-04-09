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
ms.openlocfilehash: 466edeee5f45ec72ef265ef4855049c7852641b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164967"
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a>Chování AutoSize v ovládacím prvku TableLayoutPanel
## <a name="distinct-autosize-behaviors"></a>Chování DISTINCT AutoSize  
 <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek podporuje automatické velikosti chování následujícími způsoby:  
  
-   Až <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti;  
  
-   Prostřednictvím <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnost <xref:System.Windows.Forms.TableLayoutPanel> styly sloupců a řádků ovládacího prvku.  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a>S vlastností AutoSize řádků a styly sloupců  
 Následující tabulka popisuje interakce mezi <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost a <xref:System.Windows.Forms.TableLayoutPanel> styly sloupců a řádků ovládacího prvku.  
  
|Nastavení AutoSize|Styl interakce|  
|----------------------|-----------------------|  
|`false`|<xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek pokračuje zleva doprava a přiděluje místo pro sloupce nebo řádku nebo v uvedeném pořadí.<br /><br /> 1.  Pokud <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> je nastavena na <xref:System.Windows.Forms.SizeType.Absolute>, určený v pixelech <xref:System.Windows.Forms.ColumnStyle.Width%2A> nebo <xref:System.Windows.Forms.RowStyle.Height%2A> je přidělen.<br />2.  Pokud <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> je nastavena na <xref:System.Windows.Forms.SizeType.AutoSize>, vrácený podřízeného ovládacího prvku v pixelech <xref:System.Windows.Forms.Control.GetPreferredSize%2A> je přidělena metoda.<br />3.  Po místo pro všechny <xref:System.Windows.Forms.SizeType.Absolute> a <xref:System.Windows.Forms.SizeType.AutoSize> sloupců nebo řádků je přidělen, všechny sloupce nebo řádky s <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> nastavena na <xref:System.Windows.Forms.SizeType.Percent> jsou používány k přidělení proporcionálně zbývající volné místo|  
|`true`|Podobně jako na předchozí interakci s výjimkou, která <xref:System.Windows.Forms.SizeType.Percent> sloupců nebo řádků získat aspekty automatické velikosti.<br /><br /> <xref:System.Windows.Forms.TableLayoutPanel> Rozšíří ovládací prvek sloupec nebo řádek, který má dostatek volného místa, vytvořit tak, aby žádný sloupec nebo řádek s <xref:System.Windows.Forms.SizeType.Percent> stylů klipy jeho obsah. <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek přiděluje nové místo proporcionálně souladu s <xref:System.Windows.Forms.ColumnStyle.Width%2A> nebo <xref:System.Windows.Forms.RowStyle.Height%2A> vlastnost.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TableLayoutPanel>
- [TableLayoutPanel – přehled ovládacího prvku](tablelayoutpanel-control-overview.md)
