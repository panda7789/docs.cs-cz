---
title: Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta
description: Podívejte se na příklad vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta. Příklad implementuje jednoduchého poskytovatele na straně klienta pro okno konzoly.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: a25966d0f11e409bd4e53f944fc2528360327039
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168478"
---
# <a name="create-a-client-side-ui-automation-provider"></a><span data-ttu-id="b396f-104">Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="b396f-104">Create a Client-Side UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="b396f-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b396f-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b396f-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="b396f-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="b396f-107">Toto téma obsahuje příklad kódu, který ukazuje, jak implementovat zprostředkovatele automatizace uživatelského rozhraní na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="b396f-107">This topic contains example code that shows how to implement a client-side UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b396f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b396f-108">Example</span></span>  
 <span data-ttu-id="b396f-109">Následující příklad kódu lze integrovat do dynamické knihovny (DLL), která implementuje velmi jednoduchého poskytovatele na straně klienta pro okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="b396f-109">The following example code can be built into a dynamic-link library (DLL) that implements a very simple client-side provider for a console window.</span></span> <span data-ttu-id="b396f-110">Kód nemá žádné užitečné funkce, ale je určen k předvedení základních kroků v nastavení sestavení zprostředkovatele, které lze registrovat pomocí klientské aplikace automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b396f-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider assembly that can be registered by a UI Automation client application.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a><span data-ttu-id="b396f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b396f-111">See also</span></span>

- [<span data-ttu-id="b396f-112">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b396f-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="b396f-113">Registrace sestavení zprostředkovatele na straně klienta</span><span class="sxs-lookup"><span data-stu-id="b396f-113">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
