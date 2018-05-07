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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
