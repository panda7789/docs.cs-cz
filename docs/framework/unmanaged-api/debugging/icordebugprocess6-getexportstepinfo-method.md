---
title: ICorDebugProcess6::GetExportStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: d92b05e3d84a230e87901378f34ed27ac38286b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123464"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo – metoda
Poskytuje informace o exportovaných funkcích modulu runtime, které vám pomůžou krokovat se spravovaným kódem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>Parametry  
 pszExportName  
 pro Název běhové funkce exportu, jak je zapsán v exportní tabulce PE.  
  
 invokeKind  
 mimo Ukazatel na člen výčtu [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) , který popisuje, jak vyexportovaná funkce bude vyvolávat spravovaný kód.  
  
 invokePurpose  
 mimo Ukazatel na člen výčtu [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) , který popisuje, proč exportovaná funkce bude volat spravovaný kód.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda může vracet hodnoty uvedené v následující tabulce.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|`S_OK`|Volání metody bylo úspěšné.|  
|`E_POINTER`|`pInvokeKind` nebo `pInvokePurpose` je **null**.|  
|Jiné neúspěšné `HRESULT` hodnoty.|Podle potřeby.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess6 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
