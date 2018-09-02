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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393195"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="f6c4e-102">Postupy: Použití slovníku zdrojů rozsahu aplikace</span><span class="sxs-lookup"><span data-stu-id="f6c4e-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="f6c4e-103">Tento příklad ukazuje, jak definovat a použití slovníku zdrojů rozsahu aplikace vlastní.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6c4e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6c4e-104">Example</span></span>  
 <span data-ttu-id="f6c4e-105"><xref:System.Windows.Application> vystavuje úložiště oboru aplikace za sdílené prostředky: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="f6c4e-106">Ve výchozím nastavení <xref:System.Windows.Application.Resources%2A> vlastnost je inicializována s instancí <xref:System.Windows.ResourceDictionary> typu.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="f6c4e-107">Použít tuto instanci při získání a nastavení vlastností pro rozsah aplikace pomocí <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="f6c4e-108">Další informace najdete v tématu [postupy: získání a nastavení prostředek oboru aplikace](https://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).</span><span class="sxs-lookup"><span data-stu-id="f6c4e-108">For more information, see [How to: Get and Set an Application-Scope Resource](https://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).</span></span>
  
 <span data-ttu-id="f6c4e-109">Pokud máte různé prostředky, které jste nastavili pomocí <xref:System.Windows.Application.Resources%2A>, místo toho můžete vlastní prostředek slovníku k ukládání těchto prostředků a nastavte <xref:System.Windows.Application.Resources%2A> s ním místo.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="f6c4e-110">Následuje ukázka, jak deklarovat pomocí XAML slovník vlastních prostředků.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="f6c4e-111">Vzájemná záměna slovníky prostředků pro celý pomocí <xref:System.Windows.Application.Resources%2A> umožňují podporovat oboru aplikace motivy, ve kterém je každý motiv zapouzdřena objektem slovník jeden prostředek.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="f6c4e-112">Následující příklad ukazuje, jak nastavit <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="f6c4e-113">Následující ukazuje, jak získat zdrojů rozsahu aplikace ze slovníku prostředků, které jsou vystavené <xref:System.Windows.Application.Resources%2A> v XAML.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="f6c4e-114">Následuje ukázka, jak můžete také získat prostředky v kódu.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="f6c4e-115">Existují dva aspekty při používání <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="f6c4e-116">První, slovníku *klíč* je objekt, takže je nutné použít přesně stejnou instanci objektu při i nastavení a získání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="f6c4e-117">(Všimněte si, že klíč je při použití řetězce malá a velká písmena.) Druhý, slovníku *hodnotu* je objekt, takže budete muset převést hodnotu na požadovaný typ. při získávání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f6c4e-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c4e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6c4e-118">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [<span data-ttu-id="f6c4e-119">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="f6c4e-119">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="f6c4e-120">Slovníky sloučených prostředků</span><span class="sxs-lookup"><span data-stu-id="f6c4e-120">Merged Resource Dictionaries</span></span>](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
