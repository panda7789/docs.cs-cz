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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3deb497c3e842e25bcaa46a867dd61ea4a1c3804
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926823"
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
 pro Člen výčtu [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) , který určuje, jestli jsou proměnné přidané v profileru ReJIT instrumentace zahrnuté do snímku.  
  
 `ppValueEnum`  
 mimo Ukazatel na adresu objektu "ICorDebugValueEnum", který je enumerátorem místních proměnných v tomto snímku.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se podobá metodě [EnumerateLocalVariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) , s tím rozdílem, že volitelně přistupuje k proměnným přidaným v profileru ReJIT instrumentace. Nastavení `flags` na`ILCODE_ORIGINAL_IL` je ekvivalentní volání [ICorDebugILFrame:: EnumerateLocalVariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md). Nastavení `flags`umožníladicímu programupřístupkmístnímproměnnýmpřidanýmvprofileruReJITinstrumentace.`ILCODE_REJIT_IL` Pokud se převodní jazyk (IL) neinstrumentuje, je výčet prázdný a metoda se vrátí `S_OK`.  
  
 Enumerátor nesmí obsahovat všechny místní proměnné v běžící metodě, protože některé z nich nemusí být aktivní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugILFrame4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Průvodce postupy](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
