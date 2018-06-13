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
ms.openlocfilehash: 5a406e945a67352bc7f126b40bd56f4a11dd693b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419540"
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges – metoda
Změny v metadatech a změny v kódu Microsoft (MSIL intermediate language) se vztahuje na běžící proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbMetadata`  
 [v] Velikost v bajtech, rozdílů metadat.  
  
 `pbMetadata`  
 [v] Vyrovnávací paměti, který obsahuje delta metadata. Vrátí adresu vyrovnávací paměti [imetadataemit2::savedeltatomemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) metoda.  
  
 Vzhledem k začátku MSIL kódu by měla být relativní virtuální adresy (RVAs) v metadatech.  
  
 `cbIL`  
 [v] Velikost v bajtech, rozdílové MSIL kódu.  
  
 `pbIL`  
 [v] Vyrovnávací paměť, která obsahuje aktualizované MSIL kód.  
  
## <a name="remarks"></a>Poznámky  
 `pbMetadata` Parametr je ve formátu metadat speciální delta (jako výstupní podle [imetadataemit2::savedeltatomemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata` přebírá předchozí metadat jako základ a popisuje jednotlivé změny, které chcete použít pro tento základní.  
  
 Naopak `pbIL[`] parametr obsahuje nové MSIL pro metodu aktualizované a měl by úplně nahradit předchozí MSIL pro danou metodu  
  
 Když rozdíl MSIL a metadat byla vytvořena v paměti ladicím programu, ladicí program volá `ApplyChanges` a odešlete změny do modulu common language runtime (CLR). Modul runtime aktualizací jeho tabulky metadat, umístí nové MSIL do procesu a nastaví nové MSIL kompilací za běhu (JIT). Při použití změny by měly volat ladicího programu [imetadataemit2::resetenclog –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) připravit pro další úpravy relace. Ladicí program může pak pokračovat v procesu.  
  
 Vždy, když ladicí program volá `ApplyChanges` na modul, který obsahuje metadata rozdílů, by také zavolat [imetadataemit::applyeditandcontinue –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) s metadaty rozdílů na všech jeho kopie metadata tohoto modulu s výjimkou kopie použít pro vydávání změny. Pokud se kopie metadat nějakým způsobem stane se na synchronizaci s metadaty skutečné ladicího programu můžete kdykoli throw rychle tuto kopii nebo požádejte o novou kopii.  
  
 Pokud `ApplyChanges` metoda selže, ladění relace je v neplatném stavu a musí být restartován.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
