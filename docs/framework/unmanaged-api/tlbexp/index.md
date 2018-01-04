---
title: "Podpůrné funkce Tlbexp (referenční dokumentace nespravovaného rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a9d483e101fdb94a43055b6081fcc31a458a1ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Podpůrné funkce Tlbexp (referenční dokumentace nespravovaného rozhraní API)
[Knihovna typů – Exportér nástroj](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) načte dynamické knihovny s názvem TlbRef.dll. Tento soubor DLL obsahuje dvou pomocných funkcí a rozhraní, které používá nástroj exportu během procesu převodu sestavení na typu knihovny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [GetTypeLibInfo – funkce](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 Poskytuje informace o knihovny typů lokalizace a operačního systému.  
  
 [LoadTypeLibWithResolver – funkce](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 Načte knihovny typů pomocí implementace [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) vyřešit všechny odkazuje knihovny typů.  
  
 [ITypeLibResolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 Poskytuje [resolvetypelib – metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), který vrátí plně kvalifikovanou cestu knihovny typů.
