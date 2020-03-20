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
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177667"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod – metoda
Vytvoří definici metody nebo globální funkce se zadaným podpisem a vrátí token této definici metody.  
  
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
 [v] Token `mdTypedef` nadřazené třídy nebo nadřazeného rozhraní metody. Pokud `td` `mdTokenNil`definujete globální funkci, nastavte na .  
  
 `szName`  
 [v] Název člena v unicode.  
  
 `dwMethodFlags`  
 [v] Hodnota [cormethodattr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) výčtu, který určuje atributy metody nebo globální funkce.  
  
 `pvSigBlob`  
 [v] Podpis metody. Podpis je trvalý podle dodaných. Pokud potřebujete zadat další informace pro všechny parametry, použijte metodu [IMetaDataEmit::SetParamProps.](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)  
  
 `cbSigBlob`  
 [v] Počet bajtů v `pvSigBlob`.  
  
 `ulCodeRVA`  
 [v] Adresa kódu.  
  
 `dwImplFlags`  
 [v] Hodnota [cormethodimpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčtu, který určuje funkce implementace metody.  
  
 `pmd`  
 [out] Člen token.  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní API metadat zaručuje zachovat metody ve stejném pořadí jako volající vydává pro dané ohraničující `td` třídy nebo rozhraní, která je určena v parametru.  
  
 Další informace týkající `DefineMethod` se použití a konkrétní nastavení parametrů jsou uvedeny níže.  
  
## <a name="slots-in-the-v-table"></a>Sloty ve V-tabulce  
 Runtime používá definice metod k nastavení slotů v-table. V případě, že je třeba přeskočit jeden nebo více slotů, například zachovat paritu s rozvržením rozhraní COM, je definována fiktivní metoda, která zabere patici nebo patky ve v-tabulce; nastavte `dwMethodFlags` hodnotu `mdRTSpecialName` výčtu [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) a zadejte název jako:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 where *SequenceNumber* je pořadové číslo metody a *CountOfSlots* je počet slotů přeskočit v tabulce. Pokud *CountOfSlots* je vynechán, 1 se předpokládá. Tyto fiktivní metody nelze volat ze spravovaného ani nespravovaného kódu a jakýkoli pokus o jejich volání ze spravovaného nebo nespravovaného kódu generuje výjimku. Jejich jediným účelem je zabírají místo v tabulce, která generuje za běhu pro integraci com.  
  
## <a name="duplicate-methods"></a>Duplicitní metody  
 Neměli byste definovat duplicitní metody. To znamená, že `DefineMethod` byste neměli volat s `td` `wzName`duplicitní `pvSig` sadou hodnot v , a parametry. (Tyto tři parametry společně jednoznačně definují metodu.). Můžete však použít duplicitní trojitý za předpokladu, že pro `mdPrivateScope` jednu `dwMethodFlags` z definic metody nastavíte bit v parametru. (Bit `mdPrivateScope` znamená, že kompilátor nebude vyzařovat odkaz na tuto definici metody.)  
  
## <a name="method-implementation-information"></a>Informace o implementaci metody  
 Informace o implementaci metody často není známo v době, kdy je deklarována metoda. Proto není nutné předat hodnoty v `ulCodeRVA` `dwImplFlags` parametry a `DefineMethod`při volání . Hodnoty mohou být dodány později prostřednictvím [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) nebo [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), podle potřeby.  
  
 V některých situacích, jako je například vyvolání platformy (PInvoke) nebo `ulCodeRVA` com interop scénáře, tělo metody nebude zadána a by měla být nastavena na nulu. V těchto situacích metoda by neměla být označena jako abstraktní, protože za běhu vyhledá implementaci.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definování metody pro Vyvolání PInvoke  
 Pro každou nespravovanou funkci, která má být volána prostřednictvím PInvoke, musíte definovat spravovanou metodu, která představuje cílovou nespravovanou funkci. Chcete-li definovat spravovanou metodu, použijte `DefineMethod` s některými parametry nastavenými na určité hodnoty v závislosti na způsobu, jakým se používá PInvoke:  
  
- True PInvoke - zahrnuje vyvolání externí nespravované metody, která je umístěna v nespravované dll.  
  
- Místní PInvoke - zahrnuje vyvolání nativní nespravované metody, která je vložena do aktuálního spravovaného modulu.  
  
 Nastavení parametrů jsou uvedena v následující tabulce.  
  
|Parametr|Hodnoty pro true PInvoke|Hodnoty pro místní PInvoke|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Nastavit `mdStatic`; jasné `mdSynchronized` `mdAbstract`a .|  
|`pvSigBlob`|Platný podpis metody CLR (COMMON Language runtime) s parametry, které jsou platnými spravovanými typy.|Platný podpis metody CLR s parametry, které jsou platné spravované typy.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Nastavit `miCil` `miManaged`a .|Nastavit `miNative` `miUnmanaged`a .|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
