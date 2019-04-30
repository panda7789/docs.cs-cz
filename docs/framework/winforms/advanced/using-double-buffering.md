---
title: Použití dvojitého ukládání do vyrovnávací paměti
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: ac6c9b7f2cc1fea86a75eaaf4a2dde1ea60e4f40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777153"
---
# <a name="using-double-buffering"></a>Použití dvojitého ukládání do vyrovnávací paměti
Grafiky s dvojitou vyrovnávací pamětí můžete použít k omezení blikání v aplikacích, které obsahují komplexní Malování operace. Rozhraní .NET Framework obsahuje integrovanou podporu dvojité ukládání do vyrovnávací paměti nebo můžete spravovat a ruční zobrazení grafiky.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Grafiky s dvojitou vyrovnávací pamětí](double-buffered-graphics.md)  
 Zavádí dvojité vyrovnávací paměti koncept a jsou podrobněji popsány dále podpora rozhraní .NET Framework.  
  
 [Postupy: Omezení blikání grafiky dvojité ukládání do vyrovnávací paměti pro formuláře a ovládací prvky](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 Ukazuje, jak použít výchozí dvojité ukládání do vyrovnávací paměti podpora v rozhraní .NET Framework.  
  
 [Postupy: Ruční správa grafiky uložené do vyrovnávací paměti](how-to-manually-manage-buffered-graphics.md)  
 Ukazuje, jak spravovat dvojité ukládání do vyrovnávací paměti v aplikacích.  
  
 [Postupy: Ruční zobrazení grafiky uložené do vyrovnávací paměti](how-to-manually-render-buffered-graphics.md)  
 Ukazuje, jak pro vykreslení grafiky s dvojitou vyrovnávací pamětí.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Control.SetStyle%2A> ,  
 Metoda ovládací prvek, který umožňuje dvojité ukládání do vyrovnávací paměti.  
  
 <xref:System.Drawing.BufferedGraphicsContext> ,  
 Poskytuje metody pro vytváření grafické vyrovnávací paměti.  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 Poskytuje přístup ke kontextu grafiky uložené do vyrovnávací paměti pro doménu aplikace.
