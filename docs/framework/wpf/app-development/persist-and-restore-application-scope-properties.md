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
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a><span data-ttu-id="b1c0b-102">Postupy: Zachování a obnovení vlastností v rozsahu aplikace mezi jednotlivými relacemi aplikace</span><span class="sxs-lookup"><span data-stu-id="b1c0b-102">How to: Persist and Restore Application-Scope Properties Across Application Sessions</span></span>
<span data-ttu-id="b1c0b-103">Tento příklad ukazuje, jak k uchování vlastností pro rozsah aplikace při ukončení aplikace a jak obnovit vlastnosti oboru aplikace, pokud se aplikace chystá spuštění.</span><span class="sxs-lookup"><span data-stu-id="b1c0b-103">This example shows how to persist application-scope properties when an application shuts down, and how to restore application-scope properties when an application is next launch.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1c0b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1c0b-104">Example</span></span>  
 <span data-ttu-id="b1c0b-105">Aplikace ukládá vlastnosti oboru aplikace k a obnoví z izolovaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="b1c0b-105">The application persists application-scope properties to, and restores them from, isolated storage.</span></span> <span data-ttu-id="b1c0b-106">Izolované úložiště je chráněné úložiště, které mohou bezpečně využívat aplikace bez povolení přístupu k souboru.</span><span class="sxs-lookup"><span data-stu-id="b1c0b-106">Isolated storage is a protected storage area that can safely be used by applications without file access permission.</span></span>  <span data-ttu-id="b1c0b-107">*App.xaml* soubor definuje `App_Startup` metody jako obslužnou rutinu pro <xref:System.Windows.Application.Startup?displayProperty=nameWithType> události a `App_Exit` metody jako obslužnou rutinu pro <xref:System.Windows.Application.Exit?displayProperty=nameWithType> události, jak je znázorněno v zvýrazněné řádky v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="b1c0b-107">The *App.xaml* file defines the `App_Startup` method as the handler for the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event, and the `App_Exit` method as the handler for the  <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event, as shown in the highlighted lines of the first example.</span></span> <span data-ttu-id="b1c0b-108">Druhý příklad ukazuje část *App.xaml.cs* a *App.xaml.vb* soubory, které zvýrazní kód `App_Startup` metodu, která obnoví vlastností pro rozsah aplikace a `App_Exit` metodu, která uloží vlastnosti oboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1c0b-108">The second example shows a portion of the *App.xaml.cs* and *App.xaml.vb* files that highlights the code for the `App_Startup` method, which restores application-scope properties, and the `App_Exit` method, which saves application-scope properties.</span></span>
 
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
 
