---
title: ICorDebugVariableHome – rozhraní
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
ms.openlocfilehash: caf6a24207be98be9afb10be2bd027b51405fa3b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396536"
---
# <a name="icordebugvariablehome-interface"></a>ICorDebugVariableHome – rozhraní
Představuje místní proměnnou nebo argument funkce.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetArgumentIndex – metoda](icordebugvariablehome-getargumentindex-method.md)|Získá index argumentu funkce.|  
|[GetCode – metoda](icordebugvariablehome-getcode-method.md)|Získá instanci "ICorDebugCode", která obsahuje tento `ICorDebugVariableHome` objekt.|  
|[GetLiveRange – metoda](icordebugvariablehome-getliverange-method.md)|Získá nativní rozsah, ve kterém je tato proměnná živá.|  
|[GetLocationType – metoda](icordebugvariablehome-getlocationtype-method.md)|Získá typ nativního umístění proměnné.|  
|[GetOffset – metoda](icordebugvariablehome-getoffset-method.md)|Získá posun od základního registru pro proměnnou.|  
|[GetRegister – metoda](icordebugvariablehome-getregister-method.md)|Získá registr, který obsahuje proměnnou s typem umístění `VLT_REGISTER` a základní registr pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE` .|  
|[GetSlotIndex – metoda](icordebugvariablehome-getslotindex-method.md)|Získá spravovaný index slotu místní proměnné.|  
  
## <a name="example"></a>Příklad  
 Následující fragment kódu používá objekt [ICorDebugCode4](icordebugcode4-interface.md) s názvem `pCode4` .  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [ICorDebugVariableHomeEnum – rozhraní](icordebugvariablehomeenum-interface.md)
