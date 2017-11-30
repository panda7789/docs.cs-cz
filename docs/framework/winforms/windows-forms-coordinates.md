---
title: "Windows Forms – souřadnice"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ecb47efdd69730350cf98e1c7b1e49150ad324d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-coordinates"></a>Windows Forms – souřadnice
Souřadnicový systém pro formuláře Windows je založený na zařízení souřadnice a základní měrná jednotka služby při kreslení v systému Windows Forms je jednotka zařízení (obvykle pixelů). Bodů na obrazovce jsou popsané podle dvojic souřadnice x a y s souřadnice x zvýšení souřadnice y zvýšení shora dolů a doprava. Umístění počátek, relativně k obrazovce, budou lišit v závislosti na tom, jestli jsou zadání souřadnice obrazovky nebo klienta.  
  
## <a name="screen-coordinates"></a>Souřadnice obrazovky  
 Aplikace Windows Forms určuje pozici okna na obrazovce souřadnice obrazovky. Souřadnice obrazovky pochází levého horního rohu obrazovky. Úplné pozici okno je často popsán <xref:System.Drawing.Rectangle> struktura obsahující souřadnice obrazovky dva body, které definují rozích levém horním a pravém dolním rohu okna.  
  
## <a name="client-coordinates"></a>Souřadnice klienta  
 Aplikace Windows Forms určuje pozici bodů ve formuláři nebo ovládacího prvku s použitím souřadnice klienta. Počátek souřadnice klienta je levém horním rohu klientské oblasti formuláře nebo ovládací prvek. Souřadnice klienta Ujistěte se, že aplikace můžete použít konzistentní souřadnic hodnoty při vykreslování ve formuláři nebo ovládací prvek, bez ohledu na pozici formuláře nebo ovládacího prvku na obrazovce.  
  
 Dimenze klientské oblasti jsou také popsány podle <xref:System.Drawing.Rectangle> struktura, která obsahuje souřadnice klienta pro oblast. Ve všech případech je souřadnice levého horního obdélníku součástí klientské oblasti, zatímco je vyloučen souřadnice pravého dolního. Grafické operace nezahrnují dolní a pravé hrany klientské oblasti. Například <xref:System.Drawing.Graphics.FillRectangle%2A> metoda bude zaplnit vpravo a dolní hrany zadaný obdélníku, ale nebude obsahovat tyto okraje.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Mapování z jednoho typu souřadnice  
 Potřebujete v některých případech mapování z souřadnice obrazovky na souřadnice klienta. Toho lze snadno dosáhnout pomocí <xref:System.Windows.Forms.Control.PointToClient%2A> a <xref:System.Windows.Forms.Control.PointToScreen%2A> metody, které jsou k dispozici v <xref:System.Windows.Forms.Control> třídy. Například <xref:System.Windows.Forms.Control.MousePosition%2A> vlastnost <xref:System.Windows.Forms.Control> je uvedený v souřadnice obrazovky, ale můžete chtít převést do souřadnice klienta.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
