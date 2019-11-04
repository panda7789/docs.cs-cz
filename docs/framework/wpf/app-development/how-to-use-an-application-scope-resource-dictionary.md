---
title: 'Postupy: Použití slovníku zdrojů rozsahu aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 5bfb3ed0304598a5acf4b7682bf4a4169c5153d1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459794"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Postupy: Použití slovníku zdrojů rozsahu aplikace
Tento příklad ukazuje, jak definovat a používat vlastní slovník prostředků v rozsahu aplikace.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Application> zpřístupňuje úložiště rozsahu aplikace pro sdílené prostředky: <xref:System.Windows.Application.Resources%2A>. Ve výchozím nastavení je vlastnost <xref:System.Windows.Application.Resources%2A> inicializována s instancí typu <xref:System.Windows.ResourceDictionary>. Tuto instanci použijete při získávání a nastavování vlastností rozsahu aplikace pomocí <xref:System.Windows.Application.Resources%2A>. Další informace najdete v tématu [Postupy: získání a nastavení prostředku rozsahu aplikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).
  
 Pokud máte více prostředků, které jste nastavili pomocí <xref:System.Windows.Application.Resources%2A>, můžete místo toho použít vlastní slovník prostředků k uložení těchto prostředků a nastavit <xref:System.Windows.Application.Resources%2A>. Následující příklad ukazuje, jak deklarovat vlastní slovník prostředků pomocí jazyka XAML.
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 Výměna celého slovníku prostředků pomocí <xref:System.Windows.Application.Resources%2A> umožňuje podporu motivů rozsahu aplikace, kde je každý motiv zapouzdřený pomocí jediného slovníku prostředků. Následující příklad ukazuje, jak nastavit <xref:System.Windows.ResourceDictionary>.  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 Následující příklad ukazuje, jak můžete získat prostředky aplikačního rozsahu ze slovníku prostředků, který je vystavený <xref:System.Windows.Application.Resources%2A> v jazyce XAML.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Následující příklad ukazuje, jak lze získat prostředky v kódu.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Při použití <xref:System.Windows.Application.Resources%2A>je třeba provést dva důvody. Nejprve *klíč* slovníku je objekt, takže je nutné použít naprosto stejnou instanci objektu, pokud nastavení a získání hodnoty vlastnosti. (Upozorňujeme, že při použití řetězce se v klíči rozlišují velká a malá písmena.) Za druhé je *hodnota* slovníku objekt, takže při získávání hodnoty vlastnosti bude nutné převést hodnotu na požadovaný typ.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [Prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Slovníky sloučených prostředků](../advanced/merged-resource-dictionaries.md)
