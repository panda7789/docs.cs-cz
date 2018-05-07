---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60dbb8d8461015c791a70d6c2617b1c81e5ba17f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a>ICLRStrongName::StrongNameSignatureVerificationFromImage – metoda
Ověřuje, že je sestavení, které už je namapovaný na paměť pro přidružené veřejný klíč platný.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbBase`  
 [v] Relativní virtuální adresa manifest namapované sestavení.  
  
 `dwLength`  
 [v] Velikost v bajtech, namapované bitové kopie.  
  
 `dwInFlags`  
 [v] Příznaky, které ovlivňují chování ověření. Podporovány jsou následující hodnoty:  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001) - vynutí ověření i v případě, že je nutné přepsat nastavení registru.  
  
-   `SN_INFLAG_INSTALL` (0x00000002) - určuje, že se jedná o první ověření provést na tuto bitovou kopii.  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004). - Určuje, že mezipaměť povolí přístup pouze uživatelům, kteří mají oprávnění správce.  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008) - určuje, že sestavení budou přístupné pouze pro aktuálního uživatele.  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010) - určuje, že mezipaměti bude poskytovat žádné záruky omezení přístupu.  
  
-   `SN_INFLAG_RUNTIME` (0x80000000) - vyhrazená pro interní ladění.  
  
 `pdwOutFlags`  
 [out] Příznak pro další výstupní informace. Je podporován následující hodnotu:  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) – Tato hodnota nastavena na `false` k určení, že ověření proběhlo úspěšně z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
