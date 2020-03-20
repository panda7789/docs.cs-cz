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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73104116"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="70bf4-102">Podpůrné funkce Tlbexp (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="70bf4-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="70bf4-103">[Nástroj Exportér knihovny typů](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) načte dynamickou knihovnu odkazů s názvem TlbRef.dll.</span><span class="sxs-lookup"><span data-stu-id="70bf4-103">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="70bf4-104">Tato knihovna DLL obsahuje dvě pomocné funkce a rozhraní, které nástroj exportér používá během procesu převodu sestavení do knihovny typu.</span><span class="sxs-lookup"><span data-stu-id="70bf4-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70bf4-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="70bf4-105">In This Section</span></span>  
 [<span data-ttu-id="70bf4-106">GetTypeLibInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="70bf4-106">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="70bf4-107">Poskytuje informace o lokalizaci a operačním systému pro knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="70bf4-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="70bf4-108">LoadTypeLibWithResolver – funkce</span><span class="sxs-lookup"><span data-stu-id="70bf4-108">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="70bf4-109">Načte knihovnu typů pomocí implementace [rozhraní ITypeLibResolver](itypelibresolver-interface.md) k vyřešení všech odkazovaných knihoven typů.</span><span class="sxs-lookup"><span data-stu-id="70bf4-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="70bf4-110">ITypeLibResolver – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70bf4-110">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="70bf4-111">Poskytuje [metodu ResolveTypeLib](resolvetypelib-method.md), která vrací plně kvalifikovanou cestu knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="70bf4-111">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
