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
ms.openlocfilehash: 081ce8d350995d5321acbb24d220bed229ff17ae
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801347"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Postupy: Použití slovníku zdrojů rozsahu aplikace
Tento příklad ukazuje, jak definovat a použití slovníku zdrojů rozsahu aplikace vlastní.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Application> vystavuje úložiště oboru aplikace za sdílené prostředky: <xref:System.Windows.Application.Resources%2A>. Ve výchozím nastavení <xref:System.Windows.Application.Resources%2A> vlastnost je inicializována s instancí <xref:System.Windows.ResourceDictionary> typu. Použít tuto instanci při získání a nastavení vlastností pro rozsah aplikace pomocí <xref:System.Windows.Application.Resources%2A>. Další informace najdete v tématu [postupy: získání a nastavení prostředek oboru aplikace](https://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).
  
 Pokud máte různé prostředky, které jste nastavili pomocí <xref:System.Windows.Application.Resources%2A>, místo toho můžete vlastní prostředek slovníku k ukládání těchto prostředků a nastavte <xref:System.Windows.Application.Resources%2A> s ním místo. Následuje ukázka, jak deklarovat pomocí XAML slovník vlastních prostředků.
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 Vzájemná záměna slovníky prostředků pro celý pomocí <xref:System.Windows.Application.Resources%2A> umožňují podporovat oboru aplikace motivy, ve kterém je každý motiv zapouzdřena objektem slovník jeden prostředek. Následující příklad ukazuje, jak nastavit <xref:System.Windows.ResourceDictionary>.  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 Následující ukazuje, jak získat zdrojů rozsahu aplikace ze slovníku prostředků, které jsou vystavené <xref:System.Windows.Application.Resources%2A> v XAML.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Následuje ukázka, jak můžete také získat prostředky v kódu.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Existují dva aspekty při používání <xref:System.Windows.Application.Resources%2A>. První, slovníku *klíč* je objekt, takže je nutné použít přesně stejnou instanci objektu při i nastavení a získání hodnoty vlastnosti. (Všimněte si, že klíč je při použití řetězce malá a velká písmena.) Druhý, slovníku *hodnotu* je objekt, takže budete muset převést hodnotu na požadovaný typ. při získávání hodnoty vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [Prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Slovníky sloučených prostředků](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
