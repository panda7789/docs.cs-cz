---
title: Volání funkce DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98d363b6c0838ff1211d969391f04ce8ccddd003
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643566"
---
# <a name="calling-a-dll-function"></a>Volání funkce DLL
I když volání nespravovaných funkcí DLL je téměř shodná volání jiného spravovaného kódu, existují rozdíly, kterým funkcí knihovny DLL připadat složité zpočátku. Tato část představuje témata, která popisují některé z neobvyklé problémy související s voláním.  
  
 Struktury, které jsou vráceny z platformy vyvolat volání musí být datové typy, které zabírají stejné množství spravovaného a nespravovaného kódu. Tyto typy jsou označovány jako *přenositelné typy* protože nevyžadují převod (viz [přenositelné a Non-přenositelné typy](../../../docs/framework/interop/blittable-and-non-blittable-types.md)). Volat funkci, která má nepřenositelné struktury jako její typ vrácené hodnoty, můžete definovat typu blittable pomocné rutiny stejné velikosti jako typ nepřenositelné a převést data po vrácení funkce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Předávání struktur](../../../docs/framework/interop/passing-structures.md)  
 Identifikuje problémy s předáním datových struktur s předdefinovanou rozložení.  
  
 [Funkce zpětného volání](../../../docs/framework/interop/callback-functions.md)  
 Poskytuje základní informace o funkcích zpětného volání.  
  
 [Postupy: Implementace funkcí zpětného volání](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 Popisuje způsob implementace funkcí zpětného volání ve spravovaném kódu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Používání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Popisuje, jak volat nespravovaný volání funkcí knihovny DLL pomocí platformy.  
  
 [Zařazování dat s voláním platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 Popisuje, jak deklarovat parametry metody a předání argumentů funkcí exportovaných knihovnou nespravovaných knihoven.
