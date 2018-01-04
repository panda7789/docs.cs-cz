---
title: "Přehled grafiky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3438fe2f1c3a6fc40efda0ff2583208f38bf7d5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-graphics"></a>Přehled grafiky
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]je programovací rozhraní aplikace (API), která tvoří subsystém operačního systému Microsoft Windows. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]zodpovídá za zobrazení informací na obrazovky a tiskárny. Jak naznačuje název [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je nástupcem [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], rozhraní grafických zařízení, která je zahrnutá v dřívějších verzích systému Windows.  
  
## <a name="managed-class-interface"></a>Spravované třídy rozhraní  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Rozhraní API je k dispozici prostřednictvím sadu tříd, které jsou nasazeny jako spravovaného kódu. Tato sada třídy se nazývá *spravované třídy rozhraní* k [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Následující obory názvů tvoří rozhraní spravované třídy:  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 Zařízení rozhraní grafiky jako například [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], bez nutnosti starat o podrobnosti o konkrétní zobrazení zařízení můžete zobrazit informace na obrazovce nebo tiskárny. Programátorů provádí volání do metody poskytované [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy. Tyto metody se pak volání příslušné konkrétní ovladače. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]insulates aplikace v grafickém hardwaru. Je tato izolace, která umožňuje programátory k vytvoření nezávislé na zařízení aplikací.  
  
## <a name="see-also"></a>Viz také  
 [Přehled grafiky](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
