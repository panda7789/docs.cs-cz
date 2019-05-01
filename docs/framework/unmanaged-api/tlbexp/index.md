---
title: Podpůrné funkce Tlbexp (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f41a233e9b5338bdb0a324ff9af267a97821d4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967697"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Podpůrné funkce Tlbexp (referenční dokumentace nespravovaného rozhraní API)
[Nástroje Exportér knihovny typů](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) dynamické knihovny DLL s názvem TlbRef.dll načte (Tlbexp.exe). Tato knihovna DLL obsahuje dvě pomocné funkce a rozhraní, které používá nástroj exportu během procesu převodu sestavení na typu knihovny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [GetTypeLibInfo – funkce](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 Poskytuje informace o lokalizaci a operační systém pro knihovnu typů.  
  
 [LoadTypeLibWithResolver – funkce](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 Načte knihovnu typů pomocí implementace [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) vyřešit všechny odkazované knihovny typů.  
  
 [ITypeLibResolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 Poskytuje [resolvetypelib – metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), který vrátí plně kvalifikovanou cestu knihovny typů.
