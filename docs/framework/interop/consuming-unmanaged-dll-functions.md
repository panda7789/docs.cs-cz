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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 771d1e56d323ee4b450f25773569f7a0b7b038e6
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411158"
---
# <a name="consuming-unmanaged-dll-functions"></a>Používání nespravovaných funkcí DLL
Vyvolání platformy je služba, umožňuje spravovaným kódu volat nespravované funkce implementované v dynamické knihovny (DLL), jako jsou ty v rozhraní Windows API. Vyhledá a volá exportované funkce a zařadí argumenty (celá čísla, řetězce, pole, struktury a tak dále) napříč hranicemi podle potřeby.  
  
 Tato část představuje úloh přidružených k používání nespravovaných funkcí DLL a poskytuje další informace o platformě vyvolat. Kromě následujících úloh jsou obecné požadavky a odkaz Další informace a příklady.  
  
#### <a name="to-consume-exported-dll-functions"></a>Chcete-li využívají exportované funkce DLL  
  
1.  [Identifikace funkcí ve knihovnách DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md).  
  
     Minimálně musíte zadat název funkce a název knihovny DLL, která ji obsahuje.  
  
2.  [Vytvoření třídy k umístění funkcí DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).  
  
     Můžete použít existující třídu, vytvoření jednotlivých tříd pro každou nespravovanou funkci nebo vytvořit jednu třídu, která obsahuje sadu souvisejících nespravované funkce.  
  
3.  [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] Použití **Declare** příkaz **funkce** a **Lib** klíčová slova. Ve výjimečných případech, můžete použít **DllImportAttribute** s **sdílené funkce** klíčová slova. Tyto případy jsou vysvětleny dále v této části.  
  
     [C#] Použití **DllImportAttribute** k identifikaci knihovny DLL a funkce. Označení metody **statické** a **extern** modifikátory.  
  
     [C++] Použití **DllImportAttribute** k identifikaci knihovny DLL a funkce. Označit obalující metodu nebo s funkcí **extern "C"**.  
  
4.  [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md).  
  
     Volejte metodu na spravovanou třídu, stejně jako jiné spravované metody. [Předávání struktur](../../../docs/framework/interop/passing-structures.md) a [implementace funkcí zpětného volání](../../../docs/framework/interop/callback-functions.md) jsou zvláštní případy.  
  
 Příklady, které ukazují, jak vytvořit. Na základě NET deklarace pro použití s platformu vyvolání, naleznete v tématu [zařazování dat pomocí vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Bližší pohled na vyvolání platformy  
 Vyvolání platformy spoléhá na metadata k vyhledání exportovaných funkcí a jejich argumenty zařazování v době běhu. Tento proces je znázorněn na následujícím obrázku.  
  
 ![Vyvolání platformy](../../../docs/framework/interop/media/pinvoke.gif "pinvoke")  
Vyvolání platformy volání nespravovaných funkcí DLL  
  
 Při vyvolání platformy volá nespravovaná funkce provádí následující posloupnost akcí:  
  
1.  Vyhledá knihovny DLL obsahující tuto funkci.  
  
2.  Knihovnu DLL načte do paměti.  
  
3.  Vyhledá adresu funkce v paměti a nabízených oznámení do zásobníku, zařazování dat podle potřeby svých argumentů.  
  
    > [!NOTE]
    >  Vyhledání a načtení knihovny DLL a adresu funkce vyhledávání v paměti dojít pouze při prvním volání funkce.  
  
4.  Přenosy ovládacího prvku nespravované funkci.  
  
 Vyvolání platformy vyvolá výjimky generované nespravovanou funkci spravované volajícímu.

## <a name="see-also"></a>Viz také:
- [Spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md)
- [Příklady vyvolání platformy](../../../docs/framework/interop/platform-invoke-examples.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
