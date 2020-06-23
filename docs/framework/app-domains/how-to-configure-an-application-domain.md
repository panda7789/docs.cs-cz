---
title: 'Postupy: Konfigurace domény aplikace'
description: Nakonfigurujte doménu aplikace v rozhraní .NET. Modul CLR lze poskytnout pomocí informací o konfiguraci pro novou doménu aplikace pomocí třídy AppDomainSetup.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
ms.openlocfilehash: 27afcf161bec74143fafb5dceb20597de73e23d4
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104860"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="9350c-104">Postupy: Konfigurace domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9350c-104">How to: Configure an Application Domain</span></span>
<span data-ttu-id="9350c-105">Modul CLR (Common Language Runtime) můžete zadat s informacemi o konfiguraci pro novou doménu aplikace pomocí <xref:System.AppDomainSetup> třídy.</span><span class="sxs-lookup"><span data-stu-id="9350c-105">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="9350c-106">Při vytváření vlastních aplikačních domén je nejdůležitější vlastností <xref:System.AppDomainSetup.ApplicationBase%2A> .</span><span class="sxs-lookup"><span data-stu-id="9350c-106">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="9350c-107">Další vlastnosti **AppDomainSetup** jsou používány převážně hostiteli modulu runtime ke konfiguraci konkrétní domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9350c-107">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="9350c-108">Vlastnost **ApplicationBase** definuje kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="9350c-108">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="9350c-109">Pokud modul runtime potřebuje, aby splňoval požadavek typu, vyhledá sestavení obsahující typ v adresáři určeném vlastností **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="9350c-109">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9350c-110">Nová aplikační doména dědí pouze vlastnost **ApplicationBase** tvůrce.</span><span class="sxs-lookup"><span data-stu-id="9350c-110">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="9350c-111">Následující příklad vytvoří instanci třídy **AppDomainSetup** , používá tuto třídu k vytvoření nové domény aplikace, zapisuje informace do konzoly a poté uvolní doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9350c-111">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9350c-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="9350c-112">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9350c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9350c-113">See also</span></span>

- [<span data-ttu-id="9350c-114">Programování s aplikačními doménami</span><span class="sxs-lookup"><span data-stu-id="9350c-114">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="9350c-115">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="9350c-115">Using Application Domains</span></span>](use.md)
