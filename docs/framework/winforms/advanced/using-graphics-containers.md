---
title: Použití grafických kontejnerů
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
ms.openlocfilehash: cfad7254057a31ea8268784cd4b6849850f3e2aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766152"
---
# <a name="using-graphics-containers"></a>Použití grafických kontejnerů
A <xref:System.Drawing.Graphics> objekt, který poskytuje metody, jako <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, a <xref:System.Drawing.Graphics.DrawString%2A> pro zobrazení vektorové obrázky, rastrové obrázky a text. A <xref:System.Drawing.Graphics> objekt má také několik vlastností, které ovlivňují kvality a orientaci ovládacího prvku položek, které jsou zpracovány. Například vlastnost vyhlazování režimu určuje, zda použití vyhlazení u čar a křivek a vlastnost transformace světa ovlivňuje umístění a otočení položek, které jsou zpracovány.  
  
 A <xref:System.Drawing.Graphics> objekt je přidružený konkrétní zobrazovací zařízení. Při použití <xref:System.Drawing.Graphics> objekt nakreslete v okně <xref:System.Drawing.Graphics> objektu je taky přiřazený k této konkrétní okno.  
  
 A <xref:System.Drawing.Graphics> objektu můžete představit jako kontejner protože obsahuje sadu vlastností, které ovlivňují kreslení a je propojen informace specifické pro zařízení. Můžete vytvořit kontejner sekundární v existující <xref:System.Drawing.Graphics> objektu voláním <xref:System.Drawing.Graphics.BeginContainer%2A> metodu, která <xref:System.Drawing.Graphics> objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Správa stavu grafického objektu](managing-the-state-of-a-graphics-object.md)  
 Popisuje, jak spravovat nastavení kvality, výstřižek oblasti a transformace <xref:System.Drawing.Graphics> objektu.  
  
 [Použití vnořených grafických kontejnerů](using-nested-graphics-containers.md)  
 Ukazuje, jak používat kontejnery k řízení stavu <xref:System.Drawing.Graphics> objektu.
