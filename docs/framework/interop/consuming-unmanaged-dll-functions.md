---
title: "Používání nespravovaných funkcí DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd1e5f4fc03da2310022efdeb4530440b5e07f3d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="consuming-unmanaged-dll-functions"></a>Používání nespravovaných funkcí DLL
Vyvolání platformy je služba, což umožňuje spravovat kódu volání nespravovaných funkcí, které jsou implementované v dynamické knihovny (DLL), například v rozhraní API Win32. Vyhledá a vyvolá exportované funkce a zařazuje její argumenty (celá čísla, řetězce, pole, struktur a tak dále) přes součinnosti hranice, podle potřeby. Další informace o této službě najdete v tématu [A blíže podívejte se na vyvolání platformy](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243).  
  
 Tato část obsahuje několik úloh, které jsou přidružené k využívání nespravovaných funkcí knihovny DLL. Kromě následující úlohy jsou obecné požadavky a poskytuje další informace a příklady odkaz.  
  
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
 [Používání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
