---
title: Používání nespravovaných funkcí DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
ms.openlocfilehash: 7ec1f129dcc19300dd5a4e7c5e627d9e0edf29a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399971"
---
# <a name="consuming-unmanaged-dll-functions"></a>Používání nespravovaných funkcí DLL
Vyvolání platformy je služba, která umožňuje spravovanému kódu volat nespravované funkce implementované v knihovnách dynamických odkazů (DLL), jako jsou ty v rozhraní API systému Windows. Vyhledá a vyvolá exportovanou funkci a zařazuje její argumenty (celá čísla, řetězce, pole, struktury a tak dále) přes hranice vzájemné spolupráce podle potřeby.  
  
 Tato část zavádí úkoly spojené s využíváním nespravovaných funkcí dll a poskytuje další informace o vyvolání platformy. Kromě následujících úkolů existují obecné aspekty a odkaz poskytující další informace a příklady.  
  
#### <a name="to-consume-exported-dll-functions"></a>Využití exportovaných funkcí dll  
  
1. [Identifikujte funkce v knihovnách DLL](identifying-functions-in-dlls.md).  
  
     Minimálně je nutné zadat název funkce a název dll, která ji obsahuje.  
  
2. [Vytvořte třídu pro funkce dll](creating-a-class-to-hold-dll-functions.md).  
  
     Můžete použít existující třídu, vytvořit jednotlivé třídy pro každou nespravovanou funkci nebo vytvořit jednu třídu, která obsahuje sadu souvisejících nespravovaných funkcí.  
  
3. [Vytvořte prototypy ve spravovaném kódu](creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] Použijte **declare** prohlášení s **funkce** a **Lib** klíčová slova. V některých výjimečných případech můžete použít **DllImportAttribute** s klíčová slova **sdílené funkce.** Tyto případy jsou vysvětleny dále v této části.  
  
     [C#] Pomocí **atributu DllImportAttribute** můžete identifikovat knihovnu DLL a funkci. Označte metodu **statickými** a **extern** modifikátory.  
  
     [C++] Pomocí **atributu DllImportAttribute** můžete identifikovat knihovnu DLL a funkci. Označte metodu obálky nebo funkci **extern "C"**.  
  
4. [Volání funkce DLL](calling-a-dll-function.md).  
  
     Volání metody na spravované třídy, stejně jako jakékoli jiné spravované metody. [Předávání struktury](passing-structures.md) a [provádění funkcí zpětného volání](callback-functions.md) jsou zvláštní případy.  
  
 Příklady, které ukazují, jak vytvořit . NET založené deklarace, které mají být použity s platformy vyvolat, naleznete v [tématu zařazování dat s platformy invoke](marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Bližší pohled na vyvolání platformy  
 Platforma vyvolání spoléhá na metadata vyhledejte exportované funkce a zařazování jejich argumenty za běhu. Tento proces je znázorněn na následujícím obrázku.  
  
 ![Diagram, který znázorňuje volání platformy vyvolat.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 Když platforma vyvolá volání nespravované funkce, provede následující posloupnost akcí:  
  
1. Vyhledá dll obsahující funkci.  
  
2. Načte dll do paměti.  
  
3. Vyhledá adresu funkce v paměti a odešle své argumenty do zásobníku, zařazování dat podle potřeby.  
  
    > [!NOTE]
    > Vyhledání a načtení dll a umístění adresy funkce v paměti dojít pouze při prvním volání funkce.  
  
4. Přenese řízení na nespravovanou funkci.  
  
 Vyvolání platformy vyvolá výjimky generované nespravovanou funkcí spravovanému volajícímu.

## <a name="see-also"></a>Viz také

- [Spolupráce s nespravovaným kódem](index.md)
- [Příklady vyvolání platformy](platform-invoke-examples.md)
- [Zařazování spolupráce](interop-marshaling.md)
