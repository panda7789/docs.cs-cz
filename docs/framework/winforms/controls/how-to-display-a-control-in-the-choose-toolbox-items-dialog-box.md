---
title: 'Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: fdda72d60b0f18e76b03e9b7f05060a09763a3f7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488258"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="bf5cf-102">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="bf5cf-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="bf5cf-103">Vytvořte a rozdistribuujte ovládací prvky, možná budete chtít tyto ovládací prvky se zobrazí v **zvolit položky nástrojů** dialogové okno, které se zobrazí, když kliknete pravým tlačítkem myši **nástrojů** a vyberte  **Výběr položek**.</span><span class="sxs-lookup"><span data-stu-id="bf5cf-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="bf5cf-104">Můžete povolit ovládacího prvku se zobrazí v tomto dialogovém AssemblyFoldersEx postupem registrace.</span><span class="sxs-lookup"><span data-stu-id="bf5cf-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="bf5cf-105">Chcete-li zobrazit ovládací prvek v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="bf5cf-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
-   <span data-ttu-id="bf5cf-106">Nainstalujte sestavení ovládacího prvku do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="bf5cf-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="bf5cf-107">Další informace najdete v tématu [postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="bf5cf-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="bf5cf-108">-nebo-</span><span class="sxs-lookup"><span data-stu-id="bf5cf-108">-or-</span></span>  
  
-   <span data-ttu-id="bf5cf-109">Zaregistrujte ovládací prvek a jeho přidružené sestavení doby návrhu AssemblyFoldersEx postupem registrace.</span><span class="sxs-lookup"><span data-stu-id="bf5cf-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="bf5cf-110">AssemblyFoldersEx je umístění registru, kam dodavateli z jiných ukládat cesty pro každou verzi rozhraní framework, která podporují.</span><span class="sxs-lookup"><span data-stu-id="bf5cf-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="bf5cf-111">Doby návrhu řešení se můžete podívat v tomto umístění v registru najít referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="bf5cf-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="bf5cf-112">Skript registru můžete zadat ovládací prvky, které chcete zobrazit na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="bf5cf-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="bf5cf-113">Další informace najdete v tématu [nasazení vlastní ovládací prvek a návrhových sestavení (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span><span class="sxs-lookup"><span data-stu-id="bf5cf-113">For more information, see [Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5cf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf5cf-114">See Also</span></span>  
 [<span data-ttu-id="bf5cf-115">Zvolte dialogové okno položky panelu nástrojů (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="bf5cf-115">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="bf5cf-116">Nasazení vlastního ovládacího prvku a návrhových sestavení (Visual Studio 2013)</span><span class="sxs-lookup"><span data-stu-id="bf5cf-116">Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)</span></span>](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [<span data-ttu-id="bf5cf-117">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="bf5cf-117">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="bf5cf-118">Postupy: Instalace sestavení do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="bf5cf-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="bf5cf-119">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="bf5cf-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
