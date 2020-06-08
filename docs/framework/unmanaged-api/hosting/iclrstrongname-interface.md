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
ms.openlocfilehash: 0b6efcbe4458977e8e938afabd7ae59171bc065a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501648"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName – rozhraní
Poskytuje základní globální statické funkce pro podepisování sestavení se silnými názvy. Všechny `ICLRStrongName` metody vrací standardní model COM HRESULTs.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[GetHashFromAssemblyFile – metoda](iclrstrongname-gethashfromassemblyfile-method.md)|Načte hodnotu hash zadaného souboru sestavení pomocí zadaného algoritmu hash.|  
|[GetHashFromAssemblyFileW – metoda](iclrstrongname-gethashfromassemblyfilew-method.md)|Načte hodnotu hash souboru sestavení zadaného jako řetězec Unicode pomocí zadaného algoritmu hash.|  
|[GetHashFromBlob – metoda](iclrstrongname-gethashfromblob-method.md)|Načte hodnotu hash sestavení v zadané adrese paměti pomocí zadaného algoritmu hash.|  
|[GetHashFromFile – metoda](iclrstrongname-gethashfromfile-method.md)|Vygeneruje hodnotu hash přes obsah zadaného souboru.|  
|[GetHashFromFileW – metoda](iclrstrongname-gethashfromfilew-method.md)|Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode.|  
|[GetHashFromHandle – metoda](iclrstrongname-gethashfromhandle-method.md)|Vygeneruje hodnotu hash přes obsah souboru se zadaným popisovačem souboru pomocí zadaného algoritmu hash.|  
|[StrongNameCompareAssemblies – metoda](iclrstrongname-strongnamecompareassemblies-method.md)|Určuje, zda se dvě sestavení liší pouze signaturami silného názvu.|  
|[StrongNameFreeBuffer – metoda](iclrstrongname-strongnamefreebuffer-method.md)|Uvolní paměť, která byla přidělena předchozímu volání metody silného názvu, jako je například [StrongNameGetPublicKey –](iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey –](iclrstrongname-strongnametokenfrompublickey-method.md)nebo [StrongNameSignatureGeneration –](iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob – metoda](iclrstrongname-strongnamegetblob-method.md)|Vyplní zadanou vyrovnávací paměť binární reprezentací spustitelného souboru na zadané adrese.|  
|[StrongNameGetBlobFromImage – metoda](iclrstrongname-strongnamegetblobfromimage-method.md)|Načte binární reprezentaci image sestavení v zadané adrese paměti.|  
|[StrongNameGetPublicKey – metoda](iclrstrongname-strongnamegetpublickey-method.md)|Získá veřejný klíč z páru privátních a veřejných klíčů.|  
|[StrongNameHashSize – metoda](iclrstrongname-strongnamehashsize-method.md)|Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí zadaného algoritmu hash.|  
|[StrongNameKeyDelete – metoda](iclrstrongname-strongnamekeydelete-method.md)|Odstraní zadaný kontejner klíčů.|  
|[StrongNameKeyGen – metoda](iclrstrongname-strongnamekeygen-method.md)|Vytvoří nový pár veřejného a privátního klíče pro použití se silným názvem.|  
|[StrongNameKeyGenEx – metoda](iclrstrongname-strongnamekeygenex-method.md)|Vygeneruje nový pár veřejného a privátního klíče se zadanou velikostí klíče pro použití se silným názvem.|  
|[StrongNameKeyInstall – metoda](iclrstrongname-strongnamekeyinstall-method.md)|Importuje pár veřejného a privátního klíče do kontejneru.|  
|[StrongNameSignatureGeneration – metoda](iclrstrongname-strongnamesignaturegeneration-method.md)|Vygeneruje podpis silného názvu pro zadané sestavení.|  
|[StrongNameSignatureGenerationEx – metoda](iclrstrongname-strongnamesignaturegenerationex-method.md)|Vygeneruje podpis silného názvu pro zadané sestavení na základě zadaných příznaků.|  
|[StrongNameSignatureSize – metoda](iclrstrongname-strongnamesignaturesize-method.md)|Vrátí velikost podpisu silného názvu.|  
|[StrongNameSignatureVerification – metoda](iclrstrongname-strongnamesignatureverification-method.md)|Získá hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu, který je ověřen podle zadaných příznaků.|  
|[StrongNameSignatureVerificationEx – metoda](iclrstrongname-strongnamesignatureverificationex-method.md)|Načte hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu.|  
|[StrongNameSignatureVerificationFromImage – metoda](iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Ověřuje, že sestavení, které již bylo namapováno do paměti, je platné pro přidružený veřejný klíč.|  
|[StrongNameTokenFromAssembly – metoda](iclrstrongname-strongnametokenfromassembly-method.md)|Vytvoří ze zadaného souboru sestavení token se silným názvem.|  
|[StrongNameTokenFromAssemblyEx – metoda](iclrstrongname-strongnametokenfromassemblyex-method.md)|Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč.|  
|[StrongNameTokenFromPublicKey – metoda](iclrstrongname-strongnametokenfrompublickey-method.md)|Získá token představující veřejný klíč.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete získat instanci `ICLRStrongName` voláním metody [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) pomocí `CLSID_CLRStrongName` `IID_ICLRStrongName` parametrů a jako.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hosting](index.md)
