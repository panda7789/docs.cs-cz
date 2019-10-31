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
ms.openlocfilehash: 4f774915cdbb12b13fa334db37c8e0fa2a7e5829
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135133"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName – rozhraní
Poskytuje základní globální statické funkce pro podepisování sestavení se silnými názvy. Všechny metody `ICLRStrongName` vrací standardní model COM HRESULTs.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetHashFromAssemblyFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|Načte hodnotu hash zadaného souboru sestavení pomocí zadaného algoritmu hash.|  
|[GetHashFromAssemblyFileW – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|Načte hodnotu hash souboru sestavení zadaného jako řetězec Unicode pomocí zadaného algoritmu hash.|  
|[GetHashFromBlob – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|Načte hodnotu hash sestavení v zadané adrese paměti pomocí zadaného algoritmu hash.|  
|[GetHashFromFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|Vygeneruje hodnotu hash přes obsah zadaného souboru.|  
|[GetHashFromFileW – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode.|  
|[GetHashFromHandle – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|Vygeneruje hodnotu hash přes obsah souboru se zadaným popisovačem souboru pomocí zadaného algoritmu hash.|  
|[StrongNameCompareAssemblies – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|Určuje, zda se dvě sestavení liší pouze signaturami silného názvu.|  
|[StrongNameFreeBuffer – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Uvolní paměť, která byla přidělena předchozímu volání metody silného názvu, jako je například [StrongNameGetPublicKey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)nebo [StrongNameSignatureGeneration –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|Vyplní zadanou vyrovnávací paměť binární reprezentací spustitelného souboru na zadané adrese.|  
|[StrongNameGetBlobFromImage – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|Načte binární reprezentaci image sestavení v zadané adrese paměti.|  
|[StrongNameGetPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|Získá veřejný klíč z páru privátních a veřejných klíčů.|  
|[StrongNameHashSize – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí zadaného algoritmu hash.|  
|[StrongNameKeyDelete – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|Odstraní zadaný kontejner klíčů.|  
|[StrongNameKeyGen – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|Vytvoří nový pár veřejného a privátního klíče pro použití se silným názvem.|  
|[StrongNameKeyGenEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|Vygeneruje nový pár veřejného a privátního klíče se zadanou velikostí klíče pro použití se silným názvem.|  
|[StrongNameKeyInstall – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|Importuje pár veřejného a privátního klíče do kontejneru.|  
|[StrongNameSignatureGeneration – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|Vygeneruje podpis silného názvu pro zadané sestavení.|  
|[StrongNameSignatureGenerationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|Vygeneruje podpis silného názvu pro zadané sestavení na základě zadaných příznaků.|  
|[StrongNameSignatureSize – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|Vrátí velikost podpisu silného názvu.|  
|[StrongNameSignatureVerification – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|Získá hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu, který je ověřen podle zadaných příznaků.|  
|[StrongNameSignatureVerificationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|Načte hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu.|  
|[StrongNameSignatureVerificationFromImage – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Ověřuje, že sestavení, které již bylo namapováno do paměti, je platné pro přidružený veřejný klíč.|  
|[StrongNameTokenFromAssembly – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|Vytvoří ze zadaného souboru sestavení token se silným názvem.|  
|[StrongNameTokenFromAssemblyEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč.|  
|[StrongNameTokenFromPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|Získá token představující veřejný klíč.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete získat instanci `ICLRStrongName` voláním metody [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) pomocí `CLSID_CLRStrongName` a `IID_ICLRStrongName` jako parametrů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
