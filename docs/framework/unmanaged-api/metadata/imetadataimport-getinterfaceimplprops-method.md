---
title: IMetaDataImport::GetInterfaceImplProps – metoda
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: e5eb735acac73d694a0719c206bd22711a8c0333
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437548"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps – metoda
Získá ukazatel na tokeny metadat pro <xref:System.Type>, které implementují zadanou metodu, a pro rozhraní, které deklaruje tuto metodu.
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iiImpl`  
 pro Token metadat představující metodu pro návrat třídy a tokeny rozhraní pro.  
  
 `pClass`  
 mimo Token metadat představující třídu, která implementuje metodu.  
  
 `ptkIface`  
 mimo Token metadat představující rozhraní, které definuje implementovanou metodu.  

## <a name="remarks"></a>Poznámky

 Hodnotu pro `iImpl` získáte zavoláním metody [enuminterfaceimpls –](imetadataimport-enuminterfaceimpls-method.md) .
 
 Předpokládejme například, že třída má hodnotu `mdTypeDef` tokenu 0x02000007 a že implementuje tři rozhraní, jejichž typy mají tokeny: 

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

V koncepčních případech jsou tyto informace uloženy do tabulky implementace rozhraní jako:

| Číslo řádku | Token třídy | Token rozhraní |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Odvolání tokenu je hodnota o velikosti 4 bajty:

- Dolní 3 bajty obsahují číslo řádku nebo identifikátor RID.
- Horní bajt obsahuje typ tokenu – 0x09 pro `mdtInterfaceImpl`.

`GetInterfaceImplProps` vrátí informace uchovávané v řádku, jehož token zadáte v argumentu `iImpl`. 
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
