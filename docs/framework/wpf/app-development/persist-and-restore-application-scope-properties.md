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
ms.openlocfilehash: 2ba3a31d1fe8efde436fd76f88ccfab2853df5ee
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377134"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a><span data-ttu-id="eb4e1-102">Postupy: Zachování a obnovení vlastností v rozsahu aplikace mezi jednotlivými relacemi aplikace</span><span class="sxs-lookup"><span data-stu-id="eb4e1-102">How to: Persist and Restore Application-Scope Properties Across Application Sessions</span></span>
<span data-ttu-id="eb4e1-103">Tento příklad ukazuje, jak k uchování vlastností pro rozsah aplikace při ukončení aplikace a jak obnovit vlastnosti oboru aplikace, pokud se aplikace chystá spuštění.</span><span class="sxs-lookup"><span data-stu-id="eb4e1-103">This example shows how to persist application-scope properties when an application shuts down, and how to restore application-scope properties when an application is next launch.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb4e1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb4e1-104">Example</span></span>  
 <span data-ttu-id="eb4e1-105">Aplikace ukládá vlastnosti oboru aplikace k a obnoví z izolovaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="eb4e1-105">The application persists application-scope properties to, and restores them from, isolated storage.</span></span> <span data-ttu-id="eb4e1-106">Izolované úložiště je chráněné úložiště, které mohou bezpečně využívat aplikace bez povolení přístupu k souboru.</span><span class="sxs-lookup"><span data-stu-id="eb4e1-106">Isolated storage is a protected storage area that can safely be used by applications without file access permission.</span></span>  <span data-ttu-id="eb4e1-107">*App.xaml* soubor definuje `App_Startup` metody jako obslužnou rutinu pro <xref:System.Windows.Application.Startup?displayProperty=nameWithType> události a `App_Exit` metody jako obslužnou rutinu pro <xref:System.Windows.Application.Exit?displayProperty=nameWithType> události, jak je znázorněno v zvýrazněné řádky v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="eb4e1-107">The *App.xaml* file defines the `App_Startup` method as the handler for the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event, and the `App_Exit` method as the handler for the  <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event, as shown in the highlighted lines of the first example.</span></span> <span data-ttu-id="eb4e1-108">Druhý příklad ukazuje část *App.xaml.cs* a *App.xaml.vb* soubory, které zvýrazní kód `App_Startup` metodu, která obnoví vlastností pro rozsah aplikace a `App_Exit` metodu, která uloží vlastnosti oboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb4e1-108">The second example shows a portion of the *App.xaml.cs* and *App.xaml.vb* files that highlights the code for the `App_Startup` method, which restores application-scope properties, and the `App_Exit` method, which saves application-scope properties.</span></span>
 
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
 
