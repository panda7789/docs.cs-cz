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
ms.workload: dotnet
ms.openlocfilehash: 04dbcfb0fa16ceb4d6778ef611e926894d7840e9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="b9c39-102">Postupy: Použití slovníku zdrojů rozsahu aplikace</span><span class="sxs-lookup"><span data-stu-id="b9c39-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="b9c39-103">Tento příklad ukazuje, jak definovat a používat slovníku vlastní prostředek oboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9c39-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9c39-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9c39-104">Example</span></span>  
 <span data-ttu-id="b9c39-105"><xref:System.Windows.Application>zpřístupní úložišti oboru aplikace pro sdílené prostředky: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="b9c39-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="b9c39-106">Ve výchozím nastavení <xref:System.Windows.Application.Resources%2A> se vlastnost inicializuje instanci <xref:System.Windows.ResourceDictionary> typu.</span><span class="sxs-lookup"><span data-stu-id="b9c39-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="b9c39-107">Použít tuto instanci při získání a nastavení vlastností oboru aplikace pomocí <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="b9c39-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="b9c39-108">Další informace najdete v tématu [postupy: získání a nastavení prostředek oboru aplikace](http://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).</span><span class="sxs-lookup"><span data-stu-id="b9c39-108">For more information, see [How to: Get and Set an Application-Scope Resource](http://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).</span></span>
  
 <span data-ttu-id="b9c39-109">Pokud máte více prostředků, které můžete nastavit pomocí <xref:System.Windows.Application.Resources%2A>, místo toho můžete vlastní prostředek slovník pro ukládání tyto prostředky a nastavení <xref:System.Windows.Application.Resources%2A> s ním místo.</span><span class="sxs-lookup"><span data-stu-id="b9c39-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="b9c39-110">Následující příklad zobrazuje, jak deklarovat slovník vlastních prostředků s použitím jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="b9c39-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="b9c39-111">Vzájemná záměna slovnících celý prostředků pomocí <xref:System.Windows.Application.Resources%2A> umožňuje podporu motivy oboru aplikace, kde je každý motiv zapouzdřený slovníkem jediný zdroj.</span><span class="sxs-lookup"><span data-stu-id="b9c39-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="b9c39-112">Následující příklad ukazuje, jak nastavit <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="b9c39-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="b9c39-113">Následující ukazuje, jak můžete získat oboru aplikace prostředky ze slovníku prostředků vystavené <xref:System.Windows.Application.Resources%2A> v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="b9c39-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="b9c39-114">Následující ukazuje, jak můžete také získat prostředky v kódu.</span><span class="sxs-lookup"><span data-stu-id="b9c39-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="b9c39-115">Existují dvě informace týkající se při použití <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="b9c39-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="b9c39-116">První, slovníku *klíč* je objekt, takže je nutné použít přesně stejnou instanci objektu při nastavení i získání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b9c39-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="b9c39-117">(Všimněte si, že klíč je při použití řetězec malá a velká písmena.) Druhý, slovníku *hodnota* je objekt, takže budete muset převést hodnotu na požadovaný typ při získávání hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b9c39-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c39-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9c39-118">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [<span data-ttu-id="b9c39-119">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="b9c39-119">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="b9c39-120">Slovníky sloučených prostředků</span><span class="sxs-lookup"><span data-stu-id="b9c39-120">Merged Resource Dictionaries</span></span>](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
