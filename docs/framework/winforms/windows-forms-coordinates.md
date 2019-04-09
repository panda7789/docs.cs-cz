---
title: Windows Forms – souřadnice
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: 6feabadff17538f4a7368c348f7b72226e2d678e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116130"
---
# <a name="windows-forms-coordinates"></a>Windows Forms – souřadnice
Systém souřadnic pro formulář Windows je založen na souřadnice zařízení a základní jednotka měření při kreslení v modelu Windows Forms je jednotka zařízení (obvykle pixelů). Body na obrazovce jsou popsány pomocí dvojice souřadnice x a y, s souřadnice x zvýšení souřadnice y zvýšení shora dolů a doprava. Umístění zdroje, vzhledem k obrazovce, se bude lišit v závislosti na tom, zda jsou určení souřadnice obrazovky nebo klienta.  
  
## <a name="screen-coordinates"></a>Souřadnice obrazovky  
 Aplikace modelu Windows Forms určuje pozici okna na obrazovce v souřadnicovém systému obrazovky. Souřadnice obrazovky původ levého horního rohu obrazovky. Úplné pozice okna je často popsal <xref:System.Drawing.Rectangle> struktury obsahující souřadnice obrazovky dva body, které definují levém horním a pravém dolním rohu okna.  
  
## <a name="client-coordinates"></a>Souřadnice klienta  
 Aplikace modelu Windows Forms určuje pozici body formuláře nebo ovládacího prvku pomocí klienta souřadnic. Počátek souřadnic klienta je levém horním rohu klientské oblasti formuláře nebo ovládacího prvku. Souřadnice klienta Ujistěte se, že aplikace může používat konzistentní hodnoty souřadnic při kreslení v formulář nebo ovládací prvek, bez ohledu na umístění na formulář nebo ovládací prvek na obrazovce.  
  
 Dimenze v oblasti klienta jsou také popsány pomocí <xref:System.Drawing.Rectangle> strukturu, která obsahuje klientské souřadnice pro oblasti. Ve všech případech je souřadnice levého horního rohu obdélníku součástí klientské oblasti, zatímco vyloučené souřadnici pravého dolního rohu. Grafické operace nezahrnují okraje pravé a nižší klientské oblasti. Například <xref:System.Drawing.Graphics.FillRectangle%2A> metoda zaplní vpravo a nižší okraj zadané obdélník, ale nebude obsahovat tyto hrany.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Mapování z jednoho typu souřadnice  
 V některých případech budete muset mapování z obrazovky souřadnice na souřadnice klienta. Můžete to snadno provést pomocí <xref:System.Windows.Forms.Control.PointToClient%2A> a <xref:System.Windows.Forms.Control.PointToScreen%2A> metody, které jsou k dispozici v <xref:System.Windows.Forms.Control> třídy. Například <xref:System.Windows.Forms.Control.MousePosition%2A> vlastnost <xref:System.Windows.Forms.Control> se použije v hlášení v souřadnicovém systému obrazovky, ale můžete chtít převést na souřadnice klienta.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
