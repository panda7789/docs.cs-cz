---
title: "ICorDebugSymbolProvider2::GetGenericDictionaryInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63126e4f34ea7ea7dee7dd0b9cae0dc0fea57ed9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>ICorDebugSymbolProvider2::GetGenericDictionaryInfo – metoda
Načte mapu obecné slovníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppMemoryBuffer`  
 [out] Ukazatel na adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt obsahující obecné slovník mapy. Další informace naleznete v části Poznámky.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
 Mapy se skládá ze dvou částech nejvyšší úrovně:  
  
-   A [directory](#Directory) obsahující všechny slovníků zahrnuté v této mapě relativní virtuální adresy (RVA).  
  
-   Zarovnaný bajtů [haldy](#Heap) obsahující informace o vytvoření instance objektu. Spustí ihned po poslední položky adresáře.  
  
<a name="Directory"></a>   
## <a name="the-directory"></a>Adresář  
 Každá položka v adresáři odkazuje na posun v haldě; To znamená je posun, který je relativní vzhledem ke spuštění haldě. Hodnota jednotlivých položek není nutně jedinečný; je možné pro více položek adresáře tak, aby odkazoval na stejné posun v haldě.  
  
 Část directory mapy obecné slovník má následující strukturu:  
  
-   První 4 bajty obsahuje počet položky slovníku (to znamená, počet relativní virtuální adresy ve slovníku). Budeme odkazovat na tuto hodnotu jako *N*. Pokud je nastavena rozšířené, jsou položky seřazené podle relativní virtuální adresy ve vzestupném pořadí.  
  
-   *N* podle položek adresáře. Každý záznam se skládá z 8 bajtů v dva segmenty 4bajtový:  
  
    -   Bajty 0 až 3: RVA; relativní virtuální adresy slovníku.  
  
    -   Bajty 4-7: posun; posun vzhledem k začátku haldě.  
  
<a name="Heap"></a>   
## <a name="the-heap"></a>Halda  
 Velikost haldy pro mocninou čtečku datového proudu odečtením délka datového proudu z adresáře velikost + 4. Jinými slovy:  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 kde je velikost directory `N * 8`.  
  
 Formát pro každou položku informace o vytváření instancí v haldě je:  
  
-   Délka této položky informace o vytváření instancí v bajtech v komprimované ECMA metadata formátu. Hodnota vyloučí tyto informace délka.  
  
-   Počet typů obecné konkretizaci nebo *T*, ve formátu metadat komprimované ECMA.  
  
-   *T* typy, každý určený ve formátu podpis ECMA typu.  
  
 Zahrnutí délka pro každý prvek haldy umožňuje jednoduché řazení sekci adresáře bez ovlivnění haldě.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugSymbolProvider2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
