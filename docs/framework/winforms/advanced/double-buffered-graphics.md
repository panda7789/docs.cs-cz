---
title: "Grafiky s dvojitou vyrovnávací pamětí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89413e0958366dd39c62bfaedb7e36471123bc22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="double-buffered-graphics"></a>Grafiky s dvojitou vyrovnávací pamětí
Blikání problém je běžný, při programování grafiky. Grafické operace, které vyžadují více operací komplexní Malování může způsobit vykreslené obrázky, které chcete blikat nebo mají v opačném případě nemůže být přijata vzhled. Chcete-li tyto problémy vyřešit, rozhraní .NET Framework poskytuje přístup k dvojité ukládání do vyrovnávací paměti.  
  
 Chcete-li vyřešit blikání problémy spojené s více operací Malování dvojité ukládání do vyrovnávací paměti používá vyrovnávací paměti. Pokud dvojité ukládání do vyrovnávací paměti je povoleno, všechny operace Malování vykresleny nejprve do vyrovnávací paměti místo kreslicí plochy na obrazovce. Po dokončení všech operací Malování vyrovnávací paměť je zkopírovat přímo do kreslicí plochy s ním spojená. Vzhledem k tomu, že pouze jeden grafické operace na obrazovce, blikání bitové kopie přidružený komplexní vykreslovací operace odstranění.  
  
## <a name="default-double-buffering"></a>Výchozí dvojité ukládání do vyrovnávací paměti  
 Nejjednodušší způsob, jak pomocí dvojité vyrovnávací paměti v aplikacích se má použít výchozí dvojité ukládání do vyrovnávací paměti pro formuláře a ovládací prvky, které poskytuje rozhraní .NET Framework. Můžete povolit výchozí dvojité ukládání do vyrovnávací paměti pro Windows Forms a vytvořené ovládací prvky Windows nastavením <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost, která má `true` nebo pomocí <xref:System.Windows.Forms.Control.SetStyle%2A> metoda. Další informace najdete v tématu [postupy: omezení blikání grafiky pomocí dvojité vyrovnávací paměti pro formuláře a ovládací prvky](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md).  
  
## <a name="manually-managing-buffered-graphics"></a>Ruční správa grafiky uložené do vyrovnávací  
 Pro pokročilejší dvojité vyrovnávací paměti scénáře, jako je například animace nebo Správa rozšířené paměti můžete tříd rozhraní .NET Framework pro implementaci vlastní logiky dvojité ukládání do vyrovnávací paměti. Je třída, která přidělování a správa vyrovnávací paměti jednotlivých grafiky <xref:System.Drawing.BufferedGraphicsContext> třídy. Všechny aplikace domény má svou vlastní výchozí <xref:System.Drawing.BufferedGraphicsContext> instance, která spravuje všechny výchozí dvojité ukládání do vyrovnávací paměti pro tuto aplikaci. Ve většině případů budou existovat jenom jednu doménu aplikace na aplikaci, takže je obecně jeden výchozí <xref:System.Drawing.BufferedGraphicsContext> na aplikaci. Výchozí <xref:System.Drawing.BufferedGraphicsContext> instance jsou spravovány <xref:System.Drawing.BufferedGraphicsManager> třídy. Můžete načíst odkaz na výchozí <xref:System.Drawing.BufferedGraphicsContext> instance voláním <xref:System.Drawing.BufferedGraphicsManager.Current%2A>. Můžete také vytvořit vyhrazená <xref:System.Drawing.BufferedGraphicsContext> instance, což může zlepšit výkon pro graficky náročné aplikace. Informace o tom, jak vytvořit <xref:System.Drawing.BufferedGraphicsContext> instance najdete v tématu [postupy: ruční správa grafiky uložená do vyrovnávací paměti](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
## <a name="manually-displaying-buffered-graphics"></a>Ruční zobrazení grafiky uložené do vyrovnávací  
 Můžete použít instanci <xref:System.Drawing.BufferedGraphicsContext> třídy za účelem vytvoření grafiky vyrovnávací paměti při volání <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>, které vrací instanci třídy <xref:System.Drawing.BufferedGraphics> třídy. A <xref:System.Drawing.BufferedGraphics> objekt spravuje vyrovnávací paměti, který je přidružený prostor pro vykreslování, jako jsou formuláře nebo ovládacího prvku.  
  
 Po vytvoření instance, <xref:System.Drawing.BufferedGraphics> třída spravuje vykreslování do vyrovnávací paměti grafiky v paměti. Může vykreslit grafiky do vyrovnávací paměti pomocí <xref:System.Drawing.BufferedGraphics.Graphics%2A>, která zpřístupňuje <xref:System.Drawing.Graphics> objekt, který reprezentuje přímo vyrovnávací paměti. Můžete k tomuto malovat <xref:System.Drawing.Graphics> objektu stejně, jako byste to <xref:System.Drawing.Graphics> objekt, který reprezentuje kreslicí plochy. Po grafika byly do vyrovnávací paměti, můžete použít <xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType> zkopírovat obsah vyrovnávací paměti do kreslicí plochy na obrazovce.  
  
 Další informace o používání <xref:System.Drawing.BufferedGraphics> třídy najdete v tématu [ručně vykreslování grafiky uložená do vyrovnávací paměti](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md). Další informace o vykreslování grafiky najdete v tématu [grafika a kreslení v systému Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.BufferedGraphics>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphicsManager>  
 [Postupy: ruční zobrazení grafiky uložené do vyrovnávací](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 [Postupy: omezení blikání grafiky pomocí dvojité vyrovnávací paměti pro formuláře a ovládací prvky](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 [Postupy: ruční správa grafiky uložené do vyrovnávací](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 [Grafika a kreslení v systému Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
