---
title: ICLRStrongName::StrongNameTokenFromPublicKey – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: e61a652072b424d1245518c832f9b0856e0f2021
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762601"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a>ICLRStrongName::StrongNameTokenFromPublicKey – metoda
Získá token, který představuje veřejný klíč. Token silného názvu je zkrácenou formou veřejného klíče.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 pro Struktura typu [PublicKeyBlob –](../strong-naming/publickeyblob-structure.md) , která obsahuje veřejnou část páru klíčů sloužící k vygenerování podpisu silného názvu.  
  
 `cbPublicKeyBlob`  
 pro Velikost v bajtech `pbPublicKeyBlob` .  
  
 `ppbStrongNameToken`  
 mimo Token silného názvu odpovídající předanému klíči `pbPublicKeyBlob` . Modul CLR (Common Language Runtime) přiděluje paměť, ve které má být token vrácen. Volající musí uvolnit tuto paměť pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](iclrstrongname-strongnamefreebuffer-method.md) .  
  
 `pcbStrongNameToken`  
 mimo Velikost vráceného tokenu silného názvu (v bajtech)  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Token silného názvu je zkráceným tvarem veřejného klíče, který se používá k ukládání místa při ukládání klíčových informací v metadatech. Konkrétně tokeny se silným názvem se používají v odkazech na sestavení pro odkazování na závislé sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně Mscoree. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameGetPublicKey – metoda](iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob – struktura](../strong-naming/publickeyblob-structure.md)
- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)
