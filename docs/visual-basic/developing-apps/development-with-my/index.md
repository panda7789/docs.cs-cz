---
title: Vývoj s použitím oboru názvů My (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWpfExtension.Windows
helpviewer_keywords:
- My object
- My namespace
- My feature
- Visual Basic, programming in
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
ms.openlocfilehash: 1d9dc1cd26b4bf110526fe6d136e943be730a443
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014168"
---
# <a name="development-with-my-visual-basic"></a><span data-ttu-id="6d038-102">Vývoj s použitím oboru názvů My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d038-102">Development with My (Visual Basic)</span></span>
<span data-ttu-id="6d038-103">Visual Basic poskytuje nové funkce pro rychlý vývoj aplikací, které přináší vyšší produktivitu a snadnost použití při současném dodávání napájení.</span><span class="sxs-lookup"><span data-stu-id="6d038-103">Visual Basic provides new features for rapid application development that improve productivity and ease of use while delivering power.</span></span> <span data-ttu-id="6d038-104">Jedna z těchto funkcí, volá `My`, poskytuje přístup k informacím a výchozí instance objektů, které se vztahují k aplikaci a její prostředí za běhu.</span><span class="sxs-lookup"><span data-stu-id="6d038-104">One of these features, called `My`, provides access to information and default object instances that are related to the application and its run-time environment.</span></span> <span data-ttu-id="6d038-105">Tyto informace je organizována do formátu, který je zjistitelný prostřednictvím technologie IntelliSense a logicky vymezen podle použití.</span><span class="sxs-lookup"><span data-stu-id="6d038-105">This information is organized in a format that is discoverable through IntelliSense and logically delineated according to use.</span></span>  
  
 <span data-ttu-id="6d038-106">Nejvyšší úroveň členů `My` jsou vystaveny jako objekty.</span><span class="sxs-lookup"><span data-stu-id="6d038-106">Top-level members of `My` are exposed as objects.</span></span> <span data-ttu-id="6d038-107">Každý objekt chová podobně jako obor názvů nebo třída s atributem `Shared` členové a zpřístupňuje sadu souvisejících členů.</span><span class="sxs-lookup"><span data-stu-id="6d038-107">Each object behaves similarly to a namespace or a class with `Shared` members, and it exposes a set of related members.</span></span>  
  
 <span data-ttu-id="6d038-108">Tato tabulka ukazuje na nejvyšší úrovni `My` objekty a jejich vztahu k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="6d038-108">This table shows the top-level `My` objects and their relationship to each other.</span></span>  
  
 ![Diagram je znázorněn objektový model pro moje.](./media/index/my-object-model-relationships.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="6d038-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6d038-110">In This Section</span></span>  
 [<span data-ttu-id="6d038-111">Provádění úloh s objekty My.Application, My.Computer a My.User</span><span class="sxs-lookup"><span data-stu-id="6d038-111">Performing Tasks with My.Application, My.Computer, and My.User</span></span>](../../../visual-basic/developing-apps/development-with-my/performing-tasks-with-my-application-my-computer-and-my-user.md)  
 <span data-ttu-id="6d038-112">Popisuje tři centrální `My` objekty, `My.Application`, `My.Computer`, a `My.User`, které poskytují přístup k informacím a funkce</span><span class="sxs-lookup"><span data-stu-id="6d038-112">Describes the three central `My` objects, `My.Application`, `My.Computer`, and `My.User`, which provide access to information and functionality</span></span>  
  
 [<span data-ttu-id="6d038-113">Výchozí instance objektů poskytované třídami My.Forms a My.WebServices</span><span class="sxs-lookup"><span data-stu-id="6d038-113">Default Object Instances Provided by My.Forms and My.WebServices</span></span>](../../../visual-basic/developing-apps/development-with-my/default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 <span data-ttu-id="6d038-114">Popisuje `My.Forms` a `My.WebServices` objekty, které poskytují přístup k formulářům, zdroje dat a webové služby XML používaný vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="6d038-114">Describes the `My.Forms` and `My.WebServices` objects, which provide access to forms, data sources, and XML Web services used by your application.</span></span>  
  
 [<span data-ttu-id="6d038-115">Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings</span><span class="sxs-lookup"><span data-stu-id="6d038-115">Rapid Application Development with My.Resources and My.Settings</span></span>](../../../visual-basic/developing-apps/development-with-my/rapid-application-development-with-my-resources-and-my-settings.md)  
 <span data-ttu-id="6d038-116">Popisuje `My.Resources` a `My.Settings` objekty, které poskytují přístup k prostředkům a nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d038-116">Describes the `My.Resources` and `My.Settings` objects, which provide access to an application's resources and settings.</span></span>  
  
 [<span data-ttu-id="6d038-117">Přehled aplikačního modelu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d038-117">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="6d038-118">Popisuje model Visual Basic spuštění nebo ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d038-118">Describes the Visual Basic Application Startup/Shutdown model.</span></span>  
  
 [<span data-ttu-id="6d038-119">Závislost oboru názvů My na typu projektu</span><span class="sxs-lookup"><span data-stu-id="6d038-119">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="6d038-120">Obsahuje údaje o kterém `My` funkce jsou k dispozici v různých typech projektů.</span><span class="sxs-lookup"><span data-stu-id="6d038-120">Gives details on which `My` features are available in different project types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d038-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d038-121">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="6d038-122">Objekt My.Forms</span><span class="sxs-lookup"><span data-stu-id="6d038-122">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="6d038-123">Objekt My.WebServices</span><span class="sxs-lookup"><span data-stu-id="6d038-123">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="6d038-124">Závislost oboru názvů My na typu projektu</span><span class="sxs-lookup"><span data-stu-id="6d038-124">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
