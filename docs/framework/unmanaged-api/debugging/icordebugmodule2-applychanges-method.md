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
ms.openlocfilehash: c324019e1e62701f4f2aaba1c00948b292ba6847
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127915"
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
 pro Vyrovnávací paměť obsahující rozdílová metadata Adresa vyrovnávací paměti se vrátí z metody [IMetaDataEmit2:: SaveDeltaToMemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) .  
  
 Relativní virtuální adresy (RVA) v metadatech by měly být relativní vzhledem ke spuštění kódu jazyka MSIL.  
  
 `cbIL`  
 pro Velikost rozdílového kódu jazyka MSIL v bajtech.  
  
 `pbIL`  
 pro Vyrovnávací paměť obsahující aktualizovaný kód jazyka MSIL.  
  
## <a name="remarks"></a>Poznámky  
 Parametr `pbMetadata` je ve speciálním formátu rozdílové metadat (jako výstup pomocí [IMetaDataEmit2:: SaveDeltaToMemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata` přebírá předchozí metadata jako základní a popisuje jednotlivé změny, které se vztahují k tomuto základu.  
  
 Naproti tomu parametr `pbIL[`] obsahuje nový jazyk MSIL pro aktualizovanou metodu a je určen k úplnému nahrazení předchozího jazyka MSIL pro danou metodu.  
  
 Při vytvoření rozdílového jazyka MSIL a metadat v paměti ladicího programu volá ladicí program `ApplyChanges` k odeslání změn do modulu CLR (Common Language Runtime). Modul runtime aktualizuje své tabulky metadat, umístí nový jazyk MSIL do procesu a nastaví kompilaci JIT (just-in-time) nového jazyka MSIL. Po použití změn by ladicí program měl zavolat [IMetaDataEmit2:: ResetENCLog –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) , aby se připravil k další relaci úprav. Ladicí program může pokračovat v procesu.  
  
 Pokaždé, když ladicí program volá `ApplyChanges` v modulu, který má rozdílová metadata, měla by také volat [IMetaDataEmit:: ApplyEditAndContinue –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) se stejnými rozdílovou metadaty na všech svých kopiích tohoto modulu, s výjimkou kopie použité k vygenerování změn. Pokud se kopie metadat nějakým způsobem nesynchronizuje se skutečnými metadaty, ladicí program může vždycky vyvolat kopírování a získat novou kopii.  
  
 Pokud se metoda `ApplyChanges` nezdařila, relace ladění je v neplatném stavu a je nutné ji restartovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
