---
title: StrongNameTokenFromAssembly – funkce
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f88c0feea48ee96745effc36798bb26b4ccbf3cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000360"
---
# <a name="strongnametokenfromassembly-function"></a>StrongNameTokenFromAssembly – funkce
Vytvoří token silného názvu ze zadaného souboru sestavení.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnametokenfromassembly –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Cesta k souboru (PE portable executable) pro sestavení.  
  
 `ppbStrongNameToken`  
 [out] Token vrácený silného názvu.  
  
 `pcbStrongNameToken`  
 [out] Velikost v bajtech, silný název tokenu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Při úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Zkráceným tvarem veřejný klíč je token silného názvu. Token je hodnota hash 64-bit, který je vytvořen z veřejného klíče použitý k podepsání sestavení. Token, který je součástí silného názvu pro sestavení a může číst z metadat sestavení.  
  
 Po vytvoření tokenu, měli byste zavolat [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce přidělená paměť uvolnit.  
  
 Pokud `StrongNameTokenFromAssembly` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v mscoree.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameTokenFromAssembly – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [StrongNameTokenFromAssemblyEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
