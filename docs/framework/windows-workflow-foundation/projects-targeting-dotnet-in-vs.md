---
title: "Zápis projektech zacílených na rozhraní .NET Framework 3.0 a 3.5 v sadě Visual Studio 2010"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38f0106fedc4755aaa01d97b134c771972f509bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a><span data-ttu-id="42ed5-102">Zápis projektech zacílených na rozhraní .NET Framework 3.0 a 3.5 v sadě Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="42ed5-102">Writing Projects Targeting the .NET Framework 3.0 and 3.5 in Visual Studio 2010</span></span>
<span data-ttu-id="42ed5-103">Můžete použít [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] k vytváření projektů cílených [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] verze 3.0 nebo 3.5.</span><span class="sxs-lookup"><span data-stu-id="42ed5-103">You can use [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] to create projects that target the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version 3.0 or 3.5.</span></span> <span data-ttu-id="42ed5-104">Toto téma popisuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="42ed5-104">This topic describes how to do this.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42ed5-105">Při přidávání aktivity, ujistěte se, že požadované verzi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nastavena.</span><span class="sxs-lookup"><span data-stu-id="42ed5-105">When adding activities, make sure that the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] is set.</span></span> <span data-ttu-id="42ed5-106">Změna verze cíle pracovního postupu po přidání aktivity způsobí selhání ověření pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="42ed5-106">Changing the target version of the workflow after activities are added will cause the workflow to fail validation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="42ed5-107">Otevření existující pracovních postupů v [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] mají rozhraní .net Framework 3.5 aktivit dojde k chybě v `this.SetValue()`.</span><span class="sxs-lookup"><span data-stu-id="42ed5-107">Opening existing workflows in [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] that have .Net Framework 3.5 activities will cause an error at `this.SetValue()`.</span></span> <span data-ttu-id="42ed5-108">Chcete-li otevřít projektů vytvořených v dřívějších verzích rozhraní .net Framework, nejprve otevření prázdné workflow v návrháři a přidejte .net Framework 3.5 aktivity.</span><span class="sxs-lookup"><span data-stu-id="42ed5-108">In order to open projects created with previous versions of the .Net Framework, first open a blank workflow in the designer and add a .Net Framework 3.5 activity.</span></span>  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a><span data-ttu-id="42ed5-109">Vytvoření rozhraní .NET Framework 3.0 nebo 3.5 projekt pomocí sady Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="42ed5-109">To create a .NET Framework  3.0 or 3.5 project with Visual Studio 2010</span></span>  
  
1.  <span data-ttu-id="42ed5-110">Otevřete [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42ed5-110">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="42ed5-111">Vyberte **soubor**, **nové**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="42ed5-111">Select **File**, **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="42ed5-112">V rozevíracím seznamu v horní části dialogových oken, vybrat požadovanou verzi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42ed5-112">In the drop-down list at the top of the dialog box, select the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a><span data-ttu-id="42ed5-113">Pro upgrade cílové verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="42ed5-113">To upgrade the targeted version of the .NET Framework</span></span>  
  
1.  <span data-ttu-id="42ed5-114">Klikněte pravým tlačítkem na projekt v Průzkumníku řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="42ed5-114">Right-click the project in Solution Explorer, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="42ed5-115">V **cílové rozhraní** rozevíracího seznamu vyberte požadovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="42ed5-115">In the **Target Framework** drop-down list, select the desired version.</span></span>
