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
ms.openlocfilehash: 341a86f4c1c8367f979e193a6284bf89f1b03ca0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178806"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda
[Podporováno v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Získá čítač výčtu pro místní proměnné v rámci a volitelně zahrnuje proměnné přidané v profileru ReJIT instrumentace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 [v] Člen výčtu [ILCodeKind,](ilcodekind-enumeration.md) který určuje, zda jsou v rámci zahrnuty proměnné přidané v instrumentaci ReJIT profileru.  
  
 `ppValueEnum`  
 [out] Ukazatel na adresu objektu "ICorDebugValueEnum", který je čítatelem pro místní proměnné v tomto rámci.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobná [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) metoda, s tím rozdílem, že volitelně přistupuje proměnné přidané v profileru ReJIT instrumentace. Nastavení `flags` `ILCODE_ORIGINAL_IL` je ekvivalentní volání [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md). Nastavení `flags` `ILCODE_REJIT_IL` umožňuje ladicí program pro přístup k místním proměnným přidaným v instrumentaci ReJIT profileru. Pokud zprostředkující jazyk (IL) není instrumentovaný, výčet je `S_OK`prázdný a metoda vrátí .  
  
 Čítač nemusí obsahovat všechny místní proměnné v běžící metodě, protože některé z nich nemusí být aktivní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugILFrame4 – rozhraní](icordebugilframe4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [ReJIT: Návod, jak](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
