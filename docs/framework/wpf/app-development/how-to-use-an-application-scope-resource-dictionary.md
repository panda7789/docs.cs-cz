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
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="e4e71-102">Postupy: Použití slovníku zdrojů rozsahu aplikace</span><span class="sxs-lookup"><span data-stu-id="e4e71-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="e4e71-103">Tento příklad ukazuje, jak definovat a používat vlastní slovník prostředků v rozsahu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e4e71-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4e71-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4e71-104">Example</span></span>  
 <span data-ttu-id="e4e71-105"><xref:System.Windows.Application> zpřístupňuje úložiště rozsahu aplikace pro sdílené prostředky: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4e71-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="e4e71-106">Ve výchozím nastavení je vlastnost <xref:System.Windows.Application.Resources%2A> inicializována s instancí typu <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="e4e71-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="e4e71-107">Tuto instanci použijete při získávání a nastavování vlastností rozsahu aplikace pomocí <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4e71-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="e4e71-108">Další informace najdete v tématu [Postupy: získání a nastavení prostředku rozsahu aplikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e4e71-108">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="e4e71-109">Pokud máte více prostředků, které jste nastavili pomocí <xref:System.Windows.Application.Resources%2A>, můžete místo toho použít vlastní slovník prostředků k uložení těchto prostředků a nastavit <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4e71-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="e4e71-110">Následující příklad ukazuje, jak deklarovat vlastní slovník prostředků pomocí jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="e4e71-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="e4e71-111">Výměna celého slovníku prostředků pomocí <xref:System.Windows.Application.Resources%2A> umožňuje podporu motivů rozsahu aplikace, kde je každý motiv zapouzdřený pomocí jediného slovníku prostředků.</span><span class="sxs-lookup"><span data-stu-id="e4e71-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="e4e71-112">Následující příklad ukazuje, jak nastavit <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="e4e71-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="e4e71-113">Následující příklad ukazuje, jak můžete získat prostředky aplikačního rozsahu ze slovníku prostředků, který je vystavený <xref:System.Windows.Application.Resources%2A> v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="e4e71-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="e4e71-114">Následující příklad ukazuje, jak lze získat prostředky v kódu.</span><span class="sxs-lookup"><span data-stu-id="e4e71-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="e4e71-115">Při použití <xref:System.Windows.Application.Resources%2A>je třeba provést dva důvody.</span><span class="sxs-lookup"><span data-stu-id="e4e71-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="e4e71-116">Nejprve *klíč* slovníku je objekt, takže je nutné použít naprosto stejnou instanci objektu, pokud nastavení a získání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e4e71-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="e4e71-117">(Upozorňujeme, že při použití řetězce se v klíči rozlišují velká a malá písmena.) Za druhé je *hodnota* slovníku objekt, takže při získávání hodnoty vlastnosti bude nutné převést hodnotu na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="e4e71-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e71-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4e71-118">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="e4e71-119">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="e4e71-119">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="e4e71-120">Slovníky sloučených prostředků</span><span class="sxs-lookup"><span data-stu-id="e4e71-120">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
