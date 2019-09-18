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
ms.openlocfilehash: 275aa5bb664e9f5a50f44a72f2506d7984234b31
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051828"
---
# <a name="creating-a-class-to-hold-dll-functions"></a>Vytvoření třídy k umístění funkcí DLL
Zabalení často používané funkce knihovny DLL ve spravované třídě představuje účinný přístup k zapouzdření funkčnosti platformy. I když není nutné tak učinit v každém případě, poskytnutí obálky třídy je pohodlné, protože definování funkcí knihovny DLL může být náročné a náchylné k chybám. Pokud programujete v Visual Basic nebo C#, musíte deklarovat funkce knihovny DLL v rámci třídy nebo modulu Visual Basic.  
  
 V rámci třídy definujete statickou metodu pro každou funkci knihovny DLL, kterou chcete volat. Definice může obsahovat další informace, jako je například znaková sada nebo konvence volání používané při předávání argumentů metody; Vynecháte-li tyto informace, vyberte výchozí nastavení. Úplný seznam možností deklarace a jejich výchozí nastavení naleznete v tématu [vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md).  
  
 Po zabalení můžete volat metody pro třídu při volání statických metod na jakékoli jiné třídě. Volání platformy zpracovává základní exportovanou funkci automaticky.  
  
 Při navrhování spravované třídy pro vyvolání platformy zvažte vztahy mezi třídami a funkcemi knihovny DLL. Můžete například:  
  
- Deklarujete funkce knihovny DLL v rámci existující třídy.  
  
- Vytvořte pro každou funkci knihovny DLL jednotlivou třídu, zachováte funkce izolované a snadno najít.  
  
- Vytvořte jednu třídu pro sadu souvisejících funkcí knihoven DLL pro vytváření logických seskupení a snížení režie.  
  
 Můžete pojmenovat třídu a její metody, které jste si zařadíte. Příklady, které ukazují, jak vytvořit. Deklarace založené na síti, které se mají použít s voláním platformy, najdete v tématu [zařazování dat pomocí vyvolání platformy](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Viz také:

- [Používání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md)
- [Identifikace funkcí ve knihovnách DLL](identifying-functions-in-dlls.md)
- [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
- [Volání funkce DLL](calling-a-dll-function.md)
