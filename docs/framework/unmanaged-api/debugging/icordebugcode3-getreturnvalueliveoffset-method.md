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
ms.openlocfilehash: 7c75db784a404298b86ed42692573a509ea56cf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset – metoda
Pro zadaný korekce IL získá nativní posuny, kde má být umístěn zarážku tak, aby ladicí program můžete získat návratovou hodnotou z funkce.  
  
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
 Korekce IL. Musí být funkce lokality volání nebo volání funkce se nezdaří.  
  
 `bufferSize`  
 Počet bajtů, které jsou k dispozici pro uložení `pOffsets`.  
  
 `pFetched`  
 Ukazatel na počet posuny ve skutečnosti vrátila. Obvykle jeho hodnota je 1, ale jeden instrukce IL je možné namapovat více `CALL` pokyny sestavení.  
  
 `pOffsets`  
 Pole nativní odsazení. Obvykle `pOffsets` obsahuje jeden posun, i když jako jedinou instrukci IL je možné namapovat více mapy do několika `CALL` pokyny sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se používá spolu s [icordebugilframe3::getreturnvalueforiloffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metoda získat návratovou hodnotu metody, která vrátí hodnotu typu odkaz. Předávání IL posun do lokality volání funkce tato metoda vrátí jeden nebo více nativní posun. Ladicí program pak můžete nastavit zarážky na tyto nativní posuny ve funkci. Pokud se ladicí program dotkne některé zarážce, potom můžete předat stejnou korekce IL, který je předán tuto metodu za účelem [icordebugilframe3::getreturnvalueforiloffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metoda získat návratovou hodnotu. Ladicí program by měl zrušte zaškrtnutí všech zarážek, které ji nastavit.  
  
> [!WARNING]
>  `ICorDebugCode3::GetReturnValueLiveOffset` a [icordebugilframe3::getreturnvalueforiloffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metody vám umožňují získat informace o návratovou hodnotu pro odkazové typy pouze. Získávání informací o návratová hodnota z typů hodnot (to znamená, že všechny typy, které jsou odvozeny od <xref:System.ValueType>) není podporován.  
  
 Funkce vrátí hodnotu `HRESULT` hodnoty zobrazené v následující tabulce.  
  
|`HRESULT` Hodnota|Popis|  
|---------------------|-----------------|  
|`S_OK`|Úspěch.|  
|`CORDBG_E_INVALID_OPCODE`|Daný server posunutí IL není volání pokyn nebo funkce vrátí hodnotu `void`.|  
|`CORDBG_E_UNSUPPORTED`|Daný korekce IL je správné volání, ale návratový typ není podporován pro získání návratovou hodnotu.|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset` Metoda je k dispozici pouze na základě x86 a AMD64 systémy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [GetReturnValueForILOffset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)  
 [ICorDebugCode3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
