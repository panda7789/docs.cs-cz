---
title: 'Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů'
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db4b3ac020e967a6a0c291103d825ac71cebda23
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458282"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="9ac1c-102">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="9ac1c-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>

<span data-ttu-id="9ac1c-103">Při vývoji a distribuci ovládacích prvků můžete chtít, aby se tyto ovládací prvky zobrazovaly v dialogovém okně **zvolit položky sady nástrojů** sady Visual Studio, které se zobrazí po kliknutí pravým tlačítkem myši na **panel nástrojů** a vybrání možnosti **zvolit položky**.</span><span class="sxs-lookup"><span data-stu-id="9ac1c-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box of Visual Studio, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="9ac1c-104">Můžete povolit, aby se váš ovládací prvek zobrazil v tomto dialogovém okně pomocí postupu registrace AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="9ac1c-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>

<span data-ttu-id="9ac1c-105">Chcete-li zobrazit ovládací prvek v dialogovém okně zvolit položky sady nástrojů:</span><span class="sxs-lookup"><span data-stu-id="9ac1c-105">To display your control in the Choose Toolbox Items dialog box:</span></span>

- <span data-ttu-id="9ac1c-106">Nainstalujte sestavení ovládacího prvku do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9ac1c-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="9ac1c-107">Další informace naleznete v tématu [Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC](../../app-domains/install-assembly-into-gac.md)).</span><span class="sxs-lookup"><span data-stu-id="9ac1c-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/install-assembly-into-gac.md).</span></span>

  <span data-ttu-id="9ac1c-108">-nebo-</span><span class="sxs-lookup"><span data-stu-id="9ac1c-108">-or-</span></span>

- <span data-ttu-id="9ac1c-109">Zaregistrujte svůj ovládací prvek a jeho přidružená sestavení v době návrhu pomocí postupu registrace AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="9ac1c-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="9ac1c-110">AssemblyFoldersEx je umístění v registru, kde dodavatelé třetích stran ukládají cesty pro každou verzi rozhraní, kterou podporují.</span><span class="sxs-lookup"><span data-stu-id="9ac1c-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="9ac1c-111">Rozlišení v době návrhu může vyhledat referenční sestavení v tomto umístění registru.</span><span class="sxs-lookup"><span data-stu-id="9ac1c-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="9ac1c-112">Skript registru může určovat ovládací prvky, které se mají zobrazit v sadě nástrojů.</span><span class="sxs-lookup"><span data-stu-id="9ac1c-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ac1c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ac1c-113">See also</span></span>

- [<span data-ttu-id="9ac1c-114">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="9ac1c-114">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="9ac1c-115">Postupy: Instalace sestavení do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="9ac1c-115">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/install-assembly-into-gac.md)
- [<span data-ttu-id="9ac1c-116">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="9ac1c-116">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
