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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53fd830cdefda58d40f96f8662a80d1888d963dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod – metoda
Vytvoří definici metody nebo globální funkce zadaný podpisem a vrátí token tuto definici metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [v] `mdTypedef` Tokenu nadřazené třídy nebo rozhraní nadřazené metody. Nastavit `td` k `mdTokenNil`v případě, že definujete globální funkce.  
  
 `szName`  
 [v] Název členu v kódování Unicode.  
  
 `dwMethodFlags`  
 [v] Hodnota [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) výčet, který určuje atributy, metoda nebo globální funkce.  
  
 `pvSigBlob`  
 [v] Podpis metody. Podpis je jako trvalý, protože zadaná. Pokud je třeba zadat další informace o všech parametrů, použijte [imetadataemit::setparamprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) metoda.  
  
 `cbSigBlob`  
 [v] Počet bajtů v `pvSigBlob`.  
  
 `ulCodeRVA`  
 [v] Adresa kód.  
  
 `dwImplFlags`  
 [v] Hodnota [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčet, který určuje funkce implementace metody.  
  
 `pmd`  
 [out] Člen token.  
  
## <a name="remarks"></a>Poznámky  
 Metadat rozhraní API zaručuje udržení metody ve stejném pořadí jako volající vysílá je pro danou nadřazených třídy nebo rozhraní, které se určuje v `td` parametr.  
  
 Další informace týkající se použití `DefineMethod` a nastavení konkrétní parametrů je uveden níže.  
  
## <a name="slots-in-the-v-table"></a>Sloty v tabulce V  
 Modul runtime používá metoda definice nastavit sloty tabulky v. V případě, kdy je potřeba jeden nebo více sloty být bylo vynecháno, například tak, aby byly parita s rozložení rozhraní modelu COM, fiktivní je definována metoda tak, aby zaplnily slotu nebo sloty v v tabulce. Nastavte `dwMethodFlags` k `mdRTSpecialName` hodnotu [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) – výčet a zadejte název:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>  
  
 kde *SequenceNumber* má pořadové číslo metody a *CountOfSlots* je počet patic tak, aby přeskočil v tabulce v. Pokud *CountOfSlots* je tento parametr vynechán, předpokládá se 1. Tyto metody fiktivní nejsou možné volat z kódu spravované nebo nespravované a pokusy o jejich volat z kódu spravované nebo nespravované, vygeneruje výjimku. Jejich jediným účelem je tak, aby zaplnily místo v – tabulka, která generuje modulu runtime pro integrace COM.  
  
## <a name="duplicate-methods"></a>Duplicitní metody  
 Duplicitní metody by nemělo definovat. To znamená, by neměl volání `DefineMethod` duplicitní sadu hodnot v `td`, `wzName`, a `pvSig` parametry. (Tyto tři parametry společně jednoznačně definovat metodu.). Ale můžete použít duplicitní triple za předpokladu, že pro jeden z definice metoda nastavíte `mdPrivateScope` bit ve `dwMethodFlags` parametr. ( `mdPrivateScope` Bit znamená, že nebude kompilátor emitování odkaz na definici této metody.)  
  
## <a name="method-implementation-information"></a>Informace o implementaci – metoda  
 Informace o implementaci metoda je často není známý v době, kdy je deklarovaná metodu. Proto není potřeba předejte hodnoty `ulCodeRVA` a `dwImplFlags` parametry při volání metody `DefineMethod`. Hodnoty můžete zadat později prostřednictvím [imetadataemit::setmethodimplflags –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) nebo [imetadataemit::setrva –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)podle potřeby.  
  
 V některých situacích, jako je například vyvolání platformy (PInvoke) nebo scénářů, zprostředkovatele komunikace s objekty COM, nebude zadaný text metoda, a `ulCodeRVA` musí být nastavena na nulu. V těchto situacích by neměl být metodu označené jako abstraktní, protože modul runtime vyhledá implementace.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definování metodu pro služby PInvoke  
 Pro každou nespravované funkci, která se má volat pomocí služby PInvoke je nutné definovat spravované metodu, která představuje funkci cíl nespravované. Definujte metodu spravované pomocí `DefineMethod` pomocí některé z parametrů nastavit určité hodnoty v závislosti na způsobu, ve kterém je používána PInvoke:  
  
-   True PInvoke – zahrnuje volání metody externí nespravované, který se nachází v nespravované knihovny DLL.  
  
-   Místní PInvoke - zahrnuje vyvolání nativní nespravované metodu, která je součástí aktuální spravovaného modulu.  
  
 Nastavení parametrů jsou uvedeny v následující tabulce.  
  
|Parametr|Hodnoty true PInvoke|Hodnoty pro místní služby PInvoke|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Nastavit `mdStatic`; vymazat `mdSynchronized` a `mdAbstract`.|  
|`pvSigBlob`|Platný common language runtime (CLR) metoda podpis s parametry, které jsou platné spravované typy.|Neplatný podpis metody CLR s parametry, které jsou platné spravované typy.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Nastavit `miCil` a `miManaged`.|Nastavit `miNative` a `miUnmanaged`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
