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
ms.openlocfilehash: 2dbc6b5ffaa3a381bdd657059a682a3d12dc4cf1
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584263"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod – metoda
Vytvoří definici pro metody nebo globální funkce se zadaným podpisem a vrátí token k definici této metody.  
  
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
 [in] `mdTypedef` Token nadřazené třídu nebo rozhraní nadřazené metody. Nastavte `td` k `mdTokenNil`, pokud definujete globální funkce.  
  
 `szName`  
 [in] Název člena v kódování Unicode.  
  
 `dwMethodFlags`  
 [in] Hodnota [cormethodattr –](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) výčet, který určuje atributy metody nebo globální funkce.  
  
 `pvSigBlob`  
 [in] Podpis metody. Podpis se ukládají jako dodaného. Pokud je třeba zadat další informace o všech parametrů, použijte [imetadataemit::setparamprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) metody.  
  
 `cbSigBlob`  
 [in] Počet bajtů v `pvSigBlob`.  
  
 `ulCodeRVA`  
 [in] Adresa kód.  
  
 `dwImplFlags`  
 [in] Hodnota [cormethodimpl –](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčet, který určuje funkce implementace metody.  
  
 `pmd`  
 [out] Token členu.  
  
## <a name="remarks"></a>Poznámky  
 Zachování metody ve stejném pořadí jako volající vydává je pro danou ohraničující třídu nebo rozhraní, která je určena v zaručuje metadat rozhraní API `td` parametru.  
  
 Další informace týkající se použití `DefineMethod` a konkrétních parametrů nastavení je uvedena níže.  
  
## <a name="slots-in-the-v-table"></a>Sloty v tabulce  
 Modul runtime používá k vytvoření tabulky v sloty definice metod. V případě, kdy jeden nebo více slotů musí být bylo přeskočeno, například tak, aby byly parita s rozložením rozhraní modelu COM, fiktivní metoda je definován tak, aby zabíraly slotu nebo sloty v tabulce. Nastavte `dwMethodFlags` k `mdRTSpecialName` hodnotu [cormethodattr –](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) výčet a zadejte název:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 kde *SequenceNumber* má pořadové číslo metody a *CountOfSlots* je počtu slotů pro přeskočení v tabulce. Pokud *CountOfSlots* je vynechána, předpokládá se 1. Tyto metody fiktivní nejsou volány z spravovaného i nespravovaného kódu a jakýkoliv pokus o volání, od spravovaných nebo nespravovaných kódu, vygeneruje výjimku. Jejich jediným účelem je tak, aby zabíraly místo v tabulce, která generuje modul runtime integrace modelu COM.  
  
## <a name="duplicate-methods"></a>Duplicitní metody  
 Duplicitní metody by neměly definovat. To znamená, že byste neměli volat `DefineMethod` duplicitní sadu hodnot v `td`, `wzName`, a `pvSig` parametry. (Tyto tři parametry dohromady jedinečně definici této metody.). Ale můžete použít duplicitní triple za předpokladu, že pro jednu z definice metod, můžete nastavit `mdPrivateScope` bit ve `dwMethodFlags` parametru. ( `mdPrivateScope` Bit znamená, že kompilátor nebude generovat odkaz na definici této metody.)  
  
## <a name="method-implementation-information"></a>Informace o implementaci – metoda  
 Informace o implementaci metody se často není známý v době, kdy je deklarována jako metodu. Proto není potřeba předat hodnoty `ulCodeRVA` a `dwImplFlags` parametrů při volání metody `DefineMethod`. Hodnoty mohou být poskytnuty později prostřednictvím [imetadataemit::setmethodimplflags –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) nebo [imetadataemit::setrva –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)podle potřeby.  
  
 V některých situacích, jako je například vyvolání platformy (PInvoke) nebo COM interop scénáře, nebude zadán tělo metody, a `ulCodeRVA` musí být nastavena na nulu. V těchto situacích by neměl být označené metodu jako abstraktní, vzhledem k tomu, že modul runtime vyhledá implementace.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definování metody pro volání PInvoke  
 Pro každou nespravovanou funkci volané prostřednictvím PInvoke je nutné definovat spravované metody, která představuje cíl nespravované funkci. Chcete-li definovat spravované metody, použijte `DefineMethod` pomocí některé z parametrů nastavit určité hodnoty v závislosti na způsobu, ve kterém se používá PInvoke:  
  
-   True PInvoke – zahrnuje volání externí nespravované metody, které se nacházejí v nespravovaná knihovna DLL.  
  
-   Místní PInvoke – zahrnuje volání nativního nespravované metody, které jsou součástí aktuální spravovaný modul.  
  
 Nastavení parametrů jsou uvedeny v následující tabulce.  
  
|Parametr|Hodnoty true PInvoke|Hodnoty pro místní PInvoke|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Nastavte `mdStatic`; vymazat `mdSynchronized` a `mdAbstract`.|  
|`pvSigBlob`|Platný common language runtime (CLR) podpis metody s parametry, které jsou platné spravovaných typů.|Neplatný podpis metody CLR s parametry, které jsou platné spravovaných typů.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Nastavte `miCil` a `miManaged`.|Nastavte `miNative` a `miUnmanaged`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** použit jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
