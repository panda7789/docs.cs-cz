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
ms.openlocfilehash: dc03365b72a5f3613402faf1aed44b5683e9892c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777841"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset – metoda
U zadaného posunu IL Získá nativní posuny, kde by měla být umístěna zarážka, aby ladicí program mohl získat návratovou hodnotu z funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ILoffset`  
 Posun IL Musí se jednat o web volání funkce nebo se volání funkce nezdaří.  
  
 `bufferSize`  
 Počet bajtů, které jsou k dispozici pro uložení `pOffsets`.  
  
 `pFetched`  
 Ukazatel na počet skutečně vrácených posunů. Obvykle je jeho hodnota 1, ale jedna instrukce IL může být mapována na více `CALL` instrukcí sestavení.  
  
 `pOffsets`  
 Pole nativních posunů. `pOffsets` obvykle obsahuje jeden posun, i když jedna instrukce IL může být mapována na více mapování na více `CALL`ch instrukcí sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se používá společně s metodou [ICorDebugILFrame3:: GetReturnValueForILOffset –](icordebugilframe3-getreturnvalueforiloffset-method.md) k získání návratové hodnoty metody, která vrací typ odkazu. Předání posunu IL k webu volání funkce této metodě vrátí jedno nebo více nativních posunů. Ladicí program pak může nastavit zarážky na těchto nativních posunech ve funkci. Když ladicí program narazí na jednu ze zarážek, můžete předat stejný posun IL, který jste předali do této metody, do metody [ICorDebugILFrame3:: GetReturnValueForILOffset –](icordebugilframe3-getreturnvalueforiloffset-method.md) pro získání návratové hodnoty. Ladicí program by pak měl vymazat všechny zarážky, které nastavily.  
  
> [!WARNING]
> Metody `ICorDebugCode3::GetReturnValueLiveOffset` a [ICorDebugILFrame3:: GetReturnValueForILOffset –](icordebugilframe3-getreturnvalueforiloffset-method.md) umožňují získat informace o vrácených hodnotách pouze pro typy odkazů. Načítání informací o vrácených hodnotách z typů hodnot (tj. všechny typy, které jsou odvozeny z <xref:System.ValueType>) nejsou podporovány.  
  
 Funkce vrátí `HRESULT` hodnoty uvedené v následující tabulce.  
  
|hodnota `HRESULT`|Popis|  
|---------------------|-----------------|  
|`S_OK`|Nástup.|  
|`CORDBG_E_INVALID_OPCODE`|Daná lokalita posunu IL není instrukcí volání, nebo funkce vrací `void`.|  
|`CORDBG_E_UNSUPPORTED`|Daný posun IL je správného volání, ale návratový typ není podporován pro získání návratové hodnoty.|  
  
 Metoda `ICorDebugCode3::GetReturnValueLiveOffset` je k dispozici pouze v systémech založených na platformě x86 a AMD64.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetReturnValueForILOffset – metoda](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 – rozhraní](icordebugcode3-interface.md)
