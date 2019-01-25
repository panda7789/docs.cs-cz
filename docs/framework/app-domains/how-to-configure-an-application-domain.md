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
ms.openlocfilehash: 8989d7695f44b0cd2e8b0ce3ec8bd74a6e802102
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534563"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="d9a39-102">Postupy: Konfigurace domény aplikace</span><span class="sxs-lookup"><span data-stu-id="d9a39-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="d9a39-103">Modul common language runtime může poskytnout informace o konfiguraci pro novou doménu aplikace pomocí <xref:System.AppDomainSetup> třídy.</span><span class="sxs-lookup"><span data-stu-id="d9a39-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="d9a39-104">Při vytváření vlastních domén aplikace, je nejdůležitější vlastnost <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9a39-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="d9a39-105">Druhý **AppDomainSetup** vlastnosti jsou používány především hostitelská prostředí modulu runtime pro konfiguraci domény konkrétní aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9a39-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="d9a39-106">**ApplicationBase** definuje vlastnost kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9a39-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="d9a39-107">Když modul runtime je potřeba splnit žádost o typ, sondy pro sestavení obsahující typ v adresáři určeném argumentem **ApplicationBase** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d9a39-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9a39-108">Nová doména aplikace dědí pouze **ApplicationBase** vlastnosti Tvůrce.</span><span class="sxs-lookup"><span data-stu-id="d9a39-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="d9a39-109">Následující příklad vytvoří instance **AppDomainSetup** třídy, tato třída používá k vytvoření nové aplikační doméně, zapisuje tyto informace do konzoly a poté uvolní domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9a39-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9a39-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9a39-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d9a39-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9a39-111">See also</span></span>
- [<span data-ttu-id="d9a39-112">Programování pomocí domén aplikace</span><span class="sxs-lookup"><span data-stu-id="d9a39-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="d9a39-113">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="d9a39-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
