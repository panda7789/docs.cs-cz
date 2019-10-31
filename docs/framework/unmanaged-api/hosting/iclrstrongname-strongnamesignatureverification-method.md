---
title: ICLRStrongName::StrongNameSignatureVerification – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
ms.openlocfilehash: 6b473466aefc06dc83526e65f8ee9e37703ba9e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134955"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a>ICLRStrongName::StrongNameSignatureVerification – metoda
Získá hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu, který je ověřen podle zadaných příznaků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 pro Cesta k přenositelnému spustitelnému souboru (. dll nebo. exe) pro sestavení, které se má ověřit  
  
 `dwInFlags`  
 pro Příznaky pro změnu chování ověřování. Podporovány jsou následující hodnoty:  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) – vynutí ověření i v případě, že je nutné přepsat nastavení registru.  
  
- `SN_INFLAG_INSTALL` (0x00000002) – určuje, že se jedná o první ověření manifestu.  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) – určuje, že mezipaměť bude umožňovat přístup pouze uživatelům, kteří mají oprávnění správce.  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) – určuje, zda bude sestavení přístupné pouze pro aktuálního uživatele.  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) – určuje, že mezipaměť nebude poskytovat žádné záruky omezení přístupu.  
  
- `SN_INFLAG_RUNTIME` (0x80000000) – vyhrazeno pro interní ladění.  
  
 `pdwOutFlags`  
 mimo Příznaky označující, zda byl ověřen podpis silného názvu. Je podporována následující hodnota:  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) – Tato hodnota je nastavena na hodnotu `false` a určí, že ověření proběhlo úspěšně z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureVerificationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
