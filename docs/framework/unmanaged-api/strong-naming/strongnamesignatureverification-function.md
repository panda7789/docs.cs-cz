---
title: StrongNameSignatureVerification – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c888c32a0b40d2458a919613e35ca9d1d830c4f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459225"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification – funkce
Získá hodnotu označující, zda manifest sestavení v zadaná cesta obsahuje podpis silného názvu, který bude ověřen podle zadaného příznaky.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnamesignatureverification –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [v] Cesta k přenosné spustitelný (.dll nebo .exe) soubor pro ověření sestavení.  
  
 `dwInFlags`  
 [v] Příznaky chcete změnit chování ověření. Podporovány jsou následující hodnoty:  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001) - vynutí ověření i v případě, že je nutné přepsat nastavení registru.  
  
-   `SN_INFLAG_INSTALL` (0x00000002) - určuje, že to je prvním ověření manifestu.  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004). - Určuje, že mezipaměť povolí přístup pouze uživatelům, kteří mají oprávnění správce.  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008) - určuje, že sestavení budou přístupné pouze pro aktuálního uživatele.  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010) - určuje, že mezipaměti bude poskytovat žádné záruky omezení přístupu.  
  
-   `SN_INFLAG_RUNTIME` (0x80000000) - vyhrazená pro interní ladění.  
  
 `pdwOutFlags`  
 [out] Příznaky udávající, zda se ověřit podpis silného názvu. Je podporován následující hodnotu:  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) – Tato hodnota nastavena na `false` k určení, že ověření proběhlo úspěšně z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud ověření byla úspěšná. v opačném `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameSignatureVerification – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [StrongNameSignatureVerificationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
