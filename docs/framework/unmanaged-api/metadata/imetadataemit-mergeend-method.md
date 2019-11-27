---
title: IMetaDataEmit::MergeEnd – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
ms.openlocfilehash: 34ecfc2f01f22971e135358806adeea632e02f8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448037"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd – metoda

Sloučí se do aktuálního oboru všech oborů metadat určených jedním nebo více předchozími voláními do [IMetaDataEmit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).

## <a name="syntax"></a>Syntaxe

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a>Parametry

Tato metoda nepřijímá žádné parametry.

## <a name="remarks"></a>Poznámky

Tato rutina aktivuje aktuální sloučení metadat všech oborů importu určených předchozími voláními `IMetaDataEmit::Merge`do aktuálního oboru výstupu.

Následující zvláštní podmínky platí pro sloučení:

- Identifikátor verze modulu (identifikátor MVID) se nikdy neimportuje, protože je jedinečný pro metadata v oboru importu.

- Žádné existující vlastnosti pro modul nejsou přepsány.

  Pokud již byly pro aktuální obor nastaveny vlastnosti modulu, nejsou importovány žádné vlastnosti modulu. Pokud však v aktuálním oboru nejsou nastaveny vlastnosti modulu, budou importovány pouze jednou, když jsou nejprve zjištěny. Pokud se tyto vlastnosti modulu vyskytují znovu, jsou duplicitní. Pokud se porovnají hodnoty všech vlastností modulu (kromě identifikátor MVID) a nenašly se žádné duplicity, vyvolá se chyba.

- V případě definic typů (`TypeDef`) nejsou do aktuálního oboru sloučeny žádné duplicity. `TypeDef` objektů jsou kontrolovány duplicitní hodnoty u každého *plně kvalifikovaného názvu objektu* +  + *číslo verze* *GUID* . Pokud existuje shoda na buď názvu nebo identifikátoru GUID, přičemž kterýkoli z dalších dvou prvků je jiný, vyvolá se chyba. V opačném případě, pokud se všechny tři položky shodují, `MergeEnd` provede kontrolu pomocí kurzoru, aby bylo zajištěno, že položky jsou opravdu duplicitní; v takovém případě je vyvolána chyba. Tato kontrolní pozice vypadá nějak takto:

  - Stejné deklarace členů, ke kterým dochází ve stejném pořadí. Členy, které jsou označeny jako `mdPrivateScope` (viz výčet [CorMethodAttr –](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) ), nejsou zahrnuty do této kontroly; jsou speciálně sloučeny.

  - Stejné rozložení třídy.

  To znamená, že objekt `TypeDef` musí být vždy plně a konzistentně definován v každém oboru metadat, ve kterém je deklarována. Pokud jsou jeho implementace členů (pro třídu) rozloženy mezi více kompilačních jednotek, předpokládá se, že úplná definice je přítomna v každém oboru a nikoli přírůstkově k jednotlivým oborům. Například pokud jsou názvy parametrů pro kontrakt relevantní, musí být vygenerovány stejným způsobem do každého oboru; Pokud nejsou relevantní, neměly by být generovány do metadat.

  Výjimkou je, že objekt `TypeDef` může mít přírůstkové členy označené jako `mdPrivateScope`. Při jejich zjištění `MergeEnd` přírůstkově přidá do aktuálního oboru bez ohledu na duplicity. Vzhledem k tomu, že kompilátor rozumí privátnímu oboru, musí být kompilátor zodpovědný za vynucování pravidel.

- Relativní virtuální adresy (RVA) se neimportují ani nesloučí. očekává se, že kompilátor tyto informace znovu vygeneruje.

- Vlastní atributy jsou sloučeny pouze v případě, že je sloučena položka, ke které jsou připojeny. Například vlastní atributy přidružené ke třídě jsou sloučeny při prvním zjištění třídy. Pokud jsou vlastní atributy přidruženy k `TypeDef` nebo `MemberDef`, které jsou specifické pro kompilační jednotku (například časové razítko členu zkompiluje), nejsou sloučeny a jsou až do kompilátoru pro odebrání nebo aktualizaci takových metadat.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlavička:** Cor. h

**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.

**Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
