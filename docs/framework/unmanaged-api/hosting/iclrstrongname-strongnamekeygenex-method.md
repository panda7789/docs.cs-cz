---
title: ICLRStrongName::StrongNameKeyGenEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: fb18b7b5ac73a1f270af6fae95a23e04b17ca5f1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763069"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a>ICLRStrongName::StrongNameKeyGenEx – metoda
Vygeneruje nový pár veřejného a privátního klíče se zadanou velikostí klíče pro použití silného názvu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
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
  
 `dwKeySize`  
 pro Požadovaná velikost klíče v bitech.  
  
 `ppbKeyBlob`  
 mimo Vrácený pár veřejného a privátního klíče.  
  
 `pcbKeyBlob`  
 mimo Velikost v bajtech `ppbKeyBlob` .  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 .NET Framework verze 1,0 a 1,1 vyžadují `dwKeySize` pro podepsání sestavení silným názvem 1024 bitů. verze 2,0 přidá podporu 2048 pro 64bitové klíče.  
  
 Po načtení klíče byste měli zavolat metodu [ICLRStrongName:: StrongNameFreeBuffer –](iclrstrongname-strongnamefreebuffer-method.md) pro uvolnění přidělené paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameKeyGen – metoda](iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)
