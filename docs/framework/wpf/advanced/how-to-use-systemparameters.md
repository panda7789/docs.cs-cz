---
title: "Postupy: Používání tipů SystemParameters"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4b2ee3956017e10da8adda52fa9a0ec31cb19ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-systemparameters"></a>Postupy: Používání tipů SystemParameters
Tento příklad ukazuje, jak k přístupu a použití vlastností <xref:System.Windows.SystemParameters> za účelem styl nebo na tlačítko Přizpůsobit.  
  
## <a name="example"></a>Příklad  
 Systémové prostředky vystavit několik nastavení systému, na základě prostředků, aby vám pomůže vytvořit vizuální prvky, které jsou konzistentní s nastavení systému. <xref:System.Windows.SystemParameters>je třída, která obsahuje vlastnosti hodnotu parametru systému a klíče prostředků, které vytvořit vazbu na hodnoty. Například <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> je <xref:System.Windows.SystemParameters> hodnotu vlastnosti a <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> je odpovídající klíč prostředku.  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít členy <xref:System.Windows.SystemParameters> jako použití statickou vlastnost nebo dynamické prostředků odkazy (s hodnotou statickou vlastnost jako klíč). Pokud má hodnotu systém založený na Aktualizovat automaticky při aplikaci použít odkaz na dynamické prostředků spouští; Jinak použijte statický odkaz. Prostředek klíče měly přípona `Key` připojeným k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak k přístupu a použití statické hodnoty <xref:System.Windows.SystemParameters> styl nebo na tlačítko Upravit. Tento příklad kódu velikostí tlačítka s použitím <xref:System.Windows.SystemParameters> hodnoty pro tlačítko.  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 Chcete-li použít hodnoty <xref:System.Windows.SystemParameters> v kódu nemáte použít buď odkazy statické nebo dynamické prostředků. Místo toho použijte hodnoty <xref:System.Windows.SystemParameters> třídy. I když neklíčovými vlastnostmi zjevně jsou definovány jako statické vlastnosti, modul runtime chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostované v systému bude přehodnocovat vlastnosti v reálném čase, a bude správně řízené uživatele změny hodnot systémového účtu. Následující příklad ukazuje, jak nastavit šířku a výšku tlačítka s pomocí <xref:System.Windows.SystemParameters> hodnoty.  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.SystemParameters>  
 [Malovat oblast štětcem systému](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Použití SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [Používejte klíče parametry systému](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [Postupy: témata](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
