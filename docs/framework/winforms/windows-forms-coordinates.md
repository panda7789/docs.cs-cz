---
title: Koordinuje
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: c95888f31bfc867e9c028d53072ab3d710256708
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734662"
---
# <a name="windows-forms-coordinates"></a>Windows Forms – souřadnice
Systém souřadnic pro formulář Windows je založen na souřadnicích zařízení a na základní měrné jednotce při vykreslování v model Windows Forms jednotka zařízení (obvykle pixel). Body na obrazovce jsou popsány páry x a y – souřadnice x se zvyšují vpravo a souřadnice y se zvyšují od shora dolů. Umístění zdroje vzhledem k obrazovce se bude lišit v závislosti na tom, zda určujete souřadnice obrazovky nebo klienta.  
  
## <a name="screen-coordinates"></a>Souřadnice obrazovky  
 Model Windows Forms aplikace určuje polohu okna na obrazovce v souřadnicích obrazovky. V případě souřadnic obrazovky je počátek v levém horním rohu obrazovky. Úplná poloha okna je často popsána <xref:System.Drawing.Rectangle> strukturou, která obsahuje souřadnice obrazovky dvou bodů definujících levý a pravý dolní roh okna.  
  
## <a name="client-coordinates"></a>Souřadnice klienta  
 Model Windows Forms aplikace určuje pozici bodů ve formuláři nebo ovládacím prvku pomocí souřadnic klienta. Počátek souřadnic klienta je levý horní roh oblasti klienta ovládacího prvku nebo formuláře. Souřadnice klienta zajišťují, že aplikace může při vykreslování formuláře nebo ovládacího prvku používat konzistentní hodnoty souřadnic, a to bez ohledu na pozici formuláře nebo ovládacího prvku na obrazovce.  
  
 Rozměry klientské oblasti jsou také popsány <xref:System.Drawing.Rectangle> strukturou, která obsahuje souřadnice klienta pro oblast. Ve všech případech je levá horní souřadnice obdélníku zahrnuta v oblasti klienta, zatímco je vyloučena pravá souřadnice. Grafické operace neobsahují pravé a dolní okraje oblasti klienta. Například metoda <xref:System.Drawing.Graphics.FillRectangle%2A> zaplní do pravého a dolního okraje zadaného obdélníku, ale tyto okraje nebudou zahrnuty.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Mapování z jednoho typu souřadnice na jiný  
 V některých případech může být nutné mapovat souřadnice obrazovky na souřadnice klientů. K tomu lze snadno využít metody <xref:System.Windows.Forms.Control.PointToClient%2A> a <xref:System.Windows.Forms.Control.PointToScreen%2A> dostupné ve třídě <xref:System.Windows.Forms.Control>. Například vlastnost <xref:System.Windows.Forms.Control.MousePosition%2A> <xref:System.Windows.Forms.Control> je uvedena v souřadnicích obrazovky, ale pravděpodobně je budete chtít převést na souřadnice klienta.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
