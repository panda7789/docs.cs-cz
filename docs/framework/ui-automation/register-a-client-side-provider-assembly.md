---
title: Registrace sestavení zprostředkovatele na straně klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
ms.openlocfilehash: 3c5c658ffd9b8ac6f9fcd38a9ea979ddb7e0c34c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906643"
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="67f73-102">Registrace sestavení zprostředkovatele na straně klienta</span><span class="sxs-lookup"><span data-stu-id="67f73-102">Register a Client-Side Provider Assembly</span></span>
> [!NOTE]
>  <span data-ttu-id="67f73-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="67f73-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="67f73-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="67f73-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="67f73-105">Toto téma ukazuje, jak zaregistrovat knihovnu DLL, která obsahuje zprostředkovatele automatizace uživatelského rozhraní na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="67f73-105">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67f73-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="67f73-106">Example</span></span>  
 <span data-ttu-id="67f73-107">Následující příklad ukazuje, jak zaregistrovat sestavení, která obsahuje zprostředkovatele pro okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="67f73-107">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="67f73-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67f73-108">See also</span></span>

- [<span data-ttu-id="67f73-109">Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta</span><span class="sxs-lookup"><span data-stu-id="67f73-109">Create a Client-Side UI Automation Provider</span></span>](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
