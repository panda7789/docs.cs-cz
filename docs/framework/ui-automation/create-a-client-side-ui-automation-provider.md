---
title: Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: 03f64386271565b3494b9dac42cf969fc777e40b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211306"
---
# <a name="create-a-client-side-ui-automation-provider"></a><span data-ttu-id="1dfbc-102">Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="1dfbc-102">Create a Client-Side UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="1dfbc-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1dfbc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1dfbc-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="1dfbc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="1dfbc-105">Toto téma obsahuje ukázkový kód, který ukazuje, jak pro implementaci zprostředkovatele automatizace uživatelského rozhraní na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="1dfbc-105">This topic contains example code that shows how to implement a client-side UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dfbc-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="1dfbc-106">Example</span></span>  
 <span data-ttu-id="1dfbc-107">Následující příklad kódu může být integrovaná [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] , který implementuje velmi jednoduchého zprostředkovatele na straně klienta pro okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="1dfbc-107">The following example code can be built into a [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] that implements a very simple client-side provider for a console window.</span></span> <span data-ttu-id="1dfbc-108">Kód nemá žádné užitečných funkcí, ale je za cíl předvést základní kroky obsažené v nastavení poskytovatele sestavení, které lze registrovat pomocí automatizace uživatelského rozhraní klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="1dfbc-108">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider assembly that can be registered by a UI Automation client application.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a><span data-ttu-id="1dfbc-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1dfbc-109">See also</span></span>

- [<span data-ttu-id="1dfbc-110">Přehled zprostředkovatelů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="1dfbc-110">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="1dfbc-111">Registrace sestavení zprostředkovatele na straně klienta</span><span class="sxs-lookup"><span data-stu-id="1dfbc-111">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
