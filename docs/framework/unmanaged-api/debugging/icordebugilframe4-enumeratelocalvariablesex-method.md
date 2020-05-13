---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
ms.openlocfilehash: aef28af3eff6aba03003f156b9226b61a8e72d5b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213748"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Získá enumerátor pro místní proměnnou v rámci a volitelně zahrnuje proměnné přidané v profileru ReJIT instrumentace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 pro Člen výčtu [ILCodeKind](ilcodekind-enumeration.md) , který určuje, jestli jsou proměnné přidané v profileru ReJIT instrumentace zahrnuté do snímku.  
  
 `ppValueEnum`  
 mimo Ukazatel na adresu objektu "ICorDebugValueEnum", který je enumerátorem místních proměnných v tomto snímku.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se podobá metodě [EnumerateLocalVariables –](icordebugilframe-enumeratelocalvariables-method.md) , s tím rozdílem, že volitelně přistupuje k proměnným přidaným v profileru ReJIT instrumentace. Nastavení `flags` na `ILCODE_ORIGINAL_IL` je ekvivalentní volání [ICorDebugILFrame:: EnumerateLocalVariables –](icordebugilframe-enumeratelocalvariables-method.md). Nastavení `flags` `ILCODE_REJIT_IL` umožní ladicímu programu přístup k místním proměnným přidaným v profileru ReJIT instrumentace. Pokud se převodní jazyk (IL) neinstrumentuje, je výčet prázdný a metoda se vrátí `S_OK` .  
  
 Enumerátor nesmí obsahovat všechny místní proměnné v běžící metodě, protože některé z nich nemusí být aktivní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugILFrame4](icordebugilframe4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [ReJIT: Průvodce](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
