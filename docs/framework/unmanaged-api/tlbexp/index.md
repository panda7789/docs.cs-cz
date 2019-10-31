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
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Podpůrné funkce Tlbexp (referenční dokumentace nespravovaného rozhraní API)
[Nástroj pro Exportér knihovny typů](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp. exe) načítá dynamickou knihovnu DLL s názvem TlbRef. dll. Tato knihovna DLL obsahuje dvě pomocné funkce a rozhraní, které nástroj Exportér používá během procesu převodu sestavení na typ knihovny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [GetTypeLibInfo – funkce](gettypelibinfo-function.md)  
 Poskytuje informace o lokalizaci a operačním systému pro knihovnu typů.  
  
 [LoadTypeLibWithResolver – funkce](loadtypelibwithresolver-function.md)  
 Načte knihovnu typů pomocí implementace [rozhraní ITypeLibResolver –](itypelibresolver-interface.md) k překladu všech odkazovaných knihoven typů.  
  
 [ITypeLibResolver – rozhraní](itypelibresolver-interface.md)  
 Poskytuje [metodu ResolveTypeLib –](resolvetypelib-method.md), která vrací plně kvalifikovanou cestu knihovny typů.
