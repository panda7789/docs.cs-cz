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
ms.openlocfilehash: eb1aba9e794928b0eb905722e2a5d7df84100ea4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729207"
---
# <a name="identifying-functions-in-dlls"></a>Identifikace funkcí ve knihovnách DLL
Identita funkce knihovny DLL se skládá z následujících elementů:  
  
-   Funkce názvu nebo řádu  
  
-   Název souboru knihovny DLL, ve kterém můžete najít implementaci  
  
 Například zadání **MessageBox** funkce User32.dll určuje funkci (**MessageBox**) a jeho umístění (User32.dll, User32 nebo user32). Rozhraní (API systému Win32) Windows Microsoft může obsahovat dvě verze jednotlivých funkcí, která zpracovává znaků a řetězce: verze ANSI 1 dvoubajtového znaku zjistí a 2bajtové znaky Unicode verze. Pokud tento parametr nezadáte, znakové sady reprezentována <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> pole, výchozí hodnota je ANSI. Některé funkce mohou mít více než dvě verze.  
  
 **MessageBoxA** ANSI vstupní bod pro **MessageBox** funkce; **Funkce** je verze Unicode. Názvy funkcí pro konkrétní knihovny DLL, jako je například user32.dll, můžete vytvořit seznam spuštěním širokou škálu nástrojů příkazového řádku. Například můžete použít `dumpbin /exports user32.dll` nebo `link /dump /exports user32.dll` získat názvy funkcí.  
  
 Nespravovaná funkce můžete přejmenovat na cokoli, co chcete v rámci vašeho kódu tak dlouho, dokud mapování nový název na původní vstupní bod v knihovně DLL. Pokyny k přejmenování nespravovanou funkci knihovny DLL ve spravovaném zdrojovém kódu, najdete v článku [určení vstupního bodu](../../../docs/framework/interop/specifying-an-entry-point.md).  
  
 Povolí vyvolání platformy je možné řídit podstatnou část operačního systému pomocí volání funkce v rozhraní API systému Win32 a další knihovny DLL. Kromě rozhraní API systému Win32 existuje mnoho jiných rozhraní API a volání knihovny DLL, které jsou k dispozici prostřednictvím platformy.  
  
 Následující tabulka popisuje několik běžně používané knihovny DLL v rozhraní API systému Win32.  
  
|DLL|Popis obsahu|  
|---------|-----------------------------|  
|GDI32.dll|Grafické funkce rozhraní zařízení (GDI) pro zařízení výstup, třeba kroky týkající se správy pro vykreslování a písma.|  
|Kernel32.dll|Funkce nízké úrovně operačního systému pro správu paměti a zpracování prostředků.|  
|User32.dll|Funkce správy Windows pro zpracování zpráv, časovače, nabídky a komunikace.|  
  
 Úplnou dokumentaci k rozhraní API systému Win32 naleznete v tématu Platform SDK. Příklady, které ukazují, jak vytvořit. Na základě NET deklarace pro použití s platformu vyvolání, naleznete v tématu [zařazování dat pomocí vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Viz také:
- [Používání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [Určení vstupního bodu](../../../docs/framework/interop/specifying-an-entry-point.md)
- [Vytvoření třídy k umístění funkcí DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)
- [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md)
