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
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="08838-103">Postupy: Použití slovníku zdrojů rozsahu aplikace</span><span class="sxs-lookup"><span data-stu-id="08838-103">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="08838-104">Tento příklad ukazuje, jak definovat a používat vlastní slovník prostředků v rozsahu aplikace.</span><span class="sxs-lookup"><span data-stu-id="08838-104">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08838-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="08838-105">Example</span></span>  
 <span data-ttu-id="08838-106"><xref:System.Windows.Application>zpřístupňuje úložiště oboru aplikace pro sdílené prostředky: <xref:System.Windows.Application.Resources%2A> .</span><span class="sxs-lookup"><span data-stu-id="08838-106"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="08838-107">Ve výchozím nastavení <xref:System.Windows.Application.Resources%2A> je vlastnost inicializována s instancí <xref:System.Windows.ResourceDictionary> typu.</span><span class="sxs-lookup"><span data-stu-id="08838-107">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="08838-108">Tuto instanci použijete při získávání a nastavování vlastností rozsahu aplikace pomocí <xref:System.Windows.Application.Resources%2A> .</span><span class="sxs-lookup"><span data-stu-id="08838-108">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="08838-109">Další informace najdete v tématu [Postupy: získání a nastavení prostředku rozsahu aplikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="08838-109">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="08838-110">Pokud máte více prostředků, které jste nastavili pomocí nástroje <xref:System.Windows.Application.Resources%2A> , můžete místo toho použít vlastní slovník prostředků k uložení těchto prostředků a nastavit <xref:System.Windows.Application.Resources%2A> s ním.</span><span class="sxs-lookup"><span data-stu-id="08838-110">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="08838-111">Následující příklad ukazuje, jak deklarovat vlastní slovník prostředků pomocí jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="08838-111">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="08838-112">Výměna celých slovníků prostředků pomocí nástroje <xref:System.Windows.Application.Resources%2A> umožňuje podporu motivů rozsahu aplikace, kde je každý motiv zapouzdřený pomocí jediného slovníku prostředků.</span><span class="sxs-lookup"><span data-stu-id="08838-112">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="08838-113">Následující příklad ukazuje, jak nastavit <xref:System.Windows.ResourceDictionary> .</span><span class="sxs-lookup"><span data-stu-id="08838-113">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="08838-114">Následující příklad ukazuje, jak můžete získat prostředky aplikačního rozsahu ze slovníku prostředků zveřejněného <xref:System.Windows.Application.Resources%2A> v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="08838-114">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="08838-115">Následující příklad ukazuje, jak lze získat prostředky v kódu.</span><span class="sxs-lookup"><span data-stu-id="08838-115">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="08838-116">Existují dva důvody, které je třeba provést při použití <xref:System.Windows.Application.Resources%2A> .</span><span class="sxs-lookup"><span data-stu-id="08838-116">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="08838-117">Nejprve *klíč* slovníku je objekt, takže je nutné použít naprosto stejnou instanci objektu, pokud nastavení a získání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="08838-117">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="08838-118">(Upozorňujeme, že při použití řetězce se v klíči rozlišují velká a malá písmena.) Za druhé je *hodnota* slovníku objekt, takže při získávání hodnoty vlastnosti bude nutné převést hodnotu na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="08838-118">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08838-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08838-119">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="08838-120">Zdroje XAML</span><span class="sxs-lookup"><span data-stu-id="08838-120">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="08838-121">Slovníky sloučených prostředků</span><span class="sxs-lookup"><span data-stu-id="08838-121">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
