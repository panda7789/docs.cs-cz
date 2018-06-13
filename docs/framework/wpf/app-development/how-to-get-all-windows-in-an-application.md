---
title: 'Postupy: získání všech oken v aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 476905899f5f7d573a16ba876c72f28ea34bbf9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545487"
---
# <a name="how-to-get-all-windows-in-an-application"></a>Postupy: získání všech oken v aplikaci
Tento příklad ukazuje, jak získat všechny <xref:System.Windows.Window> objekty v aplikaci.  
  
## <a name="example"></a>Příklad  
 Každé instanci <xref:System.Windows.Window> objektu, zda je viditelná nebo Ne, se automaticky přidá do kolekce odkazů na okno, které spravuje <xref:System.Windows.Application>a zveřejněné z <xref:System.Windows.Application.Windows%2A>.  
  
 Můžete vytvořit výčet <xref:System.Windows.Application.Windows%2A> získat všech instancí systému windows pomocí následujícího kódu:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
