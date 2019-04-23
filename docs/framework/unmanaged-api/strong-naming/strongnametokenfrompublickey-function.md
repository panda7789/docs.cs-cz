---
title: StrongNameTokenFromPublicKey – funkce
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbfd3ae32f4d3033894fdaf6b1bcc880c324e928
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219795"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey – funkce
Získá token představující veřejný klíč. Zkráceným tvarem veřejný klíč je token silného názvu.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 [in] Strukturu typu [publickeyblob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů podpis silného názvu.  
  
 `cbPublicKeyBlob`  
 [in] Velikost v bajtech, z `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [out] Silný název tokenu odpovídající klíči předaný `pbPublicKeyBlob`. Modul common language runtime přiděluje paměť ke vrácení tokenu. Volající musí uvolnit tato paměť pomocí [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce.  
  
 `pcbStrongNameToken`  
 [out] Velikost v bajtech, token vrácený silného názvu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Při úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Token silného názvu je zkrácený tvar veřejný klíč používaný pro úsporu místa při ukládání informací o klíči v metadatech. Konkrétně tokeny silným názvem se používají v odkazy na sestavení odkázat na závislého sestavení.  
  
 Pokud `StrongNameTokenFromPublicKey` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v mscoree.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameTokenFromPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob – struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
