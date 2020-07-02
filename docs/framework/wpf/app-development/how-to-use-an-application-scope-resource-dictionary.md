---
title: 'Postupy: Použití slovníku zdrojů rozsahu aplikace'
description: Naučte se definovat a používat vlastní slovník prostředků v oboru aplikace v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 9d117dea6c554339b4b462b9bf37b80da2dc477f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613706"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Postupy: Použití slovníku zdrojů rozsahu aplikace
Tento příklad ukazuje, jak definovat a používat vlastní slovník prostředků v rozsahu aplikace.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Application>zpřístupňuje úložiště oboru aplikace pro sdílené prostředky: <xref:System.Windows.Application.Resources%2A> . Ve výchozím nastavení <xref:System.Windows.Application.Resources%2A> je vlastnost inicializována s instancí <xref:System.Windows.ResourceDictionary> typu. Tuto instanci použijete při získávání a nastavování vlastností rozsahu aplikace pomocí <xref:System.Windows.Application.Resources%2A> . Další informace najdete v tématu [Postupy: získání a nastavení prostředku rozsahu aplikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).
  
 Pokud máte více prostředků, které jste nastavili pomocí nástroje <xref:System.Windows.Application.Resources%2A> , můžete místo toho použít vlastní slovník prostředků k uložení těchto prostředků a nastavit <xref:System.Windows.Application.Resources%2A> s ním. Následující příklad ukazuje, jak deklarovat vlastní slovník prostředků pomocí jazyka XAML.
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 Výměna celých slovníků prostředků pomocí nástroje <xref:System.Windows.Application.Resources%2A> umožňuje podporu motivů rozsahu aplikace, kde je každý motiv zapouzdřený pomocí jediného slovníku prostředků. Následující příklad ukazuje, jak nastavit <xref:System.Windows.ResourceDictionary> .  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 Následující příklad ukazuje, jak můžete získat prostředky aplikačního rozsahu ze slovníku prostředků zveřejněného <xref:System.Windows.Application.Resources%2A> v jazyce XAML.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Následující příklad ukazuje, jak lze získat prostředky v kódu.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Existují dva důvody, které je třeba provést při použití <xref:System.Windows.Application.Resources%2A> . Nejprve *klíč* slovníku je objekt, takže je nutné použít naprosto stejnou instanci objektu, pokud nastavení a získání hodnoty vlastnosti. (Upozorňujeme, že při použití řetězce se v klíči rozlišují velká a malá písmena.) Za druhé je *hodnota* slovníku objekt, takže při získávání hodnoty vlastnosti bude nutné převést hodnotu na požadovaný typ.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [Zdroje XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Slovníky sloučených prostředků](../advanced/merged-resource-dictionaries.md)
