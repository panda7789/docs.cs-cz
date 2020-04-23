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
Vyvolání platformy je služba, která umožňuje spravovanému kódu volat nespravované funkce implementované v knihovně DLL (Dynamic Link Library), jako jsou ty v rozhraní API systému Windows. Vyhledá a vyvolá exportovanou funkci a zařadí argumenty (celá čísla, řetězce, pole, struktury atd.) v rámci hranice mezioperace podle potřeby.  
  
 V této části jsou uvedeny úlohy spojené s používáním nespravovaných funkcí knihovny DLL a další informace o vyvolání platformy. Kromě následujících úkolů existují obecné požadavky a odkaz, který poskytuje další informace a příklady.  
  
#### <a name="to-consume-exported-dll-functions"></a>Využití exportovaných funkcí DLL  
  
1. [Identifikujte funkce v knihovnách DLL](identifying-functions-in-dlls.md).  
  
     Minimální je nutné zadat název funkce a název knihovny DLL, která ji obsahuje.  
  
2. [Vytvořte třídu pro uchovávání funkcí knihovny DLL](creating-a-class-to-hold-dll-functions.md).  
  
     Můžete použít existující třídu, vytvořit jednotlivou třídu pro každou nespravovanou funkci nebo vytvořit jednu třídu, která obsahuje sadu souvisejících nespravovaných funkcí.  
  
3. [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] Použijte příkaz **Declare** s klíčovými slovy **Function** a **lib** . V některých vzácných případech můžete použít **DllImportAttribute** pomocí klíčových slov **sdílených funkcí** . Tyto případy jsou vysvětleny dále v této části.  
  
     Jazyk Použijte **DllImportAttribute** k identifikaci knihovny DLL a funkce. Označte metodu **statickými** a **externými** modifikátory.  
  
     Volat Použijte **DllImportAttribute** k identifikaci knihovny DLL a funkce. Označte obálkovou metodu nebo funkci s **extern "C"**.  
  
4. [Volání funkce knihovny DLL](calling-a-dll-function.md).  
  
     Volejte metodu na spravované třídě stejně jako jakoukoli jinou spravovanou metodu. [Předání struktur](passing-structures.md) a [implementace funkcí zpětného volání](callback-functions.md) jsou zvláštní případy.  
  
 Příklady, které ukazují, jak vytvořit. Deklarace založené na síti, které se mají použít s voláním platformy, najdete v tématu [zařazování dat pomocí vyvolání platformy](marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Bližší pohled na vyvolání platformy  
 Vyvolání platformy spoléhá na metadata pro vyhledání exportovaných funkcí a zařazování jejich argumentů za běhu. Tento proces je znázorněn na následujícím obrázku.  
  
 ![Diagram, který zobrazuje volání vyvolání platformy.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 Když vyvolání platformy volá nespravovanou funkci, provede následující posloupnost akcí:  
  
1. Vyhledá knihovnu DLL obsahující funkci.  
  
2. Načte knihovnu DLL do paměti.  
  
3. Vyhledá adresu funkce v paměti a vloží její argumenty do zásobníku, zařazování dat podle potřeby.  
  
    > [!NOTE]
    > Vyhledání a načtení knihovny DLL a vyhledání adresy funkce v paměti dochází pouze při prvním volání funkce.  
  
4. Přenáší řízení na nespravovanou funkci.  
  
 Vyvolání platformy vyvolá výjimku vygenerovanou nespravovanou funkcí spravovanému volajícímu.

## <a name="see-also"></a>Viz také

- [Spolupráce s nespravovaným kódem](index.md)
- [Příklady vyvolání platformy](platform-invoke-examples.md)
- [Zařazování spolupráce](interop-marshaling.md)
