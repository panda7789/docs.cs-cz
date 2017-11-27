---
title: "Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f7bbb13e8a2b877d0f503e091b5bb8b1e7e89d00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="3b17d-102">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="3b17d-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="3b17d-103">Při vývoji a distribuovat ovládací prvky, můžete se zobrazí v těchto ovládací prvky **výběr položek sady nástrojů** dialogové okno, které se zobrazí, když kliknete pravým tlačítkem na **sada nástrojů** a vyberte  **Zvolte položky**.</span><span class="sxs-lookup"><span data-stu-id="3b17d-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="3b17d-104">Ovládací prvek se objeví v tomto dialogovém pomocí postupu registrace AssemblyFoldersEx můžete povolit.</span><span class="sxs-lookup"><span data-stu-id="3b17d-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="3b17d-105">Chcete-li zobrazit vlastního ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="3b17d-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
-   <span data-ttu-id="3b17d-106">Instalovat vaše sestavení ovládacího prvku do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3b17d-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="3b17d-107">Další informace najdete v tématu [postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="3b17d-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="3b17d-108">-nebo-</span><span class="sxs-lookup"><span data-stu-id="3b17d-108">-or-</span></span>  
  
-   <span data-ttu-id="3b17d-109">Pomocí postupu registrace AssemblyFoldersEx zaregistrujte vlastní ovládací prvek a jeho přidružené sestavení návrhu.</span><span class="sxs-lookup"><span data-stu-id="3b17d-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="3b17d-110">AssemblyFoldersEx je registru umístění, kam jiných dodavatelů ukládat cesty pro každou verzi rozhraní, které podporují.</span><span class="sxs-lookup"><span data-stu-id="3b17d-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="3b17d-111">Návrh řešení můžete hledat v tomto umístění registru najít referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="3b17d-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="3b17d-112">Skript registru můžete zadat ovládací prvky, které se má zobrazit v panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="3b17d-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="3b17d-113">Další informace najdete v tématu [nasazení vlastní ovládací prvek a návrhu sestavení (Visual Studio 2013)](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span><span class="sxs-lookup"><span data-stu-id="3b17d-113">For more information, see [Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b17d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b17d-114">See Also</span></span>  
 [<span data-ttu-id="3b17d-115">Výběr dialogové okno položek sady nástrojů (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="3b17d-115">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="3b17d-116">Nasazení vlastního ovládacího prvku a návrhu sestavení (Visual Studio 2013)</span><span class="sxs-lookup"><span data-stu-id="3b17d-116">Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)</span></span>](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [<span data-ttu-id="3b17d-117">Vývoj Windows Forms – ovládací prvky v době návrhu</span><span class="sxs-lookup"><span data-stu-id="3b17d-117">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="3b17d-118">Postupy: Instalace sestavení do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="3b17d-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="3b17d-119">Návod: Automatické vyplnění nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="3b17d-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
