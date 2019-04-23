---
title: Vytvoření třídy k umístění funkcí DLL
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 399ad6649016e53d91d5d9d30ecc031ae8a97a4a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149354"
---
# <a name="creating-a-class-to-hold-dll-functions"></a>Vytvoření třídy k umístění funkcí DLL
Obtékání často používané funkce knihovny DLL ve spravované třídě je efektivního přístupu k zapouzdření funkce platformy. Ačkoli to není nutné provést ve všech případech, za předpokladu, že třída obálky je pohodlné, protože definice funkcí knihovny DLL může být náročné a náchylné k chybě. Pokud programujete v jazyce Visual Basic nebo C#, je třeba deklarovat funkce knihovny DLL v rámci třídy nebo modulu jazyka Visual Basic.  
  
 V rámci třídy můžete definovat statické metody pro každou funkci knihovny DLL, kterou chcete volat. Definice může obsahovat další informace, jako je znaková sada nebo použití předání argumentů metody; konvence volání vynecháním tyto informace, vyberte výchozí nastavení. Úplný seznam možností deklarace a výchozí nastavení, najdete v části [vytváření prototypů ve spravovaného kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
 Jakmile zabalená, můžete volat metody ve třídě jako volání statické metody na jinou třídu. Vyvolání platformy zpracovává základní exportované funkce automaticky.  
  
 Při navrhování spravovanou třídu pro platformu vyvolání, vezměte v úvahu vztahy mezi třídami a funkcí knihovny DLL. Například můžete:  
  
-   Deklarování funkcí knihovny DLL v rámci existující třídy.  
  
-   Vytvoření jednotlivých tříd pro každou funkci knihovny DLL, udržování funkce izolované a snadno najít.  
  
-   Vytvořte jednu třídu sady souvisejících funkcí knihovny DLL tvoří logické seskupení a snížit režii.  
  
 Název třídy a můžete její metody, jako je prosím. Příklady, které ukazují, jak vytvořit. Na základě NET deklarace pro použití s platformu vyvolání, naleznete v tématu [zařazování dat pomocí vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Viz také:

- [Používání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [Identifikace funkcí ve knihovnách DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md)
- [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md)
