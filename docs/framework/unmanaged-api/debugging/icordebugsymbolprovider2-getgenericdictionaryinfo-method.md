---
title: ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5696dc8fcf4b5c84e12ca60f93679f7b67d5f7e9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476318"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method
Načte mapování generický slovník.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppMemoryBuffer`  
 [out] Ukazatel na adresu [icordebugmemorybuffer –](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje generický slovník mapování. Další informace naleznete v části Poznámky.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
 Mapa se skládá ze dvou částí nejvyšší úrovně:  
  
-   A [directory](#Directory) relativních virtuálních adres (RVA) obsahující všechny adresářů, které jsou součástí této mapy.  
  
-   Zarovnané bajtové [haldy](#Heap) , který obsahuje informace o vytvoření instance objektu. Začne okamžitě po poslední položky adresáře.  
  
<a name="Directory"></a>   
## <a name="the-directory"></a>Adresář  
 Každá položka v adresáři odkazuje na posun uvnitř haldy; To znamená je posunu, který je relativní vzhledem k začátku haldy. Hodnota jednotlivých položek, které není nutně jedinečné; je možné pro více položek adresáře tak, aby odkazoval na stejný posun v haldě.  
  
 Část adresáře generický slovník mapování má následující strukturu:  
  
-   První 4 bajty obsahuje počet položek slovníku (to znamená, že počet relativních virtuálních adres ve slovníku). Společnost Microsoft bude odkazovat na tuto hodnotu jako *N*. Pokud je vysoký bit nastaven, jsou položky seřazené podle relativní virtuální adresa ve vzestupném pořadí.  
  
-   *N* postupujte podle položek adresáře. Každý záznam se skládá z 8 bajtů v dva segmenty 4bajtovou:  
  
    -   Bajty 0 až 3: ADRESA RVA; relativní virtuální adresu do slovníku.  
  
    -   Bajty 4 – 7: Posun; posun vzhledem k začátku haldy.  
  
<a name="Heap"></a>   
## <a name="the-heap"></a>Haldy  
 Velikost haldy můžete vypočítat čtečka stream tak, že se délka datového proudu z velikosti adresářů a 4. Jinými slovy:  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 kde je velikost adresáře `N * 8`.  
  
 Formát pro každou položku informace o vytvoření instance na haldě je:  
  
-   Délka této položky informace o vytvoření instance v bajtech ve formátu metadat komprimované ECMA. Hodnota nezahrnuje informace o délce.  
  
-   Počet typů obecné vytváření instancí, nebo *T*, v komprimované formát metadat ECMA.  
  
-   *T* typy, znázorněny ve formátu podpisu typu ECMA.  
  
 Zahrnutí délka pro každý prvek haldy umožňuje jednoduché řazení sekci adresáře aniž by to ovlivnilo haldy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugSymbolProvider2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
