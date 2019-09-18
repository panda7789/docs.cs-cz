---
title: 'Postupy: Konfigurace domény aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06883646982aa6bd642dc4fce7881a289dad5901
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053195"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="8488f-102">Postupy: Konfigurace domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8488f-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="8488f-103">Modul CLR (Common Language Runtime) můžete zadat s informacemi o konfiguraci pro novou doménu aplikace <xref:System.AppDomainSetup> pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="8488f-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="8488f-104">Při vytváření vlastních aplikačních domén je <xref:System.AppDomainSetup.ApplicationBase%2A>nejdůležitější vlastností.</span><span class="sxs-lookup"><span data-stu-id="8488f-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="8488f-105">Další vlastnosti **AppDomainSetup** jsou používány převážně hostiteli modulu runtime ke konfiguraci konkrétní domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="8488f-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="8488f-106">Vlastnost **ApplicationBase** definuje kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="8488f-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="8488f-107">Pokud modul runtime potřebuje, aby splňoval požadavek typu, vyhledá sestavení obsahující typ v adresáři určeném vlastností **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="8488f-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8488f-108">Nová aplikační doména dědí pouze vlastnost **ApplicationBase** tvůrce.</span><span class="sxs-lookup"><span data-stu-id="8488f-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="8488f-109">Následující příklad vytvoří instanci třídy **AppDomainSetup** , používá tuto třídu k vytvoření nové domény aplikace, zapisuje informace do konzoly a poté uvolní doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="8488f-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8488f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8488f-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8488f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8488f-111">See also</span></span>

- [<span data-ttu-id="8488f-112">Programování s aplikačními doménami</span><span class="sxs-lookup"><span data-stu-id="8488f-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="8488f-113">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="8488f-113">Using Application Domains</span></span>](use.md)
