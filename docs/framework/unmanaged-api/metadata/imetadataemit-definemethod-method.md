---
title: IMetaDataEmit::DefineMethod – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: c46b075341742aac605537a08b762b3cf47ef35b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431815"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod – metoda
Vytvoří definici metody nebo globální funkce se zadaným podpisem a vrátí do této definice metody token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 pro Token `mdTypedef` nadřazené třídy nebo nadřazeného rozhraní metody Pokud definujete globální funkci, nastavte `td` na `mdTokenNil`.  
  
 `szName`  
 pro Název člena v kódování Unicode.  
  
 `dwMethodFlags`  
 pro Hodnota výčtu [CorMethodAttr –](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) , která určuje atributy metody nebo globální funkce.  
  
 `pvSigBlob`  
 pro Signatura metody. Signatura je trvalá jako dodaná. Pokud potřebujete zadat další informace pro všechny parametry, použijte metodu [IMetaDataEmit:: setparamprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) .  
  
 `cbSigBlob`  
 pro Počet bajtů v `pvSigBlob`.  
  
 `ulCodeRVA`  
 pro Adresa kódu.  
  
 `dwImplFlags`  
 pro Hodnota výčtu [CorMethodImpl –](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) , která určuje implementační funkce metody.  
  
 `pmd`  
 mimo Token členu.  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní API metadat zaručuje uchování metod ve stejném pořadí, ve kterém je volající vygeneruje pro danou ohraničující třídu nebo rozhraní, které jsou zadány v parametru `td`.  
  
 Další informace týkající se použití `DefineMethod` a konkrétního nastavení parametrů jsou uvedeny níže.  
  
## <a name="slots-in-the-v-table"></a>Sloty v tabulce v  
 Modul runtime používá k nastavení slotů v tabulce definice metod. V případě, kdy je třeba jeden nebo více slotů přeskočit, například pro zachování parity pomocí rozložení rozhraní modelu COM, je definována fiktivní metoda, která zabere slot nebo sloty v tabulce v. Nastavte `dwMethodFlags` na `mdRTSpecialName` hodnotu výčtu [CorMethodAttr –](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) a zadejte název jako:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 kde *SequenceNumber* je pořadové číslo metody a *CountOfSlots* je počet slotů, které se mají přeskočit v tabulce v. Pokud je hodnota *CountOfSlots* vynechána, předpokládá se hodnota 1. Tyto fiktivní metody nelze volat z spravovaného nebo nespravovaného kódu a jakékoli pokusy o jejich volání z spravovaného nebo nespravovaného kódu generují výjimku. Jediným účelem je zabírat místo v tabulce, kterou modul runtime generuje pro integraci modelu COM.  
  
## <a name="duplicate-methods"></a>Duplicitní metody  
 Neměli byste definovat duplicitní metody. To znamená, že byste neměli volat `DefineMethod` s duplicitní sadou hodnot v parametrech `td`, `wzName`a `pvSig`. (Tyto tři parametry společně definují jedinečnou metodu.). Můžete však použít duplicitní trojnásobný předpoklad, že pro jednu z definic metod nastavíte bit `mdPrivateScope` v parametru `dwMethodFlags`. (`mdPrivateScope` bit znamená, že kompilátor negeneruje odkaz na tuto definici metody.)  
  
## <a name="method-implementation-information"></a>Informace o implementaci metody  
 Informace o implementaci metody často nejsou známy v době, kdy je metoda deklarována. Proto není nutné předávat hodnoty do `ulCodeRVA` a `dwImplFlags` parametrů při volání `DefineMethod`. Hodnoty lze zadat později prostřednictvím [IMetaDataEmit:: SetMethodImplFlags –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) nebo [IMetaDataEmit:: setrva –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), podle potřeby.  
  
 V některých situacích, například ve scénářích volání platformy (PInvoke) nebo zprostředkovateli komunikace s objekty COM, nebude tělo metody dodáno a `ulCodeRVA` by měl být nastaven na hodnotu nula. V těchto situacích by neměla být metoda označena jako abstraktní, protože modul runtime vyhledá implementaci.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definování metody pro PInvoke  
 Pro každou nespravovanou funkci, která má být volána prostřednictvím PInvoke, je nutné definovat spravovanou metodu, která představuje cílovou nespravovanou funkci. Pro definování spravované metody použijte `DefineMethod` s některými parametry nastavenými na určité hodnoty, v závislosti na způsobu použití PInvoke:  
  
- True PInvoke – zahrnuje vyvolání externí nespravované metody, která se nachází v nespravované knihovně DLL.  
  
- Místní PInvoke – zahrnuje vyvolání nativní nespravované metody, která je vložena do aktuálního spravovaného modulu.  
  
 Nastavení parametru jsou uvedena v následující tabulce.  
  
|Parametr|Hodnoty pro True PInvoke|Hodnoty pro místní PInvoke|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Nastavit `mdStatic`; zrušte zaškrtnutí `mdSynchronized` a `mdAbstract`.|  
|`pvSigBlob`|Platný podpis metody modulu CLR (Common Language Runtime) s parametry, které jsou platnými spravovanými typy.|Platná signatura metody CLR s parametry, které jsou platnými spravovanými typy.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Nastavte `miCil` a `miManaged`.|Nastavte `miNative` a `miUnmanaged`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
