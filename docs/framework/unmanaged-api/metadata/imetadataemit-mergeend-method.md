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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 277e7e57ae01128039c3a280158110acde3363a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230002"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd – metoda
Sloučení do aktuální obor oborů metadat zadán jeden nebo více předchozích volání [imetadataemit::merge –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MergeEnd ();  
```  
  
## <a name="parameters"></a>Parametry  
 Tato metoda nemá žádné parametry.  
  
## <a name="remarks"></a>Poznámky  
 Tato rutina spustí skutečné sloučení metadat, všech importovat obory zadané před volání `IMetaDataEmit::Merge`, do aktuálního oboru výstup.  
  
 Sloučení platí následující zvláštní podmínky:  
  
-   Identifikátor verze modulu (identifikátor MVID) je nikdy importován, protože je jedinečný v oboru importu metadat.  
  
-   Žádné existující vlastnosti celý modul přepsány.  
  
     Pokud již nebyly nastaveny vlastnosti modulu pro aktuální obor, žádné vlastnosti modulu importují. Nicméně pokud nebyly nastaveny vlastnosti modulu v aktuálním oboru, jejich importování pouze jednou, při jejich prvním výskytu. Pokud tyto vlastnosti modulu nedojde k znovu, jsou duplicitní položky. Pokud jsou porovnány hodnoty všech vlastností modulu (s výjimkou identifikátor MVID) a nenajdou žádné duplicity, je vyvolána k chybě.  
  
-   Typ definice (`TypeDef`), žádné duplicitní hodnoty jsou sloučeny do aktuálního oboru. `TypeDef` objekty jsou zkontrolovat duplicitu jednotlivá *objekt plně kvalifikovaný název* + *GUID* + *číslo verze*. Pokud není nalezena shoda pro název nebo identifikátor GUID a některý další dva elementy se liší, je vyvolána k chybě. Jinak, pokud se shodují všechny tři položky `MergeEnd` provede zběžné kontrolu, aby položky jsou ve skutečnosti duplicitní; v opačném případě dojde k chybě. Zběžné Kontrola vyhledá:  
  
    -   Stejný člen prohlášení, ke kterým dochází ve stejném pořadí. Členy, které jsou označeny jako `mdPrivateScope` (najdete v článku [cormethodattr –](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) výčet) nejsou součástí této kontroly; jsou speciálně sloučeny.  
  
    -   Stejné rozložení třídy.  
  
     To znamená, že `TypeDef` objektu musí vždy plně a konzistentně definovat v každé metadata rozsahu ve kterém je deklarována, pokud jeho implementace členů (pro třídu) jsou rozděleny mezi několika kompilačních jednotek, úplná definice se předpokládá se, že k dispozici v každé oboru, ne přírůstková k jednotlivým oborům. Například pokud názvy parametrů jsou relevantní pro kontrakt, se musí emitovat stejným způsobem jako do každé obor; Pokud nejsou relevantní, by neměly být vložen do metadat.  
  
     Výjimkou je, že `TypeDef` , může být označený jako přírůstkové členy `mdPrivateScope`. Na tyto, zjištění `MergeEnd` postupně se přidají do aktuálního oboru bez ohledu na duplicitní položky. Protože kompilátor rozpozná oboru privátní, kompilátor musí být za vynucování pravidel.  
  
-   Relativních virtuálních adres (RVA) nejsou importovány nebo sloučit; Kompilátor by měl znovu vygenerovat tyto informace.  
  
-   Vlastní atributy jsou sloučeny pouze v případě, že se sloučí položku, ke kterému jsou připojené. Například vlastní atributy přidružené třídy jsou sloučeny při prvním výskytu třídy se. Pokud uživatelských atributů, které jsou přidruženy `TypeDef` nebo `MemberDef` , která je specifická pro kompilační jednotky (například časové razítko člen kompilace), nejsou sloučené a je kompilátor odebrat nebo aktualizovat tato metadata.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
