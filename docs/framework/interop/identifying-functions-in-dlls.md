---
title: Identifikace funkcí ve knihovnách DLL
ms.date: 03/30/2017
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc160678817266dc649f60dc3f2cc77044c05691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388616"
---
# <a name="identifying-functions-in-dlls"></a>Identifikace funkcí ve knihovnách DLL
Identitu funkce DLL se skládá z následujících elementů:  
  
-   Název funkce nebo pořadí  
  
-   Název souboru DLL, ve kterém implementace naleznete  
  
 Například zadání **MessageBox** funkce v User32.dll identifikuje funkce (**MessageBox**) a jeho umístění (User32.dll, User32 nebo user32). Rozhraní (Win32 API) Microsoft Windows může obsahovat dvě verze jednotlivé funkce, která zpracovává znaky a řetězce: ANSI verze 1 znakovou a verzi 2bajtová znak Unicode. Pokud tento parametr nezadáte, znaková sada, reprezentována <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> pole, výchozí hodnota je ANSI. Některé funkce mohou mít více než dvě verze.  
  
 **MessageBoxA** ANSI vstupní bod pro **MessageBox** funkce; **Funkce** je verze kódování Unicode. Názvy funkcí pro konkrétní knihovny DLL, jako je například user32.dll, můžete vytvořit seznam spuštěním celou řadu nástrojů pro příkazový řádek. Například můžete použít `dumpbin /exports user32.dll` nebo `link /dump /exports user32.dll` získat názvy funkcí.  
  
 Ať se vám líbí vašeho kódu tak dlouho, dokud je nový název namapovat na původní vstupní bod v knihovně DLL, můžete přejmenovat nespravované funkce. Pokyny k přejmenování nespravované funkce knihovny DLL ve spravovaných zdrojovém kódu, najdete v článku [určení vstupního bodu](../../../docs/framework/interop/specifying-an-entry-point.md).  
  
 Umožňuje vyvolání platformy vám umožňují řídit podstatnou část operačního systému při volání funkce rozhraní API Win32 a další knihovny DLL. Kromě rozhraní Win32 API existuje mnoho dalších rozhraní API a knihovny DLL, které jsou k dispozici prostřednictvím platformy vyvolat.  
  
 Následující tabulka popisuje několik knihoven DLL běžně používané v rozhraní API Win32.  
  
|DLL|Popis obsahu|  
|---------|-----------------------------|  
|Gdi32.dll|Grafické rozhraní zařízení (GDI) funkce pro výstup, jako jsou ty pro vykreslování a písma správu zařízení.|  
|Kernel32.dll|Funkce nízké úrovně operačního systému pro správu paměti a zpracování prostředků.|  
|User32.dll|Funkce správy systému Windows pro zpracování zpráv, časovače, nabídky a komunikace.|  
  
 Úplnou dokumentaci k rozhraní API Win32 najdete v části sada SDK pro platformu. Příklady, které ukazují, jak vytvořit. Na základě NET deklarace, který se má použít s platformou vyvolání najdete v tématu [zařazování dat s vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [Určení vstupního bodu](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [Vytvoření třídy k umístění funkcí DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md)
