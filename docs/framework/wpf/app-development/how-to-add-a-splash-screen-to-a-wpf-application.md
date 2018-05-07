---
title: 'Postupy: Přidání úvodní obrazovky do aplikace WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 06d6cb7c5a5081d3b6c4979ab50e1caaa726acbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Postupy: Přidání úvodní obrazovky do aplikace WPF
Toto téma ukazuje, jak přidat okno spuštění nebo *úvodní obrazovka*, k aplikaci Windows Presentation Foundation (WPF).  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a>Chcete-li přidat bitovou kopii existující jako úvodní obrazovka  
  
1.  Vytvořit nebo najít bitovou kopii, kterou chcete použít pro úvodní obrazovka. Můžete použít všechny bitové kopie formátu, který je podporován ve vytváření bitové kopie součást WIC (Windows). Například můžete pomocí formátu BMP, GIF, JPEG, PNG nebo TIFF.  
  
2.  Přidání souboru bitové kopie do projektu aplikace WPF. Další informace najdete v tématu [NIB: postupy: Přidání existujících položek do projektu](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
3.  V Průzkumníku řešení vyberte bitovou kopii.  
  
4.  V okně vlastností klikněte na šipku rozevíracího seznamu pro **akce sestavení** vlastnost.  
  
5.  Vyberte **SplashScreen** z rozevíracího seznamu.  
  
    > [!NOTE]
    >  Pokud se nezobrazí **SplashScreen** možnost, zkontrolujte, že používáte [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 nebo novější.  
  
6.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
     Obrázek úvodní obrazovky se zobrazí v centru obrazovky a pak zmenšuje až se zobrazí okno hlavní aplikace.  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>Chcete-li odebrat úvodní obrazovka z aplikace  
  
1.  V Průzkumníku řešení vyberte obrázek úvodní obrazovky.  
  
2.  V okně vlastnosti nastavit **akce sestavení** k **žádné**.  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>Chcete-li odebrat úvodní obrazovka z aplikace  
  
-   V Průzkumníku řešení odstraňte obrázek úvodní obrazovky.  
  
-   Obrázek úvodní obrazovky vylučte z projektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.SplashScreen>  
 [NIB: postupy: Přidání existujících položek do projektu](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
