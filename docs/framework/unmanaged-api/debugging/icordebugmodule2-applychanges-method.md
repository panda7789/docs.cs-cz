---
title: ICorDebugModule2::ApplyChanges – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
ms.openlocfilehash: 99824e9a7fd759fb30bfa377156fc28eb934a2b4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212214"
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges – metoda
Aplikuje změny v metadatech a změny v kódu jazyka MSIL (Microsoft Intermediate Language) na běžící proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbMetadata`  
 pro Velikost rozdílových metadat v bajtech.  
  
 `pbMetadata`  
 pro Vyrovnávací paměť obsahující rozdílová metadata Adresa vyrovnávací paměti se vrátí z metody [IMetaDataEmit2:: SaveDeltaToMemory –](../metadata/imetadataemit2-savedeltatomemory-method.md) .  
  
 Relativní virtuální adresy (RVA) v metadatech by měly být relativní vzhledem ke spuštění kódu jazyka MSIL.  
  
 `cbIL`  
 pro Velikost rozdílového kódu jazyka MSIL v bajtech.  
  
 `pbIL`  
 pro Vyrovnávací paměť obsahující aktualizovaný kód jazyka MSIL.  
  
## <a name="remarks"></a>Poznámky  
 `pbMetadata`Parametr je ve speciálním formátu rozdílové metadat (jako výstup pomocí [IMetaDataEmit2:: SaveDeltaToMemory –](../metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata`bere předchozí metadata jako základní a popisuje jednotlivé změny, které se vztahují k tomuto základu.  
  
 Naproti tomu `pbIL[` parametr] obsahuje nový jazyk MSIL pro aktualizovanou metodu a je určen k úplnému nahrazení předchozího jazyka MSIL pro danou metodu.  
  
 Když se rozdílové rozhraní MSIL a metadata v paměti ladicího programu vytvoří, ladicí program zavolá `ApplyChanges` k odeslání změn do modulu CLR (Common Language Runtime). Modul runtime aktualizuje své tabulky metadat, umístí nový jazyk MSIL do procesu a nastaví kompilaci JIT (just-in-time) nového jazyka MSIL. Po použití změn by ladicí program měl zavolat [IMetaDataEmit2:: ResetENCLog –](../metadata/imetadataemit2-resetenclog-method.md) , aby se připravil k další relaci úprav. Ladicí program může pokračovat v procesu.  
  
 Vždy, když ladicí program volá `ApplyChanges` modul, který má rozdílová metadata, by měl také volat [IMetaDataEmit:: ApplyEditAndContinue –](../metadata/imetadataemit-applyeditandcontinue-method.md) se stejnými rozdílová metadata na všech svých kopiích tohoto modulu, s výjimkou kopie použité k vygenerování změn. Pokud se kopie metadat nějakým způsobem nesynchronizuje se skutečnými metadaty, ladicí program může vždycky vyvolat kopírování a získat novou kopii.  
  
 Pokud se `ApplyChanges` Metoda nezdařila, ladicí relace je v neplatném stavu a je nutné ji restartovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
