---
title: ICLRStrongName::StrongNameKeyGen – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: db5c0dbe57607c7a3bf8b97cee734415aa934336
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763082"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a>ICLRStrongName::StrongNameKeyGen – metoda
Vytvoří nový pár veřejného a privátního klíče pro použití se silným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszKeyContainer`  
 pro Požadovaný název kontejneru klíčů. `wszKeyContainer`aby bylo možné vygenerovat dočasný název, musí být buď neprázdný řetězec, nebo hodnota null.  
  
 `dwFlags`  
 pro Hodnota, která určuje, zda má být klíč ponechán zaregistrovaný. Podporovány jsou následující hodnoty:  
  
- 0x00000000 – používá se `wszKeyContainer` , pokud je null k vygenerování dočasného názvu kontejneru klíčů.  
  
- 0x00000001 ( `SN_LEAVE_KEY` ) – určuje, že klíč by měl zůstat registrovaný.  
  
 `ppbKeyBlob`  
 mimo Vrácený pár veřejného a privátního klíče.  
  
 `pcbKeyBlob`  
 mimo Velikost v bajtech `ppbKeyBlob` .  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Metoda [ICLRStrongName:: StrongNameKeyGen –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) vytvoří 1024 bitový klíč. Po načtení klíče byste měli zavolat metodu [ICLRStrongName:: StrongNameFreeBuffer –](iclrstrongname-strongnamefreebuffer-method.md) pro uvolnění přidělené paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameKeyGenEx – metoda](iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)
