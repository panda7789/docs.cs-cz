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
ms.openlocfilehash: d9c2dda2745e7528902b6b1c4f46d17264d1a8d8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666729"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a><span data-ttu-id="08a7e-102">Postupy: Zachování a obnovení vlastností v rozsahu aplikace mezi jednotlivými relacemi aplikace</span><span class="sxs-lookup"><span data-stu-id="08a7e-102">How to: Persist and Restore Application-Scope Properties Across Application Sessions</span></span>
<span data-ttu-id="08a7e-103">Tento příklad ukazuje, jak zachovat vlastnosti rozsahu aplikace při vypnutí aplikace a jak obnovit vlastnosti rozsahu aplikace při dalším spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="08a7e-103">This example shows how to persist application-scope properties when an application shuts down, and how to restore application-scope properties when an application is next launch.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08a7e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="08a7e-104">Example</span></span>  
 <span data-ttu-id="08a7e-105">Aplikace přechovává vlastnosti rozsahu aplikace a obnoví je z izolovaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="08a7e-105">The application persists application-scope properties to, and restores them from, isolated storage.</span></span> <span data-ttu-id="08a7e-106">Izolované úložiště je chráněná oblast úložiště, kterou můžou bezpečně používat aplikace bez oprávnění k přístupu k souborům.</span><span class="sxs-lookup"><span data-stu-id="08a7e-106">Isolated storage is a protected storage area that can safely be used by applications without file access permission.</span></span>  <span data-ttu-id="08a7e-107">Soubor *App. XAML* definuje `App_Startup` metodu jako obslužnou rutinu pro <xref:System.Windows.Application.Startup?displayProperty=nameWithType> událost a `App_Exit` metodu jako obslužnou rutinu <xref:System.Windows.Application.Exit?displayProperty=nameWithType> události, jak je znázorněno na zvýrazněných řádcích prvního příkladu.</span><span class="sxs-lookup"><span data-stu-id="08a7e-107">The *App.xaml* file defines the `App_Startup` method as the handler for the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event, and the `App_Exit` method as the handler for the  <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event, as shown in the highlighted lines of the first example.</span></span> <span data-ttu-id="08a7e-108">Druhý příklad ukazuje část souborů *App.XAML.cs* a *App. XAML. vb* , která zvýrazňuje `App_Startup` kód pro metodu, která obnoví vlastnosti rozsahu aplikace a `App_Exit` metodu, která uloží rozsah aplikace. vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="08a7e-108">The second example shows a portion of the *App.xaml.cs* and *App.xaml.vb* files that highlights the code for the `App_Startup` method, which restores application-scope properties, and the `App_Exit` method, which saves application-scope properties.</span></span>

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=14-45)]
