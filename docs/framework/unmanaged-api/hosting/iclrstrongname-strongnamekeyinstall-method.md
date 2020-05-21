---
title: ICLRStrongName::StrongNameKeyInstall – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
ms.openlocfilehash: e0c60d6e74c48531a223f6dbb35125b5a2017cbb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763035"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a>ICLRStrongName::StrongNameKeyInstall – metoda
Importuje pár veřejného a privátního klíče do kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszKeyContainer`  
 pro Název kontejneru klíčů. `wszKeyContainer`musí být neprázdný řetězec.  
  
 `pbKeyBlob`  
 pro Dvojice binárních klíčů.  
  
 `cbKeyBlob`  
 pro Velikost v bajtech `pbKeyBlob` .  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 K odstranění kontejneru klíčů použijte metodu [ICLRStrongName:: StrongNameKeyDelete –](iclrstrongname-strongnamekeydelete-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameKeyDelete – metoda](iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)
