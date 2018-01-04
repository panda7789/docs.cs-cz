---
title: "StrongNameGetPublicKeyEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2.StrongNameGetPublicKeyEx
api_location: mscoree.dll
api_type: COM
f1_keywords: StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e94498cc8841a95e1918d3f26bd19256793564ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx – metoda
Získá veřejný klíč z páru veřejného a privátního klíče RSA a určuje algoritmus hash a algoritmus podpisu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzKeyContainer`  
 [v] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče. Pokud `pbKeyBlob` má hodnotu null, `szKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V takovém případě `StrongNameGetPublicKeyEx` metoda extrahuje veřejný klíč z tohoto páru klíčů ukládat do kontejneru.  
  
 Pokud `pbKeyBlob` nemá hodnotu null, dvojici klíčů se předpokládá, že mají být obsažena v klíče binární rozsáhlý objekt (binární rozsáhlý OBJEKT).  
  
 Klíče musí být Rivest-Shamir-Adleman 1024 bitů (RSA) podpisových klíčů. Žádné jiné typy klíčů jsou podporovány v tuto chvíli.  
  
 `pbKeyBlob`  
 [v] Ukazatel na pár veřejného a privátního klíče. Tato dvojice je ve formátu vytvořené Win32 `CryptExportKey` funkce. Pokud `pbKeyBlob` je null, kontejner klíčů určeného `szKeyContainer` se předpokládá, že obsahovat dvojici klíčů.  
  
 `cbKeyBlob`  
 [v] Velikost v bajtech z `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [out] Vrácený veřejný klíč objektu BLOB. `ppbPublicKeyBlob` Parametr je přidělena modul common language runtime a vrácen volajícímu. Volající musí uvolnění paměti pomocí [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metoda.  
  
 `pcbPublicKeyBlob`  
 [out] Velikost veřejného klíče vráceného objektu BLOB.  
  
 `uHashAlgId`  
 [v] Algoritmus hash sestavení. Najdete v části poznámky seznam možné hodnoty.  
  
 `uReserved`  
 [v] Vyhrazeno pro budoucí použití; Výchozí hodnota je null.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="remarks"></a>Poznámky  
 Veřejný klíč je součástí [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) struktury.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny sadu přijaté hodnoty pro `uHashAlgId` parametr.  
  
|Název|Hodnota|  
|----------|-----------|  
|Žádné|0|  
|SHA-1|0x8004|  
|ALGORITMUS SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameTokenFromPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [PublicKeyBlob – struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [StrongNameGetPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
