---
title: Podpůrné funkce Tlbexp (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: cbde2af9c8a03e6c41f571120027030713f1b8d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104116"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="9e552-102">Podpůrné funkce Tlbexp (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="9e552-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="9e552-103">[Nástroj pro Exportér knihovny typů](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp. exe) načítá dynamickou knihovnu DLL s názvem TlbRef. dll.</span><span class="sxs-lookup"><span data-stu-id="9e552-103">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="9e552-104">Tato knihovna DLL obsahuje dvě pomocné funkce a rozhraní, které nástroj Exportér používá během procesu převodu sestavení na typ knihovny.</span><span class="sxs-lookup"><span data-stu-id="9e552-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e552-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9e552-105">In This Section</span></span>  
 [<span data-ttu-id="9e552-106">GetTypeLibInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="9e552-106">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="9e552-107">Poskytuje informace o lokalizaci a operačním systému pro knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="9e552-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="9e552-108">LoadTypeLibWithResolver – funkce</span><span class="sxs-lookup"><span data-stu-id="9e552-108">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="9e552-109">Načte knihovnu typů pomocí implementace [rozhraní ITypeLibResolver –](itypelibresolver-interface.md) k překladu všech odkazovaných knihoven typů.</span><span class="sxs-lookup"><span data-stu-id="9e552-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="9e552-110">ITypeLibResolver – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e552-110">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="9e552-111">Poskytuje [metodu ResolveTypeLib –](resolvetypelib-method.md), která vrací plně kvalifikovanou cestu knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="9e552-111">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
