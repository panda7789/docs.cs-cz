---
title: ICorDebugCode3::GetReturnValueLiveOffset – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df50a4f5b0bdd0c1e70d7c47fe115f4a28b9bbc2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526441"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset – metoda
Pro zadaný posun IL získá nativní posuny, kde by měl být zarážku umístěn tak, aby ladicí program můžete získat návratová hodnota z funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ILoffset`  
 Posun IL. Musí to být web pro volání funkce nebo volání funkce se nezdaří.  
  
 `bufferSize`  
 Počet bajtů dostupných k uložení `pOffsets`.  
  
 `pFetched`  
 Ukazatel na počet skutečně vrácených posunů. Obvykle je jeho hodnota 1, ale jediná instrukce IL může mapovat na více `CALL` pokyny k sestavení.  
  
 `pOffsets`  
 Pole nativních posunů. Obvykle `pOffsets` obsahuje jediný posun, i když se jediná instrukce IL může mapovat na více k několika `CALL` pokyny k sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se používá spolu s [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metodu k získání vrácené hodnoty metody vracející typ odkazu. Předání posunu IL pro web volání funkce do této metody vrátí jeden nebo více nativních posunů. Ladicí program může potom nastavit zarážky u těchto nativních posunů funkce. Pokud ladicí program narazí na jednu ze zarážek, můžete předat stejné odsazení IL, které jste předali do této metody můžete [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metodu k získání vrácené hodnoty. Ladicí program by měl poté zrušit všechny zarážky, které nastavil.  
  
> [!WARNING]
>  `ICorDebugCode3::GetReturnValueLiveOffset` a [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metody umožňují získat informace o vrácené hodnotě pouze pro typy odkazů. Načítají se informace o vrácené hodnotě z typů hodnot (to znamená, že všechny typy, které jsou odvozeny z <xref:System.ValueType>) se nepodporuje.  
  
 Funkce vrátí `HRESULT` hodnoty uvedené v následující tabulce.  
  
|`HRESULT` Hodnota|Popis|  
|---------------------|-----------------|  
|`S_OK`|Úspěch.|  
|`CORDBG_E_INVALID_OPCODE`|Zadaný posun IL není instrukcí volání nebo funkce vrátí `void`.|  
|`CORDBG_E_UNSUPPORTED`|Zadaný posun IL je správným voláním, ale návratový typ není podporován pro načítání návratové hodnoty.|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset` Metoda je k dispozici pouze na základě x86 a AMD64 systémy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [GetReturnValueForILOffset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
