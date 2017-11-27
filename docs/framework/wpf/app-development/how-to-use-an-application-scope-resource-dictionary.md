---
title: "Postupy: Použití slovníku zdrojů rozsahu aplikace"
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
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 417fea4dcbb5a8d0a27f9605be19de5921aaf0ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Postupy: Použití slovníku zdrojů rozsahu aplikace
Tento příklad ukazuje, jak definovat a používat slovníku vlastní prostředek oboru aplikace.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Application>zpřístupní úložišti oboru aplikace pro sdílené prostředky: <xref:System.Windows.Application.Resources%2A>. Ve výchozím nastavení <xref:System.Windows.Application.Resources%2A> se vlastnost inicializuje instanci <xref:System.Windows.ResourceDictionary> typu. Použít tuto instanci při získání a nastavení vlastností oboru aplikace pomocí <xref:System.Windows.Application.Resources%2A>. Další informace najdete v tématu [postupy: získání a nastavení prostředek oboru aplikace](http://msdn.microsoft.com/en-us/39e0420c-c9fc-47dc-8956-fdd95b214095).
  
 Pokud máte více prostředků, které můžete nastavit pomocí <xref:System.Windows.Application.Resources%2A>, místo toho můžete vlastní prostředek slovník pro ukládání tyto prostředky a nastavení <xref:System.Windows.Application.Resources%2A> s ním místo. Následující příklad zobrazuje, jak deklarovat slovník vlastních prostředků s použitím jazyka XAML.
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 Vzájemná záměna slovnících celý prostředků pomocí <xref:System.Windows.Application.Resources%2A> umožňuje podporu motivy oboru aplikace, kde je každý motiv zapouzdřený slovníkem jediný zdroj. Následující příklad ukazuje, jak nastavit <xref:System.Windows.ResourceDictionary>.  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 Následující ukazuje, jak můžete získat oboru aplikace prostředky ze slovníku prostředků vystavené <xref:System.Windows.Application.Resources%2A> v jazyce XAML.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Následující ukazuje, jak můžete také získat prostředky v kódu.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Existují dvě informace týkající se při použití <xref:System.Windows.Application.Resources%2A>. První, slovníku *klíč* je objekt, takže je nutné použít přesně stejnou instanci objektu při nastavení i získání hodnoty vlastnosti. (Všimněte si, že klíč je při použití řetězec malá a velká písmena.) Druhý, slovníku *hodnota* je objekt, takže budete muset převést hodnotu na požadovaný typ při získávání hodnotu vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [Prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Slovnících sloučené prostředků](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
