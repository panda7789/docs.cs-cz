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
ms.openlocfilehash: 3166d6c95532706781188da0c56ebf9022038a50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="consuming-unmanaged-dll-functions"></a>Používání nespravovaných funkcí DLL
Vyvolání platformy je služba, což umožňuje spravovat kódu volání nespravovaných funkcí, které jsou implementované v dynamické knihovny (DLL), například v rozhraní API Win32. Vyhledá a vyvolá exportované funkce a zařazuje její argumenty (celá čísla, řetězce, pole, struktur a tak dále) přes součinnosti hranice, podle potřeby.  
  
 Tato část uvádí úkoly spojené s využívání nespravovaných funkcí DLL a poskytuje další informace o platformě vyvolání. Kromě následující úlohy jsou obecné požadavky a poskytuje další informace a příklady odkaz.  
  
#### <a name="to-consume-exported-dll-functions"></a>Využívat exportované funkce DLL  
  
1.  [Identifikace funkcí ve knihovnách DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md).  
  
     Minimálně musíte zadat název funkce a název knihovny DLL, která ji obsahuje.  
  
2.  [Vytvoření třídy k umístění funkcí DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).  
  
     Můžete použít existující třídy, vytvoření jednotlivých tříd pro jednotlivé nespravované funkce nebo vytvořte jednu třídu, která obsahuje sadu související nespravovaných funkcí.  
  
3.  [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] Použití **Declare** příkaz s **funkce** a **Lib** klíčová slova. Ve výjimečných případech, můžete použít **DllImportAttribute** s **sdílené funkce** klíčová slova. Těchto případech jsou vysvětleny později v této části.  
  
     [C#] Použití **DllImportAttribute** k identifikaci knihovny DLL a funkce. Označit metodu s **statické** a **extern** modifikátory.  
  
     [C++] Použití **DllImportAttribute** k identifikaci knihovny DLL a funkce. Označit obálku metody nebo funkce s **extern "C"**.  
  
4.  [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md).  
  
     Volejte metodu v třídě spravované stejně jako jiné spravované metody. [Předávání struktur](../../../docs/framework/interop/passing-structures.md) a [implementace funkce zpětného volání](../../../docs/framework/interop/callback-functions.md) jsou zvláštní případy.  
  
 Příklady, které ukazují, jak vytvořit. Na základě NET deklarace, který se má použít s platformou vyvolání najdete v tématu [zařazování dat s vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Vyvolání bližší pohled na platformy  
 Vyvolání platformy spoléhá na metadata pro vyhledání exportovaných funkcí a jejich argumentů zařazování v době běhu. Tento proces je znázorněn na následujícím obrázku.  
  
 ![Vyvolání platformy](../../../docs/framework/interop/media/pinvoke.gif "pinvoke")  
Nespravovaného volání nespravovaného funkce DLL  
  
 Při vyvolání platformy volání nespravované funkce, provede následující posloupnost akcí:  
  
1.  Vyhledá knihovnu DLL obsahující danou funkci.  
  
2.  Knihovnu DLL načte do paměti.  
  
3.  Vyhledá adresu funkce v paměti a nabízených oznámení její argumenty do zásobníku, zařazování dat podle potřeby.  
  
    > [!NOTE]
    >  Vyhledání a načtení knihovny DLL a adresu funkce vyhledávání v paměti se provádějí pouze při prvním volání funkce.  
  
4.  Ovládací prvek přenos nespravovaného funkce.  
  
 Vyvolání platformy generuje výjimky generované funkci nespravované na spravované volajícího.  
  
## <a name="see-also"></a>Viz také  
 [Spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md)  
 [Příklady vyvolání platformy](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)  
