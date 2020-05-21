---
title: ICLRStrongName::StrongNameTokenFromAssemblyEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
ms.openlocfilehash: e504aa067d51ec62d42f019c3a9e40538e374ea1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762614"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a>ICLRStrongName::StrongNameTokenFromAssemblyEx – metoda
Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč, který token představuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 pro Cesta k přenosnému spustitelnému souboru (PE) pro sestavení.  
  
 `ppbStrongNameToken`  
 mimo Vrácený token silného názvu.  
  
 `pcbStrongNameToken`  
 mimo Velikost tokenu silného názvu v bajtech.  
  
 `ppbPublicKeyBlob`  
 mimo Vrácený veřejný klíč.  
  
 `pcbPublicKeyBlob`  
 mimo Velikost veřejného klíče v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Token silného názvu je zkrácenou formou veřejného klíče. Token je 64 hodnota hash, která je vytvořena z veřejného klíče použitého k podepsání sestavení. Token je součástí silného názvu sestavení a lze ho číst z metadat sestavení.  
  
 Po načtení klíče a vytvoření tokenu byste měli zavolat metodu [ICLRStrongName:: StrongNameFreeBuffer –](iclrstrongname-strongnamefreebuffer-method.md) pro uvolnění přidělené paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameTokenFromAssembly – metoda](iclrstrongname-strongnametokenfromassembly-method.md)
- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)
