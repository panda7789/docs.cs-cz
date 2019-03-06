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
# <a name="how-to-get-all-windows-in-an-application"></a>Postupy: Získat všechny Windows v aplikaci
Tento příklad ukazuje, jak získat všechny <xref:System.Windows.Window> objekty v aplikaci.  
  
## <a name="example"></a>Příklad  
 Každý vytvořena instance <xref:System.Windows.Window> objektu, zda je viditelný či nikoli, je automaticky přidán do kolekce odkazů na okno, které spravuje <xref:System.Windows.Application>a vystavené z <xref:System.Windows.Application.Windows%2A>.  
  
 Můžete zobrazit výčet <xref:System.Windows.Application.Windows%2A> zobrazíte všechny instance windows pomocí následujícího kódu:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
