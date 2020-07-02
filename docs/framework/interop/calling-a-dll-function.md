---
title: Volání funkce DLL
description: Přečtěte si problémy o volání funkce knihovny DLL, která může být matoucí. Proces volání funkce se liší v závislosti na tom, zda je návratový typ přenositelný.
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
ms.openlocfilehash: 90f8f47148e652a9942a35be1564bed94c155216
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620895"
---
# <a name="calling-a-dll-function"></a>Volání funkce DLL
I když volání nespravovaných knihoven DLL je téměř totožné s voláním jiného spravovaného kódu, existují rozdíly v tom, že funkce knihovny DLL se jeví jako nematoucí jako první. V této části najdete témata, která popisují některé neobvyklé problémy související s voláním.  
  
 Struktury, které jsou vraceny voláními vyvolání platformy, musí být datové typy, které mají stejnou reprezentaci ve spravovaném a nespravovaném kódu. Tyto typy se nazývají přenositelné *typy* , protože nevyžadují konverzi (viz [přenositelné a nepřímo přenositelné typy](blittable-and-non-blittable-types.md)). Chcete-li volat funkci, která má jako návratový typ nepřímou strukturu, můžete definovat typ přenositelného pomocníka stejné velikosti jako nepřenosný typ a převést data poté, co funkce vrátí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Předávání struktur](passing-structures.md)  
 Určuje problémy předávání datových struktur s předdefinovaným rozložením.  
  
 [Funkce zpětného volání](callback-functions.md)  
 Poskytuje základní informace o funkcích zpětného volání.  
  
 [Postupy: Implementace funkcí zpětného volání](how-to-implement-callback-functions.md)  
 Popisuje, jak implementovat funkce zpětného volání ve spravovaném kódu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Používání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md)  
 Popisuje, jak volat nespravované funkce knihovny DLL pomocí vyvolání platformy.  
  
 [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)  
 Popisuje, jak deklarovat parametry metody a předávat argumenty funkcím exportovaným nespravovanými knihovnami.
