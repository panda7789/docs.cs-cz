---
title: Element <oidEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: c686d2b99ad66aec753a356b09fa3c7151193808
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674743"
---
# <a name="oidentry-element"></a>\<oidentry – > – Element
Identifikátor objektu (OID) ASN.1 se mapuje na popisný název.  
  
 \<Konfigurace >  
\<mscorlib>  
\<cryptographySettings>  
\<oidMap>  
\<oidEntry>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**OID**|Požadovaný atribut.<br /><br /> Určuje Identifikátor ASN.1 odpovídající algoritmus implementovaný pomocí vaší třídy.|  
|**Jméno**|Požadovaný atribut.<br /><br /> Určuje hodnotu **název** atribut [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) značky.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`cryptographySettings`|Obsahuje nastavení šifrování.|  
|`mscorlib`|Obsahuje `cryptographySettings` elementu.|  
|`oidMap`|Obsahuje ASN.1 objekt identifikátor (OID), mapování na třídy.|  
  
## <a name="remarks"></a>Poznámky  
 Identifikátory objektů ASN.1 identifikovat v některé formáty kryptografické algoritmy. Mapování identifikátorů objektů na popisné názvy algoritmů, které chcete identifikovat.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití  **\<oidentry – >** element namapovat identifikátor objektu pro algoritmus hash RIPEMD 160 implementace algoritmu hash.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Schéma nastavení šifrování](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [Kryptografické služby](../../../../../docs/standard/security/cryptographic-services.md)
- [Konfigurace šifrovacích tříd](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [Mapování identifikátorů objektů na algoritmy šifrování](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
