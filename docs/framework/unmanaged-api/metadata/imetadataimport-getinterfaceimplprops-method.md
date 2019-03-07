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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb38c61e8dbd29a0ff87165b5daf49e733b34047
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466541"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps – metoda
Získá ukazatel na tokeny metadat pro <xref:System.Type> zadanou metodu, která implementuje a rozhraní, která deklaruje dané metody.
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iiImpl`  
 [in] Představující metodu vrátit třídu a interface tokeny pro token metadat.  
  
 `pClass`  
 [out] Token metadat představující třídu, která implementuje metodu.  
  
 `ptkIface`  
 [out] Představuje rozhraní, které definuje implementované metody token metadat.  

## <a name="remarks"></a>Poznámky

 Získat hodnotu pro `iImpl` voláním [enuminterfaceimpls –](imetadataimport-enuminterfaceimpls-method.md) metody.
 
 Předpokládejme například, že třída má `mdTypeDef` token hodnota 0x02000007 a implementuje tři rozhraní, jejichž typy mají tokeny: 

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

Obecně tyto informace jsou uloženy do tabulky implementace rozhraní jako:

| Číslo řádku | Token třídy | Token rozhraní |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Odvolat token, který je 4 bajty. hodnota:

- Nižší 3 bajtů obsahovat číslo řádku, nebo identifikátorů RID.
- Horní bajtů obsahuje typ tokenu – 0x09 pro `mdtInterfaceImpl`.

`GetInterfaceImplProps` Vrátí informace uchovávané v řádku, jehož token, který zadáte v `iImpl` argument. 
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
