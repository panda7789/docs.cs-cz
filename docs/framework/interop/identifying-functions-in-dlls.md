---
title: Identifikace funkcí ve knihovnách DLL
description: Identifikujte funkce v knihovnách DLL. Identita funkce knihovny DLL se skládá z názvu funkce nebo pořadového čísla a názvu souboru DLL, ve kterém lze implementovat implementaci.
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
ms.openlocfilehash: 054d1351a9ee6adab17117c9f423aa26d0d9ed59
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622728"
---
# <a name="identifying-functions-in-dlls"></a>Identifikace funkcí ve knihovnách DLL
Identita funkce knihovny DLL se skládá z následujících prvků:  
  
- Název funkce nebo ordinální číslo  
  
- Název souboru DLL, ve kterém se dá najít implementace  
  
 Například zadání funkce **MessageBox** v User32.dll identifikuje funkci (**MessageBox**) a její umístění (User32.dll, User32 nebo user32). Programovací rozhraní aplikace systému Microsoft Windows (rozhraní Windows API) může obsahovat dvě verze každé funkce, která zpracovává znaky a řetězce: 1 bajtovou verzi znakové sady ANSI a 2 bajtovou verzi znakové sady Unicode. Je-li tento parametr zadán, je znaková sada reprezentovaná polem standardně <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> ANSI. Některé funkce můžou mít víc než dvě verze.  
  
 **MessageBox** je vstupní bod ANSI pro funkci **MessageBox** ; **MessageBoxW** je verze Unicode. Pomocí různých nástrojů příkazového řádku můžete zobrazit seznam názvů funkcí pro konkrétní knihovnu DLL, například user32.dll. Můžete například použít `dumpbin /exports user32.dll` nebo `link /dump /exports user32.dll` k získání názvů funkcí.  
  
 Nespravovanou funkci můžete přejmenovat bez ohledu na to, co byste chtěli v kódu, Pokud namapujete nový název na původní vstupní bod v knihovně DLL. Pokyny k přejmenování nespravované funkce DLL ve spravovaném zdrojovém kódu naleznete v tématu [určení vstupního bodu](specifying-an-entry-point.md).  
  
 Vyvolání platformy umožňuje řídit významnou část operačního systému voláním funkcí v rozhraní API systému Windows a dalších knihovnách DLL. Kromě rozhraní API systému Windows existuje mnoho dalších rozhraní API a knihoven DLL, které jsou k dispozici prostřednictvím vyvolání platformy.  
  
 Následující tabulka popisuje několik běžně používaných knihoven DLL v rozhraní Windows API.  
  
|DLL|Popis obsahu|  
|---------|-----------------------------|  
|GDI32.dll|Funkce GDI (GDI) pro výstup zařízení, například pro vykreslování a správu písem.|  
|Kernel32.dll|Funkce operačního systému nižší úrovně pro správu paměti a zpracování prostředků.|  
|User32.dll|Funkce správy systému Windows pro zpracování zpráv, časovače, nabídky a komunikaci.|  
  
 Úplnou dokumentaci k rozhraní API systému Windows najdete v sadě SDK platformy. Příklady, které ukazují, jak vytvořit. Deklarace založené na síti, které se mají použít s voláním platformy, najdete v tématu [zařazování dat pomocí vyvolání platformy](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Viz také:

- [Používání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md)
- [Určení vstupního bodu](specifying-an-entry-point.md)
- [Vytvoření třídy k umístění funkcí DLL](creating-a-class-to-hold-dll-functions.md)
- [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
- [Volání funkce DLL](calling-a-dll-function.md)
