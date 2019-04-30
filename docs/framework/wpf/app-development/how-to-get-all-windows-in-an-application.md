---
title: 'Postupy: Získání všech oken v aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 34316f0c6f81b960a8e00131a30b9a237b9ca938
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947768"
---
# <a name="how-to-get-all-windows-in-an-application"></a>Postupy: Získání všech oken v aplikaci
Tento příklad ukazuje, jak získat všechny <xref:System.Windows.Window> objekty v aplikaci.  
  
## <a name="example"></a>Příklad  
 Každý vytvořena instance <xref:System.Windows.Window> objektu, zda je viditelný či nikoli, je automaticky přidán do kolekce odkazů na okno, které spravuje <xref:System.Windows.Application>a vystavené z <xref:System.Windows.Application.Windows%2A>.  
  
 Můžete zobrazit výčet <xref:System.Windows.Application.Windows%2A> zobrazíte všechny instance windows pomocí následujícího kódu:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
