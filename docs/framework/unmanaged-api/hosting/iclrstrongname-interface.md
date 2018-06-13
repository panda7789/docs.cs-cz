---
title: ICLRStrongName – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRStrongName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName
helpviewer_keywords:
- ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92ae4c2f4a6fb126f5d86cee216e5b2bb6170e66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436108"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName – rozhraní
Poskytuje základní globální statické funkce pro podepisování sestavení se silnými názvy. Všechny `ICLRStrongName` metody vrací standardní hodnoty HRESULT COM.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetHashFromAssemblyFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|Získá hodnotu hash souboru zadaného sestavení pomocí zadaný algoritmus hash.|  
|[GetHashFromAssemblyFileW – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|Získá hodnotu hash souboru sestavení, který je zadán jako řetězec znaků Unicode, pomocí zadaný algoritmus hash.|  
|[GetHashFromBlob – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|Získá hodnotu hash sestavení na adrese zadaná paměťová, pomocí zadaný algoritmus hash.|  
|[GetHashFromFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|Generuje součet hash přes obsah zadaného souboru.|  
|[GetHashFromFileW – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Generuje součet hash přes obsah soubor určený touto řetězec znaků Unicode.|  
|[GetHashFromHandle – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|Generuje součet hash přes obsah souboru s popisovačem zadaný soubor, použití zadaný algoritmus hash.|  
|[StrongNameCompareAssemblies – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|Určuje, zda dva sestavení liší pouze jejich podpisy silným názvem.|  
|[StrongNameFreeBuffer – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Uvolní paměť, který byl přidělen s předchozí volání metody silným názvem, jako [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), nebo [strongnamesignaturegeneration – ](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|Vyplní zadanou vyrovnávací paměť binární reprezentace spustitelný soubor na zadané adrese.|  
|[StrongNameGetBlobFromImage – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|Získá binární reprezentace sestavení image na adrese zadaná paměťová.|  
|[StrongNameGetPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|Získá veřejný klíč z páru soukromého a veřejného klíče.|  
|[StrongNameHashSize – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash, pomocí zadaný algoritmus hash.|  
|[StrongNameKeyDelete – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|Odstraní zadaný kontejner klíčů.|  
|[StrongNameKeyGen – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|Vytvoří nový pár veřejného a privátního klíče pro silné jméno použití.|  
|[StrongNameKeyGenEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|Generuje nový pár veřejného a privátního klíče pomocí zadané velikost klíče pro použití silným názvem.|  
|[StrongNameKeyInstall – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|Importuje pár veřejného a privátního klíče do kontejneru.|  
|[StrongNameSignatureGeneration – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|Podpis silného názvu generuje pro zadané sestavení.|  
|[StrongNameSignatureGenerationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|Generuje pro zadané sestavení, podle zadaného příznaky podpis silného názvu.|  
|[StrongNameSignatureSize – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|Vrátí velikost podpis silného názvu.|  
|[StrongNameSignatureVerification – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|Získá hodnotu označující, zda manifest sestavení v zadaná cesta obsahuje podpis silného názvu, který bude ověřen podle zadaného příznaky.|  
|[StrongNameSignatureVerificationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|Získá hodnotu označující, zda manifest sestavení v zadaná cesta obsahuje podpis silného názvu.|  
|[StrongNameSignatureVerificationFromImage – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Ověřuje, že je sestavení, které už je namapovaný na paměť pro přidružené veřejný klíč platný.|  
|[StrongNameTokenFromAssembly – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|Vytvoří token silným názvem ze zadaného souboru sestavení.|  
|[StrongNameTokenFromAssemblyEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|Vytvoří token silným názvem ze zadaného souboru sestavení a vrátí veřejný klíč.|  
|[StrongNameTokenFromPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|Získá token představující veřejný klíč.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete získat instanci `ICLRStrongName` voláním [iclrruntimeinfo::getinterface –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metoda pomocí `CLSID_CLRStrongName` a `IID_ICLRStrongName` jako parametry.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
