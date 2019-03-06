---
title: 'Postupy: Získat všechny Windows v aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 34316f0c6f81b960a8e00131a30b9a237b9ca938
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378817"
---
# <a name="how-to-get-all-windows-in-an-application"></a><span data-ttu-id="828dd-102">Postupy: Získat všechny Windows v aplikaci</span><span class="sxs-lookup"><span data-stu-id="828dd-102">How to: Get all Windows in an Application</span></span>
<span data-ttu-id="828dd-103">Tento příklad ukazuje, jak získat všechny <xref:System.Windows.Window> objekty v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="828dd-103">This example shows how to get all <xref:System.Windows.Window> objects in an application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="828dd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="828dd-104">Example</span></span>  
 <span data-ttu-id="828dd-105">Každý vytvořena instance <xref:System.Windows.Window> objektu, zda je viditelný či nikoli, je automaticky přidán do kolekce odkazů na okno, které spravuje <xref:System.Windows.Application>a vystavené z <xref:System.Windows.Application.Windows%2A>.</span><span class="sxs-lookup"><span data-stu-id="828dd-105">Every instantiated <xref:System.Windows.Window> object, whether visible or not, is automatically added to a collection of window references that is managed by <xref:System.Windows.Application>, and exposed from <xref:System.Windows.Application.Windows%2A>.</span></span>  
  
 <span data-ttu-id="828dd-106">Můžete zobrazit výčet <xref:System.Windows.Application.Windows%2A> zobrazíte všechny instance windows pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="828dd-106">You can enumerate <xref:System.Windows.Application.Windows%2A> to get all instantiated windows using the following code:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
