---
title: 'Postupy: Použití slovníku prostředků v rozsahu aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 589e28b3c05496e3fc17055b98240e389faed068
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125372"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="f134c-102">Postupy: Použití slovníku prostředků v rozsahu aplikace</span><span class="sxs-lookup"><span data-stu-id="f134c-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="f134c-103">Tento příklad ukazuje, jak definovat a použití slovníku zdrojů rozsahu aplikace vlastní.</span><span class="sxs-lookup"><span data-stu-id="f134c-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f134c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f134c-104">Example</span></span>  
 <xref:System.Windows.Application> <span data-ttu-id="f134c-105">vystavuje úložiště oboru aplikace za sdílené prostředky: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="f134c-105">exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="f134c-106">Ve výchozím nastavení <xref:System.Windows.Application.Resources%2A> vlastnost je inicializována s instancí <xref:System.Windows.ResourceDictionary> typu.</span><span class="sxs-lookup"><span data-stu-id="f134c-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="f134c-107">Použít tuto instanci při získání a nastavení vlastností pro rozsah aplikace pomocí <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="f134c-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="f134c-108">Další informace najdete v tématu [jak: Získání a nastavení prostředek oboru aplikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f134c-108">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="f134c-109">Pokud máte různé prostředky, které jste nastavili pomocí <xref:System.Windows.Application.Resources%2A>, místo toho můžete vlastní prostředek slovníku k ukládání těchto prostředků a nastavte <xref:System.Windows.Application.Resources%2A> s ním místo.</span><span class="sxs-lookup"><span data-stu-id="f134c-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="f134c-110">Následuje ukázka, jak deklarovat pomocí XAML slovník vlastních prostředků.</span><span class="sxs-lookup"><span data-stu-id="f134c-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="f134c-111">Vzájemná záměna slovníky prostředků pro celý pomocí <xref:System.Windows.Application.Resources%2A> umožňují podporovat oboru aplikace motivy, ve kterém je každý motiv zapouzdřena objektem slovník jeden prostředek.</span><span class="sxs-lookup"><span data-stu-id="f134c-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="f134c-112">Následující příklad ukazuje, jak nastavit <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="f134c-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="f134c-113">Následující ukazuje, jak získat zdrojů rozsahu aplikace ze slovníku prostředků, které jsou vystavené <xref:System.Windows.Application.Resources%2A> v XAML.</span><span class="sxs-lookup"><span data-stu-id="f134c-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="f134c-114">Následuje ukázka, jak můžete také získat prostředky v kódu.</span><span class="sxs-lookup"><span data-stu-id="f134c-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="f134c-115">Existují dva aspekty při používání <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="f134c-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="f134c-116">První, slovníku *klíč* je objekt, takže je nutné použít přesně stejnou instanci objektu při i nastavení a získání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f134c-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="f134c-117">(Všimněte si, že klíč je při použití řetězce malá a velká písmena.) Druhý, slovníku *hodnotu* je objekt, takže budete muset převést hodnotu na požadovaný typ. při získávání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f134c-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f134c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f134c-118">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="f134c-119">Zdroje XAML</span><span class="sxs-lookup"><span data-stu-id="f134c-119">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="f134c-120">Slovníky sloučených prostředků</span><span class="sxs-lookup"><span data-stu-id="f134c-120">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
