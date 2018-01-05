---
title: "Grafika a kreslení v rozhraní Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ae9810b10a7357f7f8d00783335335a391a5211
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Grafika a kreslení v rozhraní Windows Forms
Pokročilé implementace rozhraní Windows grafiky zařízení používá modul common language runtime ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) názvem [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. S [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete vytvořit grafiky, kreslení textu a manipulaci s grafickým rozhraním obrázky jako objekty. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]je určená k poskytování výkonu a snadného použití. Můžete použít [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] k vykreslení grafické Image na Windows Forms a ovládacích prvků. I když nelze použít [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] přímo na webových formulářů, můžete zobrazit grafické obrázky prostřednictvím ovládacího prvku Obrázek webového serveru.  
  
 V této části najdete témata, která zavést Základy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programování. I když nemají být komplexní odkaz, tato část obsahuje informace o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, a <xref:System.Drawing.Color> objektů a vysvětluje, jak provádět úlohy, jako jsou kreslení tvarů, kreslení textu, nebo zobrazení obrázků. Další informace najdete v tématu [GDI + odkaz](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).  
  
 Pokud chcete v přeskočit a rovnou začít, najdete v článku [Začínáme s programováním grafiky](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md). Obsahuje témata týkající se používání kódu kreslení čar, tvarů, text a informace v rozhraní Windows forms.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled grafiky](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 Poskytuje úvod do související grafika spravované třídy.  
  
 [Informace o spravovaném kódu GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 Poskytuje informace o spravovaný [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy.  
  
 [Použití spravovaných grafických tříd](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 Ukazuje, jak dokončit různé úkoly pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] spravované třídy.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Drawing>  
 Poskytuje přístup k [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] základní grafické funkce.  
  
 <xref:System.Drawing.Drawing2D>  
 Poskytuje pokročilé dvourozměrná a vektorové grafiky funkce.  
  
 <xref:System.Drawing.Imaging>  
 Poskytuje pokročilé [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkce pro zpracování obrázků.  
  
 <xref:System.Drawing.Text>  
 Poskytuje pokročilé [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typografii funkce. Vytvoření a použití písem, lze použít třídy v tomto oboru názvů.  
  
 <xref:System.Drawing.Printing>  
 Poskytuje funkce, tisku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Malování a vykreslování vlastního ovládacího prvku](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 Podrobnosti, jak poskytnout kód pro vykreslování ovládacích prvků.
