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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 860b87b09ee487f893a1bba2aaa34292c50ffcb7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764337"
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges – metoda
Změny v metadatech a změny v kódu Microsoft intermediate language (MSIL) se vztahuje na běžící proces.  
  
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
 [in] Velikost v bajtech, rozdílové metadat.  
  
 `pbMetadata`  
 [in] Vyrovnávací paměť, která obsahuje delta metadata. Adresa vyrovnávací paměti je vrácen z [imetadataemit2::savedeltatomemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) metody.  
  
 Relativních virtuálních adres (RVA) v metadatech by měla být relativní vzhledem k začátku kód jazyka MSIL.  
  
 `cbIL`  
 [in] Velikost v bajtech, rozdílových kód jazyka MSIL.  
  
 `pbIL`  
 [in] Vyrovnávací paměť, která obsahuje aktualizovaný kód jazyka MSIL.  
  
## <a name="remarks"></a>Poznámky  
 `pbMetadata` Parametr má formát metadat speciální delta (jako výstupní podle [imetadataemit2::savedeltatomemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata` má předchozí metadat jako základ a popisuje jednotlivé změny se můžou použít k této základní třídě.  
  
 Oproti tomu, `pbIL[`] parametr obsahuje nový jazyk MSIL pro metodu aktualizované a slouží k úplnému nahrazení předchozí MSIL pro metody  
  
 Při rozdílové jazyk MSIL a metadata byly vytvořeny v paměti ladicího programu, ladicí program volá `ApplyChanges` k odeslání změn do common language runtime (CLR). Modul runtime aktualizuje její tabulky metadat, umístí nový jazyk MSIL do procesu a nastaví just-in-time (JIT) kompilaci nového MSIL. Když změny se použily, ladicí program by měly volat [imetadataemit2::resetenclog –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) připravit pro další relaci. Ladicí program může potom pokračujte v procesu.  
  
 Vždy, když ladicí program volá `ApplyChanges` na modul, který má delta metadata, měla by také zavolat [imetadataemit::applyeditandcontinue –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) s na stejná metadata delta ve všech jeho kopie metadat tohoto modulu s výjimkou kopie použít ke generování změny. Pokud kopie metadat nějakým způsobem stane mimo synchronizace skutečné metadata, ladicí program můžete kdykoli se zbavovat tuto kopii nebo získat nové kopie.  
  
 Pokud `ApplyChanges` metoda selže, ladění relace je v neplatném stavu a je nutné restartovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
