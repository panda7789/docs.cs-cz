---
title: Vývoj s použitím oboru názvů My
ms.date: 07/20/2015
f1_keywords:
- My.MyWpfExtension.Windows
helpviewer_keywords:
- My object
- My namespace
- My feature
- Visual Basic, programming in
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
ms.openlocfilehash: 3befac591de8fbc7250777a8b87247ee395abf25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411703"
---
# <a name="development-with-my-visual-basic"></a><span data-ttu-id="52838-102">Vývoj s použitím oboru názvů My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52838-102">Development with My (Visual Basic)</span></span>

<span data-ttu-id="52838-103">Visual Basic poskytuje nové funkce pro rychlý vývoj aplikací, které zvyšují produktivitu a usnadňují používání a zároveň dodávají sílu.</span><span class="sxs-lookup"><span data-stu-id="52838-103">Visual Basic provides new features for rapid application development that improve productivity and ease of use while delivering power.</span></span> <span data-ttu-id="52838-104">Jedna z těchto funkcí, která je volána `My` , poskytuje přístup k informacím a výchozím instancím objektů, které se vztahují k aplikaci a jejímu prostředí za běhu.</span><span class="sxs-lookup"><span data-stu-id="52838-104">One of these features, called `My`, provides access to information and default object instances that are related to the application and its run-time environment.</span></span> <span data-ttu-id="52838-105">Tyto informace jsou uspořádány ve formátu, který je zjistitelný prostřednictvím technologie IntelliSense a logicky vymezený podle použití.</span><span class="sxs-lookup"><span data-stu-id="52838-105">This information is organized in a format that is discoverable through IntelliSense and logically delineated according to use.</span></span>  
  
 <span data-ttu-id="52838-106">Členové nejvyšší úrovně `My` jsou vystaveni jako objekty.</span><span class="sxs-lookup"><span data-stu-id="52838-106">Top-level members of `My` are exposed as objects.</span></span> <span data-ttu-id="52838-107">Každý objekt se chová podobně jako obor názvů nebo třída se `Shared` členy a zpřístupňuje sadu souvisejících členů.</span><span class="sxs-lookup"><span data-stu-id="52838-107">Each object behaves similarly to a namespace or a class with `Shared` members, and it exposes a set of related members.</span></span>  
  
 <span data-ttu-id="52838-108">Tato tabulka zobrazuje objekty nejvyšší úrovně `My` a jejich vzájemný vztah.</span><span class="sxs-lookup"><span data-stu-id="52838-108">This table shows the top-level `My` objects and their relationship to each other.</span></span>  
  
 ![Diagram znázorňuje objektový model pro My.](./media/index/my-object-model-relationships.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="52838-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="52838-110">In This Section</span></span>  

 [<span data-ttu-id="52838-111">Provádění úloh s objekty My.Application, My.Computer a My.User</span><span class="sxs-lookup"><span data-stu-id="52838-111">Performing Tasks with My.Application, My.Computer, and My.User</span></span>](performing-tasks-with-my-application-my-computer-and-my-user.md)  
 <span data-ttu-id="52838-112">Popisuje tři centrální `My` objekty,, `My.Application` `My.Computer` a `My.User` , které poskytují přístup k informacím a funkcím.</span><span class="sxs-lookup"><span data-stu-id="52838-112">Describes the three central `My` objects, `My.Application`, `My.Computer`, and `My.User`, which provide access to information and functionality</span></span>  
  
 [<span data-ttu-id="52838-113">Výchozí instance objektů poskytované třídami My.Forms a My.WebServices</span><span class="sxs-lookup"><span data-stu-id="52838-113">Default Object Instances Provided by My.Forms and My.WebServices</span></span>](default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 <span data-ttu-id="52838-114">Popisuje `My.Forms` objekty a `My.WebServices` , které poskytují přístup k formulářům, zdrojům dat a webovým službám XML, které vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="52838-114">Describes the `My.Forms` and `My.WebServices` objects, which provide access to forms, data sources, and XML Web services used by your application.</span></span>  
  
 [<span data-ttu-id="52838-115">Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings</span><span class="sxs-lookup"><span data-stu-id="52838-115">Rapid Application Development with My.Resources and My.Settings</span></span>](rapid-application-development-with-my-resources-and-my-settings.md)  
 <span data-ttu-id="52838-116">Popisuje `My.Resources` objekty a `My.Settings` , které poskytují přístup k prostředkům a nastavením aplikace.</span><span class="sxs-lookup"><span data-stu-id="52838-116">Describes the `My.Resources` and `My.Settings` objects, which provide access to an application's resources and settings.</span></span>  
  
 [<span data-ttu-id="52838-117">Přehled aplikačního modelu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52838-117">Overview of the Visual Basic Application Model</span></span>](overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="52838-118">Popisuje model spuštění nebo vypnutí aplikace Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="52838-118">Describes the Visual Basic Application Startup/Shutdown model.</span></span>  
  
 [<span data-ttu-id="52838-119">Závislost oboru názvů My na typu projektu</span><span class="sxs-lookup"><span data-stu-id="52838-119">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)  
 <span data-ttu-id="52838-120">Poskytuje podrobnosti o tom, které `My` funkce jsou k dispozici v různých typech projektů.</span><span class="sxs-lookup"><span data-stu-id="52838-120">Gives details on which `My` features are available in different project types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52838-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="52838-121">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="52838-122">My.Forms – objekt</span><span class="sxs-lookup"><span data-stu-id="52838-122">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="52838-123">My.WebServices – objekt</span><span class="sxs-lookup"><span data-stu-id="52838-123">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="52838-124">Závislost oboru názvů My na typu projektu</span><span class="sxs-lookup"><span data-stu-id="52838-124">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
