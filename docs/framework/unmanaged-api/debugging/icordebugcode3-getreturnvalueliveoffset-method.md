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
ms.openlocfilehash: 34d543dd76de05bdf55d8187cf192455d1387a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178945"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset – metoda
Pro zadaný posun IL získá nativní posuny, kde by měla být umístěna zarážka tak, aby ladicí program mohl získat vrácenou hodnotu z funkce.  
  
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
 Posun IL. Musí se jednat o stránku s voláním funkce, jinak se volání funkce nezdaří.  
  
 `bufferSize`  
 Počet bajtů, které `pOffsets`jsou k dispozici pro uložení .  
  
 `pFetched`  
 Ukazatel na počet posunů skutečně vrácených. Obvykle je jeho hodnota 1, ale jedna instrukce `CALL` IL může mapovat na více instrukcí sestavení.  
  
 `pOffsets`  
 Pole nativní posuny. Obvykle `pOffsets` obsahuje jeden posun, i když jeden IL instrukce můžete `CALL` mapovat na více map na více instrukcí sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se používá spolu s [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) metoda získat vrácenou hodnotu metody, která vrací typ odkazu. Předání mdloby posunu do webu volání funkce této metodě vrátí jeden nebo více nativní posuny. Ladicí program pak můžete nastavit zarážky na tyto nativní posuny ve funkci. Když ladicí program zasáhne jeden z zarážek, můžete pak předat stejný IL posun, který jste předali této metodě [iCorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) metoda získat vrácenou hodnotu. Ladicí program by pak měl vymazat všechny zarážky, které nastaví.  
  
> [!WARNING]
> Metody `ICorDebugCode3::GetReturnValueLiveOffset` a a [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) umožňují získat informace o vrácené hodnotě pouze pro typy odkazů. Načítání informací o vrácené hodnotě z typů hodnot <xref:System.ValueType>(tj. všechny typy, které jsou odvozeny z ) není podporováno.  
  
 Funkce vrátí `HRESULT` hodnoty uvedené v následující tabulce.  
  
|`HRESULT`Hodnotu|Popis|  
|---------------------|-----------------|  
|`S_OK`|Úspěch|  
|`CORDBG_E_INVALID_OPCODE`|Daný server offset IL není instrukce volání nebo `void`funkce vrátí .|  
|`CORDBG_E_UNSUPPORTED`|Daný posun IL je správné volání, ale návratový typ není podporován pro získání vrácené hodnoty.|  
  
 Metoda `ICorDebugCode3::GetReturnValueLiveOffset` je k dispozici pouze v systémech x86 a AMD64.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetReturnValueForILOffset – metoda](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 – rozhraní](icordebugcode3-interface.md)
