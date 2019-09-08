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
ms.openlocfilehash: a95ff535a4d0847fbd4b8af28f873b67a1829a4f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798832"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Podpůrné funkce Tlbexp (referenční dokumentace nespravovaného rozhraní API)
[Nástroj pro Exportér knihovny typů](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp. exe) načítá dynamickou knihovnu DLL s názvem TlbRef. dll. Tato knihovna DLL obsahuje dvě pomocné funkce a rozhraní, které nástroj Exportér používá během procesu převodu sestavení na typ knihovny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [GetTypeLibInfo – funkce](gettypelibinfo-function.md)  
 Poskytuje informace o lokalizaci a operačním systému pro knihovnu typů.  
  
 [LoadTypeLibWithResolver – funkce](loadtypelibwithresolver-function.md)  
 Načte knihovnu typů pomocí implementace [rozhraní ITypeLibResolver –](itypelibresolver-interface.md) k překladu všech odkazovaných knihoven typů.  
  
 [ITypeLibResolver – rozhraní](itypelibresolver-interface.md)  
 Poskytuje [metodu ResolveTypeLib –](resolvetypelib-method.md), která vrací plně kvalifikovanou cestu knihovny typů.
