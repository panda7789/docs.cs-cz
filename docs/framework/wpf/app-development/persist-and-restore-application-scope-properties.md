---
title: 'Postupy: Zachování a obnovení vlastností v rozsahu aplikace mezi jednotlivými relacemi aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application-scope properties [WPF], persisting
- persisting application-scope properties [WPF]
- properties [WPF], persisting
- restoring application-scope properties [WPF]
- properties [WPF], restoring
- application-scope properties [WPF], restoring
ms.assetid: 55d5904a-f444-4eb5-abd3-6bc74dd14226
ms.openlocfilehash: c64b13717a427bf7ad8f9cab0a450162ad0c6cde
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204697"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>Postupy: Zachování a obnovení vlastností v rozsahu aplikace mezi jednotlivými relacemi aplikace
Tento příklad ukazuje, jak k uchování vlastností pro rozsah aplikace při ukončení aplikace a jak obnovit vlastnosti oboru aplikace, pokud se aplikace chystá spuštění.  
  
## <a name="example"></a>Příklad  
 Aplikace ukládá vlastnosti oboru aplikace k a obnoví z izolovaného úložiště. Izolované úložiště je chráněné úložiště, které mohou bezpečně využívat aplikace bez povolení přístupu k souboru.  *App.xaml* soubor definuje `App_Startup` metody jako obslužnou rutinu pro <xref:System.Windows.Application.Startup?displayProperty=nameWithType> události a `App_Exit` metody jako obslužnou rutinu pro <xref:System.Windows.Application.Exit?displayProperty=nameWithType> události, jak je znázorněno v zvýrazněné řádky v prvním příkladu. Druhý příklad ukazuje část *App.xaml.cs* a *App.xaml.vb* soubory, které zvýrazní kód `App_Startup` metodu, která obnoví vlastností pro rozsah aplikace a `App_Exit` metodu, která uloží vlastnosti oboru aplikace.
 
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
 
