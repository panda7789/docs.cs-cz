---
title: "Volání funkce DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8755173b9c64a6457b94e689204c6a5aabc971cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="calling-a-dll-function"></a>Volání funkce DLL
Přestože volání nespravovaných funkcí knihovny DLL je téměř shodná volání jiných spravovaného kódu, jsou rozdíly, které můžou vypadat matoucí funkcí knihovny DLL na první. Tato část obsahuje témata, která popisují některá z neobvyklého problémy související s volání.  
  
 Struktury, které jsou vráceny z platformy vyvolat volání musí být typy dat, které mají stejnou reprezentaci v spravovanými a nespravovanými kódu. Tyto typy jsou označovány jako *přenositelné typy* protože nevyžadují převodu (viz [přenositelné a Non-přenositelné typy](../../../docs/framework/interop/blittable-and-non-blittable-types.md)). K volání funkce, která má strukturu nepřenositelné jako její návratový typ, můžete definovat typu blittable pomocná stejnou velikost jako typ nepřenositelné a převést data po funkce vrátí hodnotu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Předávání struktur](../../../docs/framework/interop/passing-structures.md)  
 Identifikuje problémy předat datové struktury předdefinované rozložení.  
  
 [Funkce zpětného volání](../../../docs/framework/interop/callback-functions.md)  
 Poskytuje základní informace o funkce zpětného volání.  
  
 [Postupy: Implementace funkcí zpětného volání](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 Popisuje způsob implementace funkcí zpětného volání ve spravovaném kódu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Používání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Popisuje, jak volat nespravovaný volání funkcí knihovny DLL pomocí platformy.  
  
 [Zařazování dat s voláním platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 Popisuje, jak deklarace parametry metody a předání argumentů funkce exportované sadou nespravované knihovny.
