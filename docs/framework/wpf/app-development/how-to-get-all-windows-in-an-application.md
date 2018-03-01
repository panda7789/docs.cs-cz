---
title: "Postupy: získání všech oken v aplikaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fdb1baad8b779b6ef0443a05e5f6575b552b1c19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-all-windows-in-an-application"></a><span data-ttu-id="00067-102">Postupy: získání všech oken v aplikaci</span><span class="sxs-lookup"><span data-stu-id="00067-102">How to: Get all Windows in an Application</span></span>
<span data-ttu-id="00067-103">Tento příklad ukazuje, jak získat všechny <xref:System.Windows.Window> objekty v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="00067-103">This example shows how to get all <xref:System.Windows.Window> objects in an application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00067-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="00067-104">Example</span></span>  
 <span data-ttu-id="00067-105">Každé instanci <xref:System.Windows.Window> objektu, zda je viditelná nebo Ne, se automaticky přidá do kolekce odkazů na okno, které spravuje <xref:System.Windows.Application>a zveřejněné z <xref:System.Windows.Application.Windows%2A>.</span><span class="sxs-lookup"><span data-stu-id="00067-105">Every instantiated <xref:System.Windows.Window> object, whether visible or not, is automatically added to a collection of window references that is managed by <xref:System.Windows.Application>, and exposed from <xref:System.Windows.Application.Windows%2A>.</span></span>  
  
 <span data-ttu-id="00067-106">Můžete vytvořit výčet <xref:System.Windows.Application.Windows%2A> získat všech instancí systému windows pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="00067-106">You can enumerate <xref:System.Windows.Application.Windows%2A> to get all instantiated windows using the following code:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
